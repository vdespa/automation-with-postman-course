# Postman Beginner's Course - API Test Automation

## Unit 1 - Introduction to API testing

### Lesson 1 - Welcome

- this course is ideal if you already know how to use Postman for creating requests
- in this course you will learn:
    - write API tests in Postman
    - automate test execution with various Postman tools (Collection Runner, Postman CLI)
    - running tests with the help of the CI/CD tool Github Actions
- Postman offers an official badge for completing this course and doing all assignments

 #### 📚 - Resources

 * [Check out Valentin's YouTube channel](https://www.youtube.com/@vdespa?sub_confirmation=1)
 * [Check out Postman's YouTube channel](https://www.youtube.com/@postman?sub_confirmation=1)


### Lesson 2 - Introduction to the project

- before we can automate the testing of an API, we first need to do a manual test
- create a new public workspace which will store all collections used during the course
- to run or make changes to a collection from a workspace that isn't yours, you need to make a copy (create a fork)

#### 📚 - Resources

 * [Open Postman on the web](https://go.postman.co/build)
 * [Postman workspace - FORK from here](https://www.postman.com/valentins-team/workspace/test-automation-valentino-s-artisan-coffee-house-api/overview)

#### 🆘 - Troubleshooting

- if you can't get a status 200 OK reply from the sever when trying the Status endpoint, check the following:
    - ensure you are on postman.com
- if the error persists, [submit an issue](https://github.com/vdespa/automation-with-postman-course/issues/new) and add as many details as possible, including screenshots of any errors that appear.


### Lesson 3 - What is API testing

- API testing involves verifying the functionality, reliability, performance, and security of an API
- the goal of API testing is to identify issues and defects in the API before it is released
- this course focuses on functional testing


### Lesson 4 - Manually testing the API

- to automate the API tests, we first need to know how to perform them manually
- the goal of this lecture is to go through all the endpoints of this API


### Lesson 5 - Using to Postman variables to store secrets

- regardless if the collection is public or private, it is a best practice to store secrets (like API keys, passwords, tokens) in Postman variables
- Postman auth helpers can configure different types of authentication
- keep in mind that authentication can be configured on one level (collection, folder) and inherited


### Lesson 6 - Writing scripts in Postman

- automated testing is a way to check if the API works correctly by letting Postman run tests
- we write scripts to automate the testing of the API
- API tests are written using scripts
- Postman uses JavaScript for writing tests
- don't confuse JavaScript with Java, as they are two different programming languages
- console.log can be used to write a message to the Postman console: `console.log(“Hello from the Tests!”);`


### Lesson 7 - Use the Postman console for debugging scripts

- the Postman console can be used to view any information about the request and the response (URL, headers, body)
- any messages logged using console.log can also be seen there
- to clear the Postman console of entries you can use the "Clear" button or use the following script: `console.clear()`


### Lesson 8 - Writing an API test

- the following script can be added to the "Tests" to check if the response status code is 200 OK.

```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```

### Lesson 9 - JavaScript basics

- to write tests in Postman, you need to know some JavaScript basics
- these are the most important concepts you need to be familiar with:
    -  variables and their scope
    -  data types including objects and arrays
    -  functions

### Lesson 10 - JavaScript basics - Variables
