# JFrogArtifactUpload

## Overview

This GitHub Action sets up JFrog Artifactory and pushes artifacts to a specified target path.

## Author

- **George Nana Ekow-Daniels**

## Branding

- **Icon:** `package`
- **Color:** `blue`

## Inputs

| Name              | Description                            | Default  | Required |
|------------------|------------------------------------|----------|----------|
| `file_publish_path` | Relative path to the packages     | N/A    | ✅ |
| `target`         | Target path in Artifactory         | N/A      | ✅ |
| `artifactory_url` | Artifactory URL                   | N/A      | ✅ |
| `artifactory_token` | Artifactory Token               | N/A      | ✅ |

## Usage

To use this action in your GitHub workflow, add the following step:

```yaml
jobs:
  publish:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Push artifacts to JFrog Artifactory
        uses: gekowdaniels/JFrogArtifactUpload@v1
        with:
          file_publish_path: "<your-file-to-upload>"
          target: "<your-target-path>"
          artifactory_url: "<your-artifactory-url>"
          artifactory_token: "${{ secrets.ARTIFACTORY_TOKEN }}"
```

### Example: Publishing NuGet Packages
To upload .nupkg files to Artifactory, you can define the workflow like this:

```yaml
jobs:
  publish:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Push NuGet packages to JFrog Artifactory
        uses: gekowdaniels/JFrogArtifactUpload@v1
        with:
          file_publish_path: "**/*.nupkg"
          target: "nuget-release-local/testrepo/1.0.0/1.0.0"
          artifactory_url: "artifactory.mydomain.com"
          artifactory_token: "${{ secrets.ARTIFACTORY_TOKEN }}"
```

