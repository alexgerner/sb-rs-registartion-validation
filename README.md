# sb-rs-registartion-validation
The project is build by Alexander Gerner on 09/11/2019

Task Specification
===================

Write a password validation service, meant to be configurable via IoC (using dependency
injection engine of your choice). The service is meant to check a text string for compliance
to any number of password validation rules. The rules currently known are:
 
⦁Must consist of a mixture of lowercase letters and numerical digits only, with at least one
of each.
⦁Must be between 5 and 12 characters in length.
⦁Must not contain any sequence of characters immediately followed by the same sequence.

Build Environment
==================
Spring Tool Suite 3
Version: 3.9.9.RELEASE
Build Id: 201906181741
OS: Windows 10, v.10.0, x86_64 / win32
Java version: 1.8.0_221

Logs
=====
\sb-rs-registartion-validation\logs\*

ApplicationpProperties
=========================
\sb-rs-registartion-validation\src\main\resources\appplivation.properties

JUnit
===========
suites: \sb-rs-registartion-validation\src\test\java\com\gernera\app\suites\
- TestsSuiteInputParameters
- TestsSuiteRegExp
- TestsSuiteSequence
tests: \sb-rs-registartion-validation\src\test\java\com\gernera\app\tests\*


Basic Smoke Test Use Cases (Rest Service API)
===============================================
access login sucess:
-------------------- 
request: http://localhost:8080/greeting?loginName=User&pwd=123abc4
response: {"content":"Hello, User. Password is valid."}

access login sucess:
-------------------- 
request: http://localhost:8080/greeting?loginName=User&pwd=123a12
response: {"content":"Hello, User. Password is valid."}
 
access login falure (Capital letter K):
---------------------------------------
request: http://localhost:8080/greeting?loginName=User&pwd=123abc4K
response: {"content":"Hello, User. Password is invalid. Please provide LoginName and Password [5-12 characters lower case or numeric, at least one of each. No repeatable sequences]"}
 
access login falure (Special Character $):
------------------------------------------
request: http://localhost:8080/greeting?loginName=User&pwd=123abc4$aa
response: {"content":"Hello, User. Password is invalid. Please provide LoginName and Password [5-12 characters lower case or numeric, at least one of each. No repeatable sequences]"}

access login falure (repeatable sequence):
------------------------------------------
request: http://localhost:8080/greeting?loginName=User&pwd=123a123
response:  {"content":"Hello, User. Password is invalid. Please provide LoginName and Password [5-12 characters lower case or numeric, at least one of each. No repeatable sequences]"}

access login falure (Login Name not provided):
-----------------------------------------------
request: http://localhost:8080/greeting
response:   {"content":"Hello, Unknown User. Please provide LoginName and Password [5-12 characters lower case or numeric, at least one of each. No repeatable sequences]"}

access login falure (Password not provided):
-----------------------------------------------
request: http://localhost:8080/greeting?loginName=User
response:   {"content":"Hello, User. Please provide LoginName and Password [5-12 characters lower case or numeric, at least one of each. No repeatable sequences]"}

 
