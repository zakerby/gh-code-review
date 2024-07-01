# Github GenAI Code Review

This GitHub Action automates the process of code review by leveraging the Ollama language model. It checks out your code, installs Ollama, identifies modified files in a pull request, and uses Ollama to review those files. Finally, it posts the review comments to the pull request.

## Features

- **Automatic Checkout**: Checks out the codebase for review.
- **Ollama Installation**: Installs the Ollama tool for code analysis.
- **Identify Modified Files**: Detects files changed in the pull request.
- **Code Review with Ollama**: Utilizes Ollama to review the modified files.
- **Post Review Comments**: Automatically posts review comments to the pull request.

## Usage

To use this action in your workflow, follow these steps:

1. **Create a Workflow File**: In your repository, create a workflow file in the `.github/workflows/` directory. For example, `.github/workflows/ollama_review.yml`.

2. **Configure the Workflow**: Add the following content to your workflow file, adjusting the `inputs` as necessary:

```yaml
name: Automated Ollama Code Review

on:
  pull_request:
    branches:
      - main

jobs:
  ollama_review:
    runs-on: ubuntu-latest
    name: Ollama Code Review Job
    steps:
      - name: Checkout Repository
        uses: actions/checkout@v2

      - name: Ollama Code Review
        uses: ./.github/actions/ollama-code-review
        with:
          llm-model: 'codegemma'
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```