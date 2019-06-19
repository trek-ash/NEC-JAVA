
## Example program 1
``` Java
package hiberanteExample;
import org.hibernate.*;
public class createStudent {

    public static void main(String[] args) {
        // TODO Auto-generated method stub
        student s = new student();
        s.setStudentName("DDD");
        s.setRollNumber(04);
        s.setCourse("LCA");
        SessionFactory sessionFactory = hibernateUtil.getSessionFactory();
        Session session = sessionFactory.openSession();
        session.beginTransaction();

        /*

        CREATE Logic

        session.save(s);
        System.out.println("Inserted Successfully");
        ------------------------------------------------------------------------------

        DISPLAY Logic

        Query query = session.createQuery("from student");
        List<student> stu = query.list();
        for(student stud : stu) {
            System.out.println("\nRoll No" + stud.getRollNumber()+ "\nStudent name :"+stud.getStudentName()
                    +"\nStudent Course :"+stud.getCourse()+"\n----------------------------------------------------");
        }
        --------------------------------------------------------------------------------

        UPDATE Logic

        student stu = (student) session.load(student.class, 02) ;
        stu.setStudentName("Hero Heera lal");
        --------------------------------------------------------------------------------

        DELETE Logic

        student stu = (student) session.load(student.class, 01) ;
        session.delete(stu);
        */
        session.getTransaction().commit();
        session.close();
        sessionFactory.close();
    }

}
```


``` Java
<?xml version='1.0' encoding='utf-8'?>
<!DOCTYPE hibernate-configuration PUBLIC
    "-//Hibernate/Hibernate Configuration DTD//EN"
    "http://www.hibernate.org/dtd/hibernate-configuration-3.0.dtd">
<hibernate-configuration>
  <session-factory>
      <property name="connection.url">jdbc:mysql://localhost:3306/nec</property>
      <property name="connection.driver_class">com.mysql.jdbc.Driver</property>
      <property name="connection.username">shubhesh</property>
      <property name="connection.password">akshita</property>
      <property name="hibernate.dialect">org.hibernate.dialect.MySQL5Dialect</property>
<!--     DB schema will be updated if needed -->
     <property name="hibernate.hbm2ddl.auto">update</property>
<!--       Disable the second level cache -->

      <mapping class="hiberanteExample.student"/>
  </session-factory>
</hibernate-configuration>
```


``` Java
package hiberanteExample;
import java.io.Serializable;
import javax.persistence.*;
@Entity
@Table(name="STUDENT")

public class student implements Serializable {
    private static final long serialVersionUID = 8633415090390966715L;
    @Id
    @Column(name="ID")
    @GeneratedValue(strategy=GenerationType.IDENTITY)
    private int id;
    @Column(name="STUDENT_NAME")
    private String studentName;
    @Column(name="ROLL_NUMBER")
    private int rollNumber;
    @Column(name="Course")
    private String course;
    public int getId(){
        return id;
    }
    public void setId(int id){
        this.id=id;
    }
    public String getStudentName(){
        return studentName;
    }
    public void setStudentName(String studentName){
        this.studentName=studentName;
    }
    public int getRollNumber(){
        return rollNumber;
    }
    public void setRollNumber(int rollNumber){
        this.rollNumber=rollNumber;
    }
    public String getCourse(){
        return course;
    }
    public void setCourse(String course){
        this.course=course;
    }

}
```


``` Java
package hiberanteExample;

import org.hibernate.*;
import org.hibernate.boot.MetadataSources;
import org.hibernate.boot.registry.StandardServiceRegistry;
import org.hibernate.boot.registry.StandardServiceRegistryBuilder;

public class hibernateUtil {
    final static StandardServiceRegistry registry = new StandardServiceRegistryBuilder().configure().build();
    private static SessionFactory sessionFactory = null;
    private static SessionFactory buildSessionFactory(){
        try{
            sessionFactory = new MetadataSources(registry).buildMetadata().buildSessionFactory();
            return sessionFactory;
        }
        catch(Exception e){
            StandardServiceRegistryBuilder.destroy(registry);
            throw new ExceptionInInitializerError(e);
        }
    }
    public static SessionFactory getSessionFactory(){
        if(sessionFactory==null){
            buildSessionFactory();
        }
        return sessionFactory;
    }
}

```

