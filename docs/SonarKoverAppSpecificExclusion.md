## App Specific Exclusions for Sonar & Kover

1. Update the [GradleBuild Android](https://bitbucket.org/7peakssoftware/gradlebuild-android/src/master/) version tag to `2.6.3`.
2. Create two files with name `exclusions_kover`, `exclusions_kover_annotation` and `exclusions_sonar` at the **project's root directory**.
3. And add the app specific exclusions to the respective files.

Example `exclusions_kover`

```
*CountryData
*Constants
*PhoneFieldWithCodeSelection*
*EmailField*
*OtpField*
*PasswordField*
```

Example `exclusions_kover_annotation`

```
*Generated
*CustomAnnotationToExclude
```

Example `exclusions_sonar`

```
**/*CountryData
**/*Constants
**/*PhoneFieldWithCodeSelection*
**/*EmailField*
**/*OtpField*
**/*PasswordField*
```

> Please kindly be sure to add the exclusions to both files consistently following the respective wildcard rules of [sonarqube](https://docs.sonarsource.com/sonarqube/latest/analyzing-source-code/test-coverage/test-execution-parameters/) and [kover](https://kotlin.github.io/kotlinx-kover/gradle-plugin/configuring#class-name-with-wildcards) for correct coverage report.