## Project Overview

We'll look at two comparable cases. The first example is demonstrated in the accompanying figure.
![enter image description here](https://i.postimg.cc/GtxDdxPF/ESP32-ESP8266-HTML-Form-Input-Data-Project-Overview.webp)

You can visit a web page with three input fields using any networked browser. Your ESP will update a variable with the new value when you enter a new value and click the "Submit" button.

Later on, we'll also demonstrate how to access such variables as well as permanently preserve them using SPIFFS. Here is how the second illustration functions.
![enter image description here](https://i.postimg.cc/kgpbJ4Sp/ESP32-ESP8266-HTML-Form-Input-Data-Project-Overview-SPIFFS.webp)

This web page allows you to enter three types of variables: String, Int and Float. Then, every time you submit a new value, that value is stored in a SPIFFS file. This web page also contains a placeholder to show the current values.
## Prerequisites
### 1. Install ESP32/ESP8266 Board in Arduino IDE

We’ll program the ESP32 and ESP8266 using Arduino IDE. So, you must have the ESP32 or ESP8266 add-on installed. Follow one of the next tutorials to install the ESP add-on:

-   [Installing ESP32 Board in Arduino IDE (Windows, Mac OS X, Linux)]
-   [Installing ESP8266 Board in Arduino IDE (Windows, Mac OS X, Linux)]
### . Installing Libraries

To build the asynchronous web server, you need to install these libraries.

-   **ESP32:** install the [ESPAsyncWebServer](https://github.com/me-no-dev/ESPAsyncWebServer) and the [AsyncTCP](https://github.com/me-no-dev/AsyncTCP) libraries.
-   **ESP8266:**  install the [ESPAsyncWebServer](https://github.com/me-no-dev/ESPAsyncWebServer) and the [ESPAsyncTCP](https://github.com/me-no-dev/ESPAsyncTCP) libraries.

### How the code works

Let’s take a quick look at the code and see how it works.

#### Including libraries

First, include the necessary libraries. You include different libraries depending on the board you’re using. If you’re using an ESP32, the code loads the following libraries:

    #include <WiFi.h>  
    #include <AsyncTCP.h> 
    #include <ESPAsyncWebServer.h>
    
#### Network credentials

Don’t forget to insert your network credentials in the following variables, so that the ESP32 or ESP8266 can connect to your network.

    const  char* ssid =  "REPLACE_WITH_YOUR_SSID";  
    const  char* password =  "REPLACE_WITH_YOUR_PASSWORD";

#### HTML Forms and Input Fields

First, let’s take a look at the HTML that we need to display the input fields.

In our example, we display three input fields and each field has a “Submit” button. When the user enters data and presses the “Submit” button, that value is sent to the ESP and updates the variable.

For that, create three forms:

    <form action="/get"> 
    input1: <input type="text" name="input1"> 
    <input type="submit" value="Submit">  
    </form>
    <br>  
    <form action="/get"> 
    input2: <input type="text" name="input2">  
    <input type="submit" value="Submit">  
    </form>
    <br>  
    <form action="/get"> 
    input3: <input type="text" name="input3"> 
    <input type="submit" value="Submit">  </form>
    
In HTML, the `<form>` tag is used to create an HTML form for user input. In our case, the form should contain an input field and a submit button.

![enter image description here](https://i.postimg.cc/jSKsNTK3/input-web-browser-2.webp)
