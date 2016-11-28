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

#11. Is it a good or bad practice to use AngularJS together with jQuery?
It is definitely a bad practice. We need to stay away from jQuery and try to realize the solution with an AngularJS approach. jQuery takes a traditional imperative approach to manipulating the DOM, and in an imperative approach, it is up to the programmer to express the individual steps leading up to the desired outcome.

AngularJS, however, takes a declarative approach to DOM manipulation. Here, instead of worrying about all of the step by step details regarding how to do the desired outcome, we are just declaring what we want and AngularJS worries about the rest, taking care of everything for us. Here is [a detailed explanation](https://www.quora.com/Is-AngularJS-a-good-replacement-for-jQuery)

#12. Explain the concept of scope hierarchy?  How many scope can an application have?
Each angular application consist of one root scope but may have several child scopes. As child controllers and some directives create new child scopes, application can have multiple scopes. When new scopes are formed or created they are added as a children of their parent scope. Similar to DOM, they also creates a hierarchical structure.

#13. Mention what are the advantages of using Angular.js framework ?
* Bullet list Advantages of using Angular.js as framework are
Supports two way data-binding
Supports MVC pattern
Support static template and angular template
Can add custom directive
Supports REST full services
Supports form validations
Support both client and server communication
Support dependency injection
Applying Animations
Event Handlers

#14. Explain what is the difference between link and compile in Angular.js?
Compile function: It is used for template DOM Manipulation and collect all of the directives.
Link function: It is used for registering DOM listeners as well as instance DOM manipulation. It is executed once the template has been cloned.

#15. Explain what is linking function and type of linking function?
Link combines the directives with a scope and produce a live view.  For registering DOM listeners as well as updating the DOM, link function is responsible. After the template is cloned it is executed.
Pre-linking function: Pre-linking function is executed before the child elements are linked.  It is not considered as the safe way for DOM transformation.
Post linking function: Post linking function is executed after the child elements are linked. It is safe to do DOM transformation by post-linking function

#16. Explain what is services in AngularJS ?
In AngularJS services are the singleton objects or functions that are used for carrying out specific tasks.  It holds some business logic and these function can be called as controllers, directive, filters and so on.

#17. Explain what is factory method in AngularJS?
For creating the directive, factory method is used.  It is invoked only once, when compiler matches the directive for the first time.  By using $injector.invoke the factory method is invoked.

#18. How would you specify that a scope variable should have one-time binding only?
By using “::” in front of it. This allows the check if the candidate is aware of the available variable bindings in AngularJS.

#19. Explain how $scope.$apply() works
$scope.$apply re-evaluates all the declared ng-models and applies the change to any that have been altered (i.e. assigned to a new value)
Explanation: $scope.$apply() is one of the core angular functions that should never be used explicitly, it forces the angular engine to run on all the watched variables and all external variables and apply the changes on their values
Source: https://docs.angularjs.org/api/ng/type/$rootScope.Scope

#20. What directive would you use to hide elements from the HTML DOM by removing them from that DOM not changing their styling?
The ngIf Directive, when applied to an element, will remove that element from the DOM if it’s condition is false.

#21. What makes the angular.copy() method so powerful?
It creates a deep copy of the variable.
A deep copy of a variable means it doesn’t point to the same memory reference as that variable. Usually assigning one variable to another creates a “shallow copy”, which makes the two variables point to the same memory reference. Therefore if we change one, the other changes as well
Sources:
– https://docs.angularjs.org/api/ng/function/angular.copy

#22. What is the role of services in AngularJS and name any services made available by default?
– AngularJS Services are objects that provide separation of concerns to an AngularJS app.
– AngularJS Services can be created using a factory method or a service method.
– Services are singleton components. All components of the application (into which the service is injected) will work with single instance of the service.
– An AngularJS service allows developing of business logic without depending on the View logic which will work with it.
Few of the inbuilt services in AngularJS are:
– the $http service: The $http service is a core Angular service that facilitates communication with the remote HTTP servers via the browser’s XMLHttpRequest object or via JSONP
– the $log service: Simple service for logging. Default implementation safely writes the message into the browser’s console
– the $anchorScroll: it scrolls to the element related to the specified hash or (if omitted) to the current value of $location.hash()
Why should one know about AngularJS Services, you may ask. Well, understanding the purpose of AngularJS Services helps bring modularity to AngularJS code.
Services are the best may to evolve reusable API within and AngularJS app
Overview:
AngularJS Services help create reusable components.
A Service can be created either using the service() method or the factory() method.
A typical service can be injected into another service or into an AngularJS Controller.
Source:
– https://docs.angularjs.org/guide/services
– http://www.tutorialspoint.com/angularjs/angularjs_services.htm

#23. When creating a directive, it can be used in several different ways in the view. Which ways for using a directive do you know? How do you define the way your directive will be used?
When you create a directive, it can be used as an attribute, element or class name. To define which way to use, you need to set the restrict option in your directive declaration.
The restrict option is typically set to:
‘A’ – only matches attribute name
‘E’ – only matches element name
‘C’ – only matches class name
These restrictions can all be combined as needed:
‘AEC’ – matches either attribute or element or class name
For more information, feel free to check out the AngularJS documentation.

#24. When should you use an attribute versus an element?
Use an element when you are creating a component that is in control of the template. Use an attribute when you are decorating an existing element with new functionality.
This topic is important so developers can understand the several ways a directive can be used inside a view and when to use each way.
Sources: https://docs.angularjs.org/api/ng/service/$compile#directive-definition-object

#25. What are the basic steps to unit test an AngularJS filter?
1. Inject the module that contains the filter.
2. Provide any mocks that the filter relies on.
3. Get an instance of the filter using $filter('yourFilterName').
4. Assert your expectations.
Dependency injection is a powerful software design pattern that Angular employs to compose responsibilities through an intrinsic interface. However, for those new to the process, it can be puzzling where you need to configure and mock these dependencies when creating your isolated unit tests. The open-source project “Angular Test Patterns” is a free resource that is focused on dispelling such confusion through high-quality examples.
Source:
https://github.com/daniellmb/angular-test-patterns/blob/master/patterns/filter.md
https://docs.angularjs.org/guide/unit-testing

#26. What should be the maximum number of concurrent “watches”? Bonus: How would you keep an eye on that number?
TL;DR Summary: To reduce memory consumption and improve performance it is a good idea to limit the number of watches on a page to 2,000. A utility called ng-stats can help track your watch count and digest cycles.
Jank happens when your application cannot keep up with the screen refresh rate. To achieve 60 frames-per-second, you only have about 16 milliseconds for your code to execute. It is crucial that the scope digest cycles are as short as possible for your application to be responsive and smooth. Memory use and digest cycle performance are directly affected by the number of active watches. Therefore, it is best to keep the number of watches below 2,000. The open-source utility ng-stats gives developers insight into the number of watches Angular is managing, as well as the frequency and duration of digest cycles over time.
Caution: Be wary of relying on a “single magic metric” as the golden rule to follow. You must take the context of your application into account. The number of watches is simply a basic health signal. If you have many thousands of watches, or worse, if you see that number continue to grow as you interact with your page. Those are strong indications that you should look under the hood and review your code.
This question is valuable as it gives insight into how the candidate debugs runtime issues while creating a discussion about performance and optimization.
Sources:
https://github.com/kentcdodds/ng-stats
