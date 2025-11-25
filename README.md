# Secure Software Development - Security Scanning Project

## Overview

This project contains Semgrep security rules for detecting common web application vulnerabilities, specifically **Command Injection** and **Cross-Site Scripting (XSS)** vulnerabilities in PHP applications.

## Project Structure

```
.
├── semgrep-rules/          # Semgrep security detection rules
│   ├── command-injection.yaml
│   ├── xss-detection.yaml
│   ├── xss-detection2.yaml
│   └── xss-detection3.yaml
└── scan-results/           # Security scan results
    ├── command-injection-results.txt
    ├── xss-results.txt
    └── summary.txt
```

## Security Rules

### Command Injection Detection
- **File**: `semgrep-rules/command-injection.yaml`
- **Target**: PHP applications
- **Detects**: Unsafe use of `shell_exec()` function that may lead to command injection vulnerabilities

### XSS Detection
- **Files**: `semgrep-rules/xss-detection*.yaml`
- **Target**: PHP applications
- **Detects**: Direct output without proper encoding that may lead to XSS vulnerabilities

## Scan Results

The project includes scan results from security analysis:
- **Total Vulnerabilities Found**: 870
- **Command Injection**: 14 instances
- **XSS**: 859 instances

## Features

- ✅ Custom Semgrep rules for PHP security scanning
- ✅ Detection of command injection vulnerabilities
- ✅ Detection of XSS vulnerabilities
- ✅ Comprehensive scan results and summaries

## Requirements

- [Semgrep](https://semgrep.dev/) installed and configured
- PHP codebase to scan

## Quick Start

1. Install Semgrep (if not already installed):
   ```bash
   pip install semgrep
   ```

2. Run security scans using the provided rules:
   ```bash
   semgrep --config=semgrep-rules/command-injection.yaml /path/to/php/code
   semgrep --config=semgrep-rules/xss-detection.yaml /path/to/php/code
   ```

For detailed setup and usage instructions, see [SETUP.md](SETUP.md).

## License

This project is part of a Secure Software Development assignment.

## Author

Secure Software Development - Assignment 04
    Mohamed osama
    2305180

