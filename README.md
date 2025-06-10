# JavaFX Test Action

This GitHub Action runs JavaFX Maven tests using a virtual display (`Xvfb`) so they can execute in a CI environment like Ubuntu runners.

## ✨ Features

- Testing for JavaFX using `Xvfb`
- Customizable Java version
- Support for submodules or custom `pom.xml` paths
- Extra Maven arguments (e.g., `verify`, `-DskipTests=false`, etc.)

## 📥 Inputs

| Name           | Description                                              | Default    | Required |
|----------------|----------------------------------------------------------|------------|----------|
| `java-version` | The Java version to install (`temurin` distribution)     | `21`       | ❌       |
| `project-dir`  | Relative path to the project containing `pom.xml`        | `.`        | ❌       |
| `maven-args`   | Arguments passed to `mvn` (e.g., `verify`, `test`, etc.) | `test`     | ❌       |

## 🚀 Usage

```yaml
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Run JavaFX tests
        uses: erwanclx/javafx-test@v1
        with:
          java-version: '21'
          project-dir: './my-javafx-module'
          maven-args: 'verify -DskipTests=false'

