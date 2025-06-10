# JavaFX Test Action ![GitHub release](https://img.shields.io/github/v/release/erwanclx/maven-javafx-testing?label=release)

This GitHub Action runs JavaFX Maven tests using a virtual display (`Xvfb`) so they can execute in a CI environment like Ubuntu runners.

## ✨ Features

- Headless testing for JavaFX using `Xvfb`
- Customizable Java version
- Support for submodules or custom `pom.xml` paths
- Extra Maven arguments (e.g., `verify`, `-DskipTests=false`, etc.)

## 📥 Inputs

| Name           | Description                                              | Default    | Required |
|----------------|----------------------------------------------------------|------------|----------|
| `java-version` | The Java version to install (`temurin` distribution)     | `21`       | ❌       |
| `project-dir`  | Relative path to the project containing `pom.xml`        | `.`        | ❌       |
| `maven-args`   | Arguments passed to `mvn` (e.g., `verify`, `test`, etc.) | `test`     | ❌       |
| `screen-size`  | Virtual screen resolution and depth used by `Xvfb` | `1024x768x24`     | ❌       |

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
```
