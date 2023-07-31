# Servelet

Buliding Sever Side Program
===========================
These programs are responsible to process user/Browser request and generates response/content and sends reponse to the user/browser
These program side program willbe excuted by web server
Every server side program will have ana unique url
we can build these program by using following two technologies...................
1)Services..........
2)JSP(java server pages).....................................................................

Servelets technology
====================
By using this technology we can build dynamic web pages/server side program Code of server side program will be written using java language.We can also use HTML tags in these program .
Class  of these program must implement javax.servelet.servelet interface either directly or indirectly.Classes and interfaces of this technology has beeen built by web server vendors jar file (servlet-api.jar) of these classes and interface must be added into project using build path .

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
Since class of these programs implement serverlet interface that's why these programs are also know as the servlet 
servlet interface has the following 5 method ............................................................

1) public void init (serveltConfig config) :: will be called by once when servlet will be  created object also  created  
2) public void service (serveltRequest req ,sreveletResponse res)
3) public void destroy()

 these above methods are life cycle methods of servlet that will be called by web service 
 =================================================================================
 4)public String getServletInfo()
 5) public ServletConfig getServletConfig()


 The life cycle of Servlet
 =====================
 The life cycle of the servelet is managed by the web server. It has the following 5 phases /states 
 1) Loading servelet: it is done only once before creating an object
 2) Instantiating servlet: an object of the class is created. It is done only once
 3) Initializing servlet: The object is initialized. It is done only once
 4) Invoking service method: It is done each time a user sends a request
 5) Destroying servlet: when the object is destroyed. It is done only once

 Remember activities performed between the construction of the object and the destruction of the object are called the life cycle.
===================================================================================================================

Service() method 
================
Since this method is called by the web server on each request of the user, so request processing code should be written inside this method. We can override it by following the way .........................................................
1) By implementing the Servlet interface.......................
2) By inheriting GenericServlet class: It is an implementation of the servelet interface
3)  By inheriting HttpServlet class: It is a child  of GenericServelet Class

1)first way 
public class DemoServerlet implements Servlet
{
//override all 5 methods here 
}

2) Second Way
public class DemoServerlet extends  GenericServlet
{
//override service method only .you can override other methods also. 
}   

3) Third way
public class DemoServerlet extends  HtttpServlet
{
//override  methods that you want  
}

public void service(ServeletRequest req, HttpServletResponse res): It is a method of Servlet interface ..........

These are methods HttpServlet class...................................
=======================================================================
public void service(HttpServeletRequest req,HttpServletResponse res)
public void doGet(HttpServeletRequest req,HttpServletResponse res)
public void doPost(HttpServeletRequest req,HttpServletResponse res)
public void doPut(HttpServeletRequest req,HttpServletResponse res)
public void doDelete(HttpServeletRequest req,HttpServletResponse res)
etc 

The web server invokes/calls the original service method
========================================================
if the original service method is overridden by the current servlet then it will be executed
If not overridden then the original service method calls the duplicate service method 
If a duplicate service method is overridden by the current servlet then it will be executed
If not overridden then duplicate service method calls together do post or do put or do delete etc method

public void service(HttpServeletRequest req, HttpServletResponse res)
====================================================================
As we see service method is parametrized and we know this method will be called by the web server, so the web server will pass two objects to this method. these objects are as follows 
 
1)Request object
2)Request object

Request object
==============
It is an object of the HttpServletRequest interface. This object is created by the web server before calling the service method. In this object web server stores data coming from the browser(either along with URL or as the body )
If the request method is getting than data will be sent along with URL of the request
If the request method is post then data will be sent along with URL of the request
As we know this data will be stored in request object by the web server and the web server passes the reference of this object to the service method,so the service method can get this
data from the request object
The request object holds data in the map as key-value pair

