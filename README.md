# Midstream KIE Tools Builder

This repository hosts a GitHub Action to automate building artifacts from the [KIE Tools repository](https://github.com/kiegroup/kie-tools) for local testing and integration. It allows you to download artifacts as dependencies in other projects, specifically for testing the `sonataflow-quarkus-devui` component in a Quarkus project.

## Purpose

The GitHub Action here:
- Compiles and builds the `kie-tools` repository.
- Uploads the following artifacts as downloadable build results:
  - `sonataflow-quarkus-devui-999-SNAPSHOT.jar`
  - `sonataflow-quarkus-devui-deployment-999-SNAPSHOT.jar`
  - `sonataflow-management-console-webapp-999-SNAPSHOT-image-build.zip`

These artifacts can then be used as dependencies in other projects, allowing for faster local testing without requiring manual builds.

## Usage

1. **Run the GitHub Action**:
   - In the GitHub Actions tab, manually trigger the action with the following inputs:
     - `repository`: The repository to build (e.g., `kiegroup/kie-tools`)
     - `branch`: The branch to build (e.g., `main` or a specific feature branch)

2. **Download Artifacts**:
   - Upon completion, the action will upload the specified artifacts. Navigate to the workflow run summary to download them.

3. **Install Artifacts Locally**:
   - After downloading, install the artifacts in your local Maven repository to use them in your project. For example:
     ```bash
     mvn install:install-file -Dfile=path/to/sonataflow-quarkus-devui-999-SNAPSHOT.jar -DgroupId=org.apache.kie.sonataflow -DartifactId=sonataflow-quarkus-devui -Dversion=999-SNAPSHOT -Dpackaging=jar
     ```

4. **Integrate in Your Project**:
   - Add the downloaded dependencies to your `pom.xml`:
     ```xml
     <dependency>
         <groupId>org.apache.kie.sonataflow</groupId>
         <artifactId>sonataflow-quarkus-devui</artifactId>
         <version>999-SNAPSHOT</version>
     </dependency>
     ```
