## Jest Test Driven Development Practice

This project is my first use of the Jest testing framework and test driven development, which I used to create a series of pure functions for performing simple arithmetic, string manipulation, and array analysis. With my current experience in TDD, I have found the process - writing tests, followed by the simplest code that will pass it, before continuing to refine with new tests to catch different cases - to produce shorter and easier to understand code, and while initially slow to progress it results in fewer bugs, as they can be caught individually and early.

To make writing the tests themselves quicker, I developed a narrow data-oriented approach that I was able to expand to encompass all of the requirements for this project, though it does not extend to all Jest testing usecases, such as non-pure functions, those requiring object mocks, or use of methods like beforeAll, beforeEach, afterEach, and afterAll. 

<br>

My approach defines a test suite as an array of objects each with a function to be tested, a description of the function, and an array of test cases, with each case itself being an array. 

Each test case array requires at minimum a description of the test case, an array of inputs to the function, and the expected output, using the 'toBe' Jest matcher by default.

Optionally, a different matcher can be specified as a string along with any extra parameters it takes in as an array. This is all used in the line of code:

```
expect(testItem.function(...inputs))[matcher](expected, ...matcherParams)
```
<br>

I also added the ability to check for errors being thrown by functions when neccessary. This requires slightly different syntax, so this case is detected by "throw" being present in the name of the matcher, since all standard Jest matchers that check for errors contain this string. In this case, a slightly different line of code is run:

```
expect(() => testItem.function(...inputs))[matcher](expected, ...matcherParams)
```

These two lines encompass all testing syntax necessary for the pure functions I made as part of this project, allowing cases to be written more easily as short arrays rather than blocks of code, for example the test cases for a function that performs a Caesar Cypher on a given string is written:

```
// Defines test cases for a function that performs a Caesar Cipher shift by a specified amount on a string
const ceasarCases = [
    ['Shift right', ['ace', 3], 'dfh'],
    ['Shift right (2)', ['gnb', 7], 'nui'],
    ['Shift left', ['xpq', -4], 'tlm'],
    ['End-of-alphabet looping', ['adv', -5], 'vyq'],
    ['Do nothing', ['gdq', 0], 'gdq'],
    ['Full cycle leaves result unchanged', ['hci', 26], 'hci'],
    ['Handle uppercase letters', ['HDU', 2], 'JFW'],
    ['Ignore non-alphabetical characters', ['abG&")!*846`@~{/?, 2]', 10], 'klQ&")!*846`@~{/?, 2]']
]
```

<br>

GitHub repository: https://github.com/MilesRigby/odin-jest-test/tree/main