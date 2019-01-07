# Angular Azure DevOps PhantomJS (headless browser)
How to setup Karma config using PhantomJS to run tests on Azure DevOps

## Visual Studio Code
- npm install phantomjs-prebuilt --save-dev
- npm install karma-phantomjs-launcher --save-dev

### karma.config.js
- Add 'require('karma-phantomjs-launcher')' to the the plugins array

### pollyfills.ts
- Uncomment the BROWSER POLYFILLS section

### package.json
- Add '"test-headless": "ng test --browsers=PhantomJS --watch=false"' to the script section

## Azure DevOps
- Add an npm Steps with the following 'custom' command 'run test-headless'
