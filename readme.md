FS1010 Code Construct 1

Objective: build an app that displays a new activity in a list, every time a button is pressed. The activities will come from an API ('https://www.boredapi.com/api/activity) and will be displayed on an HTML page.

---
STEP 1: Identify what the app will do

1. Create an eventListener to check that the document has been loaded. Include everything else in a function triggered by this eventListener.
2. Get elements from DOM: button and ul.
3. Create a JS class for the activities:
	a. define the object
	b. define a method to fetch an activity
	c. use the DOM API to create and display fetched elements
4. Define a function that creates an activity and displays it:
	a. creat a new instance of the activity object
	b. call the object method for fetch contents, then method to add it to list and display it
5. add eventListener for click on button that will execute function at point 4.

---
STEP 2: Verify necessary competencies

1. DOM
2. DOM
3. Classes (initialization), DOM; classList, fetch, promises (.then)
4. Classes (create object), promises (.then)

---
STEP 3: Competencies breakdown, explanations and exercises

1. document.addEventListener('DOMContentLoaded', function () { /* Entire code here */ }
	>> Already provided, tells the browser to only execute the code after the entire document has been completely loaded.
	
	>> Ref: https://developer.mozilla.org/en-US/docs/Web/API/Window/DOMContentLoaded_event
	
2. TODO: Get the element `<ul id="activities">` and store it in the `activities` property
	>> "elements" is an objects with 2 properties: boredButton and activities.
	>> boredButton corresponds to the HTML element with id #suggest-activity-button, while activities must correspond to the element with id #activities.
	
	>> Ref: https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector
	
3. 
	a.
	class ExcitingActivity {
		constructor() {
		this.description = null;
		this.price = null;
		this.element = document.createElement('li');
	>> A class called ExcitingActivity is being created. A new object will be created through this classe later (see 4.a)
	
	>> Ref: https://www.w3schools.com/js/js_classes.asp
	
	TODO: Add DOM class `activity` to `this.element`
	>> Use the "Element.classList" property to add the DOM class activity (.activity) to "this.element"
	>> Ref: https://developer.mozilla.org/en-US/docs/Web/API/Element/classList
	
	b.
	TODO:
		1. Return a call to `fetch()` with the following URL: https://www.boredapi.com/api/activity
		2. Parse the response as JSON
		3. The response is an object with the property `activity`, assign this to `this.description`
		4. The response is an object with the property `price`, assign this to `this.price`
	>> Create a method (a function inside the class ExcitingActivity) that fetches an element from an API, using the fetch API
	>> Usage:
	myFetchFunction() {
		return fetch('https://example.com/api')
			.then((response) => {
			// return fetched element parsed as json;
			})
			.then((data) => {
			// assignments as per points 3 and 4 above
			return data;
			});
	}
	
	>> Ref: https://developers.google.com/web/updates/2015/03/introduction-to-fetch
	
	c.
	addToList() {
      		let descriptionElement = document.createElement('p');
      		descriptionElement.classList.add('activity-description');
      		descriptionElement.textContent = this.description;
      		this.element.appendChild(descriptionElement);
	>> This block creates a new paragraph (into the variable descriptionElement), assigns the DOM class .activity-description to it, then inserts in it the text coming from the this.description property of the activity object and finally appends the new paragraph to this.element as a child.
	
	TODO: Creates a `span` element and stores it in a variable named `priceElement`
	>> Same as let descriptionElement = document.createElement('p');
	
	TODO: Add the DOM class to this `span` named `activity-price`
	>> Same as descriptionElement.classList.add('activity-description');
	
	TODO: Assign `this.price` prepended by a `$` character to `priceElement.textContent`
	>> Same as descriptionElement.textContent = this.description;
	>> Remember to use template literals and escape the $ character in order for it to appear on the screen
	
	>> Ref: https://devdocs.io/javascript/template_literals
	
	>> Ref: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals
	
	TODO: Append `priceElement` to `this.element` after `descriptionElement` is appended to it
	>> Append the two elements in the correct order, similar to this.element.appendChild(descriptionElement); (it doesen't say child in the instructions) 
	
	TODO: Appends `this.element` to `elements.activities` as a child
	>> Same as this.element.appendChild(descriptionElement); (always pay attention to the order of the elements and which is appended to which)
	
4.
	>> The function addActivity() will be called every time the button is pressed. Each time the button is pressed, a new activity is displayed (one at a time).
	>> The first step is to create a new instance of the ExcitingActivity object.
	>> The second one, call the method to fetch the contents, then the method to add it to the list.
	a.
	let activity;
	>> We defined a class in 3.a, now we need to create an object from that and assign it to the variable called activity.
	
	>> Ref: https://www.w3schools.com/js/js_classes.asp
	>> Note the difference in the constructor() statement between our ExcitingActivity and the Car in the example. It will reflect on the way we create the new element.
	
	b.
	TODO: Initialize a new instance of `ExcitingActivity` into a new variable called `activity`
	return activity.then;
	>> Keep this line unchanged and write above it.
	
	TODO: Fetch the exciting activity then display it
     *   1. Call `fetchContents` function off of the new instance of `ExcitingActivity` which should return a promise
     *   2. After the promise returned by `fetchContents` is resolved, call the `addToList` function
	>> Remember that the two functions we need to call are methods of the activity objects defined above.
	
	>> Ref: https://www.w3schools.com/js/js_classes.asp (methods section)
	
	>> The example found here https://javascript.info/promise-basics#then explains the use of .then() with the following example:
	promise.then(
		function(result) { /* handle a successful result */ },
		function(error) { /* handle an error */ }
	);
	>> We can ignore the error part for this example, so we remain with this:
	promise.then(
		function(result) { /* handle a successful result */ },
	);
	>> As specified above, fetchContents() and addToList() are methods of the activity object we created in the previous step, so make sure to use the dot notation when you call them.
	>> In this case, fetchContents() is my promise and addToList() is the function called inside then().
	>>
	object.method() 	// This is the same as the promise in the example above
    .then ( () => { 	// This is just how then() is used, nothing particular to do
      object.method();	// This is  the method that will be called by then() in case the promise resolves correctly
    });
	
