# Authentication and Testing Sprint Challenge

**Read these instructions carefully. Understand exactly what is expected _before_ starting this Sprint Challenge.**

This challenge allows you to practice the concepts and techniques learned over the past sprint and apply them in a concrete project. This sprint explored **Authentication and Testing**. During this sprint, you studied **authentication, JSON web tokens, unit testing, and backend testing**. In your challenge this week, you will demonstrate your mastery of these skills by creating **a dad jokes app**.

This is an individual assessment. All work must be your own. All projects will be submitted to Codegrade for automated review. You will also be given feedback by code reviewers on Monday following the challenge submission. For more information on the review process [click here.](https://www.notion.so/lambdaschool/How-to-View-Feedback-in-CodeGrade-c5147cee220c4044a25de28bcb6bb54a)

You are not allowed to collaborate during the sprint challenge. However, you are encouraged to follow the twenty-minute rule and seek support by dropping a :wave: in your help channel should a blocker arise.

_Sprint challenges open at Midnight PST on Thursday and close at 5pm PST on Friday. You will receive feedback on what you have submitted by 5pm. No retakes will be accepted._

## Introduction

Dad jokes are all the rage these days! In this challenge, you will build a real wise-guy application.

Users must be able to call the `[POST] /api/auth/register` endpoint to create a new account, and the `[POST] /api/auth/login` endpoint to get a token.

We also need to make sure nobody without the token can call `[GET] /api/jokes` and gain access to our dad jokes.

We will hash the user's password using `bcryptjs`, and use JSON Web Tokens and the `jsonwebtoken` library.

## Instructions

### Task 1: Project Set Up

- [ ] Fork and clone the repo. Delete your old fork from Github first if you are repeating this Unit.
- [ ] Open the assignment in Canvas and click on the "Set up git" option.
- [ ] Follow instructions to set up Codegrade's Webhook and Deploy Key.
- [ ] Push your first commit: `git commit --allow-empty -m "first commit" && git push`.
- [ ] Check to see that Codegrade has accepted your git submission.

For a step-by-step on setting up Codegrade see [this guide.](https://www.notion.so/lambdaschool/Submitting-an-assignment-via-Code-Grade-A-Step-by-Step-Walkthrough-07bd65f5f8364e709ecb5064735ce374)

### Task 2: Project Requirements

Your finished project must include all of the following requirements (further instructions are found inside each file):

- [ ] An authentication workflow with functionality for account creation and login, implemented inside `api/auth/auth-router.js`.
- [ ] Middleware used to restrict access to resources from non-authenticated requests, implemented inside `api/middleware/restricted.js`.
- [ ] A minimum of 2 tests per API endpoint, written inside `api/server.test.js`.

**Notes:**

- Execute all tests locally (Codegrade's and your own) by running `npm test`.
- You are welcome to create additional files but **do not move or rename existing files** or folders.
- Do not alter your `package.json` file except to install extra libraries. The "test" script has been added for you.
- The database already has the `users` table, but if you run into issues, the migration is available.
- In your solution, it is essential that you follow best practices and produce clean and professional results.
- Schedule time to review, refine, and assess your work and perform basic professional polishing including spell-checking and grammar-checking on your work.
- It is better to submit a challenge that meets MVP than one that attempts too much and does not.

### Task 3: Stretch Goals

**IMPORTANT:** Don't break MVP by working on stretch goals! Run `npm test` and keep an eye on your tests.

After finishing your required elements, you can push your work further. These goals may or may not be things you have learned in this module but they build on the material you just studied. Time allowing, stretch your limits and see if you can deliver on the following optional goals:

- [ ] Write at least 4 tests per endpoint.
- [ ] Extract user validation into a separate method and write unit tests for it.
- [ ] Implement authentication using sessions instead of tokens. Build separate auth endpoints & middleware for this to avoid breaking tests.

## Submission format

- [ ] Submit via Codegrade by committing and pushing any new changes.
- [ ] Create a pull request to merge `<firstName-lastName>` branch into `main`.
- [ ] Please don't merge your own pull request and make sure **you are on your own repo**.
- [ ] Check Codegrade for automated feedback.
- [ ] Check Codegrade on Monday following the Sprint Challenge for reviewer feedback.
- [ ] Any changes pushed after the deadline will not receive any feedback.

## Interview Questions

Be prepared to demonstrate your understanding of this week's concepts by answering questions on the following topics.

1. Differences between using _sessions_ or _JSON Web Tokens_ for authentication.
 - Most modern systems use JSON web tokens for authentication. The main difference is that the state of the json web tokens are stored on the client side, while the state of the sessions are stored on the server side.
 Using JSON web tokens really help with issues like scalabililty and are really helpful for mobile apps.


2. What does `bcryptjs` do to help us store passwords in a secure manner?
 - It hashes our passwords so they are kept secret from people we don't want to know our passwords. Hashes use a hash algorithm, which isn't essential to know in the case of being able to use a hash algorithm. Which in the case of bcrypt, utilizes a certain time of processing in order to have passwords and encrypting to be able to keep up with processing power.


3. How are unit tests different from integration and end-to-end testing?
 - Unit tests are for specific modules of code and are supposed to be used so that all lines of code are useful, tested and accounted for. Integration testing is used for integrating and testing the interconnectedness of different components within your system. End to end testing is used to test from the client end all the way to the server end part of the code. Unit tests are more grandular, and they should be so numerous that running every single unit test within your suite should take up too much time. Also, due to the nature of unit tests, the interconnectedness of each code part, or dependencies within each class or section, are supposed to be mocked, so that only the class itself is being tested. The downside is, that if you run all of your unit tests, the dependencies within your code base are not tested!  Which is why we need integration tests and end to end tests. Smoke tests, which are a subsection of end to end tests, are the tests we find critical to our system and we run to know if our code base is figuratively on fire, as these are the critical business aspects of our code, that if don't work, risk a critical meltdown of everything in our code base that we care about.


4. How does _Test Driven Development_ change the way we write applications and tests?
 - Test driven development is the method of which we write the tests first, then write the code to fulfill the tests, and then refactor the code. In this way we specify what we want the code to do, as well as cover all of the edge cases, and write the simplest code possible to fulfill that requirement.
 It in itself feels a little backwards to write code in this way, but it drasticly decreases the amount of boilerplate code within the codebase as well as increases the speed of which we code, because we organize and think of edgecases beforehand.
 There are also a lot of good resources and tools that work with test driven development, and help cover edge cases, things such as linters, and mutation test runners.