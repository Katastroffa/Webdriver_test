# Webdriver_test
WebDriver I/O
#1. Requirement
1.1. Node.js:
Install the latest Node.js from https://nodejs.org/en/
*To check if you have Node.js installed, run this command in your terminal:
node -v
*To confirm that you have npm installed you can run this command in your terminal:
npm -v

1.2. Git:
Install the latest Git from https://git-scm.com/
If you have an existing project and you want to start using Git to keep track of its changes, run 
git init 
from the existing project’s directory: git init creates a new .git subdirectory in the current directory. 
This is where Git stores your configurations.

1.3. Eslint (optional)
Local Installation and Usage
npm i eslint
If you want to include ESLint as part of your project's build system, we recommend installing it locally. You can do so using npm:
npm install eslint --save-dev
You should then setup a configuration file:
./node_modules/.bin/eslint --init
After that, you can run ESLint on any file or directory like this:
./node_modules/.bin/eslint (yourfile.js)

#2. Creating project

2.1. Create project folder:
In terminal open folder:
cd projects/

Create a folder for automation project.

mkdir automation-webdriver-test
cd automation-webdriver-test

2.2. Initialize your project:
 npm init
It will create package.json file.

#3. Modules installation and configuration

3.1. Install webDriver I/O:
 npm i --save-dev webdriverio
3.3. Install Selenium:
 npm i --save-dev wdio-selenium-standalone-service
3.3. Create WebDriver I/O configuration:
 ./node_modules/.bin/wdio config
 
Answers for following items and click ENTER:

1.Where do you want to execute your tests?: On my local machine
2.Which framework do you want to use?: mocha
3.Type Yes for the following: Shall I install the framework adapter for you? (Y/n): Y
4.Type ./test/**/*.js 
5.Where are your test specs located? ./test/**/*.js
6.Which reporter do you want to use? dot
7.Do you want to add a service to your test setup? selenium-standalone
8.Level of logging verbosity: silent
9.In which directory should screenshots gets saved if a command fails? (./errorShots/)
Optional:
Type https://artsenius.github.io and click Enter:
1.What is the base url? https://artsenius.github.io

#4. Creating the first test
4.1. Create test folder:
mkdir test
cd test
4.2. Create test.js file:
touch test.js
open test.js
4.3. Add the first test:(Optional)
const assert = require('assert');

describe('Page opening', function () {
  it('get title', function(){
    browser.url('/Bug-Tracker'); //open baseUrl + string passed in .url() function
    let title = browser.getTitle(); //get page title and assign it to the "title" variable
    browser.pause(5000); //just pause to visually see that something is happening on the page
    console.log(title); //log "title" variable
    assert.equal(title, 'Bug Tracker', 'Title is incorrect'); //compare that "title" variable equals to "Bug Tracker" and error-message if not
  })
});

#5. WebDriver I/O initial configuration
5.1. Add a script for running WebDriver I/O tests:
Open package.json and modify test script:
"test": "wdio wdio.conf.js"

#6. Install additional reporters
6.1. Spec reporter:
npm install wdio-spec-reporter --save-dev
6.2. Allure reporter:
npm install wdio-allure-reporter --save-dev

#7. wdio.conf.js configuration
7.1. Turn on sync mode:
sync: false => sync: true
7.2. Configure browser:
browserName: 'firefox' => browserName: 'chrome'
7.3. Configure reporters:
uncomment // services: [], and then:
services: ['selenium-standalone'],
7.4. Configure services:
uncomment // reporters: ['dot'], and then:

reporters: ['dot', 'spec', 'allure'],
  reporterOptions: {
    allure: {
      outputDir: 'allure-results'
    }
  },

#8. Running the first test
8.1. Run the first test:
npm test
Recieve the message- 1 test passed.
