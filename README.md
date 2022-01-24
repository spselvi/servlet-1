import java.io.*;
import javax.servlet.*;
import javax.servlet.http.*;
public class HelloWorld extends HttpServlet {
 
   private String message;

   public void init() throws ServletException {
      message = "Hello World";
   }

   public void doGet(HttpServletRequest request, HttpServletResponse response)
      throws ServletException, IOException {
      response.setContentType("text/html");
      PrintWriter out = response.getWriter();
      out.println("<h1>" + message + "</h1>");
   }
   public void destroy() {
   }
   }
 web.xml:
   <servlet>
   <servlet-name>HelloWorld</servlet-name>
   <servlet-class>HelloWorld</servlet-class>
   </servlet>
   <servlet-mapping>
   <servlet-name>HelloWorld</servlet-name>
   <url-pattern>/HelloWorld</url-pattern>
   </servlet-mapping>
 DemoServlet.java:
   import javax.servlet.http.*;  
   import javax.servlet.*;  
   import java.io.*;  
   public class DemoServlet extends HttpServlet{  
   public void doGet(HttpServletRequest req,HttpServletResponse res)  
   throws ServletException,IOException  
  {  
   res.setContentType("text/html");  
   PrintWriter pw=res.getWriter();
   pw.println("<html><body>");  
  pw.println("Welcome to servlet");  
  pw.println("</body></html>");  
  pw.close();//closing the stream  
}}
public service method:
public void service(ServletRequest req, ServletResponse res)  
        throws ServletException, IOException  
    {  
        HttpServletRequest request;  
        HttpServletResponse response;  
        try  
        {  
            request = (HttpServletRequest)req;  
            response = (HttpServletResponse)res;  
        }  
        catch(ClassCastException e)  
        {  
            throw new ServletException("non-HTTP request or response");  
        }  
        service(request, response);  
    }  
