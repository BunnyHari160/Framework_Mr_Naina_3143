Java 21 Upgrade Guide

This repository was updated to target Java 21 (LTS).

What I changed
- `framework/pom.xml`:
  - Set `maven.compiler.source` and `maven.compiler.target` to 21.
  - Added `maven-compiler-plugin` with `<release>21</release>`.
  - Added `maven-enforcer-plugin` execution to require Java 21.

- `test-framework/pom.xml`:
  - Merged duplicate `<build>` sections.
  - Set `maven.compiler.source` and `maven.compiler.target` to 21.
  - Added `maven-compiler-plugin` with `<release>21</release>`.
  - Added `maven-enforcer-plugin` execution to require Java 21.

Why
- Using `<release>21</release>` ensures compilation against Java 21 APIs and produces correct bytecode.
- The enforcer plugin prevents accidental builds with older JDKs and gives a clear error message.

How to prepare your system (Windows PowerShell)

1) Check current Java and Maven:

```powershell
java -version
mvn -v
```

2) If you don't have JDK 21, install it via winget (recommended when available):

```powershell
# Install Eclipse Temurin JDK 21
winget install --id Eclipse.Temurin.21.JDK -e
```

If winget is not available, download JDK 21 from Adoptium/Eclipse Temurin or Microsoft and install it.

3) Set JAVA_HOME for the current PowerShell session (replace path with your JDK install path):

```powershell
$env:JAVA_HOME = 'C:\Program Files\Java\jdk-21'
$env:PATH = $env:JAVA_HOME + '\bin;' + $env:PATH
```

4) From the `SPRINT1` folder, run a Maven build:

```powershell
cd 'C:\Users\HP\Desktop\all\S5\MrNaina\FRAMEWORK_FINAL_3143\Framework_Mr_Naina_3143\SPRINT1'
# Clean and build, with update and verbose errors
mvn -U -e clean package
```

Troubleshooting
- If Maven fails with the enforcer error that Java is not 21, confirm `java -version` and that `mvn -v` shows the Java 21 JVM.
- If compilation errors occur, paste the `mvn` output and I will suggest fixes (likely dependency or API usage issues).

What I'll do next if you ask me to run the build here
- I will run `mvn -U -e clean package` in `SPRINT1` and report the output.
- If the build fails due to missing JDK 21, I'll report the exact error and give next steps.

If you want me to proceed with the build now, reply: "Run the build".
