
Title of the Project: Student Attendance System

Description: It is used to manage student attendance online. The easy to use online student attendance system designed to take attendance 
quick and less prone to errors. Record a student’s attendance on the colored chart with a click of the mouse. The information pertaining to the student
attendance can then be immediately shared.

Benefits of Using JsonPowerDB:
      * All Mobile applications that require backend database.
      * Session Caching.
      * Page Caching.
      * Existing Database applications to improve their reporting / analytics performance.
      * Best suited as backend Database for IoT.
      * Live HTML templates / themes.
      * Any software application that needs backend database
      
Release History:
      This application was developed instantly on 24/04/2022 with use os Netbeans, HTML, CSS,JAVASCRIPT, AJAX,JSONDB, BOOTSTRAP and was released
      at Github on 24/04/2022 at 6:10pm.
 
 Scope of functionalities:
      USN
      STUDENT NAME
      DEPARTMENT
      JAVA
      PYTHON
      UNIX
      Save
         
 Examples of use:
      Front end:
      USN          :123
      STUDENT NAME :Sharan
      DEPARTMENT   :Mca
      JAVA          :55
      PYTHON        :66
      UNIX          :77
      
   Project status:
            This project is developed for time purpose with limited number of functionalities, we try to add more functionalities in future
         
         
<Codings>         
         
<!DOCTYPE html>
<!--
To change this license header, choose License Headers in Project Properties.
To change this template file, choose Tools | Templates
and open the template in the editor.
-->
<html lang="en">
<head>
<title>Bootstrap Example</title>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<link rel="stylesheet"
href="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/css/bootstrap.min.css">
<script
src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
<script
src="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/js/bootstrap.min.js"></script>
</head>
<body>
<div class="container">
<h2>Student attendace</h2>
<form id="empForm" method="post">
<div class="form-group">
<span><label for="empId">USN:</label> <label id="empIdMsg">
</label></span>
<input type="text" class="form-control" name="empId" id="empId"
placeholder="Enter USN" required>
</div>
<div class="form-group">
<label for="empName">Student Name:</label>
<input type="text" class="form-control" id="empName"
placeholder="Enter Student Name" name="empName">
</div>
<div class="form-group">
<label for="empEmail">Department:</label>
<input type="email" class="form-control" id="empEmail"
placeholder="Enter Department" name="empEmail">
</div>
<div class="form-group">
<label for="empEmail">Java:</label>
<input type="email" class="form-control" id="empJava"
placeholder="Enter Java Details" name="empEmail">
</div>
<div class="form-group">
<label for="empEmail">Python:</label>
<input type="email" class="form-control" id="empPython"
placeholder="Enter Python Details" name="empEmail">
</div>
<div class="form-group">
<label for="empEmail">Unix:</label>
<input type="email" class="form-control" id="empUnix"
placeholder="Enter Unix Details" name="empEmail">
</div>
<input type="button" class="btn btn-primary" id="empSave" value="Save"
onclick="saveEmployee();">
</form>
</div>
<script>
$("#empId").focus();
function validateAndGetFormData() {
var empIdVar = $("#empId").val();
if (empIdVar === "") {
alert("Employee ID Required Value");
$("#empId").focus();
return "";
}
var empNameVar = $("#empName").val();
if (empNameVar === "") {
alert("Employee Name is Required Value");
$("#empName").focus();
return "";
}
var empEmailVar = $("#empEmail").val();
if (empEmailVar === "") {
alert("Employee Email is Required Value");
$("#empEmail").focus();
return "";
}
var empJavaVar = $("#empJava").val();
if (empJavaVar === "") {
alert("Java details required");
$("#empJava").focus();
return "";
}
var empPythonVar = $("#empPython").val();
if (empPythonVar === "") {
alert("python details required");
$("#empPython").focus();
return "";
}
var empUnixVar = $("#empUnix").val();
if (empUnixVar === "") {
alert("Unix details required");
$("#empUnix").focus();
return "";
}
var jsonStrObj = {
empId: empIdVar,
empName: empNameVar,
empEmail: empEmailVar,
empJava: empJavaVar,
empPython: empPythonVar,
empUnix: empUnixVar,
};
return JSON.stringify(jsonStrObj);
}
// This method is used to create PUT Json request.
function createPUTRequest(connToken, jsonObj, dbName, relName) {
var putRequest = "{\n"
+ "\"token\" : \""
+ connToken
+ "\","
+ "\"dbName\": \""
+ dbName
+ "\",\n" + "\"cmd\" : \"PUT\",\n"
+ "\"rel\" : \""
+ relName + "\","
+ "\"jsonStr\": \n"
+ jsonObj
+ "\n"
+ "}";
return putRequest;
}
function executeCommand(reqString, dbBaseUrl, apiEndPointUrl) {
var url = dbBaseUrl + apiEndPointUrl;
var jsonObj;
$.post(url, reqString, function (result) {
jsonObj = JSON.parse(result);
}).fail(function (result) {
var dataJsonObj = result.responseText;
jsonObj = JSON.parse(dataJsonObj);
});
return jsonObj;
}
function resetForm() {
$("#empId").val("")
$("#empName").val("");
$("#empEmail").val("");
$("#empJava").val("");
$("#empPython").val("");
$("#empUnix").val("");
$("#empId").focus();
}
function saveEmployee() {
var jsonStr = validateAndGetFormData();
if (jsonStr === "") {
return;
}
var putReqStr = createPUTRequest("90938625|-31949286451693115|90946106",
jsonStr, "Student", "Stu-rel");
alert(putReqStr);
jQuery.ajaxSetup({async: false});
var resultObj = executeCommand(putReqStr,
"http://api.login2explore.com:5577", "/api/iml");
alert(JSON.stringify(resultObj));
jQuery.ajaxSetup({async: true});
resetForm();
}
</script>
</body>
</html>
