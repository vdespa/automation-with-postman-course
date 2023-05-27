# Postman Beginner's Course - API Test Automation

## Unit 1 - Introduction to API testing

### Lesson 1 - Welcome

- this course is ideal if you already know how to use Postman for creating requests
- in this course you will learn:
    - write API tests in Postman
    - automate test execution with various Postman tools (Collection Runner, Postman CLI)
    - running tests with the help of the CI/CD tool Github Actions
- Postman offers an official badge for completing this course and doing all assignments

 #### 📚 Resources

 * [Check out Valentin's YouTube channel](https://www.youtube.com/@vdespa?sub_confirmation=1)
 * [Check out Postman's YouTube channel](https://www.youtube.com/@postman?sub_confirmation=1)


### Lesson 2 - Introduction to the project

- before we can automate the testing of an API, we first need to do a manual test
- create a new public workspace which will store all collections used during the course
- to run or make changes to a collection from a workspace that isn't yours, you need to make a copy (create a fork)

#### 📚 Resources

 * [Open Postman on the web](https://go.postman.co/build)
 * [Postman workspace - FORK from here](https://www.postman.com/valentins-team/workspace/test-automation-valentino-s-artisan-coffee-house-api/overview)

#### 🆘 Troubleshooting

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

```javascript
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

- variables are like containers that store data
- you can define a variable named "name" with the value "jamie" and log the value to the console like this:

```javascript
let name = “Jamie”;
console.log(name);
```

### Lesson 11 - JavaScript basics - Variable scopes

- variables defined within a block statement are available only to code within that block
- variables defined outside of a block statement are in the global scope can can be access from anywhere

#### 📚 Resources

 * [let - JavaScript - MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let)
 * [block statement - JavaScript - MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/block)

### Lesson 12 - JavaScript basics - Data types

- JavaScript has various data types to represent information
- the most likely data types you need to know about are: string, number, boolean, object, and array
- if you are unsure of a data type you can use the `typeof` operator. Example: `console.log(typeof "John"); `
- example of an object contaning various data types:

```javascript
let person = {
   name: "Jake", // string
   age: 29, //number
   isAdult: true, // boolean
   'e-mail': 'jake@example.com', // string
   hobbies: ['reading', 'travelling', 'gardening', 'cooking'] // array of strings
};
```

#### 📚 Resources

[typeof - JavaScript - MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/typeof)


### Lesson 13 - JavaScript basics - Functions

- functions are fundamental concepts in programming:
    - they are blocks of code designed to perform specific tasks
    - they allow us to organize and reuse code effectively
- A simple function definition in JavaScript:

```javascript
function greet() {
  console.log("Hello from Postman!");
}
```
- a function needs to be invoked to work, using the following example syntax: greet()
- functions can take inputs in the form of arguments:

```javascript
function greet(name) {
  console.log("Hello from Postman, " + name + "!");
}
greet('Valentin');
```

- using console.log in a function is primarily used for debugging and doesn't mean the function returns a value
- the `return` statement specifies the value that a function should return after executing. 
- using `return` is necessary when you want to use the result of a function in another part of your code:

```javascript
function add(a, b) {
	let sum = a + b;
	console.log(sum);
    return sum;
}

console.log("The sum is: " + add(1,2));
```


### Lesson 14 - JavaScript basics - Methods

- you can also define a function inside an object:

```javascript
let person = {
   firstName: "Jake",
   age: 29,
   isAdult: true,
   'e-mail': 'jake@example.com',
   hobbies: ['reading', 'travelling', 'gardening', 'cooking'],
   greet: function(name) {
       console.log('Hello from Postman ' + name + '. My name is + ' + this.firstName);
   }
};
person.greet('Jake');
```

- when a function is defined insite an object, we call it a method



### Lesson 15 - JavaScript basics - Callback functions

- callback functions are an essential concept in JavaScript programming and allow for more efficient and flexible code.
- functions can be stored in variables:

```javascript
const sayHello = function() {
    console.log('Hello');
}
```
- functions without a name are called anonymous functions and can only be called by referencing the variable they're stored in, e.g., sayHello.
- functions can be passed as arguments to another function:

```javascript
function doSomething(someFunction) {
	someFunction(); // function is invoked here
}

doSomething(sayHello); // function passed as an argument
```

- functions can be defined directly inside another function:

```javascript
function doSomething(someFunction) {
    someFunction();
}

doSomething(function() {
    sayHello();
});
```

- this syntax is used in Postman for writing tests



### Lesson 16 - JSON format

- most APIs use the JSON format
- JSON and JavaScript objects are not the same

#### 📚 Resources

[JSON - JavaScript - MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON)


### Lesson 17 - Accessing data from the response body

- to access any information from a JSON response body, you first need to parse the response:

```javascript
const response = pm.response.json();
console.log(response);
```


### Lesson 18 - Passing data from one request to the other

- using Postman variables is a good way to reduce duplication and to have be able to control multiple requests
- using Postman variables reduces or elimitates the need to copy/paste data or to manually reconfigure requests


### Lesson 19 - Setting Postman variables from scripts

- JavaScript variables are not the same with Postman variables
- JavaScript variables are scoped only to the script where they are defined and any variable set from there are not persisted
- Postman variables useful for:
	- storing settings and persisting data on the long term, such as the baseUrl, API key or other details
	- passing data between requests
- it is possible to create or update a Postman collection variable from a script:

```javascript
pm.collectionVariables.set('firstName', 'Jamie');
```

### Lesson 20 - Assignment #1

- fork the Assignment #1 collection and follow the instructions from the documentation

#### 📚 Resources

 * [Postman workspace - FORK Assignment #1 from here](https://www.postman.com/valentins-team/workspace/test-automation-valentino-s-artisan-coffee-house-api/overview)
 * [Postman community](https://community.postman.com/)


## Unit 2 - Writing API tests

### Lesson 1 - Unit overview

- we have a Postman collection which we can run request by reqy from the beginning to the end.
- in this unit we will focus on writing tests for the API

### Lesson 2 - Test structure in Postman

- the basic structure of a test in Postman is the following:

```javascript
pm.test('Name of the test', function () {
	// assertions
});
```

- assertions can be written with `pm.expect`:

```javascript
pm.expect(1).to.eql(1); - test passes
pm.expect(1).to.eql(2); - test fails
```

### Lesson 3 - Making assertions about the status code

- alternartive way of writing a status code test using `pm.expect`:

```javascript
pm.test('Status is 200', function () {
	pm.expect(pm.response.status).to.eql(200);
});
```

### Lesson 4 - Assignment #2

- fork the Assignment #2 collection and follow the instructions from the documentation

#### 📚 Resources

 * [Postman workspace - FORK from here](https://www.postman.com/valentins-team/workspace/test-automation-valentino-s-artisan-coffee-house-api/overview)


### Lesson 5 - Asserting the response body is JSON

- an API may return a response that is not JSON
- before trying to parse the response, it is best to check if the response body is JSON.

```javascript
pm.test("Response body is JSON", () => {
    pm.response.to.be.json;
});
```

### Lesson 6 - Writing simple assertions against the response body

- it is important to assert different aspects about the response body
- example checking the product name which is a string:

```javascript
pm.test("Product is Espresso", () => {
    const response = pm.response.json();
    pm.expect(response.name).to.eql('Espresso');
});
```

- example checking a boolean value:

```javascript
pm.test("Product is in stock", () => {
    const response = pm.response.json();
    pm.expect(response.isAvailable).to.eql(true);
    pm.expect(response.isAvailable).to.be.true;
});
```

- example where the expected value is a Postman variable:

```javascript
pm.expect(response.id).to.eql(pm.collectionVariables.get('productId'));
```

### Lesson 7 - Asserting the data-type of a property

- instead of checking for a specific value, it is possible to check if a property exists
- example checking if the response as a property called `name`:

```javascript
expect(response).to.have.property('name');
```

- example checking if a property of the response is a number
- 
```javascript
expect(response.price).to.be.a('number');
```

#### 📚 Resources

[Chai Assertion Library](https://www.chaijs.com/api/bdd/)


### Lesson 8 - Using Postman random variables in assertions

### Lesson 9 - Regular expressions in tests

- it is possible to use regular expressions in assertions:

```javascript
pm.expect(response.id).to.match(/^[A-Z0-9]{9}$/);
```

### Lesson 10 - Assignment #3 - Write API tests against the response body

- fork the Assignment #3 collection and follow the instructions from the documentation

#### 📚 Resources

 * [Postman workspace - FORK Assignment #3 from here](https://www.postman.com/valentins-team/workspace/test-automation-valentino-s-artisan-coffee-house-api/overview)

### Lesson 11 - JSON schema validations

```javascript
pm.test('Schema is valid', function () {
    const schema = {
        "type": "object",
        "properties": {
            "id": {
                "type": "string"
            },
            "clientId": {
                "type": "string"
            },
            "created": {
                "type": "string",
            },
            "customerName": {
                "type": "string"
            },
            "products": {
                "type": "array"
            }
        }
    };
    pm.response.to.have.jsonSchema(schema);
});
```

### Lesson 12 - Using Postman mock servers

- using Postman mock servers is an effective way to test if the tests written will fail

### Lesson 13 - Advanced JSON schema validation

```
{
    "type": "object",
    "properties": {
        "id": {
            "type": "string",
            "pattern": "^[A-Z0-9]{9}$"
        },
        "clientId": {
            "type": "string",
            "pattern": "^[a-zA-Z0-9]{9}$"
        },
        "created": {
            "type": "string",
            "format": "date-time"
        },
        "customerName": {
            "type": "string"
        },
        "products": {
            "type": "array",
            "items": {
                "type": "object",
                "properties": {
                    "id": {
                        "type": "integer"
                    },
                    "quantity": {
                        "type": "integer",
                        "minimum": 1
                    }
                },
                "required": ["id", "quantity"]
            }
        }
    },
    "required": ["id", "clientId", "created", "customerName", "products"]
}
```

### Lesson 14 - Common pitfalls with JSON schema validation 

#### 📚 Resources

* [Understanding JSON Schema](https://json-schema.org/understanding-json-schema/)


### Lesson 15 - Assignment #4 - Write a JSON schema

- fork the Assignment #3 collection and follow the instructions from the documentation

#### 📚 Resources

 * [Postman workspace - FORK Assignment #4 from here](https://www.postman.com/valentins-team/workspace/test-automation-valentino-s-artisan-coffee-house-api/overview)


### Lesson 16 - Testing response headers

```javascript
pm.expect(pm.response.headers.get('X-Powered-By')).to.eql(‘Express’);

```


## Unit 3 - Automation first steps

### Lesson 2 - Collection runner

- the Postman collection runner is the first step toward testing if an automated run is possible
- the Postman collection runner is a useful tool for debugging

### Lesson 3 - Scheduled runs

- runs are executed on the Postman Cloud
- no need to keep Postman open or your computer on during the run
- excellent tool for API monitoring after deployment, ensuring it continues to function as expected.
- variable issues: if a variable isn't being resolved during the run, ensure that the variable has been correctly defined in the selected environment.
- best suited for APIs that are publicly accessible.
- limited use for pre-production environments which are typically not publicly accessible.
