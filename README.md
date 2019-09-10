# sb-rs-registartion-validation
Java Tech Lead - Newton, MA


The project is build in:
Spring Tool Suite 3
Version: 3.9.9.RELEASE
Build Id: 201906181741
OS: Windows 10, v.10.0, x86_64 / win32
Java version: 1.8.0_221
sb-rs-registartion-validation\logs\*
sb-rs-registartion-validation\src\main\resources\appplivation.properties

access login sucess: 
request: http://localhost:8080/greeting?loginName=User&pwd=123abc4
response: {"content":"Hello, User. Your Password is valid."}

access login falure :
request: http://localhost:8080/greeting?loginName=User&pwd=123abc4KKK
response: {"{"content":"Hello, User. Your Password is invalid. Please provide LoginName and Password [5-12 characters lower case or numeric, at least one of each. No repeatable sequences]"}"}

access login/password not provided:  
request: http://localhost:8080/greeting
response:   {"content":"Hello, UnknownUser. Please provide LoginName and Password [5-12 characters lower case or numeric, at least one of each. No repeatable sequences]"}

unit tests: sb-rs-registartion-validation\src\test\java\com\gernera\app\ApplicationControllerTests.java
