# CHANGELOG

#### Linked versions are to releases.

> `Added` for new features.
> `Changed` for changes in existing functionality.
> `Deprecated` for soon-to-be removed features.
> `Removed` for now removed features.
> `Fixed` for any bug fixes.
> `Security` in case of vulnerabilities.

_These new formats are from >2.0.0 (alpha-1)_


### v2.0.0

#### Added

- Install via Maven Central

### v2.0.0-a2

#### Added

- Maven Wrapper is now being used to build the project
- Detailed `README.md` with instructions on how to use the project


#### Changed

- Project moved to new repository [jgrade2](https://github.com/dscpsyl/jgrade2) from [jgrade](https://github.com/tkutcher/jgrade).
- Dependencies updated to reflect new project.

#### Fixed

- Project now us upgraded to follow jUnit5 API protocols.

### 2.0.0 (alpha-1)

- Renamed `Observer` to `Formatter` everywhere
- Renamed domain to `com.github.tkutcher` to match GitHub username.

### 1.1.4

_4.15.2019_

- `addCommandLineArg(String)` in `CLITester`

### 1.1.3

_2.4.2019_

- `CheckstyleGrader` adds the error type to it's output
- Method `getErrorTypes()` to get the `Map` of error types to their count.
- Method `getErrorTypeCount()` to get the number of error types encountered.

### 1.1.2

_2.1.2019_

- Changed fail message to not include the `Failure.toString()`
  - If a test failed not using the message parameter, it added some useless output that was confusing to students
  - Instead just print (no description provided)

### 1.1.1

_1.31.2019_

- Fixed bug in `DeductiveGraderStrategy` where starting point value test wasn't added in all cases.

### 1.1.0

_1.31.2019_

- Added strategy design pattern to `Grader` so when a client calls `runJUnitGradedTests` the strategy for those test results treats them accordingly.
  - This is the `GraderStrategy` interface class
  - Added a private class `DefaultGraderStrategy` that does nothing so as to preserve original behavior for tests, etc.
  - _Note this pattern should probably eventually be moved out to be a strategy for the `GradedTestListener` class rather than the `Grader` but would be a little messier work and wanted to get it working quickly to use this semester._
- Added `DeductiveGraderStrategy` class to go through graded test results from JUnit tests and treat their scores as deductive.
  - Constructor sets a starting score, failed tests deduct by the amount of points they are worth up to some floor (0 by default).
  - Tracks the total points deducted.
  - Appends a message to the test result's output if not all (or no) points were deducted so as to not go beyond the floor.
- `DeductiveGraderStrategyTest` unit tests
  - Added to `AllJGradeTests`

### 1.0.3

_1.29.2019_

- Checkstyle compliance in all files.
- Docs based on GitHub's community standards.
- Maven checkstyle plugin added to object model.
- Updated naming of jars to **not** include patch number.

### 1.0.2

_1.28.2019_

- Bug in `CLIResult` that returned a `List` of size `1` rather than `0` when the stream actually had an empty string.
- Captures the exit value for the sub-process that runs the main program being tested.
- `getOutput()` without parameters defaults to returning the standard out.
- Some (very basic) unit tests in `CLITesterExecutionResultTest` to test these tweaks and that they work as expected.

### 1.0.1

_1.24.2019_

- Bug in `CheckstyleGrader` excluding files named with `test` anywhere in the path, now ignores case.

### 1.0.0

_1.17.2019_

- Initial release
- Added `CLITester` and `CLIResult` for command line help.
- Added `CheckstyleGrader` for creating a `GradedTestResult` based off a checkstyle run.
- Made domain for package `com.github.tkutche1`
- pom to correctly build jar with dependencies (appended with `-all`).
- pom with option to build javadoc.
- Full gradescope example.

### 1.0.0 (alpha)

- For internal use
- Maven setup
- Main program that takes a class name as a String on the command line and runs the annotated methods in that class to produce output
  - `@AfterGrading`, `@BeforeGrading`, and `@Grade` annotations.
  - JSON output
- Classes for producing output specific to Gradescope's specifications.
  - _Note: **no** textual output support._
