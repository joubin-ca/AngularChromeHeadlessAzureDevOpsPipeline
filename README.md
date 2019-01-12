# Run Angular tests using Headless Chrome, publish test results and code coverage
How to setup Karma config using headless Chrome to run tests on Azure DevOps

## Visual Studio Code
### Install required npm packages
- npm i karma-chrome-launcher --save-dev
- npm i karma-junit-reporter --save-dev
### karma.config.js
#### Add to plugins:
- Add 'require('karma-chrome-launcher')'
- Add 'require('karma-junit-reporter')'
- Add junitReport section according to https://www.npmjs.com/package/karma-junit-reporter
##### Add to reporters array:
- 'junit'
### pollyfills.ts
- Remains unchanged
### package.json
- Add '"test-headless": "ng test --browsers=ChromeHeadless --watch=false"' to the 'script' section

It's important to include the watch=false flag since the pipeline task will timeout if it's continuously running.
### angular.json
- If you need code coverage reports add '"codeCoverage": true' to the projects->name->test->options section
### .gitignore
- Exlude the report folders from junit reporter and coverage reporter
## Azure DevOps
### Build Pipeline
- Add an 'npm' task with the following 'custom' command 'run test-headless'
- Add Publish Tests Results task
- Add Publish Code Coverage task
