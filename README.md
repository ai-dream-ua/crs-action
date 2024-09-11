## GitHub Action for integration with CRS(code review system)


### Usage

Add this action to your `pull_request` workflow:

```yaml
name: My Workflow

on:
  pull_request:
    branches:
      - master
    types: [opened, synchronize]

jobs:
  code_review:
    name: 'Code Review'
    runs-on: ubuntu-latest

    permissions:
      contents: read 
      pull-requests: write # required for commenting in PR
 
    steps:
      - name: Code review
        uses: ai-dream-ua/crs-gh-action@v1
        with:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }} # required for commenting in PR
          crs-api-token: ${{ secrets.CRS_API_TOKEN }} # contact CRS team to get the token
          exclude: "**/*.md, **/*-lock.json" # exclude files from review process
```
