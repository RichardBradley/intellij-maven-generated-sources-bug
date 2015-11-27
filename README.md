# Intellij Maven plugin "generated-sources" bug repro

This demonstrates (TODO:bug id).

The project will build in maven:

    mvn compile

But if you import it into IntelliJ, it will not complile:

    Error:(4, 40) java: package com.example.db.model.public_ does not exist

If you uncomment the commented-out section in pom.xml, then IntelliJ will work.

It looks like the IntelliJ Maven plugin is pattern-matching against the "build-helper-maven-plugin" instead of running the build and inspecting the POM.
The "jooq-codegen-maven" plugin auto-adds the "generated-sources" dir to the POM -- that should suffice.
