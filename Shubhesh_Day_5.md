
## Example program 1
``` Jsp
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
    pageEncoding="ISO-8859-1" import="java.util.*,java.io.*"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1">
<title>Example</title>
</head>
<body>
<% Date now = new Date(); %>
<h2>Server date and time is
<%=now %>
</body>
</html>
```


## Example program 2
``` Jsp
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
    pageEncoding="ISO-8859-1"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1">
<title>Insert title here</title>
</head>
<body>
<h2>This is index page</h2>
  <jsp:forward page="Main.jsp"/>
</body>
</html>
```


``` Jsp
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
    pageEncoding="ISO-8859-1"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1">
<title>Insert title here</title>
</head>
<body>
<h1>Read from data</h1>
<ul>
<li><p><b>First Name:</b>
<%=request.getParameter("fname") %>
</p></li>
<li><p><b>Last Name:</b>
<%=request.getParameter("lname") %>
</p>
</li></ul>
</body>
</html>
```


``` HTML
<!DOCTYPE html>
<html>
<head>
<meta charset="ISO-8859-1">
<title>Insert title here</title>
</head>
<body>
<h1>This is your company site</h1>
</body>
</html>
```


``` HTML
<!DOCTYPE html>
<html>
<head>
<meta charset="ISO-8859-1">
<title>Insert title here</title>
</head>
<body>
<form action="Main.jsp">
<br>First name:<input type="text" name="fname">
<br>Last name:<input type="text" name="lname">
<br><input type="submit" value="submit">
</form>
</body>
</html>
```


``` JSP
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
    pageEncoding="ISO-8859-1"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1">
<title>Insert title here</title>
</head>
<body>
<%@ include file="Header.html" %>
Today is:<%=java.util.Calendar.getInstance().getTime() %>
</body>
</html>
```


## Example program 3
``` Jsp
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
    pageEncoding="ISO-8859-1"%>
<%@ page errorPage="errorpage.jsp" %>

<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1">
<title>UseSession</title>
</head>
<body>
<%
//Try and get the currrent count from session integer count
Integer count=(Integer)session.getAttribute("COUNT");
if(count == null){
	count=new Integer(1);
	session.setAttribute("COUNT",count);
}
else{
	count=new Integer(count.intValue() + 1);
	session.setAttribute("count",count);
}
out.println("<b>Hello you have visited the site: "+count+"times.</b>");
%>
</body>
</html>
```


## Example program 4
``` Java


import java.io.IOException;
import java.io.PrintWriter;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

/**
 * Servlet implementation class LoginServlet
 */
@WebServlet("/LoginServlet")
public class LoginServlet extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
    /**
     * @see HttpServlet#HttpServlet()
     */
    public LoginServlet() {
        super();
        // TODO Auto-generated constructor stub
    }

	/**
	 * @see HttpServlet#doGet(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		response.getWriter().append("Served at: ").append(request.getContextPath());
	}

	/**
	 * @see HttpServlet#doPost(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		response.setContentType("text/html");
		PrintWriter out = response.getWriter();
		
		String n = request.getParameter("username");
		String p = request.getParameter("userpass");
		if(n.equals("NEC")&& p.equals("nec"))
			out.print("Welcome "+n);
		else
			out.print("Wrong username or password.");
		//doGet(request, response);
	}

}

```


``` HTML
<!DOCTYPE html>
<html>
<head>
<meta charset="ISO-8859-1">
<title>Insert title here</title>
</head>
<body>
<form action="LoginServlet" method="post">
Name:<input type="text" name="username"/><br/><br/>
Password:<input type="password" name="userpass"/><br><br>
<input type="submit" value="login"/>
</form>
</body>
</html>
```


## Example program 5
``` Java
//import java.beans.Statement;
import java.sql.*;

public class Hello {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		try{
			Class.forName("oracle.jdbc.driver.OracleDriver");
			Connection con=DriverManager.getConnection("jdbc:oracle:thin:@localhost:1521:orcl", "hr", "hr");
			Statement st = con.createStatement();
			ResultSet rs = st.executeQuery("select * from EmpTbl");
			while(rs.next())
				System.out.println(rs.getInt(1)+" "+rs.getString(2)+" "+rs.getInt(3));
			con.close();
				
			}catch(Exception e){
			System.out.println(e);
		}

	}

}

```


``` Java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.Statement;

public class OracleCon {

	public static void main(String[] args)  throws Exception{
		Class.forName("oracle.jdbc.driver.OracleDriver");
		Connection con=DriverManager.getConnection("jdbc:oracle:thin:@localhost:1521:orcl", "hr", "hr");
		Statement st = con.createStatement();
		//st.executeUpdate("insert into EmpTbl values(33,'Emp3',50000)");
		//int result = st.executeUpdate("update EmpTbl set name='Emp4',salary=70000 where id=33");
		int result = st.executeUpdate("delete from EmpTbl where id=33");
		System.out.println(result+"records affected");
		//ResultSet rs = st.executeQuery("select * from EmpTbl");
		System.out.println("records affected");
		con.close();
		// TODO Auto-generated method stub

	}

}

```


## Example program 6
``` HTML
<!DOCTYPE html>
<html>
<head>
<meta charset="ISO-8859-1">
<title>Register</title>
</head>
<body>
<h2>Register</h2>
<table border=1>
<tr>
<td> <form method="post" action="Register">
First name:<input type="text" name="fname"/>
Last name:<input type="text" name="lname"/>
<input type=submit></form>
</td>
</tr>
</table>
</body>
</html>




```


``` Java


import java.io.IOException;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

/**
 * Servlet implementation class Register
 */
@WebServlet("/Register")
public class Register extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
    /**
     * @see HttpServlet#HttpServlet()
     */
    public Register() {
        super();
        // TODO Auto-generated constructor stub
    }

	/**
	 * @see HttpServlet#doGet(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		response.getWriter().append("Served at: ").append(request.getContextPath());
	}

	/**
	 * @see HttpServlet#doPost(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		//doGet(request, response);
		String fname=request.getParameter("fname");
		String lname=request.getParameter("lname");
		if((fname!=null && fname.trim().length()!=0)&&(lname!=null && lname.trim().length()!=0))
		{
			request.getRequestDispatcher("Success").forward(request,response);
		}
		else{
			request.setAttribute("errorattr", "first name or last name not entered");
			request.getRequestDispatcher("Error").include(request, response);
			request.getRequestDispatcher("index.html").include(request, response);
		}
	}

}

```


``` Java


import java.io.IOException;
import java.io.PrintWriter;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

/**
 * Servlet implementation class Success
 */
@WebServlet("/Success")
public class Success extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
    /**
     * @see HttpServlet#HttpServlet()
     */
    public Success() {
        super();
        // TODO Auto-generated constructor stub
    }

	/**
	 * @see HttpServlet#doGet(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		response.getWriter().append("Served at: ").append(request.getContextPath());
	}

	/**
	 * @see HttpServlet#doPost(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		response.setContentType("text/html");
		PrintWriter out = response.getWriter();
		out.println("<html><head><title>Success</title>");
		out.println("</head><body>");
		out.println("Thanks <I>"+request.getParameter("fname")+"</I>");
		out.println("</body></html>");
		//doGet(request, response);
	}

}

```


``` Java


import java.io.IOException;
import java.io.PrintWriter;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

/**
 * Servlet implementation class Error
 */
@WebServlet("/Error")
public class Error extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
    /**
     * @see HttpServlet#HttpServlet()
     */
    public Error() {
        super();
        // TODO Auto-generated constructor stub
    }

	/**
	 * @see HttpServlet#doGet(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		response.getWriter().append("Served at: ").append(request.getContextPath());
	}

	/**
	 * @see HttpServlet#doPost(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		PrintWriter out = response.getWriter();
		response.setContentType("text/html");
		out.println("<html><head><title>login</title></head>");
		out.println("<body><font color=red><b>");
		String err = (String)request.getAttribute("errorattr");
		if(err!=null)
		{
			out.println(err);
		}
		out.println("</font><b><br></body></html>");
		//doGet(request, response);
	}

}

```

