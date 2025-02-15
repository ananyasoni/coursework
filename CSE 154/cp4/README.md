# Creative Project 4 Specification
## Overview
For your fourth Creative Project, you will create your own Node.js web service available for use with AJAX and fetch. Once again, as a Creative Project, you have freedom to have more ownership in your work, as long as you meet the requirements listed below.

## Ideas for CP4
Being that this is our last Creative Project, it is also your chance to wrap up your work in CSE 154 with a final portfolio you can publish, showcasing your exploration of web programming technologies. As always, we encourage you to explore the new material covered in class, as well as related (but optional) content we may link to along the way, as long as you follow the CSE 154 Code Quality Guidelines and adhere to Academic Integrity policies. In past quarters, some students have built upon their Creative Project each week. You may choose to do a new website for each CP or build on the existing project from previous CP's.

As long as you meet the requirements outlined below, you have freedom in what kind of website you create.
* **IF YOUR CP CLOSELY RESEMBLES SECTION OR LECTURE CONTENT, YOU WILL BE INELLIGIBLE FOR CREDIT**
* This CP is designed to give you an opportunity to practice writing both client (JS) and server-side (Node.js) code on your website. This is a great chance to think about how your project could showcase what you've learned so far in web programming for your own code portfolio after the quarter ends, so we encourage you to explore implementing different features of your web service!

## External Requirements
* Your project must include the following seven files at a minimum (make sure that all files are **correctly named**):
  * `index.html` - main page of your website
  * `styles.css` - file to style your `.html` file
  * `index.js` - containing your client-side JavaScript code
  * **new:** an `app.js` web service your `index.js` file fetches from with at least two different requests.
  * **new:** an `APIDOC.md` file to document your `app.js` web service (see below for more details on what should be included).
  * **new:** your project's `package.json` file generated using `npm init` and including any dependencies you use (at minimum `express`). Remember that you should never directly edit this file, as `npm` will update it as needed.
  * **new:** a `.txt` or `.json` file that at least one of your endpoints reads/writes from

**Important Note**: all static "view" files (HTML/CSS/Client-side JS/any images) must be inside a `public` folder as discussed in class. All other files (e.g. your Node.js/Express web service) should be at the root. DO NOT push `node_modules` in your `cp4-node-api` repo. To help with this we have included a `.gitignore` file so you don't have to. Make sure to not modify this file or move it from the root of your repo. We will run `npm install` using your submitted `package.json` to install the modules necessary for your project. **We will not grade assignments with incorrect directory structure. Please confirm yours is correct with a TA/Instructor if you are unsure.**

* Similar to what you'll see in the next assignment, you will be writing both client-side JS and Node.js to incorporate in your website, where your `index.js` makes AJAX requests to **your** Node.js web service which responds with information.
* Client-Side HTML and CSS must be **non-trivial**.
* Client-Side JavaScript: Your website must somehow dynamically load information from the web API you've implemented and present information from that response on the page. This requires that you must:
  * Respond to some event (any UI event **other than the `load` event** ) to determine when to fetch the data (using `fetch`). You must make at least three (3) fetch calls (one to each of your defined endpoints) and each fetch must be in response to a *different* UI event (**other than the `load` event**).
  * Dynamically integrate the data returned from your API into the page by manipulating the DOM elements of the page in some non-trivial way using `element.appendChild`, `element.removeChild`, or `element.replaceChild`.
  * Use the `statusCheck` function from lecture/section to throw an Error if the fetch response status is not `ok` before processing the data. You are required to use this function (with JSDoc) in your AJAX programs.
  * Handle any errors caused in the fetch request/response process by displaying a helpful message to the user on the page (i.e. without using `alert`, `console.log` or `console.error`). To do so, you should define a function (e.g. `handleError`) to implement the error-message-displaying.

* **new:** Your Node.js web service should handle at least three (3) **distinct, different** endpoints. At least one endpoint must output JSON data (i.e. at least something with a user-defined attribute or index) and at least one must output plain text. You must handle at least one POST endpoint (described below) but you may choose whether your other endpoints use GET or POST.
  * As mentioned above, at least one endpoint needs to use POST.
    * This endpoint must both read and write to either a `.txt` or `.json` file. This can be the same file or multiple different files.
    * You must use the promisified version of `readFile` and `writeFile` as shown in class. Feel free to reach out on Ed or in office hours if you have questions about this.
    * You must properly handle server errors (with a `500` error header and a descriptive message) when reading and writing to files.
  * You must properly handle at least one invalid request (with a `400` error header and a descriptive message) as shown in class.
    * You are encouraged to handle more than one type of invalid request but it is not required. You may include other error codes as well, but must support at least one `400` (invalid client request) error for full credit.
  * All of your Node endpoints should do something that is not trivial.
    * Examples of this could include updating the server state, storing information in a variable stored on the server side, customizing responses based on a parameter and/or reading/writing to a file. An endpoint that looks like the example below (**only** setting the type and sending a hardcoded response) will **not** meet the requirements for this cp.
    ```javascript
    app.<type>(() => {
      res.type('<insert type>');
      res.send('<insert response>');
    });
    ```
  * You should implement _at minimum_ **two (2)** non-trivial, named functions in your `app.js` code.

## API Documentation
  * Document your API in [`APIDOC.md`](APIDOC.md). An `.md` file is written in Markdown, documentation on which is [here](https://docs.gitlab.com/ce/user/markdown.html).
  * Each endpoint should be well documented and include:
    * the request format (i.e. the path), including any parameters
    * the request type (`GET` or `POST`)
    * the format of the returned data (`Plain Text` or `JSON`)
    * a description of the endpoint
    * an example request and response
    * error handling: you should document **any and all** errors that your endpoint might respond with (this includes both `400` and `500` errors)

## Internal Requirements
For full credit, your page must not only match the External Requirements listed above, you must also demonstrate that you understand what it means to write code following a set of programming standards. Your code should maintain good code quality by following the [CSE154 Code Quality Guide](https://courses.cs.washington.edu/courses/cse154/codequalityguide). Make sure to review the section specific to JavaScript! We also expect you to implement relevant feedback from previous assignments. Some guidelines that are particularly important to remember for this assignment are included below.

### HTML/CSS
* Continue to follow the standards for your HTML/CSS, including consistent whitespace/indentation, proper use of classes/ids, separation of languages, avoiding redundancy in CSS, etc.
* HTML and CSS files must be well-formed and pass the linters.

### Client-Side JS
* Continue to follow the standards in the JS Code Quality Guidelines and CP2/HW2/CP3/HW3 specs. This includes good use of function decomposition, separation of JS from HTML/CSS, minimizing module-global variables, etc. A few reminders of Code Quality requirements for JS so far:
  * Any `.js` code you write must declare `"use strict";` at the top.
  * All client-side JS must use the module-global pattern (remember that you should not use this module pattern in `app.js` though).
  * Define program constants with `UPPER_CASED` naming conventions (using `const` instead of `let` in JS). Examples of common program constants include a file path to your images if you are working with many images in your JS or an API base url as demonstrated in class.
  * Decompose your JS by writing smaller, more generic functions that complete one task rather than a few larger "do-everything" functions.
  * Localize your variables as much as possible. You should not use any global variables (i.e. variables outside the module pattern) - see [Code Quality Guide](https://courses.cs.washington.edu/courses/cse154/codequalityguide/_site/javascript/#module-pattern) for reference. Only use module-global variables whenever absolutely necessary. Do not store DOM element objects, such as those returned by the `document.getElementById` function, as module-global variables.
  * Limit your use of anonymous functions - meaningful behavior should be factored out with a named function.
  * Do not make unnecessary requests to your API. That is, there should be no code in your JS that requests from an API and **never** does anything with the response.
  * All your JS code must pass ESLint with no errors.

### Server-Side JS
* **New CP4-Specific Requirements** (in addition to following the Node.js section of the Code Quality Guide):
  * Your Node.js web service should specify the correct content type by setting the header using a consistent convention before outputting a response (this includes errors). These headers should only be set when necessary and should not be overridden.
  * Your Node.js code should not generate any HTML.
  * Similar to your client-side JS, decompose your Node.js/Express API by writing smaller, more generic functions that complete one task rather than a few larger "do-everything" functions - no function should be more than 30 lines of code, and your Node.js should have **at least** two (2) helper functions defined and used. Consider factoring out important behavior for your different GET/POST requests into functions.

### All
Requirements continuing from previous CP/HW assignments:
* Your HTML, CSS, JavaScript, and Node.js should demonstrate consistent and readable source code aesthetics as demonstrated in class and detailed in the [CSE 154 Code Quality Guidelines](https://courses.cs.washington.edu/courses/cse154/codequalityguide). Part of your grade will come from using consistent indentation, proper naming conventions, curly brace locations, etc.
* Place a comment header in each file with your name, section, and a brief description of the file (examples have been given on previous assignments).
* If you want to explore other HTML/CSS/JS features beyond what we've taught in class, you must cite what resources you used to learn them in order to be eligible for credit. We strongly encourage students to ask the staff for resources instead of finding online tutorials on their own (some are better than others).
* **New CP4-Specific Requirements** (in addition to following the Node.js section of the Code Quality Guide):
  * Document your Node.js functions using the same JSDoc requirements as your client-side JS file (e.g. `@param` and `@return`).
  * Briefly document any request-handling functions (e.g. `app.get`, `app.post`, etc.) with a comment above the endpoint describing what it does.
  * Include a description of your Node.js web service at the top of the page (as part of your header comment).
  * Use your `APIDOC.md` for a more descriptive public documentation of your API (used by clients).

## Grading
Grading for Creative Projects is lighter with the chance to explore and learn without the overhead of having to match strict external requirements. Our goal is to give you feedback, particularly on the internal requirements and documentation, so you can incorporate this feedback in your homework assignments which will be worth more towards your final grade.

This CP will be out of 10 points and will likely (subject to adjustments) be distributed as:

- External Correctness (~50%)
- Internal Correctness (~40%)
- Documentation (~10%)

## Academic Integrity
Creative Projects are unique in that students may look for outside resources for inspiration or assistance in accomplishing their goals. On occasion students may wish to use portions of sample code that has been obtained on our course website or others. In order to avoid academic misconduct for a Creative Project in CSE 154 you must include school appropriate content and follow the Academic Integrity/Collaboration Policies outlined in more detail on the syllabus. If we find inappropriate content or plagiarism in CPs **you will be ineligible for any points on the CP**. Ask the instructor if you're unsure if your work is cited appropriately. Any external sources like images should be cited where used in the source code or (ideally) visible in a page footer. Refer to this [copyright example](https://courses.cs.washington.edu/courses/cse154/24sp/resources/assets/code-examples/copyright-examples/copyrightexample2.html) page for how to cite images from different sources.
