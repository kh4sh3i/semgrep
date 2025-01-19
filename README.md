<h1 align="center">
  <br>
  <a href=""><img src="/img/logo.webp" alt="" width="400px;"></a>
  <br>
  <img src="https://img.shields.io/badge/PRs-welcome-blue">
  <img src="https://img.shields.io/github/last-commit/kh4sh3i/semgrep">
  <img src="https://img.shields.io/github/commit-activity/m/kh4sh3i/semgrep">
  <a href="https://twitter.com/intent/follow?screen_name=kh4sh3i_"><img src="https://img.shields.io/twitter/follow/kh4sh3i_?style=flat&logo=twitter"></a>
  <a href="https://github.com/kh4sh3i"><img src="https://img.shields.io/github/stars/kh4sh3i?style=flat&logo=github"></a>
</h1>


# semgrep
Semgrep is an open-source static analysis tool designed to find vulnerabilities, bugs, and enforce code quality standards across multiple programming languages.

* Core Feature: It uses abstract syntax tree (AST) pattern matching, allowing it to detect issues based on the structure of code rather than simple text patterns.

### Key Benefits:

*   Fast and Flexible: Performs static analysis quickly and can be adapted to various codebases.
*   Precision: Detects vulnerabilities that might be missed by traditional text-based tools.
*   Customizability: Allows users to write their own rules or use pre-defined ones from the Semgrep Registry.
*   Security and Quality: Helps identify security vulnerabilities (e.g., SQL injection, XSS) and improve code quality by enforcing best practices.
*   Supported Languages: Semgrep supports several popular programming languages, including Python, JavaScript, Java, Go, and more.
*   CI/CD Integration: Seamlessly integrates with CI/CD pipelines (e.g., GitLab, GitHub) for continuous static analysis, making it an excellent tool for DevSecOps teams.


### Use Cases:

* Automating code review to detect vulnerabilities early.
* Enforcing code style guidelines.
* Integrating into the security testing pipeline for proactive vulnerability detection.


## Install Semgrep
```bash
pip install semgrep
semgrep --version
```

## Choose or Create Rules
```
https://github.com/semgrep/semgrep-rules
```

## Integrate into CI/CD Pipeline
```bash
stages:
  - test

test:
  image: semgrep/semgrep
  script:
    - semgrep --config=python-security --path=./my-python-project/
```

## Running Semgrep rules locally
tips : in offline mode we should download all rules from this [repo](https://github.com/semgrep/semgrep-rules) or use pro rule that upload above.
```bash
semgrep scan --config="RULESET-ID" --config=PATH/TO/MYRULE.YAML PATH/TO/SRC
semgrep scan -config=/ProRules/   PATH/TO/sourcecode
```

## semgrep Pro analysis
we can login to https://semgrep.dev/orgs/-/settings to use semgrep portal,
we upload localy project to semgrep portal and we can use pro rule and some sca !

```bash
python3 -m pip install --upgrade semgrep
semgrep login
semgrep install-semgrep-pro
semgrep --config auto --pro
go to root of git repo and run
semgrep ci
```

## Learn Semgrep Syntax
```
https://semgrep.dev/learn
```

## execute live code
```
https://semgrep.dev/playground/new
```

## Create a Basic Custom Rule
* Example 1: Detecting Hardcoded Passwords in Python
```bash
# hardcoded_password_rule.yml
rules:
  - id: python-hardcoded-password
    pattern: |
      password = "$PASSWORD"
    message: "Hardcoded password detected. Avoid hardcoding sensitive information."
    severity: WARNING
    languages: [python]
    metadata:
      category: security
```

* Example 2: Detecting Use of eval in Python (Potential Security Risk)
```bash
# use_of_eval_rule.yml
rules:
  - id: python-use-of-eval
    pattern: |
      eval($EXPR)
    message: "Avoid using eval(). It can lead to code injection vulnerabilities."
    severity: ERROR
    languages: [python]
    metadata:
      category: security
```


## refrences
* [semgrep.dev](https://semgrep.dev/docs/semgrep-code/semgrep-pro-engine-intro#run-cross-file-analysis-in-the-cli)


