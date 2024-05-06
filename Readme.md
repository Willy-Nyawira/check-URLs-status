## Description:
The URL Checker is a simple Spring Boot application that allows users to check whether a given URL is up or down. It provides a RESTful API endpoint /check where users can pass a URL as a query parameter, and the application will respond with a message indicating whether the site is up or down.

## Code

/* package demo.isthesiteup.controllers;

import java.io.IOException;
import java.net.HttpURLConnection;
import java.net.MalformedURLException;
import java.net.URL;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class URLCheckerController {
    // Constants for response messages
    private final String SITE_IS_UP = "Site is up!";
    private final String SITE_IS_DOWN = "Site is down!";
    private final String INCORRECT_URL = "URL is incorrect!";

    // Mapping for GET request to /check endpoint with URL parameter
    @GetMapping("/check")
    public String getUrlMessageStatus(@RequestParam String url) {
        String returnMessage = ""; // Initialize return message variable
        try {
            URL urlObj = new URL(url); // Create URL object from the provided URL
            HttpURLConnection conn = (HttpURLConnection) urlObj.openConnection(); // Open HTTP connection to the URL
            conn.setRequestMethod("GET"); // Set request method to GET
            conn.connect(); // Connect to the URL
            int responseCode = conn.getResponseCode(); // Get HTTP response code
            // Determine if the response code indicates success (2xx)
            if (responseCode >= 200 && responseCode < 300) {
                returnMessage = SITE_IS_UP; // Set return message to "Site is up!"
            } else {
                returnMessage = SITE_IS_DOWN; // Set return message to "Site is down!"
            }
        } catch (MalformedURLException e) { // Catch exception for malformed URL
            returnMessage = INCORRECT_URL; // Set return message to "URL is incorrect!"
        } catch (IOException e) { // Catch exception for IO errors (e.g., site unreachable)
            returnMessage = SITE_IS_DOWN; // Set return message to "Site is down!"
        }
        return returnMessage; // Return the determined message
    }
}
*/

## Explanation
Package Declaration: The code is declared within the package demo.isthesiteup.controllers. Packages are used for organizing related classes. In this case, it's likely part of a larger Spring Boot application.
Imports: The necessary classes from Java and Spring Framework are imported. These classes provide functionality for handling URLs, making HTTP connections, and defining RESTful web services.
Controller Annotation: @RestController annotation is used to indicate that this class serves as a RESTful controller. It's part of the Spring Web framework and simplifies the creation of RESTful web services.
Constants: Three constant strings are defined to represent different states of the URL: SITE_IS_UP, SITE_IS_DOWN, and INCORRECT_URL. These will be used to provide consistent responses to clients.
Mapping Annotation: @GetMapping("/check") annotation is used to map HTTP GET requests to the /check endpoint. When a GET request is made to this endpoint, the getUrlMessageStatus method will be invoked.
Method Definition: The getUrlMessageStatus method is defined to handle GET requests to the /check endpoint. It accepts a URL parameter provided as a query parameter in the request.
Method Body: Inside the method, a try-catch block is used to handle exceptions that may occur during the URL checking process. Within the try block:
A URL object is created from the provided URL string.
An HTTP connection is opened to the URL using HttpURLConnection.
The request method is set to GET, and the connection is established.
The HTTP response code is retrieved.
Based on the response code, the appropriate message (SITE_IS_UP or SITE_IS_DOWN) is assigned to the returnMessage variable.
Exception Handling: Two types of exceptions are caught:
MalformedURLException: If the provided URL is malformed, indicating an incorrect URL format.
IOException: If an IO error occurs during the connection attempt, indicating that the site may be unreachable.
Return Statement: Finally, the method returns the determined returnMessage, which indicates whether the site is up, down, or if the URL is incorrect.
Usage:

## Run the Spring Boot application.
Access the /check endpoint with a URL query parameter to check the status of the site.
Example: http://localhost:8080/check?url=https://example.com
## Dependencies:

 Spring Boot: Provides the framework for building the application.
 Java.net: Used for creating URL objects and making HTTP connections.
 Java.io: Used for handling IOExceptions.