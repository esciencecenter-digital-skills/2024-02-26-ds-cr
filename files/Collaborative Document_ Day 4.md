![](https://i.imgur.com/iywjz8s.png)


# Collaborative Document: Day 4

2024-02-26--29 Good Practices in Research Software Development Day 4.

Welcome to The Workshop Collaborative Document.

This Document is synchronized as you type, so that everyone viewing this page sees the same text. This allows you to collaborate seamlessly on documents.

----------------------------------------------------------------------------

##  🫱🏽‍🫲🏻 Code of Conduct

Participants are expected to follow these guidelines:
* Use welcoming and inclusive language.
* Be respectful of different viewpoints and experiences.
* Gracefully accept constructive criticism.
* Focus on what is best for the community.
* Show courtesy and respect towards other community members.
 
## 🎓 Certificate of attendance

If you attend the full workshop you can request a certificate of attendance by emailing to training@esciencecenter.nl .

## ⚖️ License

All content is publicly available under the Creative Commons Attribution License: [creativecommons.org/licenses/by/4.0/](https://creativecommons.org/licenses/by/4.0/).

## 🙋Getting help

To ask a question, raise your hand in zoom. Click on the icon labeled "Reactions" in the toolbar on the bottom center of your screen,
then click the button 'Raise Hand ✋'. For urgent questions, just unmute and speak up!

You can also ask questions or type 'I need help' in the chat window and helpers will try to help you.
Please note it is not necessary to monitor the chat - the helpers will make sure that relevant questions are addressed in a plenary way.
(By the way, off-topic questions will still be answered in the chat)


## 🖥 Workshop website

[link](https://esciencecenter-digital-skills.github.io/2024-02-26-ds-cr/)

🛠 Setup

[link](https://esciencecenter-digital-skills.github.io/2024-02-26-ds-cr/#setup)

Slides

[link](https://lyashevska.github.io/ds-cr-slides/)

## 👩‍🏫👩‍💻🎓 Instructors

Sander van Rijn, Sven van der Burg, Olga Lyashevska

## 🧑‍🙋 Helpers

Dani Bodor

## 🗓️ Agenda
| Time | Topic |
|--:|:---|
| 9:00 | Welcome and icebreaker |
| 9:15 | Introduction to testing |
| 10:15 | Coffee break |
| 10:30 | Introduction to Continuous Integration |
| 11:30 | Coffee break |
| 11:45 | More advanced testing |
| 12:45 | Wrap-up |
| 13:00 | END |


## Welcome
- Feedback from yesterday ""Buzz
- Questions about yesterday?


## 🔧 Exercises


### Exercise: Test-driven development

The function `fizz_buzz()` takes an integer argument and returns it, BUT:

- It fails on zero or negative numbers
- It returns "Fizz" on multiples of 3
- It returns "Buzz" on multiples of 5
- It instead returns "FizzBuzz" on multiples of 3 and 5

You will use test-driven development to write this function.

1. Create an empty function `fizz_buzz()`
2. Go through the conditions listed above, one by one:
    1. Write a test for the condition
    2. Edit the `fizz_buzz()` function until the test passes
3. Share your tests in the collaborative document.

What did you think of this style of developing?

- Sample solution:
### Solution fizz buzz
```python=
import pytest

def fizz_buzz(input):
    if input <= 0:
        raise ValueError('Negative or zero input not allowed')
    if input % 3 == 0 and input % 5 == 0:
        return 'FizzBuzz'
    if input % 3 == 0:
        return 'Fizz'
    if input % 5 == 0:
        return 'Buzz'
    return input

def test_fizz_buzz():
    with pytest.raises(ValueError):
        fizz_buzz(0)
    with pytest.raises(ValueError):
        fizz_buzz(-2)
    assert fizz_buzz(1) == 1
    assert fizz_buzz(3) == 'Fizz'
    assert fizz_buzz(4) == 4
    assert fizz_buzz(5) == 'Buzz'
    assert fizz_buzz(6) == 'Fizz'
    assert fizz_buzz(10) == 'Buzz'
    assert fizz_buzz(15) == 'FizzBuzz'
```


### Exercise: Full-cycle collaborative workflow

The exercise takes 30-40 minutes.

In this exercise, everybody will:

A. Set up automated tests with GitHub Actions
B. Make test fail / find a bug in their repository
C. Open an issue in their repository
D. Then each one will clone the repo of one of their exercise partners, fix the bug, and open a pull request (GitHub)
E. Everybody then merges their co-worker’s change


#### Step 1: Create a new repository on GitHub

- Select a different repository name than your colleagues (otherwise forking the same name will be strange)
- Before you create the repository, select “Initialize this repository with a README” (otherwise you try to clone an empty repo).
- Share the repository URL with your exercise group via shared document or chat

#### Step 2: Clone your own repository, add code, commit, and push

Clone the repository.

Add a file `example.py` containing:

```python=
def add(a, b):
    return a + b

def subtract(a, b):
    return a + b  # do not change this line until prompted to do so.
```

Write a test function `def test_add()` in a separate file `test_example.py` for `add` to check that this function is working properly. Do NOT add a test function for `subtract` (yet).
Run pytest to ensure it works 

Then stage the file (`git add <filename>`), commit (`git commit -m "some commit message"`),
and push the changes (`git push`).


#### Step 3: Enable automated testing

In this step we will enable GitHub Actions.
- Select "Actions" from your GitHub repository page. You get to a page "Get started with GitHub Actions". 
- Select the button for "Set up this workflow" under Python Application.

![](https://i.imgur.com/7QOplAg.png)
Select “Python application” as the starter workflow.

GitHub creates the following file for you in the subfolder `.github/workflows`:


   ```yaml
# This workflow will install Python dependencies, run tests and lint with a single version of Python
# For more information see: https://help.github.com/actions/language-and-framework-guides/using-python-with-github-actions

name: Python application

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  build:

    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v3
    - name: Set up Python 3.9
      uses: actions/setup-python@v3
      with:
        python-version: 3.9
    - name: Install dependencies
      run: |
        python -m pip install --upgrade pip
        pip install flake8 pytest
        if [ -f requirements.txt ]; then pip install -r requirements.txt; fi
    - name: Lint with flake8
      run: |
        # stop the build if there are Python syntax errors or undefined names
        flake8 . --count --select=E9,F63,F7,F82 --show-source --statistics
        # exit-zero treats all errors as warnings. The GitHub editor is 127 chars wide
        flake8 . --count --exit-zero --max-complexity=10 --max-line-length=127 --statistics
    - name: Test with pytest
      run: |
        pytest
   ```



Commit the change by pressing the "Start Commit" button.

#### Step 4: Verify that tests have been automatically run

Observe in the repository how the test succeeds. While the test is executing, the repository has a yellow marker.
This is replaced with a green check mark, once the test succeeds.

![](https://i.imgur.com/b8dI8XH.png)

Green check means passed.

Also browse the "Actions" tab and look at the steps there and their output.

#### Step 5: Add a test which reveals a problem

After you committed the workflow file, your GitHub repository will be ahead of your local cloned repository. Update your local cloned repository:

```
$ git pull origin main
```

Next uncomment add a test function `test_subtract` for to check that the `subtract` function can subtract two numbers from each other, and push it to your remote repository.
Verify that the test suite now fails on the “Actions” tab (GitHub).


#### Step 6: Open an issue on GitHub
Open a new issue in your repository about the broken test (click the “Issues” button on GitHub and write a title for the issue). The plan is that your colleague will fix the issue through a pull request

#### Step 7: Fork and clone the repository of your colleague

Fork the repository using the GitHub web interface. 
Make sure you clone the fork after you have forked it. Do not clone your colleague’s repository directly.


#### Step 8: Fix the broken test

Fix the function now and run pytest to check that it works.
Then push to _your fork_. Check whether the action now also passes.

#### Step 9: Open a pull request (GitHub)

Then before accepting the pull request from your colleague, observe how GitHub Actions automatically tested the code.

If you forgot to reference the issue number in the commit message, you can still add it to the pull request: `my pull request title, closes #NUMBEROFTHEISSUE`

#### Step 10

Observe how accepting the pull request automatically closes the issue (provided the commit message or the pull request contained the correct issue number).

Discuss whether this is a useful feature. And if it is, why do you think is it useful?



## 🧠 Collaborative Notes

### Questions from yesterday/previous days:

#### In which situations would you opt for Object Oriented Coding
A: it depends on many factors. E.g., some languages (e.g. Python) force OOC. In others (e.g. Java), it is highly encouraged. In other languages it's an option. 
Generally, when a you expect a group of functions or properties or (types of) data to be reused a lot, OOC is a good choice.

### Testing

#### Why test?
- Preserve functionality
    - Detect errors early
    - Facilitate reproducibility (across systems)
- Help users
    - Verify correct installation
    - Improve correctness for research output
- Enable developers
    - Make refactoring easier
    - Simplify external contributions
- **Manage complexity**

#### Types of testing
- Unit test
    - Smallest possible unit
    - No dependency on outside code...
    - (...replace them by mocks, stubs, etc)
- Integration test
    - Test unit interaction
    - Can be on small scales, or system wide, or anything in between

#### How much testing is enough?
Ideally: As many as you can and as many as necessary...

In practice: there are some metrics (but they are not perfect)

##### Metrics:
- Ratio (lines of code):(lines of tests)
    - Target 1:3
- Coverage (% of lines of code that the tests execute)
    - Target >= 80%
    - IMPORTANT: coverage **DOES NOT** mean that the lines give the expected output, just that they are executed at all
- These metrics are necessary, but not sufficient.
    - It would easily be possible to write tests that hit all metrics and targets but are completely meaningless. The targets are just there to guide you rather than be the goal of test writing.


### Using PyTest (for Python)
```bash
mkdir pytest-example
cd pytest-example

# create and activate virtual environment (not needed if you are already working in a conda env)
python -m venv venv
source venv/Scripts/activate

# install pytest
pip install pytest

# check installation
pytest --version

# create a new file
nano example.py
```

```python
def add(a, b):
    return a+b
```

To test this, you could manually start a python session and feed some examples into the function and see that the results are correct.
Instead we will create an automated test for it in the python file

```python
def add(a, b):
    return a+b

def test_add():
    assert add(2,3) == 5
    assert add(1,0) == 1
```

Now we can ask pytest to test it for us, and give us some metrics

```bash
pytest -v example.py
```

But what if we gave a "bad test"

```python
def add(a, b):
    return a+b

def test_add():
    assert add(2,3) == 5
    assert add(1,0) == 1
    assert add(2,0) == 0
```

Pytest now fails, and gives a lot of information to help you find where and why the test fails.
Pytest by default only runs functions that start or end with the word "test"

Especially for large projects, it's better to have tests in a (or multiple) separate test file(s) rather than in the same file as your functionality

```python
from example import add

def test_add():
    assert add(2,3) == 5
    assert add(1,0) == 1
```

Pytest automatically looks for all files that start with "test_", and run all functions inside that start or end with test.

So we can now just run `pytest` in the terminal without specifying any location or function 

So if the file looked like this
```python
from example import add

def test_add():
    assert add(2,3) == 5
    assert add(1,0) == 1

def test_string_add():
    assert add("hi ", "there") == "hi there"

def helper():
    print("hi there")
```

Running `pytest` in this case will execute the first 2 functions, but not the last because it doesn't start or end with "test".


Note that tests are considered as passed if no error is returned, irrespective of the actual output.


#### Pure functions are very easy to test
Because they are
- deterministic
- have a return value
- have no side effects
- have referential transparency


#### Take away
- Use pure functions when possible
- Testing does not hgave to be hard
    - In practice you often test anyway, but often throw them away
- You don't have to strive to 100% coverage
- Aim for a balance between unit and integration tests
- Testing removes the dread of refactoring
    - because you can easily ensure that things still work
-  Collaborators (including future you) will thank you if you use testing!

#### Test driven development
A specific style of software development that rather than first writing functionality and then write tests to ensure that the functionality works as intended, instead you first write the tests that check that your functions do as intended, and then write the functions to make it happen afterwards.

#### Discussing answers to FizzBuzz exercise
- It's good to test edge cases as well as obvious cases, but not necessary to go overboard (e.g. testing 100s of similar examples).
- How to test many different conditions without explicitly writing each?
    - usage of loops, use [pytest parametrize](https://docs.pytest.org/en/6.2.x/parametrize.html), more complex options exist as well (you can look them up online, we will not cover these).


### Continuous Integrations
Automating the integration of code changes from multiple contributors into a single software project
_Something_ will happen on a change to your code base, e.g.:
- Automated testing
- Linting (style/quality checks)
- Security analysis
- Send messages
    - slack, discord, ...
- Building/compiling
    - documentation
    - environment
- Deployment (PyPi, Kubernetes, GitHub pages)
    - e.g. these slides

## 📚 Resources

### Testing
[Pytest parametrize](https://docs.pytest.org/en/6.2.x/parametrize.html)
[Advanced] [Hypothesis for property-based testing in Python](https://hypothesis.readthedocs.io/en/latest/quickstart.html#an-example)

### Continuous Integration
[Learn GithubActions](https://docs.github.com/en/actions/learn-github-actions)
[GitHub Marketplace](https://github.com/marketplace?type=actions)

[Github secrets](https://docs.github.com/en/actions/security-guides/using-secrets-in-github-actions)
