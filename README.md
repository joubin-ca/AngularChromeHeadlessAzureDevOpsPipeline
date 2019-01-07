# Angular Azure DevOps PhantomJS (headless browser)
How to setup Karma config using PhantomJS to run tests on Azure DevOps

## Visual Studio Code
### Install required npm packages
- npm install phantomjs-prebuilt --save-dev
- npm install karma-phantomjs-launcher --save-dev
### karma.config.js
- Add 'require('karma-phantomjs-launcher')' to the the plugins array
### pollyfills.ts
- Uncomment the BROWSER POLYFILLS section
### package.json
- Add '"test-headless": "ng test --browsers=PhantomJS --watch=false"' to the 'script' section
### angular.json
- If you need code coverage reports add '"codeCoverage": true' to the projects->name->test->options section
## Azure DevOps
### Build Pipeline
- Add an 'npm' task with the following 'custom' command 'run test-headless'

## References
- https://www.npmjs.com/package/phantomjs-prebuilt
- https://www.npmjs.com/package/karma-phantomjs-launcher
- http://anthonygiretti.com/2017/12/11/how-to-run-unit-tests-in-vsts-during-ci-with-angular-5-and-phantomjs-part-1/
- http://anthonygiretti.com/2017/12/11/how-to-run-unit-tests-in-vsts-during-ci-with-angular-5-and-phantomjs-part-2/
