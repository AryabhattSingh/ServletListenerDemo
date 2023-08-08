# ServletListenerDemo

This Java project demonstrates the usage of Servlet Listeners in a web application. Servlet Listeners allow our application to react to specific 
events that occur within the web container. This project illustrates how to create and implement a simple listener `ServletRequestListener`

## Overview

Servlet Listeners play a crucial role in enabling a web application to respond to events triggered by the web container. These events can include:

- Request creation and destruction.
- User session creation or destruction.
- Web application loading or unloading (context-level events).
- Asynchronous events like `onComplete` and `onStart`.

In this project, you will find examples of how to create and utilize listeners to perform actions in response to these events.

## Getting Started

To create custom listeners, you will need to implement corresponding listener interfaces. For example:

- To count the number of active users in a session, implement the `HttpSessionListener` interface by overriding its methods. Here's an example:

  ```java
  import javax.servlet.annotation.WebListener;
  import javax.servlet.http.HttpSessionEvent;
  import javax.servlet.http.HttpSessionListener;

  @WebListener
  public class UserCountListener implements HttpSessionListener {
      // Override methods to handle session events
  }
  ```

- For request-level events, you can implement the `ServletRequestListener` interface. We will be implementing this in our code.
  ```java
  import javax.servlet.ServletRequestEvent;
  import javax.servlet.ServletRequestListener;
  import javax.servlet.annotation.WebListener;

  @WebListener
  public class UserCountListener implements ServiceRequestListener {
      // Override methods to handle/receive notification events about requests coming into and
      // going out of the scope of a web application
  }
  ```

### Configuring Listeners

To inform the web container about the implemented listeners, you can use annotations or configure them in the `web.xml` file.

Using annotations:

```java
import javax.servlet.annotation.WebListener;

@WebListener
public class UserCountListener implements HttpSessionListener {
    // Listener implementation
}
```

Using `web.xml`:

```xml
<listener>
    <listener-class>UserCountListener</listener-class>
</listener>
```

## Creating Listeners in Eclipse

Here's how you can create listeners in the Eclipse IDE:

1. Right-click on the `src` folder of your project.
2. Select `New` -> `Other`.
3. In the dialog box, type `Listener`. You will find "Listener" inside the `Web folder` in the wizard.
4. Select "Listener" and click `Next`.
5. Provide a package name and class name for the listener.
6. Click `Next`.
7. In the `Create Listener dialog box`, select the type of listener you want to create.  We are interested in `Service Request Events`.
8. Check the `Lifecycle checkbox`.
9. Click `Finish`.

Eclipse will generate the necessary listener class with methods like `requestDestroyed()` and `requestInitialized()`. These methods will be called by the web container
(e.g., Tomcat) when request and response objects are created.

## Usage

This project serves as a reference for understanding and implementing Servlet Listeners. You can use the examples provided here as a starting point for integrating listeners
into your own web applications to handle various events effectively.
