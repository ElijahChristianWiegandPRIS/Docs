# PRIS Local Setup - Shortened 

## Prerequisites
- GitHub account with naming convention: FirstNameLastNameOrgName
- Request SFC for GW access from team leads
- Infrastructure approval for offline-repo access

## Quick Setup Steps

### 1. Environment Setup
- Create directories: `C:/workgit` and `C:/innovation/a`
- Extract Corretto 11 to `C:/innovation/a`
- Set environment variables:
  - JAVA_HOME : Point to Corretto JDK path
  - Add JAVA_HOME\bin; to PATH (both User and System)

### 2. MySQL 8.0.33 Installation
- Download mysql-installer-web-community-8.0.33.0.msi
- Use Developer Default setup
- Root password: `innovation!`
- Create databases: `custPRIS` and `custPRIS_dw` (latin1 charset)
- Create Java user: username `java`, password `kaffe9`, with roles: MonitorAdmin, DBManager, DBDesigner, BackupAdmin
- Set max_allowed_packet to 50M in Options File

### 3. Code Setup
```bash
cd /c/workgit
git clone [repo-url]
# Extract offline-repository.zip to workgit
```
### 4. IntelliJ Setup
- Install Community Edition via JetBrains Toolbox
- Open project: File > New > Module from Existing Source > build.gradle
- Set heap size to 10000 MB (Help > Change Memory Settings)
- Project Structure: Set Project SDK to Amazon Corretto 11
- Gradle Settings: Build with IntelliJ IDEA, Gradle JVM to JAVA_HOME
### 5. Run Configuration
- Create Application config: Main class `com.guidewire.webapp.InsuranceNow`
- Module: `custPRIS.test`
- VM Options:
``` 
-DPrefsDirectory=out/test/resources/APP-INF
-DBirtDirectory=out/test/resources/birt-viewer
-DIN_PORT=9090
-DIN_HTTPS_PORT=9443
```
- Shorten Command Line: JAR manifest

### 6. Initialize & Start
1. Run Gradle task: `custPRIS > Tasks > devtools > resetDB`
2. Run Gradle task: `setupConfigResources`
3. Start server: Run configuration or `runWebApp` Gradle task
4. Access: [http://localhost:9090](http://localhost:9090) or [https://localhost:9443](https://localhost:9443)

## Notes
- Repo directory must start with `custPRIS` or end with `-spi`
- Wait for IntelliJ indexing to complete before configuration
- DBeaver recommended for RedShift access (post-Mock Implementation)
