
> Note: the layout of the GUI may look different depending on your OS; the
> provided screenshots were taken on a Mac.

Stop the application by closing its window. Then save a screenshot as
`submissions/task1-running.png`.

## Run the feature tests

```sh
mvn test
```

On the starter code, the smoke test passes and the feature tests fail with
messages for Tasks 2–4. This is expected. Re-run the tests as you work until
all tests pass.

## IntelliJ IDEA setup

1. Open the repository root and import it as a Maven project. Do not configure
   source folders or JARs by hand.
2. Open **File > Project Structure > Project** and choose the project SDK:
   JDK 8 on macOS, or JDK 8/11 on Windows and Linux. If it is not installed,
   choose **Add SDK > Download JDK** and download the required version.
3. Open **Settings > Build, Execution, Deployment > Build Tools > Maven >
   Runner** and select the same JDK as the runner JRE. Also select it as the
   Maven importer JDK if your IntelliJ version offers that setting.
4. Wait for Maven import and indexing to finish.
5. Select the shared **Sweet Home 3D** run configuration and click Run. You can
   also open `SweetHome3D.java` and click the green arrow beside `main`.

Tests may be run with the green arrows beside a test class/method or from the
Maven tool window. If you enable **Delegate IDE build/run actions to Maven**,
the Maven runner JRE from step 3 is especially important.

The Maven tool window's **Skip Tests** toggle applies to lifecycle goals such
as `package`. It is not needed to launch the application, and it should be
turned off before using `mvn test` to check your work.

## Troubleshooting
- note that the first build might take some time to run, as it has to
  compile all the source files and download various dependencies specified in the pom.xml.
- `invalid flag: --release`: confirm that `pom.xml` uses version 3.13.0 or
  newer of `maven-compiler-plugin`, then reload the Maven project.
- `release version 8 not supported`: Maven is using a JDK older than Java 8.
- macOS errors mentioning `com.apple.eawt` or `Unimplemented`: first confirm
  that `mvn -version` reports Java 8. If it does, sync your fork with the
  latest assignment repository; older copies may launch Maven with the
  bundled Apple API stubs instead of the macOS JDK classes.
- IntelliJ and the terminal behave differently: compare IntelliJ's Project SDK
  and Maven runner JRE with the JDK reported by `mvn -version`.
- No window appears: make sure you ran the launch command in a graphical
  session, not a headless SSH session. Use a lab desktop if necessary.
- The bottom-right area is empty: this is expected because 3D is disabled.
- Maven cannot download plugins or JUnit: connect to the network once, or run
  on a lab machine with the course Maven cache.
- To discard only generated build output, run `mvn clean`. It does not remove
  source files or screenshots.

### Issues with JDK version
If directly running Maven commands from the terminal, you would need to ensure that the
correct JDK version and Maven version are being used.
You can check the tools available on your machine using:

```sh
java -version
mvn -version
```

On macOS, both commands must report Java 8. On Windows and Linux, both should
report either Java 8 or Java 11. If Maven reports a different JDK, update
`JAVA_HOME` or Maven's JRE setting in your IDE before continuing.

## Getting further help
If after trying the above you still encounter errors building the project and running the tests,
please post a question on the discussion board. Including screenshots or error messages can help
diagnose the issue.
