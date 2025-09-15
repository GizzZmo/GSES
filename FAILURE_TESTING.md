# Workflow Failure Testing Guide

## Overview

The GSES project includes a sophisticated workflow failure testing system designed to validate CI/CD resilience and failure handling mechanisms.

## Failure Testing Workflow

The `failure-testing.yml` workflow provides controlled failure scenarios to test:

### Available Failure Types

1. **Build Failure** (`build_failure`) - Default
   - Simulates compilation or build process failures
   - Tests build system error handling

2. **Test Failure** (`test_failure`)
   - Simulates unit test failures
   - Validates test reporting and failure notifications

3. **Deployment Failure** (`deployment_failure`)
   - Simulates deployment environment issues
   - Tests deployment rollback and error recovery

4. **Timeout Failure** (`timeout_failure`)
   - Simulates operations that exceed time limits
   - Tests timeout handling and resource cleanup

5. **Dependency Failure** (`dependency_failure`)
   - Simulates package/dependency resolution failures
   - Tests dependency management error handling

## Running Failure Tests

### Automatic Triggers
The failure testing workflow runs automatically on:
- Push to `main` or `develop` branches
- Pull request creation/updates
- Default failure type: `build_failure`

### Manual Execution
You can manually trigger specific failure scenarios:

1. Go to GitHub Actions tab
2. Select "Failure Testing Workflow"  
3. Click "Run workflow"
4. Choose your desired failure type
5. Click "Run workflow" to execute

### Using GitHub CLI
```bash
# Trigger build failure test
gh workflow run "Failure Testing Workflow" --ref main

# Trigger specific failure type
gh workflow run "Failure Testing Workflow" --ref main -f failure_type=test_failure
```

## Best Practices

1. **Regular Testing**: Run failure tests weekly
2. **Scenario Coverage**: Test all failure types monthly  
3. **Documentation**: Keep failure scenarios updated
4. **Team Training**: Ensure team knows how to interpret results

---

This failure testing system ensures the robustness and reliability of the GSES governance system workflows.