## Gradle Build Android

This repository contains shared gradle scripts for static code analyzer (KtLint), test coverage, build checks, firebase app distribution  and lints to be used across android projects.

### Usage (Gradle KTS)

1. Apply the [git-dependencies](https://github.com/alexvasilkov/GradleGitDependenciesPlugin) gradle plugin to the project's `settings.gradle.kts`.

```
plugins {
    id("com.alexvasilkov.git-dependencies").version("{LATEST_VERSION}")
}
```

2. Create `gradlebuild-android.gradle` at the project's root directory with the following git config block

```
git {
    defaultAuthGroup 'bitbucket'
    fetch 'https://bitbucket.org/7peakssoftware/gradlebuild-android.git', {
        dir "$rootDir/gradle/scripts"
        tag '{REQUIRED_TAG}'
    }
}
```

3. Apply the `gradlebuild-android.gradle` to the `settings.gradle.kts` (**after applying the** `git-dependency` **gradle plugin in step 1**).

```
apply(from = "gradlebuild-android.gradle")
```
4. Finally, sync the project with gradle files. This repository with the specified tag will be cloned in `$rootDir/gradle/scripts` after project build.

### Usage (Gradle Groovy)

1. Apply and configure the [git-dependencies](https://github.com/alexvasilkov/GradleGitDependenciesPlugin) gradle plugin to the project's `settings.gradle`.

```
// After the pluginManagement block and before dependencyResolutionManagement block
plugins {
    id 'com.alexvasilkov.git-dependencies' version '2.0.4'
}


// After the dependencyResolutionManagement block
git {
    defaultAuthGroup 'bitbucket'
    fetch 'https://bitbucket.org/7peakssoftware/gradlebuild-android.git', {
        dir "$rootDir/gradle/scripts"
        tag '{REQUIRED_TAG}'
    }
}
```

2. And, sync the project with gradle files. This repository with the specified tag will be cloned in `$rootDir/gradle/scripts` after project build.


### Related Docs

* [App Specific Exclusions for Sonar & Kover](docs/SonarKoverAppSpecificExclusion.md)