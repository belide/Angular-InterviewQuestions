# Angular-InterviewQuestions
<hr>
#1. What is AngularJS?
AngularJS is a javascript framework used for creating single web page applications.  It allows you to use HTML as your template language and enables you to extend HTML’s syntax to express your application’s components clearly.

#2. What is the difference between one-way binding and two-way binding?
– One way binding implies that the scope variable in the html will be set to the first value its model is bound to (i.e. assigned to)
<br>
– Two way binding implies that the scope variable will change it’s value every time its model is assigned to a different value .
#3. Explain what is a `$scope` in AngularJS
Scope is an object that refers to the application model. It is an execution context for expressions. Scopes are arranged in hierarchical structure which mimic the DOM structure of the application. Scopes can watch expressions and propagate events. Scopes are objects that refer to the model. They act as glue between controller and view.

This question is important as it will judge a persons knowledge about a $scope object, and it is one of the most important concepts in AngularJS. Scope acts like a bridge between view and model.

#4. What are Directives?

Directives are markers on a DOM element (such as an attribute, element name, comment or CSS class) that tell AngularJS’s HTML compiler ($compile) to attach a specified behavior to that DOM element (e.g. via event listeners), or even to transform the DOM element and its children. Angular comes with a set of these directives built-in, like ngBind, ngModel, and ngClass. Much like you create controllers and services, you can create your own directives for Angular to use. When Angular bootstraps your application, the HTML compiler traverses the DOM matching directives against the DOM elements.

This question is important because directives define the UI while defining a single page app. You need to be very clear about how to create a new custom directive or use the existing ones already pre-build in AngularJS.

Source: [https://docs.angularjs.org/guide/directive](https://docs.angularjs.org/guide/directive)
 
[]()
#5. What is a singleton pattern and where we can find it in Angularjs?

Is a great pattern that restricts the use of a class more than once. We can find singleton pattern in angular in dependency injection and in the services.

In a sense, if you do 2 times `new Object()` without this pattern, you will be allocating 2 pieces of memory for the same object. With singleton pattern, if the object exists, you reuse it.

Source: [http://joelhooks.com/blog/2013/05/01/when-is-a-singleton-not-a-singleton/](http://joelhooks.com/blog/2013/05/01/when-is-a-singleton-not-a-singleton/) 

#6. What is an interceptor? What are common uses of it?

An interceptor is a middleware code where all the $http requests go through.
The interceptor is a factory that are registered in $httpProvider. You have 2 types of requests that go through the interceptor, request and response (with requestError and responseErrorrespectively). This piece of code is very useful for error handling, authentication or middleware in all the requests/responses.
Source: [https://docs.angularjs.org/api/ng/service/$http](https://docs.angularjs.org/api/ng/service/$http) 

#7. How do you share data between controllers?

Create an AngularJS service that will hold the data and inject it inside of the controllers.
Using a service is the cleanest, fastest and easiest way to test.
However, there are couple of other ways to implement data sharing between controllers, like:
– Using events
– Using $parent, nextSibling, controllerAs, etc. to directly access the controllers
– Using the $rootScope to add the data on (not a good practice)
The methods above are all correct, but are not the most efficient and easy to test.
#8. What is the difference between ng-show/ng-hide and ng-if directives?

ng-show/ng-hide will always insert the DOM element, but will display/hide it based on the condition. ng-if will not insert the DOM element until the condition is not fulfilled.
ng-if is better when we needed the DOM to be loaded conditionally, as it will help load page bit faster compared to ng-show/ng-hide.

#9. What is a digest cycle in AngularJS?

In each digest cycle Angular compares the old and the new version of the scope model values. The digest cycle is triggered automatically. We can also use $apply() if we want to trigger the digest cycle manually.
#10. Where should we implement the DOM manipulation in AngularJS?

In the directives. DOM Manipulations should not exist in controllers, services or anywhere else but in directives.Here is a detailed explanation
