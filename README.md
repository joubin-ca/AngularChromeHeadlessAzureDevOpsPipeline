# Run tests using Headless Chrome in Azure DevOps Build pipeline
How to setup Karma config using PhantomJS to run tests on Azure DevOps

## Visual Studio Code
### Install required npm packages
- npm install karma-chrome-launcher --save-dev
### karma.config.js
- Add 'require('karma-chrome-launcher')' to the the plugins array
### pollyfills.ts
- Remains unchanged
### package.json
- Add '"test-headless": "ng test --browsers=ChromeHeadless --watch=false"' to the 'script' section

It's important to include the watch=false flag since the pipeline task will timeout if it's continuously running.
### angular.json
- If you need code coverage reports add '"codeCoverage": true' to the projects->name->test->options section
## Azure DevOps
### Build Pipeline
- Add an 'npm' task with the following 'custom' command 'run test-headless'
