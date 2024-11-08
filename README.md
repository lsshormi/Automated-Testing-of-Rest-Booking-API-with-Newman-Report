### **Rest Booking API Testing with Postman and Report Generating with Newman**
This project demonstrates API testing using Postman, providing a collection of tests to validate various endpoints of the API. 

### **Features**

- Tests for GET, POST, PUT, DELETE requests
- Collection of tests covering different API endpoints
- Environment setup for easy switching between environments
- Pre-request scripts for data setup
- Test scripts for assertions and validations

## API Documentation:
- https://documenter.getpostman.com/view/36696138/2sAY517fUK
  
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
  git clone https://github.com/lsshormi/Automated-Testing-of-Rest-Booking-API-with-Newman-Report.git
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
    var FirstName = pm.variables.replaceIn("{{$randomFirstName}}")
    // console.log(FirstName)
    pm.environment.set("firstName", FirstName)

    var LastName = pm.variables.replaceIn("{{$randomLastName}}")
    // console.log(LastName)
    pm.environment.set("lastName", LastName)

    var TotalPrice = pm.variables.replaceIn("{{$randomPrice}}")
    pm.environment.set("totalPrice", TotalPrice)

    var depositPaid = pm.variables.replaceIn("{{$randomBoolean}}")
    pm.environment.set("depositPaid", depositPaid)

    
    //Date
    const moment = require("moment")
    const today = moment()
    var checkIn = (today.add(5, 'd').add(1, 'M').format("YYYY-MM-DD"))
    pm.environment.set("checkin", checkIn)

    var checkOut = (today.add(10, 'd').format("YYYY-MM-DD"))
    pm.environment.set("checkout", checkOut)

    var Additionalneeds = pm.variables.replaceIn("{{$randomNoun}}")
    pm.environment.set("additionalNeeds", Additionalneeds)
```
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
    "bookingid": 744,
    "booking": {
        "firstname": "Burdette",
        "lastname": "Jenkins",
        "totalprice": 462,
        "depositpaid": true,
        "bookingdates": {
            "checkin": "2024-12-11",
            "checkout": "2024-12-21"
        },
        "additionalneeds": "firewall"
    }
  }
```
 ## _**2. Get Booking Details By ID**_
### Request URL: https://restful-booker.herokuapp.com/booking/bookingid
### Request Method: GET
### Response Body:
 ```console 
  {
    "bookingid": 744,
    "booking": {
        "firstname": "Burdette",
        "lastname": "Jenkins",
        "totalprice": 462,
        "depositpaid": true,
        "bookingdates": {
            "checkin": "2024-12-11",
            "checkout": "2024-12-21"
        },
        "additionalneeds": "firewall"
    }
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
    "token": "06eb798bf6f2caa"
}
```

 ## _**4. Update the Booking Details**_
### Request URL: https://restful-booker.herokuapp.com/booking/bookingid
### Request Method: PUT
### Pre-request Script:
```console 
    var FirstName = pm.variables.replaceIn("{{$randomFirstName}}")
    // console.log(FirstName)
    pm.environment.set("firstName", FirstName)

    var LastName = pm.variables.replaceIn("{{$randomLastName}}")
    // console.log(LastName)
    pm.environment.set("lastName", LastName)

    var TotalPrice = pm.variables.replaceIn("{{$randomPrice}}")
    pm.environment.set("totalPrice", TotalPrice)

    var depositPaid = pm.variables.replaceIn("{{$randomBoolean}}")
    pm.environment.set("depositPaid", depositPaid)

    
    //Date
    const moment = require("moment")
    const today = moment()
    var checkIn = (today.add(5, 'd').add(1, 'M').format("YYYY-MM-DD"))
    pm.environment.set("checkin", checkIn)

    var checkOut = (today.add(10, 'd').format("YYYY-MM-DD"))
    pm.environment.set("checkout", checkOut)

    var Additionalneeds = pm.variables.replaceIn("{{$randomNoun}}")
    pm.environment.set("additionalNeeds", Additionalneeds)
```
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
        "firstname": "Vada",
        "lastname": "McLaughlin",
        "totalprice": 990,
        "depositpaid": true,
        "bookingdates": {
            "checkin": "2024-12-11",
            "checkout": "2024-12-21"
        },
        "additionalneeds": "Morning"
    }
```

 ## _**5. Delete Booking Record**_

### Request URL: https://restful-booker.herokuapp.com/booking/bookingid
### Request Method: DELETE
### Response Body: None 

## Run Command:  
- Run Command for Console: 
```console 
newman run LS_Shormi_SQA.postman_collection.json -e LS_Shormi_SQA.postman_environment.json 
```
- Run Command for Report: 
```console 
newman run LS_Shormi_SQA.postman_collection.json -e LS_Shormi_SQA.postman_environment.json -r cli,htmlextra
```

## Newman Report Summary:
![image](https://github.com/user-attachments/assets/2070a7c9-44b3-4270-a840-9486fb06ed5c)
![image](https://github.com/user-attachments/assets/4c6acfd9-f3bb-47d4-8d2f-3608877408f2)
![image](https://github.com/user-attachments/assets/caa09d2a-7a42-4c35-b70a-caaec96e7729)
![image](https://github.com/user-attachments/assets/1b5ccd40-5835-4cbd-8c9d-9d8167d24aa3)





