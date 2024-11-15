# RESTful Web Services

### Date:

## Aim

To create RESTful web services using both server-side and client-side implementations.

## Procedure

### Server-Side Implementation

1. **Create a New Java Web Project:**
   - Follow steps 1-5 from the SOAP-based Web Services section to set up a new Java Web Project.

2. **Create RESTful Web Services:**
   - Right-click on the project name and select `New` -> `RESTful Web Services from Patterns`.

3. **Configure Resource:**
   - In the new window, select `Simple Root Resource` and click `Next`.
   - Provide a Resource Package name and choose `MIME Type` as `text/html`. Click `Finish`.

4. **Edit Resource:**
   - Two editing tabs will appear. Close `ApplicationConfig.java` and implement the required functionalities in `GenericResource.java`.

5. **Modify Method:**
   - Alter the `getHtml()` method as needed.

6. **Build and Deploy:**
   - Save your project, clean and build it. Deploy your project to the server.

7. **Test Your Web Service:**
   - Open a browser and type the URL `http://localhost:8080/project_name/webresources/generic?params=45&params=35` to test the web service functionality.

### Client-Side Implementation

1. **Create a New Java Web Project:**
   - Follow steps 1-5 from the SOAP-based Web Services section to set up a new Java Web Project.

2. **Create RESTful Java Client:**
   - Right-click on the project and select `New` -> `RESTful Java Client`.

3. **Configure Client:**
   - In the new window, provide a name for your client, a package name, and select `From Project` under the `Select the REST resource:` tab. Click `Browse` and select your RESTful resource. Click `OK`, then `Finish`.

4. **Edit Client Code:**
   - Modify the `getHtml()` method as required.

5. **Add JAR File:**
   - Right-click on the `Libraries` folder under your project and select `Add JAR/Folder`.
   - Navigate to where the `javax.ws.rs-api2.0.1.jar` file is located and add it.

6. **Create JSP Page:**
   - Right-click on the `Web Pages` folder and select `JSP`.
   - Provide a name for the JSP page and click `Finish`.

7. **Include Client Code in JSP:**
   - Edit the JSP page to include the necessary code for invoking the client Java code.

8. **Build and Run:**
   - Save the project, build it, and run the JSP file to see the output in a new browser window.

### Client-Side Remote Invocation (Optional)

1. **Adjust Client Configuration:**
   - Follow steps 1-5 from the Client-Side Implementation.
   - In the generated `NewJerseyClient.java` file, update `BASE_URI` from `private static final String BASE_URI = "http://localhost:8080/RESTful_Server/webresources";` to `private static final String BASE_URI = "http://192.168.116.62:8080/RESTful_Server/webresources";`.

2. **Complete the Remaining Steps:**
   - Follow steps 6-12 from the Client-Side Implementation to finalize and test the remote client.
## Program 

### Genericresource.java
```java
/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package com.example;

import javax.ws.rs.core.Context;
import javax.ws.rs.core.UriInfo;
import javax.ws.rs.Consumes;
import javax.ws.rs.Produces;
import javax.ws.rs.GET;
import javax.ws.rs.Path;
import javax.ws.rs.PUT;

/**
 * REST Web Service
 *
 * @author SEC
 */
@Path("generic")
public class GenericResource {

    @Context
    private UriInfo context;

    /**
     * Creates a new instance of GenericResource
     */
    public GenericResource() {
    }

    /**
     * Retrieves representation of an instance of com.example.GenericResource
     * @return an instance of java.lang.String
     */
    @GET
    @Produces(javax.ws.rs.core.MediaType.TEXT_HTML)
    public String getHtml() {
        //TODO return proper representation object
       return "<html><body><h1>Welcome to the RESTful Web Service</h1><p>This is a simple HTML response created by JAYABHARATHI.</p></body></html>";
    }

    /**
     * PUT method for updating or creating an instance of GenericResource
     * @param content representation for the resource
     */
    @PUT
    @Consumes(javax.ws.rs.core.MediaType.TEXT_HTML)
    public void putHtml(String content) {
    }
}

```

### JerseyClient.java

```java
/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package example.client;

/**
 * Jersey REST client generated for REST resource:GenericResource [generic]<br>
 * USAGE:
 * <pre>
 *        JerseyClient client = new JerseyClient();
 *        Object response = client.XXX(...);
 *        // do whatever with response
 *        client.close();
 * </pre>
 *
 * @author SEC
 */
public class JerseyClient {

    private javax.ws.rs.client.WebTarget webTarget;
    private javax.ws.rs.client.Client client;
    private static final String BASE_URI = "http://localhost:8080/rest-service/webresources";

    public JerseyClient() {
        client = javax.ws.rs.client.ClientBuilder.newClient();
        webTarget = client.target(BASE_URI).path("generic");
    }

    public String getHtml() throws javax.ws.rs.ClientErrorException {
    // Send GET request to retrieve HTML content from the server
    String htmlResponse = webTarget.request(javax.ws.rs.core.MediaType.TEXT_HTML).get(String.class);

    // Return the HTML response as a String
    return htmlResponse;
}

    public void putHtml(Object requestEntity) throws javax.ws.rs.ClientErrorException {
        webTarget.request(javax.ws.rs.core.MediaType.TEXT_HTML).put(javax.ws.rs.client.Entity.entity(requestEntity, javax.ws.rs.core.MediaType.TEXT_HTML));
    }

    public void close() {
        client.close();
    }
    
}

```
# Output

### Server Terminal :
![image](https://github.com/user-attachments/assets/a210b622-aeac-4e67-8dd8-493fbff2589a)

### Output page :
![image](https://github.com/user-attachments/assets/cbdf3e79-3bd2-472c-8e4b-8ef1bdcb822d)

## Result

The implementation of RESTful web services using both server-side and client-side components was successfully created and executed.
