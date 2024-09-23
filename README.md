### **Rest Booking Performance Testing with JMeter**
This project demonstrates Performance testing using JMeter, providing a collection of tests to validate various endpoints of the Performance. 

### **Features**

- Tests for GET, POST, PUT, DELETE requests
- Collection of tests covering different tests
- Environment setup for easy switching between environments
- Pre-request scripts for data setup
- Test scripts for assertions and validations

  
### **Technology used:**
- JMeter


### **Prerequisite:**
- Node Js
- JMeter
- Java JRE or JDK Installation (Requires Java 8+)

### **Installation**

1. JMeter: If you haven't already, [download JDK file (https://www.oracle.com/tr/java/technologies/javase-downloads.html))]
2. Download: latest release of JMeter (Binaries -> zip extension) and unzip file.
 ```console 
[(https://jmeter.apache.org/)]
```
3. collection:
    - Open Postman.
    - Click on the Import button.
    - Select the file from the repository.
4. Import the Postman environment:
    - In Postman, click on the gear icon in the top right corner.
    - Select **Import** and choose the file.
5. JMeter  Installation Process:
    -plugins-manager.jar and put it into JMeter's lib/ext directory, then restart JMeter.
    - https://jmeter-plugins.org/install/Install/
   
### **Usage**
1. Select Environment:
    -   Start bin/jmeter.sh on MacOS or bin/jmeter.bat file Windows OS.
    -   Open PerformanceTestScenarios.jmx file from Jmeter GUI
    -  Use Thread Group to set your virtual user load and test time
    -   Select the desired listeners.
    -   Start your test and view Test Results on listeners (View Results Tree, Aggregate Graph, ...)

8. View Results:
    -   Once the tests are complete, view the results in the View Results tree
    -   Detailed test results can be viewed for each request.

## **Testing**

## Test Case Scenarios:

## _**1. Create New Booking**_

### Request URL: https://restful-booker.herokuapp.com/booking/
### Request Method: POST
### Pre-request Script:
```console 
    var firstname = pm.variables.replaceIn("{{$randomFirstName}}");
pm.environment.set("firstname",firstname)

var lastname = pm.variables.replaceIn("{{$randomLastName}}");
pm.environment.set("lastname", lastname)

var totalprice = pm.variables.replaceIn("{{$randomInt}}");
pm.environment.set("totalprice",totalprice)

var depositpaid = pm.variables.replaceIn("{{$randomBoolean}}");
pm.environment.set("depositpaid",depositpaid)

//moment for checkin and checkout
const moment =require("moment");
const today = moment()

pm.environment.set("checkin",today.format ("YYYY-MM-DD"));
pm.environment.set("checkout",today.format ("YYYY-MM-DD"));

var additionalneeds = pm.variables.replaceIn("{{$randomProduct}}");
pm.environment.set("additionalneeds",additionalneeds)



    
  **Request Body:** 
 ```console 
  { "bookingid": 278,
    "booking":
	  "firstname" : "{{firstName}}",
	  "lastname" : "{{lastName}}",
	  "totalprice" : {{totalPrice}},
	  "depositpaid" : {{depositPaid}},
	  "bookingdates" : {
    	  "checkin" : "{{checkin}}",
    	  "checkout" : "{{checkout}}"
	  },
	  "additionalneeds" : "{{additionalNeeds}}"
  }
```
  **Response Body:**
 ```console 
 {
    "bookingid": 278,
    "booking": {
        "firstname": "Sally",
        "lastname": "Brown",
        "totalprice": 111,
        "depositpaid": true,
        "bookingdates": {
            "checkin": "2013-02-23",
            "checkout": "2014-10-23"
        },
        "additionalneeds": "Breakfast"
    }
}
```
 ## _**2. Get Booking Details By ID**_
### Request URL: https://restful-booker.herokuapp.com/booking/bookingid
### Request Method: GET
### Response Body:
 ```console 
{
    "firstname": "Sally",
    "lastname": "Brown",
    "totalprice": 111,
    "depositpaid": true,
    "bookingdates": {
        "checkin": "2013-02-23",
        "checkout": "2014-10-23"
    },
    "additionalneeds": "Breakfast"
}
```
## _**3. Create A Token For Authentication.**_
### Request URL: https://restful-booker.herokuapp.com/auth
### Request Method: POST
### Pre-request Script: None
### Request Body:
 ```console 
{
	"username": "admin",
	"password": "password123"
}
```
  **Response Body:**
 ```console 
{
    "token": "468e2fae49c9db8"
}
```

 ## _**4. Update the Booking Details**_
### Request URL: https://restful-booker.herokuapp.com/booking/bookingid
### Request Method: PUT
### Pre-request Script:
```console 
   var firstname = pm.variables.replaceIn("{{$randomFirstName}}");
pm.environment.set("firstname",firstname)

var lastname = pm.variables.replaceIn("{{$randomLastName}}");
pm.environment.set("lastname", lastname)

var totalprice = pm.variables.replaceIn("{{$randomInt}}");
pm.environment.set("totalprice",totalprice)

var depositpaid = pm.variables.replaceIn("{{$randomBoolean}}");
pm.environment.set("depositpaid",depositpaid)

//moment for checkin and checkout
const moment =require("moment");
const today = moment()

pm.environment.set("checkin",today.format ("YYYY-MM-DD"));
pm.environment.set("checkout",today.format ("YYYY-MM-DD"));

var additionalneeds = pm.variables.replaceIn("{{$randomProduct}}");
pm.environment.set("additionalneeds",additionalneeds)
  
  **Request Body:** 
 ```console 
  {
	  "firstname" : "{{firstName}}",
	  "lastname" : "{{lastName}}",
	  "totalprice" : {{totalPrice}},
	  "depositpaid" : {{depositPaid}},
	  "bookingdates" : {
    	  "checkin" : "{{checkin}}",
    	  "checkout" : "{{checkout}}"
	  },
	  "additionalneeds" : "{{additionalNeeds}}"
  }
```
  **Response Body:**
 ```console 
 {
    "firstname": "James",
    "lastname": "Brown",
    "totalprice": 111,
    "depositpaid": true,
    "bookingdates": {
        "checkin": "2018-01-01",
        "checkout": "2019-01-01"
    },
    "additionalneeds": "Breakfast"
}
```

 ## _**5. Delete Booking Record**_

### Request URL: https://restful-booker.herokuapp.com/booking/bookingid
### Request Method: DELETE
### Response Body: Created



## Newman Report Summary:
![1]

