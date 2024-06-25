<h1>**Building Java Application With Gradle**</h1>

Gradle is a well-known build automation tool that works across a variety of platforms and languages. 
This project includes establishing a Java application and breaking it down into subprojects in order to modularize it.

I initialized a project as Java application, ran the build and build its test report. I executed a Java application and build it in an archive.

**What I used**
1. A text editor or IDE (VS Code)
2. A Java Development Kit (JDK), version 8 or higher
3. The latest Gradle distribution

**Steps**
1. **Creating a project folder:** Gradle comes with a built-in task, called init, that initializes a new Gradle project in an empty folder. The init task uses the (also built-in) wrapper task to create a Gradle wrapper script, gradlew.
   The first step was to create a folder for the new project and change directory into it.

2. **Running the init task:** From inside the new project directory, I ran the init task using the following command in a terminal: gradle init.
   When prompted, I selected the 1: application project type, and 1: Java as implementation language.
   Next I chose the DSL for writing buildscripts - 2 : Groovy. For the other questions, I used the default values.
   The init task generates the new project with the following structure: Generated folder for wrapper files, Generated version catalog, Gradle wrapper start scripts, Settings file to define build name and subprojects,
   Build script of app project, Default Java source folder, and Default Java test source folder.

   The settings.gradle(.kts) file has two interesting lines: i. rootProject.name assigns a name to the build, which overrides the default behavior of naming the build after the directory it’s in.
   It’s recommended to set a fixed name as the folder might change if the project is shared - e.g. as root of a Git repository
   ii. include("app") defines that the build consists of one subproject called app that contains the actual code and build logic.

   The build contains one subproject called app that represents the Java application we are building. It is configured in the app/build.gradle(.kts) file.
   I applied the application plugin to add support for building a CLI application in Java, used Maven Central for resolving dependencies, used JUnit Jupiter for testing.
   The dependency is used by the application. I defined the main class for the application, and used JUnit Platform for unit tests.
   The generated test class has a single JUnit Jupiter test. The test instantiates the App class, invokes a method on it, and checks that it returns the expected value.

3. **Running the application:** Thanks to the application plugin, I could run the application directly from the command line.
   The run task tells Gradle to execute the main method in the class assigned to the mainClass property.

4. **Bundling the application:** The application plugin also bundles the application, with all its dependencies. The archive also contains a script to start the application with a single command.

**That's it:**
I successfully configured and built a Java application project with Gradle by:
Initializing a project that produces a Java application,
Running the build and view the test report,
Executing a Java application using the run task from the application plugin, and
Bundling the application in an archive.
