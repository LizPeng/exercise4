# 练习4

### 目标

## add coverall

    npm install mocha --save-dev

    npm install istanbul --save-dev

Now your package.json should have both scripts:

    "scripts": {
        "test": "mocha",
        "cover": "istanbul cover _mocha",
    },
 **cd 到测试文件所在目录**
 
    cd test 

    npm run cover

    npm install --save-dev coveralls mocha-lcov-reporter  

Add this line to your package.json "script",which pipes istanbul's report over to Coveralls:

    "coveralls": "npm run cover -- --report lcovonly && cat ./coverage/lcov.info | coveralls"
    
Then add this to your .travis.yml, will tells Travis to update Coveralls automatically after a successful build:

	after_success:
	- npm run coveralls

Push a new build to Github.

Now, whenever a build passes on Travis, it will send updated code coverage metrics to Coveralls.

You can also use `$ npm run coveralls` commadn to update Coveralls locally, but you'll first need to add a `.coveralls.yml` file to your project with your repo key. Be sure to `.gitignore` it to keep it confidential.

> 复习一下`this`和`声明提升`。