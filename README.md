# Resume Automation

This repository contains an automated system for managing and deploying a professional resume using GitHub Actions. The setup ensures that any updates to the resume are processed, compiled, and deployed seamlessly.

## Features
- **Automated Deployment**: Uses GitHub Actions to compile and deploy the latest version of the resume.
- **Continuous Integration**: Ensures the resume is always up-to-date with the latest modifications.
- **Version Control**: Maintains a history of changes, allowing easy rollback if needed.
- **PDF Generation**: Automatically compiles the resume into a high-quality PDF format.

## How It Works
1. **Update Your Resume**: Modify the source `.tex` file with new content.
2. **Commit Changes**: Push the changes to the repository.
3. **Automated Workflow**: GitHub Actions triggers the build process.
4. **Deployment**: The generated PDF is automatically uploaded and made available.

## Setup Instructions
1. Fork or clone this repository.
2. Install LaTeX dependencies (`TeX Live` recommended).
3. Modify `resume.tex` with your details.
4. Push the changes to trigger the GitHub Actions workflow.

## GitHub Actions Workflow
The workflow is defined in `.github/workflows/build.yml` and includes:
- Checking out the latest repository state.
- Installing LaTeX dependencies.
- Compiling the `.tex` file to generate a PDF.
- Deploying the generated PDF as an artifact.

## Example Usage
After making updates to `resume.tex`, simply commit and push. The workflow will handle:
- Compiling the LaTeX source.
- Generating an updated PDF version.
- Uploading the latest resume automatically.

## Why Use This Setup?
- Eliminates manual compilation steps.
- Ensures consistency in resume formatting.
- Provides an automated way to keep the resume readily available.

## Reference
For more details on setting up GitHub Actions for resume deployment, check out my blog post: [Using GitHub Actions for Automated Resume Deployment](https://swiftlysingh.com/using-github-actions-for-automated-resume-deployment)

## License
This project is licensed under the Apache License 2.0. See `LICENSE` for more details.

