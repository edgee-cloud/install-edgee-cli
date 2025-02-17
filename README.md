# Install Edgee's CLI Github Action

## Overview
This GitHub Action automates the process of installing Edgee CLI's, building and testing Edgee components

## Features
- Installs the Edgee CLI via the `edgee-cloud/install-edgee-cli`.

## Example Usage
To use this action in your GitHub workflows, add the following to your `.github/workflows/build.yml` file:

```yaml
name: Build and Deploy

on:
  push:
    branches:
      - "*"
  pull_request:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Install Edgee
        uses: edgee-cloud/install-edgee-action@v0.1.0-beta

      - name: Build
        run: |
          edgee components build

      - name: Verify .wasm file exists
        run: |
          if [ -f "./example-js-component.wasm" ]; then
            echo "✅ WASM file generated successfully!"
          else
            echo "❌ Error: example-js-component.wasm not found! There's an issue with your build" >&2
            exit 1
          fi

      - name: Run tests
        run: npm test
```

## Inputs
This action does not require additional user inputs.

## Environment Variables
No specific environment variables are required for this action.
