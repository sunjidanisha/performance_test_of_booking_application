### **Rest Booking API Testing with Postman Newman**
This project demonstrates API testing using Postman, providing a collection of tests to validate various endpoints of the API. 

### **Features**

- Tests for GET, POST, PUT, DELETE requests
- Collection of tests covering different API endpoints
- Environment setup for easy switching between environments
- Pre-request scripts for data setup
- Test scripts for assertions and validations

## API Documentation:
- https://documenter.getpostman.com/view/33497181/2sA35EZNDy
  
### **Technology used:**
- Postman
- Newman

### **Prerequisite:**
- Node Js
- Newman
- Newman Html Report Library

### **Installation**

1. Postman: If you haven't already, [download and install Postman.](https://www.postman.com/downloads/)
2. Clone the repository:
 ```console 
  git clone https://github.com/ebrahimhossaincse/Automated-Testing-of-Rest-Booking-API-with-Newman-Report.git
```
3. Import the Postman collection:
    - Open Postman.
    - Click on the Import button.
    - Select the file from the repository.
4. Import the Postman environment:
    - In Postman, click on the gear icon in the top right corner.
    - Select **Import** and choose the file.
5. Newman and Report Installation Process:
    - Newman Install Command:
     ```console 
      npm install -g newman
    ```
    - Newman Html Report Install Command:
     ```console 
      npm install -g newman-reporter-htmlextra
    ```
### **Usage**
1. Select Environment:
    -   In Postman, select the appropriate environment (e.g., Development, Production) from the top-right dropdown.
3. Run Collection:
    -   Select the imported collection from the Collections sidebar.
    -   Click on the Runner button to open the collection runner.
    -   Select the desired environment.
    -   Click Start Test to run the collection.
8. View Results:
    -   Once the tests are complete, view the results in the Runner tab.
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
![1](https://github.com/sunjidanisha/Automated-Testing-of-Rest-Booking-API-with-Newman-Report/assets/78694676/e56b9032-6653-4d78-817d-3be03053bf51)
![2](https://github.com/sunjidanisha/Automated-Testing-of-Rest-Booking-API-with-Newman-Report/assets/78694676/2a8b27c9-e291-4799-b70a-ca3c15e3c269)
![3](https://github.com/sunjidanisha/Automated-Testing-of-Rest-Booking-API-with-Newman-Report/assets/78694676/baa2a550-6527-43b4-8b4e-2bdba6d39035)
![4](https://github.com/sunjidanisha/Automated-Testing-of-Rest-Booking-API-with-Newman-Report/assets/78694676/8d13c74d-7d99-4323-abe1-e9176640ef5d)
![5](https://github.com/sunjidanisha/Automated-Testing-of-Rest-Booking-API-with-Newman-Report/assets/78694676/21cce5a3-d974-4518-9487-37b72979a794)


