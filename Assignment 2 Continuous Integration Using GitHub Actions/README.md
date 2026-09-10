# GitHub Actions CI Demo

## Project Overview
This is a beginner-friendly Node.js project designed to demonstrate how Continuous Integration (CI) works using GitHub Actions. The project includes a simple Node.js application, necessary configuration files, and GitHub Actions workflow files to automate the build and testing processes.

## Folder Structure
```text
.
├── .github/
│   └── workflows/
│       ├── ci.yml               # Corrected workflow file that succeeds
│       └── ci-failing.yml       # Intentionally failing workflow file example
├── .gitignore                   # Specifies files/folders to be ignored by Git
├── index.js                     # Main application code
├── package.json                 # Project metadata and npm scripts
└── README.md                    # Project documentation
```

## Purpose of Each File
- **`index.js`**: A simple Node.js script that prints "Hello from GitHub Actions CI!" when executed.
- **`package.json`**: Contains the project configuration, including the name, version, and the `start`, `build`, and `test` scripts used by the CI pipeline.
- **`.gitignore`**: Tells Git which files and directories to ignore, such as the `node_modules` folder, preventing unnecessary files from being committed to the repository.
- **`.github/workflows/ci.yml`**: The correct GitHub Actions workflow file that defines the steps for the CI pipeline. It checks out the code, sets up Node.js, installs dependencies, builds the project, and runs the tests.
- **`.github/workflows/ci-failing.yml`**: An alternate version of the CI workflow that intentionally contains an error (running `npm xyz`) to demonstrate how GitHub Actions catches failures.

## How the GitHub Actions Workflow Works
GitHub Actions allows you to automate workflows directly in your GitHub repository. The workflow defined in `ci.yml` works as follows:

1. **Trigger**: The workflow is triggered automatically every time code is pushed to the `main` branch.
2. **Environment**: It runs on an `ubuntu-latest` virtual machine provided by GitHub.
3. **Checkout**: It uses the `actions/checkout@v4` action to pull your repository's code into the virtual machine.
4. **Setup Node**: It uses `actions/setup-node@v4` to install Node.js version 20 so that we can run `npm` commands.
5. **Install Dependencies**: It runs `npm install` to install any packages defined in `package.json` (even if none are needed for this simple app, it's best practice).
6. **Build**: It runs `npm run build` which simulates building the application.
7. **Test**: It runs `npm run test` which simulates running unit tests. If this step or any previous step fails, the entire workflow fails automatically.

## Running the Project Locally
To run the application locally, use the following commands:
```bash
# Run the application
npm start

# Run the build script
npm run build

# Run the tests
npm test
```
