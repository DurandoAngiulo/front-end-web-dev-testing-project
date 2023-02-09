# Front End Development Project
This project is designed to exercise your web development skills, specifically focusing on Javascript and testing application code using a tool called [Cypress](https://www.cypress.io/). The goal of this project is to install a web application on your machine and write end-to-end tests that cover the outlined test cases below.

### Setup
1. Download this repository via zip file or clone it on your local machine
2. Install Node v14
    - Recommended to use nvm (Node Version Manager). [Here is a link for Linux/Mac machines](https://github.com/nvm-sh/nvm), and a separate [link for Windows machines](https://github.com/coreybutler/nvm-windows)

### How to run
1. Open up a terminal or command prompt and switch to the directory where you installed this repository
2. To install the application's dependencies, run `yarn install`
3. To run the application, run `yarn dev`
4. To run Cypress, open up a separate terminal, navigate to this repo's directory and run `yarn cypress:open`
5. At this point, you should have 2 applications running - the real-world payment application and the cypress application
6. You are now ready to start writing tests! Open this repository in your favorite code editor (We recommend [VSCode](https://code.visualstudio.com/) for front-end development) and review the project structure. The test files that you will be updating are located at `cypress/tests/ui`. The source code for the application is located in the `src` directory

### Test coverage to be added
The following test cases are currently missing from the end-to-end test suite and thus we are asking you to help us out by resolving these gaps in test coverage. The test cases are outlined at a high level - you will be responsible for deciding which assertions are valuable and sufficient in order to make sure the test effectively covers the functionality being exercised.

#### Test cases
1. Sign up as a new user, onboard by creating a new bank account, and logout
    - fill in the empty test named `"should allow a visitor to sign-up, login, and logout"` within `cypress/tests/ui/auth.spec.ts`
1. Send a payment transaction to a contact as an existing user
    - fill in the empty test named `"navigates to the new transaction form, selects a user and submits a transaction payment"` within `cypress/tests/ui/new-transaction.spec.ts`
1. Update account settings as an existing user
    - fill in the empty test named `"updates first name, last name, email and phone number"` within `cypress/tests/ui/user-settings.spec.ts`

### Helpful notes
- Cypress has great docs so it is advised to refer to them for questions/guidance on writing great end-to-end tests. [Here are the intro docs](https://docs.cypress.io/guides/core-concepts/introduction-to-cypress#What-you-ll-learn), which is recommended reading ahead of writing your first test
- The application is seeded with fresh data every time it is started (by running `yarn dev`). This seed data can be found at `data/database-seed.json`
- You can use any user you'd like for testing purposes, which can be found in the database-seed JSON file. The default password for all users is `s3cret`
- While cypress is running (`yarn cypress:open`), any saved modifications to the test files will automatically reload cypress and re-run the tests
- The real-world app and example Cypress tests are written in [Typescript](https://www.typescriptlang.org/), which is a typed programming language built on top of Javascript. It is **not** required for you to write your tests with Typescript, plain Javascript is perfectly valid
- The existing cypress tests in `cypress/tests/ui` can be used as inspiration for how to structure your tests and take advantage of various patterns/selectors within cypress
- Cypress has a notion of custom commands. Throughout the existing tests you will see 2 commonly referenced - `getBySel` and `getBySelLike`:
    - `getBySel` yields elements with a `data-test` attribute that match a specified selector.
    - `getBySelLike` yields elements with a `data-test` attribute that contains a specified selector.
```
// These are custom commands that are helpful when writing tests. Feel free to use these or even make your own if you think it would be a useful abstraction!
Cypress.Commands.add('getBySel', (selector, ...args) => {
  return cy.get(`[data-test=${selector}]`, ...args)
})

Cypress.Commands.add('getBySelLike', (selector, ...args) => {
  return cy.get(`[data-test*=${selector}]`, ...args)
})
```

### Solutions are Judged on
1. Readability of your code - Can another developer review your code and easily understand the intent/purpose?
1. Maintainability of your code - Will this code be easy for another developer to update in the future? Have you considered abstracting reusable code/functions? Do the tests pass consistently? Can individual tests run be in isolation?
1. Correctness - All user stories have been sufficiently tested and reasonable assertions are made to guarantee the app works as expected
1. Documentation - Helpful comments or notes added to the test files and/or readme. You can also add notes regarding any questions or issues you encountered while adding test coverage and how you resolved or worked around them


### Submission
Submit your project by providing a github url or zip file containing your submission.
