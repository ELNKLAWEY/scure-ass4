# Setup and Usage Guide

This document provides detailed instructions for setting up and using the security scanning tools in this project.

## Prerequisites

Before you begin, ensure you have the following installed:

- **Python 3.7+** - Required for Semgrep
- **pip** - Python package manager
- **Git** - For cloning repositories (if applicable)

## Installation

### Step 1: Install Semgrep

Install Semgrep using pip:

```bash
pip install semgrep
```

Or using pipx (recommended for isolated installation):

```bash
pipx install semgrep
```

Verify the installation:

```bash
semgrep --version
```

### Step 2: Clone or Download the Project

If you have the project in a Git repository:

```bash
git clone <repository-url>
cd Secure-Software-Develpment-2305180-Assignment-04
```

Or extract the project files to your desired location.

## Usage

### Running Security Scans

#### Command Injection Scan

To scan for command injection vulnerabilities:

```bash
semgrep --config=semgrep-rules/command-injection.yaml /path/to/your/php/codebase
```

Example:
```bash
semgrep --config=semgrep-rules/command-injection.yaml ./src
```

#### XSS Detection Scan

To scan for XSS vulnerabilities using the first rule:

```bash
semgrep --config=semgrep-rules/xss-detection.yaml /path/to/your/php/codebase
```

To use all XSS detection rules:

```bash
semgrep --config=semgrep-rules/xss-detection.yaml --config=semgrep-rules/xss-detection2.yaml --config=semgrep-rules/xss-detection3.yaml /path/to/your/php/codebase
```

#### Running All Security Scans

To run all security rules at once:

```bash
semgrep --config=semgrep-rules/ /path/to/your/php/codebase
```

### Saving Scan Results

To save scan results to a file:

```bash
semgrep --config=semgrep-rules/command-injection.yaml /path/to/codebase --json > scan-results/command-injection-results.json
```

Or in text format:

```bash
semgrep --config=semgrep-rules/command-injection.yaml /path/to/codebase > scan-results/command-injection-results.txt
```

### Advanced Options

#### Output Formats

Semgrep supports multiple output formats:

- **Text** (default): Human-readable output
- **JSON**: Machine-readable output
- **SARIF**: Standard format for security tools

Example with JSON output:

```bash
semgrep --config=semgrep-rules/ --json /path/to/codebase
```

#### Excluding Files or Directories

To exclude certain files or directories from scanning:

```bash
semgrep --config=semgrep-rules/ --exclude="vendor/**" --exclude="node_modules/**" /path/to/codebase
```

#### Setting Severity Filter

To only show high-severity issues:

```bash
semgrep --config=semgrep-rules/ --severity=ERROR /path/to/codebase
```

## Understanding the Rules

### Command Injection Rule

The `command-injection.yaml` rule detects:
- Use of `shell_exec()` function
- Potential for command injection when user input is passed to shell commands

**Severity**: ERROR

### XSS Detection Rules

The XSS detection rules identify:
- Direct output using `echo` without proper encoding
- Potential XSS vulnerabilities in PHP applications

**Severity**: ERROR

## Troubleshooting

### Common Issues

1. **Semgrep not found**
   - Ensure Semgrep is installed: `pip install semgrep`
   - Check your PATH environment variable

2. **No results found**
   - Verify the path to your codebase is correct
   - Ensure the codebase contains PHP files
   - Check that the rules are in the correct format

3. **Too many false positives**
   - Review and customize the rules in the YAML files
   - Adjust pattern matching to be more specific

### Getting Help

- Semgrep Documentation: https://semgrep.dev/docs/
- Semgrep Community: https://semgrep.dev/community

## Best Practices

1. **Regular Scanning**: Run scans regularly during development
2. **CI/CD Integration**: Integrate Semgrep into your CI/CD pipeline
3. **Review Results**: Always review scan results and fix legitimate vulnerabilities
4. **Customize Rules**: Adjust rules based on your application's specific needs
5. **Version Control**: Keep your security rules in version control

## Next Steps

After running scans:
1. Review the results in `scan-results/` directory
2. Prioritize fixing high-severity vulnerabilities
3. Update your code to address identified security issues
4. Re-run scans to verify fixes

For more information about the project, see [README.md](README.md).

