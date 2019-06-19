
## Example program 1
``` Java
package com.springcore;
import org.springframework.beans.factory.BeanFactory;
import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;

public class MainApp {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		ApplicationContext context = new ClassPathXmlApplicationContext("Beans.xml");
		BeanFactory factory = context;
		HelloWorld obj = (HelloWorld)factory.getBean("idhello");
		//HelloWorld obj = (HelloWorld)context.getBean("idhello");
		obj.getMessage();

	}

}

```


``` Java
package com.springcore;

import org.springframework.beans.factory.BeanFactory;
import org.springframework.beans.factory.xml.XmlBeanFactory;
import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;
import org.springframework.core.io.*;

public class MainApp1 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		ApplicationContext context = new ClassPathXmlApplicationContext("Beans.xml");
		
		Resource resource = new ClassPathResource("Beans.xml");
		  BeanFactory factory=new XmlBeanFactory(resource);
		
		HelloWorld obj = (HelloWorld)context.getBean("idhello");
		obj.getMessage();

	}

}

```


``` Java
package com.springcore;

public class HelloWorld {
	public String message;

	public void setMessage(String message) {
		this.message = message;
	}
	public void getMessage() {
		System.out.println("Your message : " + message);
	}
}

```


``` Java
<?xml version="1.0" encoding="UTF-8"?>
<beans
xmlns="http://www.springframework.org/schema/beans"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="http://www.springframework.org/schema/beans
http://www.springframework.org/schema/beans/spring-beans-3.0.xsd">

<bean id="idhello"
class="com.springcore.HelloWorld">

<property name="message" value="Hello World!!"/>
</bean>
</beans>
```


## Example program 2
``` Java
package com.springcore;

public class Coffee implements IHotDring{

	@Override
	public void prepareHotDring() {
		// TODO Auto-generated method stub
		System.out.println("Dear customer, we are preparing coffee for you!!");
		
	}
	
}

```


``` Java
<?xml version="1.0" encoding="UTF-8"?>
<beans
xmlns="http://www.springframework.org/schema/beans"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="http://www.springframework.org/schema/beans
http://www.springframework.org/schema/beans/spring-beans-3.0.xsd">

<bean id="restaurantBean"
class="com.springcore.Restaurant" init-method="init" destroy-method="destroy">
<constructor-arg ref = "coffeeBean"/>
</bean>

<bean id="teaBean"
class="com.springcore.Tea">
</bean>

<bean id="coffeeBean"
class="com.springcore.Coffee">
</bean>

</beans>
```


``` Java
package com.springcore;
public interface IHotDring {
	public void prepareHotDring();
}

```


``` Java
package com.springcore;

public class Tea implements IHotDring{

	@Override
	public void prepareHotDring() {
		// TODO Auto-generated method stub
		System.out.println("Dear customer, we are preparing tea for you!!");
		
	}
	
}

```


``` Java
package com.springcore;

public class Restaurant {
	IHotDring hotDring;
	public Restaurant(IHotDring hotDring){
		this.hotDring = hotDring;
	}
	public void prepareHotDring(){
		hotDring.prepareHotDring();
	}
	
	public void init(){
		System.out.println("INIT");
	}
	
	public void destroy(){
		System.out.println("DESTROY");
	}
}

```


``` Java
package com.springcore;
import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;

public class TestSpringProject {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		ApplicationContext context = new ClassPathXmlApplicationContext("SpringConfig.xml");
		
		Restaurant restaurantObj = (Restaurant)context.getBean("restaurantBean");
		restaurantObj.prepareHotDring();

	}

}

```


## Example program 3
``` Java
<?xml version="1.0" encoding="UTF-8"?>
<beans
xmlns="http://www.springframework.org/schema/beans"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xmlns:p="http://www.springframework.org/schema/p"
xsi:schemaLocation="http://www.springframework.org/schema/beans
http://www.springframework.org/schema/beans/spring-beans-3.0.xsd">

<bean id="ds"
class="org.springframework.jdbc.datasource.DriverManagerDataSource">
<property name="driverClassName" value="oracle.jdbc.driver.OracleDriver"/>
<property name="url" value="jdbc:oracle:thin:@localhost:1521:orcl"/>
<property name="username" value="hr"/>
<property name="password" value="hr"/>
</bean>

<bean id="jdbcTemplate"
class="org.springframework.jdbc.core.JdbcTemplate">
<property name ="dataSource" ref="ds"></property>
</bean>

<bean id="edao" class="com.jdbc.EmpTblDao">
<property name ="jdbcTemplate" ref="jdbcTemplate"></property>
</bean>

</beans>
```


``` Java
package com.jdbc;
public class EmpTbl {
	private int id;
	private String name;
	private float salary;
	public EmpTbl(){
		
	}
    public EmpTbl(int id,String name,float salary){
		this.id=id;
		this.name=name;
		this.salary=salary;
	}
	public int getId() {
		return id;
	}
	public void setId(int id) {
		this.id = id;
	}
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	public float getSalary() {
		return salary;
	}
	public void setSalary(float salary) {
		this.salary = salary;
	}
	public String toString(){
		return id+" "+name+" "+salary;
	}

}

```


``` Java
package com.jdbc;
import java.sql.*;
import java.util.*;

import org.springframework.dao.DataAccessException;
import org.springframework.jdbc.core.JdbcTemplate;
import org.springframework.jdbc.core.ResultSetExtractor;

import com.sun.xml.internal.bind.v2.schemagen.xmlschema.List;

public class EmpTblDao {
	private JdbcTemplate jdbcTemplate;
	public void setJdbcTemplate(JdbcTemplate jdbcTemplate){
		this.jdbcTemplate=jdbcTemplate;
	}
	public int saveEmpTbl(EmpTbl e){
		String query="insert into EmpTbl values("+e.getId()+",'"+e.getName()+"',"+e.getSalary()+")";
		return jdbcTemplate.update(query);
	}
	public int updateEmpTbl(EmpTbl e){
		String query="update EmpTbl set name= '"+e.getName()+"',salary="+e.getSalary()+"where id="+e.getId()+" ";
		return jdbcTemplate.update(query);
	}
	public int deleteEmpTbl(EmpTbl e){
		String query="delete from EmpTbl where id= "+e.getId()+" ";
		return jdbcTemplate.update(query);
	}
	
	public List getAllEmpTbls(){
		return jdbcTemplate.query("select * from EmpTbl", new ResultSetExtractor<List>(){
			@Override
			public List<EmpTbl> extractData(ResultSet rs) throws SQLException, DataAccessException {
				List<EmpTbl> list = new ArrayList<EmpTbl>();
				while(rs.next()){
					EmpTbl e = new EmpTbl();
					e.setId(rs.getInt(1));
					e.setName(rs.getString(2));
					e.setSalary(rs.getInt(3));
					list.add(e);
				}
				return list;
			}
		});
	}
}

```


``` Java
package com.jdbc;

import java.util.List;

import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;

//import com.sun.xml.internal.bind.v2.schemagen.xmlschema.List;

public class Test {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		ApplicationContext ctx=new ClassPathXmlApplicationContext("applicationContext.xml");
		EmpTblDao dao = (EmpTblDao)ctx.getBean("edao");
		//int status = dao.saveEmpTbl(new EmpTbl(103,"Surbhi",50000));
		//System.out.println(status);
		
		List<EmpTbl> list = dao.getAllEmpTbls();
		for(EmpTbl e:list)
			System.out.println(e);
		
	}

}

```

