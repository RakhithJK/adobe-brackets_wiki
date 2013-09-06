Brackets includes a simple test-runner for internal use. You can leverage this same tool for any Brackets extensions you write (though not for other projects you're editing in Brackets... [yet](https://trello.com/c/CUoZMZM2/740-unit-test-runner-for-user-code)).

1. Learn about the [Jasmine unit-test framework](http://pivotal.github.io/jasmine/).
2. Add a `unittests.js` module in the root of your extension folder.
3. Write Jasmine test cases inside the module, using `describe() {}` blocks. [Here's an example](Simple "Hello World" extension#unittestjs).
4. Choose _Debug > Run Tests_
5. Click the _Extensions_ tab
6. Click the name of your Jasmine block to run it

### Caveats

This is not the easiest to use setup yet. Watch out for these gotchas:

* You can open dev tools for the unit test window via its own "Show Developer Tools" button.
    * _You must [disable caching](https://groups.google.com/forum/?fromgroups=#!topic/brackets-dev/E5iqcD8VqD4) once you open dev tools_ -- even if you've already done so in the dev tools for the main Brackets window.
* Your unit tests run _in_ the test-runner window by default, so the Brackets UI DOM and certain Brackets modules won't be accessible. This may cause your code to fail.
* You can run tests in a clean Brackets window using `SpecRunnerUtils.createTestWindowAndRun()`, which avoids the above problem. But this setup is not well documented and has its own pitfalls -- your test code needs to be careful about whether it's accessing something in the test-runner window vs. the popup Brackets window (for example, `$` vs. `testWindow.$`). See [ProjectManager-test](https://github.com/adobe/brackets/blob/master/test/spec/ProjectManager-test.js) for example code. [Debugging tests inside these windows](https://github.com/adobe/brackets/wiki/Debugging-Test-Windows-in-Unit-Tests) is also a bit tricky.