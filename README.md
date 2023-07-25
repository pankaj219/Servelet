# Servelet

Buliding Sever Side Program
===========================
These programs are responsible to process user/Browser request and generates response/content and sends reponse to the user/browser
These program side program willbe excuted by web server
Every server side program will have ana unique url
we can build these program by using following two technologies
1)Services
2)JSP(java server pages)

Servelets technology
====================
By using this technology we can build dynamic web pages/server side program Code of server side program will be written using java language.We can also use HTML tags in these program .
Clas  of these program must implement javax.servelet.servelet interface either directly or indirectly.Classes and interfaces of this technology has beeen built by web server vendors jar file (servlet-api.jar) of these classes and interface must be added into project using build path .

1)javax.servlrt.Servlet interface
2)javax.servlrt.GenericServelet class
3)javax.servlrt.ServletRequest interface 
4)javax.servlrt.http.HttpServlet class
5)javax.servlrt.http.HttpServletRequest interface 
6)javax.servlrt.http.HttpServletResponse interface 
7)javax.servlrt.http.HttpSession interface
8)javax.servlrt.ServetResponse inteface 
9)javax.servlrt.ServeltContext interface 


SEVERLET INTERFACE 
==================
Every server side program side program must implement this interface either directly or indirectly 

public class AA implements Servlet
{
//override all method of servlet interface
}
This is an example of server side program 
Since class of these program implement serverlet interface that 's why these program are also know as servelt 
servlet interface has following 5 method 
1) public void init (serveltConfig config) :: will be called by once when servlate will be  created object also  created  
2) public void service (serveltRequest req ,sreveletResponse res)
3) public void destroy()

 these above method are life cycle method of servlet will be called by web service 
 =================================================================================
 4)public String getServletInfo()
 5) public ServletConfig getServletConfig()


 Life cycle of Servlet
 =====================
 Life cycle of servelet is managed by web server .It has following 5 phases /states 
 1) Loading servelet : it is done only once before creating object
 2) Instantiating servlet:object of the class is created .It is done only once
 3) Initializing servlet:Object is initialized .It is done only once
 4) Invoking service method :It is done each time user send request
 5) Destroying servlet:when object is destroyed .It is done only once

 Remember activities performed between contruction of the object and destruction of the object is called life cycle .
===================================================================================================================

Service() method 
================
Since this method is called by web server on each request of user, so request processing code should be written inside thjs method.We can override it by following way 
1) By implemeting Servlet interface
2) By inherting GenericServlet class: It is implememtion of servelet interface
3)  By inheriting HttpServlet class: It is child  of GenericServelet Class

1)first way 
public class DemoServerlet implements Servlet
{
//override all 5 methods here 
}

2) Second Way
public class DemoServerlet extends  GenericServlet
{
//override service method only .you can override other method also. 
}   

3) Third way
public class DemoServerlet extends  HtttpServlet
{
//override  methods that you want  
}

public void service(ServeletRequest req,HttpServletResponse res):It is a method of Servlet inertface 

These are methods HttpServvlet class
public void service(HttpServeletRequest req,HttpServletResponse res)
public void doGet(HttpServeletRequest req,HttpServletResponse res)
public void doPost(HttpServeletRequest req,HttpServletResponse res)
public void doPut(HttpServeletRequest req,HttpServletResponse res)
public void doDelete(HttpServeletRequest req,HttpServletResponse res)
etc 

Web server invokes/calls original service method
if orginal service method is overriden by current servlet than it will be executed
If not overridden than original service method calls duplicate service method 
If duplicate service method is overriden by current servlet than it will be executed
If not overridden than duplicate service method calls dogetor dopost or doput or dodelete etc method

public void service(HttpServeletRequest req,HttpServletResponse res)
====================================================================
 As we see service method is parametrized and we know this method will be called by web server,so web server will pass two objects to this method.these objexts are as follows 
 
1)Request object
2)Request object

Request object
==============
It is an object of HttpServletRequest interface.This object is created by web server before calling the service method .In this object web server stores data coming from 
the browser(either alongwith URL or as body )
If request method is get than data will be sent alongwith url of the request
If request method is post than data will be sent alongwith url of the request
As we know this data will be stored in request object by web server and web server passes reference of this object to the service method ,so service method can get this
data from the request objetc
Request object holds data in map as key-value pair

