# Kotlin Library - Step by Step Guide

A comprehensive guide to create and publish a Kotlin library on GitHub.

## Step 1: Create a Project and Library Module

1. Open Android Studio
2. Create a new empty project
3. From the top menu, select **File** → **New** → **New Module**
4. Select **Library** as the module type

## Step 2: Configure Build Files

Configure the following files in your library module:
- `library_name/build.gradle.kts`
- `settings.gradle.kts`

Ensure all dependencies and build configurations are properly set up.

## Step 3: Write Your Main Source Code

Create your library code in the following path:
`kotlinlib/src/main/java/com/rezaul/kotlinlib/MyLib.kt`

Example implementation:

```kt
package com.rezaul.kotlinlib

object MyLib {
    fun sayHello(name: String): String {
        return "Hello $name! This is from my public Kotlin library."
    }
}
```

## Step 4: Build and Generate Build Files

Run the following command to compile your library:

```bash
./gradlew :kotlinlib:assemble
```

This will generate the build files ready for upload.

## Step 5: Define Version and Publish on GitHub

1. Define the version in `kotlinlib/build.gradle.kts`
2. Push your code to GitHub

## Step 6: Create a Release

1. Create a Git tag matching your version number
2. Create a GitHub release for that tag
3. Upload the compiled build files from `kotlinlib/build/libs/` to the release

## Step 7: Wait for JitPack Build

After creating a release on GitHub, JitPack will automatically detect it and build your library. 

Monitor the build progress at:
```
https://jitpack.io/#DeveloperRejaul/kotlinlib/TAG
```

Once the build is complete (green checkmark), your library will be available for download and can be used as a dependency in other projects.

---

## Usage

### Add the Library to Your Project

Add the JitPack repository and the library dependency to your `build.gradle.kts`:

```gradle
repositories {
    maven { url = uri("https://jitpack.io") }
}

dependencies {
    implementation("com.github.DeveloperRejaul:KotlinLibrary:VERSION")
}
```

Replace `VERSION` with the latest release version.

### Use the Library

Import and use the library in your code:

```kt
import com.rezaul.kotlinlib.MyLib

fun main() {
    val greeting = MyLib.sayHello("World")
    println(greeting)
    // Output: Hello World! This is from my public Kotlin library.
}
```