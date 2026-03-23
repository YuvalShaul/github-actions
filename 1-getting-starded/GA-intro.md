## Github Action Introduction
- GitHub Actions is a powerful automation tool built directly into your development workflow. 
- Here is the essential "need-to-know" list to get you started:

#### Automation

- **Automation by default:** It automates tasks like testing, building, and deploying your code.
- **workflows**: Aytomation scripts are called **workflow**s
- **YAML syntax:** All workflows are written in `.yml` or `.yaml` format.
- **Event-driven:** Workflows trigger based on GitHub events, such as a `push`, `pull_request`, or even a new `issue`.
- **The Runner:** GitHub provides **managed virtual machines** (Ubuntu, Windows, or macOS) to run the code that your workflow calls.

#### Directories
- **File location:** Workflow files must be stored in the `.github/workflows/` directory of your repository.

#### Workflows

- **Jobs and Steps:** A single workflow can contain multiple **Jobs** (which run in parallel) and multiple **Steps** (which run in sequence).
- **Marketplace power:** You can use pre-built "Actions" from the GitHub Marketplace to avoid writing common scripts from scratch.
- **Visibility:** You can monitor the progress and logs of every run under the **Actions** tab of your repository.


#### Secrets
- **Secrets management:** Sensitive data like API keys should be stored in **Repository Secrets**, never hardcoded in the YAML file.


