# 🚀 SonarQube

---

# 🧭 **Table of Contents**

1. [What is SonarQube?](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#what-is-sonarqube)
2. [Why SonarQube?](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#why-sonarqube)
3. [Key Features](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#key-features)
4. [SonarQube Architecture](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#sonarqube-architecture)
5. [Supported Languages](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#supported-languages)
6. [Core Concepts](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#core-concepts)
    - Bugs
    - Vulnerabilities
    - Code Smells
    - Coverage
    - Duplications
7. [Quality Profiles](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#quality-profiles)
8. [Quality Gates](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#quality-gates)
9. [Installing SonarQube](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#installing-sonarqube)
10. [SonarQube Scanners](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#sonarqube-scanners)
11. [Running Analysis](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#running-analysis)
12. [Integrations (GitHub, GitLab, Jenkins, Azure)](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#integrations)
13. [SonarQube in CI/CD Pipelines](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#sonarqube-in-cicd)
14. [Best Practices for DevOps](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#best-practices)
15. [Troubleshooting & Common Issues](https://chatgpt.com/c/692734fa-0fd8-8324-b88b-9dbb5bbba5fe#troubleshooting)

---

# 1️⃣ **What is SonarQube?**

**SonarQube is a static code analysis platform** that automatically scans your source code to find:

- Bugs
- Security vulnerabilities
- Code smells
- Duplications
- Coverage issues
- Maintainability problems

It ensures your code meets quality standards **before production**.

---

# 2️⃣ **Why SonarQube?**

Reasons teams use SonarQube:

- Ensures **clean, safe, maintainable code**
- Detects issues early in development
- Integrates with popular CI/CD pipelines
- Supports 30+ languages
- Enforces **Quality Gates**
- Works with GitHub, GitLab, Bitbucket, Azure
- Provides dashboards & trend reports

Modern DevOps pipelines use SonarQube for **shifting quality left**.

---

# 3️⃣ **Key Features**

- Static code analysis
- Security vulnerability detection
- Code duplication detection
- Code coverage visualization
- Custom Quality Gates
- Detailed metrics & dashboards
- Branch analysis
- Pull request decoration
- Integration with CI/CD tools
- Built-in rule sets for each language

---

# 4️⃣ **SonarQube Architecture**

SonarQube consists of:

### **1. SonarQube Server**

Includes:

- **Web Server** → UI & APIs
- **Compute Engine** → processes analysis reports
- **Search Engine** → stores issues

### **2. Database**

Stores:

- Issues
- Metric history
- User data
- Rules
    
    Supported DBs:
    
- PostgreSQL (recommended)
- SQL Server
- Oracle (Enterprise)

### **3. SonarScanners**

Used to analyze source code.

Types:

- SonarScanner CLI
- Maven Scanner
- Gradle Scanner
- npm/JavaScript Scanner
- .NET Scanner (MSBuild)
- Jenkins/GitHub Actions/Azure scanners

### **4. Code Repository**

GitHub / GitLab / Bitbucket / Azure Repos.

**Flow:**

1. Scanner scans your code
2. Sends report to SonarQube Server
3. Compute Engine processes it
4. Results stored in DB
5. Dashboard shows metrics

---

# 5️⃣ **Supported Languages**

SonarQube supports 30+ languages including:

- Java
- Python
- JavaScript
- TypeScript
- Go
- C/C++
- C#
- PHP
- Ruby
- Swift
- Kotlin
- Terraform
- YAML
- JSON

---

# 6️⃣ **Core Concepts**

SonarQube identifies **five key categories**:

---

## 🔶 **1. Bugs**

Logic errors causing incorrect behavior.

Example:

- Null pointer dereference
- Uninitialized variables

---

## 🔶 **2. Vulnerabilities**

Security risks.

Example:

- SQL injection
- Hardcoded credentials
- Insecure cryptography

---

## 🔶 **3. Code Smells**

Maintainability issues.

Example:

- Duplicate logic
- Long functions
- Large classes

---

## 🔶 **4. Code Coverage**

How much of your code is tested by unit tests.

Example:

```
80% coverage → good
20% coverage → risky
```

---

## 🔶 **5. Duplications**

Copy-paste code blocks.

High duplication → difficult maintenance.

---

# 7️⃣ **Quality Profiles**

A **quality profile = rule set** for a language.

Each language has:

- Default profile (recommended)
- Custom profiles

You can:

- Activate/deactivate rules
- Create custom profiles
- Assign different profiles per project

Teams often maintain:

- **“Strict” profile for production apps**
- **“Soft” profile for PoCs/experiments**

---

# 8️⃣ **Quality Gates**

A **Quality Gate = pass/fail condition** for your project.

Common conditions:

- Coverage on new code ≥ 80%
- Bugs = 0
- Vulnerabilities = 0
- Code smells < threshold
- Duplicated lines < 3%
- Maintainability rating = A
- Security rating = A

If a project **fails** the Quality Gate:

❌ CI pipeline can stop

❌ Merge request can be blocked

Quality Gates = **core of SonarQube**.

---

# 9️⃣ **Installing SonarQube**

### ✔ Install via Docker (Recommended)

```bash
docker run -d --name sonarqube \
  -p 9000:9000 \
  sonarqube:latest
```

### ✔ Install on Linux (Manual)

1. Install Java 17
2. Download SonarQube ZIP
3. Extract to `/opt/sonarqube`
4. Run:

```
./bin/linux-x86-64/sonar.sh start
```

### ✔ Default Credentials

```
Username: admin
Password: admin
```

---

# 🔟 **SonarQube Scanners**

Different projects use different scanners.

| Type | Usage |
| --- | --- |
| **CLI Scanner** | General projects |
| **Maven Scanner** | Java Maven projects |
| **Gradle Scanner** | Gradle projects |
| **npm/JS Scanner** | Node.js projects |
| **.NET Scanner** | MSBuild-based apps |
| **Jenkins Scanner Plugin** | Uses SonarScanner automatically |

---

# 1️⃣1️⃣ **Running Analysis**

---

## ✔ 1. **Using CLI Scanner**

Create `sonar-project.properties`:

```
sonar.projectKey=myproject
sonar.host.url=http://localhost:9000
sonar.login=TOKEN
```

Run:

```
sonar-scanner
```

---

## ✔ 2. **Maven Project**

```
mvn clean verify sonar:sonar \
  -Dsonar.projectKey=myproject \
  -Dsonar.host.url=http://localhost:9000 \
  -Dsonar.login=TOKEN
```

---

## ✔ 3. **Gradle Project**

```
./gradlew sonarqube \
  -Dsonar.projectKey=myproject \
  -Dsonar.host.url=http://localhost:9000 \
  -Dsonar.login=TOKEN
```

---

## ✔ 4. **npm / JavaScript**

```
npm install
npx sonar-scanner
```

---

# 1️⃣2️⃣ **Integrations**

SonarQube integrates with:

- **GitHub Actions**
- **GitLab CI/CD**
- **Jenkins**
- **Azure DevOps**
- **Bitbucket Pipelines**

These add:

- Pull Request decoration
- Quality Gate checks
- Inline comments
- PR auto-failures if quality gate fails

---

# 1️⃣3️⃣ **SonarQube in CI/CD**

---

## ✔ GitHub Actions (Basic)

```yaml
- name: SonarQube Scan
  uses: sonarsource/sonarqube-scan-action@v2
  with:
    host-url: http://localhost:9000
    token: ${{ secrets.SONAR_TOKEN }}
```

---

## ✔ Jenkins Pipeline

```groovy
stage('SonarQube Analysis') {
  withSonarQubeEnv('sonarqube-server') {
    sh 'mvn sonar:sonar'
  }
}
```

---

## ✔ Azure DevOps

```yaml
- task: SonarQubePrepare@5
  inputs:
    SonarQube: 'MySonarQube'
    scannerMode: 'Other'
    configMode: 'manual'
    cliProjectKey: 'myproject'

- task: SonarQubeAnalyze@5

- task: SonarQubePublish@5
```

---

# 1️⃣4️⃣ **Best Practices for DevOps**

- Enforce **Quality Gates** in CI pipeline
- Scan **every PR** before merging
- Use **SonarQube tokens** securely (GitHub Secrets/KeyVault/Vault)
- Run scans **before unit tests** for faster feedback
- Keep SonarQube server behind HTTPS
- Maintain custom Quality Profiles
- Update rule sets periodically
- Use branch analysis to monitor PR quality

---

# 1️⃣5️⃣ **Troubleshooting**

### 🔧 Issue: “Unauthorized”

→ Token missing or wrong

→ Check `sonar.login` value

### 🔧 Issue: Scanner not found

→ Install scanner or add to PATH

### 🔧 Issue: “Java version not supported”

→ SonarQube requires Java 17+

### 🔧 Issue: Results not visible

→ Check:

- Network access
- Runner logs
- Compute Engine status

---