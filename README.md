# Gradle Spoon Plugin

[![License](https://img.shields.io/badge/license-apache%202.0-blue.svg)](http://www.apache.org/licenses/LICENSE-2.0)
[![Build Status](https://travis-ci.org/JDFind/gradle-spoon-plugin.svg?branch=master)](https://travis-ci.org/JDFind/gradle-spoon-plugin)

Gradle plugin for a [custom Spoon](https://github.com/JDFind/spoon) 2+ and [Android Gradle Plugin](https://developer.android.com/studio/releases/gradle-plugin.html) 3+.

This project is based on https://github.com/jaredsburrows/gradle-spoon-plugin

## Download

Release versions are available in the JFrog Bintray repository: https://bintray.com/jdfind/maven/gradle-spoon-plugin

```groovy
buildscript {
  repositories {
    jcenter()
    // for Spoon snapshot, until 2.0.0 is released
    maven { url 'https://oss.jfrog.org/artifactory/oss-snapshot-local' }
  }

  dependencies {
    classpath "com.jdfind:gradle-spoon-plugin:1.4.1"
  }
}

apply plugin: "com.android.application"
apply plugin: "com.jdfind.spoon"
```

## Tasks

- `gradlew spoon{variant}`

## Usage

**Optional extension:**
```groovy
spoon {
  // Identifying title for this execution. ("Spoon Execution" by default)
  title = "My tests"
  
  // Path to output directory. ("$buildDir/spoon-output" by default)
  baseOutputDir = "spoonTests"

  // Whether or not debug logging is enabled. (false by default)
  debug = true

  // Whether or not animations are enabled. Disable animated gif generation. (false by default)
  noAnimations = true

  // Set ADB timeout. (seconds) (default is 10 mins)
  adbTimeout = 300

  // Add device serials for test execution
  devices = ["emulator-5554", "emulator-5556"]

  // Add device serials for skipping test execution.
  skipDevices = ["emulator-5555"]

  // Extra arguments to pass to instrumentation.
  instrumentationArgs = ["listener:com.foo.Listener,com.foo.Listener2", "classLoader:com.foo.CustomClassLoader"]

  // Test class name to run (fully-qualified).
  className = "com.android.foo.FooClassName"

  // Test method name to run (must also use className)
  methodName = "testMethodName"
  
  // Run annotated tests - small, medium, large
  testSize = "large"
  
  // Allow no devices to be connected. (false by default)
  allowNoDevices = true

  // Execute the tests device by device. (false by default)
  sequential = true

  // Grant all runtime permissions during installation on Marshmallow and above devices. (false by default)
  grantAll = true

  // Code coverage flag. For Spoon to calculate coverage file your app must have the `WRITE_EXTERNAL_STORAGE` permission. (false by default)
  codeCoverage = true

  // Toggle sharding. (false by default)
  shard = true

  // The number of separate shards to create.
  numShards = 10

  // The shardIndex option to specify which shard to run.
  shardIndex = 2
  
  // Run tests in separate instrumentation calls. (false by default)
  singleInstrumentationCall = true

  // Run each test class in a different instrumentation instance. (false by default)
  classLevelInstrumentation = true

  // Do not fail build if a test fails, let all the tests run and finish. (false by default)
  ignoreFailures = true
}
```

## License

    Copyright (C) 2015 Jared Burrows
    Copyright (C) 2018 JDFind

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
