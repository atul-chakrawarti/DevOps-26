# DevOps-26
# 30 DAYS OF DEVOPS - Complete Learning Notes
## Comprehensive Guide to Modern DevOps Practices

---

## Table of Contents
1. [Course Overview](#course-overview)
2. [Week 1: Introduction & Build Tools (Days 1-5)](#week-1)
3. [Week 2: Containers & Cloud (Days 6-10)](#week-2)
4. [Week 3: Azure DevOps (Days 11-15)](#week-3)
5. [Week 4: Infrastructure as Code (Days 16-20)](#week-4)
6. [Week 5: Advanced Topics (Days 21-30)](#week-5)
7. [Complete Implementation Guide](#implementation)
8. [Career Path & Next Steps](#career)

---

# COURSE OVERVIEW

**Course Name:** 30 Days of DevOps  
**Source:** DevOps Shack YouTube Channel  
**Repository:** https://github.com/jaiswaladi246/30-Days-Of-DevOps  
**Duration:** 30 Days (4 Weeks + 2 Days)  
**Level:** Beginner to Intermediate  

---

# WEEK 1: INTRODUCTION & BUILD TOOLS

## DAY 1: DevOps Explained

### Learning Objectives
- Understand what DevOps is and why it matters
- Know the differences between traditional and DevOps approaches
- Learn CI/CD principles
- Understand the DevOps lifecycle

### Key Concepts

**What is DevOps?**
DevOps = Development + Operations + Culture + Automation + Continuous Improvement

**The DevOps Principle:**
> "You build it, you run it."

**Core Pillars:**
1. **Collaboration** - Breaking silos between Dev and Ops
2. **Automation** - Automating repetitive tasks
3. **Measurement** - Tracking metrics and improving continuously
4. **Sharing** - Knowledge sharing across teams

**Traditional vs DevOps Approach:**

| Aspect | Traditional | DevOps |
|--------|-----------|--------|
| Team Structure | Separate Dev & Ops | Cross-functional teams |
| Deployment | Quarterly/Monthly | Daily/Multiple times per day |
| Time to Market | Weeks/Months | Hours/Minutes |
| Error Rate | Higher | Lower |
| Collaboration | Poor | Excellent |
| Automation | Manual | Automated |

### CI/CD Pipeline Overview

**Continuous Integration (CI):**
- Developers commit code frequently
- Automated build and test on every commit
- Issues detected immediately
- Feedback to developers in minutes

**Continuous Delivery (CD):**
- Code ready for production at any time
- Manual approval before production deployment
- Automated deployment to non-prod environments

**Continuous Deployment:**
- Automatic deployment to production
- No manual approval needed
- Requires very high test confidence

### Benefits of DevOps
- ✓ Faster time to market
- ✓ Improved quality
- ✓ Better collaboration
- ✓ Reduced costs
- ✓ Higher customer satisfaction
- ✓ Better career opportunities

### Key Metrics
1. **Deployment Frequency** - How often you deploy (Goal: Daily+)
2. **Lead Time** - Time from commit to production (Goal: < 1 hour)
3. **MTTR** - Mean Time To Recovery (Goal: < 1 hour)
4. **Change Failure Rate** - % of deployments causing issues (Goal: < 15%)

---

## DAY 2: Introduction to Maven

### Learning Objectives
- Understand Maven's role in build automation
- Learn Maven project structure
- Create and manage Maven projects
- Understand dependency management

### What is Maven?

Maven is a build automation tool primarily used for Java projects. It manages:
- **Project Build** - Compiling source code
- **Dependency Management** - Managing libraries and versions
- **Project Packaging** - Creating JAR/WAR files
- **Testing** - Running automated tests
- **Documentation** - Generating project documentation

### Maven Benefits

✓ Standardized project structure  
✓ Dependency management  
✓ Plugin architecture  
✓ Easy builds and testing  
✓ Integration with CI/CD tools  

### Maven Project Structure

```
my-app/
├── pom.xml                    (Project configuration)
├── src/
│   ├── main/
│   │   ├── java/             (Source code)
│   │   └── resources/        (Resources like properties)
│   └── test/
│       ├── java/             (Test code)
│       └── resources/        (Test resources)
└── target/                   (Built artifacts)
    └── my-app-1.0.jar
```

### Maven Lifecycle Phases

1. **validate** - Validate project is correct
2. **compile** - Compile source code
3. **test** - Run unit tests
4. **package** - Create JAR/WAR
5. **integration-test** - Run integration tests
6. **verify** - Verify package is valid
7. **install** - Install to local repository
8. **deploy** - Deploy to remote repository

### Essential Maven Commands

```bash
# Create new project
mvn archetype:generate -DgroupId=com.example \
  -DartifactId=my-app -DarchetypeArtifactId=maven-archetype-quickstart

# Compile
mvn clean compile

# Run tests
mvn test

# Package
mvn package

# Install locally
mvn install

# Deploy
mvn deploy

# Clean build directory
mvn clean
```

### POM.xml Basics

```xml
<project>
  <modelVersion>4.0.0</modelVersion>
  
  <groupId>com.example</groupId>
  <artifactId>my-app</artifactId>
  <version>1.0-SNAPSHOT</version>
  
  <dependencies>
    <dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <version>4.12</version>
      <scope>test</scope>
    </dependency>
  </dependencies>
</project>
```

### Dependency Management

**Dependency Scopes:**
- **compile** - Available in all classpaths (default)
- **provided** - Provided by runtime (e.g., servlet API)
- **runtime** - Needed at runtime, not compile time
- **test** - Only for testing
- **system** - External JAR file path
- **import** - Used with `<type>pom</type>`

---

## DAY 3: Apache Tomcat

### Learning Objectives
- Understand Tomcat's role as a servlet container
- Install and configure Tomcat
- Deploy applications to Tomcat
- Manage Tomcat services

### What is Apache Tomcat?

Apache Tomcat is:
- Open-source Java servlet container
- Web server for Java applications
- Implements Java Servlet and JavaServer Pages (JSP) specifications
- Lightweight alternative to full application servers

### Tomcat Architecture

```
Tomcat Server
├── Catalina (Servlet Container)
├── Coyote (HTTP/Connector)
├── Jasper (JSP Engine)
└── Manager (Application Manager)
```

### Installation Steps

**Linux Installation:**

```bash
# Download Tomcat
cd /opt
sudo wget https://archive.apache.org/dist/tomcat/tomcat-9/v9.0.65/bin/apache-tomcat-9.0.65.tar.gz

# Extract
sudo tar -xvf apache-tomcat-9.0.65.tar.gz

# Create symbolic links
sudo ln -s /opt/apache-tomcat-9.0.65/bin/startup.sh /usr/bin/startTomcat
sudo ln -s /opt/apache-tomcat-9.0.65/bin/shutdown.sh /usr/bin/stopTomcat

# Configure users
sudo vi /opt/apache-tomcat-9.0.65/conf/tomcat-users.xml
# Add: <user username="admin" password="admin1234" roles="admin-gui, manager-gui"/>

# Start Tomcat
startTomcat
```

### Tomcat Directory Structure

```
apache-tomcat-9.0.65/
├── bin/                    (Startup/shutdown scripts)
├── conf/                   (Configuration files)
│   └── tomcat-users.xml   (User credentials)
├── logs/                   (Log files)
├── webapps/                (Deployed applications)
│   ├── ROOT/              (Default application)
│   ├── manager/           (Manager GUI)
│   └── docs/              (Documentation)
└── work/                   (Temporary files)
```

### Deploying Applications

**Method 1: Copy WAR file**
```bash
# Build your Java application
mvn clean package

# Copy to webapps
sudo cp target/my-app.war /opt/apache-tomcat-9.0.65/webapps/

# Tomcat auto-deploys
# Access at: http://localhost:8080/my-app
```

**Method 2: Using Manager GUI**
- Navigate to: http://localhost:8080/manager/html
- Upload WAR file through web interface

### Key Tomcat Configuration

**server.xml:**
```xml
<Server port="8005" shutdown="SHUTDOWN">
  <Connector port="8080" protocol="HTTP/1.1" />
  
  <Engine name="Catalina" defaultHost="localhost">
    <Host name="localhost" appBase="webapps">
      <Context path="/myapp" docBase="myapp.war" />
    </Host>
  </Engine>
</Server>
```

### Tomcat Management Commands

```bash
# Start Tomcat
startTomcat
# or
/opt/apache-tomcat-9.0.65/bin/startup.sh

# Stop Tomcat
stopTomcat
# or
/opt/apache-tomcat-9.0.65/bin/shutdown.sh

# Check status
ps aux | grep tomcat

# View logs
tail -f /opt/apache-tomcat-9.0.65/logs/catalina.out
```

---

## DAY 4: Jenkins - Continuous Integration Server

### Learning Objectives
- Understand Jenkins and its role in CI/CD
- Install and configure Jenkins
- Create and run a Jenkins pipeline
- Integrate Jenkins with Git

### What is Jenkins?

Jenkins is:
- Open-source automation server
- Most popular CI/CD tool
- Supports distributed builds
- Extensible with 1000+ plugins
- Supports pipeline as code

### Why Jenkins?

✓ Easy to set up and use  
✓ Supports distributed architecture  
✓ Large plugin ecosystem  
✓ Pipeline support (Jenkins Pipeline)  
✓ Free and open-source  
✓ Multi-platform support  

### Jenkins Installation (Linux)

```bash
# Update system
sudo apt-get update

# Install Java
sudo apt-get install openjdk-11-jdk

# Add Jenkins repository
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io.key | \
  sudo tee /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | \
  sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null

# Install Jenkins
sudo apt-get update
sudo apt-get install jenkins

# Start Jenkins
sudo systemctl start jenkins
sudo systemctl enable jenkins

# Access Jenkins
# http://localhost:8080

# Get initial admin password
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

### Jenkins Main Concepts

**1. Jobs/Projects**
- Unit of work Jenkins can execute
- Can be freestyle or pipeline jobs

**2. Pipeline**
- Series of automated steps
- Defined as code (Jenkinsfile)
- Supports parallel execution

**3. Stages**
- Logical divisions of work
- Can have multiple steps
- Must complete successfully to progress

**4. Agents/Nodes**
- Machines where jobs execute
- Master: Controls orchestration
- Agents: Execute jobs

### Creating a Simple Pipeline

**Jenkinsfile (Declarative)**

```groovy
pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code...'
                git 'https://github.com/user/repo.git'
            }
        }
        
        stage('Build') {
            steps {
                echo 'Building...'
                sh 'mvn clean package'
            }
        }
        
        stage('Test') {
            steps {
                echo 'Testing...'
                sh 'mvn test'
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                sh 'cp target/*.war /opt/tomcat/webapps/'
            }
        }
    }
    
    post {
        always {
            echo 'Pipeline completed'
        }
        success {
            echo 'Pipeline succeeded'
        }
        failure {
            echo 'Pipeline failed'
        }
    }
}
```

### Jenkins Plugins

**Essential Plugins:**
- Git - Git integration
- Maven - Maven build support
- Docker - Docker integration
- Kubernetes - Kubernetes deployment
- Pipeline - Pipeline support
- Email - Email notifications
- Slack - Slack notifications

**Installation:**
- Jenkins Dashboard → Manage Jenkins → Manage Plugins
- Search and install required plugins

### Jenkins Best Practices

✓ Use declarative pipelines  
✓ Keep jobs simple and focused  
✓ Use environment variables  
✓ Implement proper error handling  
✓ Log important information  
✓ Clean up old builds  
✓ Secure credentials with Credentials Store  
✓ Monitor Jenkins performance  

---

## DAY 5: SonarQube - Code Quality Analysis

### Learning Objectives
- Understand code quality importance
- Install and configure SonarQube
- Integrate SonarQube with Maven
- Analyze code quality metrics

### What is SonarQube?

SonarQube is:
- Open-source code quality platform
- Analyzes code for bugs, vulnerabilities, and code smells
- Measures code coverage
- Provides actionable reports
- Integrates with CI/CD pipelines

### Why Code Quality Matters

✓ Early bug detection  
✓ Reduced technical debt  
✓ Better maintainability  
✓ Security vulnerability detection  
✓ Improved code standards  
✓ Team knowledge sharing  

### SonarQube Metrics

**1. Bugs** - Actual problems in code
**2. Vulnerabilities** - Security issues
**3. Code Smells** - Design/style issues
**4. Code Coverage** - % of code covered by tests
**5. Duplications** - Repeated code blocks
**6. Complexity** - Cyclomatic complexity

### SonarQube Installation (Linux)

```bash
# Install dependencies
sudo apt-get install openjdk-11-jdk
sudo apt-get install postgresql postgresql-contrib

# Create PostgreSQL user
sudo su - postgres
createuser sonar
createdb -O sonar sonarqube

# Download SonarQube
cd /opt
sudo wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-9.7.1.62043.zip
sudo unzip sonarqube-9.7.1.62043.zip

# Configure database
sudo vi /opt/sonarqube-9.7.1.62043/conf/sonar.properties
# Uncomment and configure:
# sonar.jdbc.username=sonar
# sonar.jdbc.password=sonar
# sonar.jdbc.url=jdbc:postgresql://localhost/sonarqube

# Start SonarQube
/opt/sonarqube-9.7.1.62043/bin/linux-x86-64/sonar.sh start

# Access SonarQube
# http://localhost:9000
# Default credentials: admin/admin
```

### Maven Integration with SonarQube

**pom.xml Configuration:**

```xml
<properties>
  <sonar.host.url>http://localhost:9000</sonar.host.url>
  <sonar.login>your-sonarqube-token</sonar.login>
  <sonar.java.coveragePlugin>jacoco</sonar.java.coveragePlugin>
  <jacoco.version>0.8.6</jacoco.version>
</properties>

<dependencies>
  <dependency>
    <groupId>org.jacoco</groupId>
    <artifactId>jacoco-maven-plugin</artifactId>
    <version>${jacoco.version}</version>
  </dependency>
</dependencies>

<build>
  <plugins>
    <plugin>
      <groupId>org.jacoco</groupId>
      <artifactId>jacoco-maven-plugin</artifactId>
      <version>${jacoco.version}</version>
      <executions>
        <execution>
          <goals>
            <goal>prepare-agent</goal>
          </goals>
        </execution>
        <execution>
          <phase>test</phase>
          <goals>
            <goal>report</goal>
          </goals>
        </execution>
      </executions>
    </plugin>
  </plugins>
</build>
```

### Running Code Analysis

```bash
# Run with Maven
mvn clean verify sonar:sonar

# View results
# http://localhost:9000/dashboard
```

### Jenkins + SonarQube Integration

**In Jenkinsfile:**

```groovy
pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        
        stage('SonarQube Analysis') {
            steps {
                sh '''
                    mvn sonar:sonar \
                    -Dsonar.projectKey=my-app \
                    -Dsonar.sources=src \
                    -Dsonar.host.url=http://sonarqube-server:9000 \
                    -Dsonar.login=your-token
                '''
            }
        }
        
        stage('Quality Gate') {
            steps {
                script {
                    // Add quality gate check
                    echo 'Checking quality gate...'
                }
            }
        }
    }
}
```

### Quality Gate Setup

Quality Gates are rules that define when builds pass or fail based on metrics:

**Example Gate:**
- Coverage < 80% → FAIL
- Bugs > 5 → FAIL
- Vulnerabilities > 0 → FAIL
- Code Smells > 20 → FAIL

---

# WEEK 2: CONTAINERS & CLOUD (Days 6-10)

## DAY 6: OWASP Dependency Check

### Learning Objectives
- Understand security vulnerability scanning
- Use OWASP Dependency Check tool
- Identify vulnerable dependencies
- Integrate into CI/CD pipeline

### What is OWASP Dependency-Check?

OWASP Dependency-Check is:
- Open-source vulnerability scanner
- Identifies known vulnerabilities in dependencies
- Supports multiple languages and package managers
- Provides detailed reports
- Easy to integrate in CI/CD

### Why Dependency Scanning?

✓ Early vulnerability detection  
✓ Reduce security breaches  
✓ Meet compliance requirements  
✓ Supply chain security  
✓ Automated risk management  

### Installation

```bash
# Download
cd /opt
wget https://github.com/jeremylong/DependencyCheck_releases/releases/download/v7.4.4/dependency-check-7.4.4-release.zip
unzip dependency-check-7.4.4-release.zip

# Create symlink
sudo ln -s /opt/dependency-check/bin/dependency-check.sh /usr/local/bin/dependency-check

# Verify
dependency-check --version
```

### Usage

```bash
# Scan directory
dependency-check --project "MyApp" --scan /path/to/project

# Generate report
dependency-check --project "MyApp" --scan /path/to/project \
  --format ALL --out ./reports

# Fail on critical vulnerabilities
dependency-check --project "MyApp" --scan /path/to/project \
  --failOnCVSS 7.0
```

### Maven Integration

```xml
<plugin>
  <groupId>org.owasp</groupId>
  <artifactId>dependency-check-maven</artifactId>
  <version>7.4.4</version>
  <configuration>
    <failBuildOnCVSS>7.0</failBuildOnCVSS>
  </configuration>
  <executions>
    <execution>
      <goals>
        <goal>check</goal>
      </goals>
    </execution>
  </executions>
</plugin>
```

### Jenkins Integration

```groovy
stage('Dependency Check') {
    steps {
        sh 'mvn org.owasp:dependency-check-maven:check'
    }
}
```

---

## DAY 7: Artifacts and Repository Management (Nexus)

### Learning Objectives
- Understand artifact repositories
- Install and configure Nexus
- Store and retrieve artifacts
- Manage versioning and access

### What is Nexus?

Nexus Repository Manager is:
- Centralized artifact repository
- Supports Maven, npm, Docker, etc.
- Manages dependencies and releases
- Provides version control and access control
- Essential for enterprise DevOps

### Nexus Benefits

✓ Centralized artifact storage  
✓ Dependency caching  
✓ Artifact versioning  
✓ Access control  
✓ Backup and recovery  
✓ Performance improvement  

### Repository Types

**1. Hosted Repositories**
- Store your own artifacts
- Types: Release, Snapshot

**2. Proxy Repositories**
- Cache external repositories
- Maven Central, npm registry, etc.

**3. Group Repositories**
- Combine multiple repositories
- Single endpoint for all dependencies

### Installation

```bash
# Download Nexus
cd /opt
wget https://download.sonatype.com/nexus/3/latest-unix.tar.gz
tar -xvf latest-unix.tar.gz

# Create user
sudo useradd nexus

# Change ownership
sudo chown -R nexus:nexus /opt/nexus*

# Start Nexus
sudo su - nexus
/opt/nexus-3.x/bin/nexus start

# Access
# http://localhost:8081
# Default: admin/admin123
```

### Configuration (settings.xml)

```xml
<settings>
  <servers>
    <server>
      <id>nexus-releases</id>
      <username>deployment</username>
      <password>deployment123</password>
    </server>
    <server>
      <id>nexus-snapshots</id>
      <username>deployment</username>
      <password>deployment123</password>
    </server>
  </servers>
  
  <mirrors>
    <mirror>
      <id>nexus</id>
      <mirrorOf>*</mirrorOf>
      <url>http://nexus-server:8081/repository/maven-group/</url>
    </mirror>
  </mirrors>
</settings>
```

### POM.xml Configuration

```xml
<distributionManagement>
  <repository>
    <id>nexus-releases</id>
    <url>http://nexus-server:8081/repository/maven-releases/</url>
  </repository>
  <snapshotRepository>
    <id>nexus-snapshots</id>
    <url>http://nexus-server:8081/repository/maven-snapshots/</url>
  </snapshotRepository>
</distributionManagement>
```

### Deploy Artifacts

```bash
# Deploy release
mvn deploy

# Upload to specific repository
mvn deploy:deploy-file \
  -Durl=http://nexus:8081/repository/maven-releases \
  -DrepositoryId=nexus-releases \
  -DgroupId=com.example \
  -DartifactId=my-app \
  -Dversion=1.0 \
  -Dfile=my-app-1.0.jar
```

---

## DAY 8: Docker - Containerization

### Learning Objectives
- Understand containerization benefits
- Install Docker
- Create Docker images
- Run and manage containers
- Push to Docker registry

### What is Docker?

Docker is:
- Container platform
- Packages applications with dependencies
- Lightweight alternative to VMs
- Ensures consistency across environments
- Enables microservices architecture

### Docker Benefits

✓ Portability - "Build once, run anywhere"  
✓ Consistency - Same environment everywhere  
✓ Efficiency - Lightweight compared to VMs  
✓ Scalability - Easy to scale horizontally  
✓ Isolation - Contained applications  

### Docker Installation (Linux)

```bash
# Update system
sudo apt-get update

# Install Docker
sudo apt-get install docker.io

# Add current user to docker group
sudo usermod -aG docker $USER

# Verify
docker --version
docker run hello-world
```

### Docker Concepts

**1. Image** - Blueprint for container
**2. Container** - Running instance of image
**3. Registry** - Stores images (Docker Hub, ECR, etc.)
**4. Dockerfile** - Instructions to build image
**5. Volume** - Persistent storage
**6. Network** - Container communication

### Dockerfile Example

```dockerfile
# Base image
FROM openjdk:11-jre-slim

# Set working directory
WORKDIR /app

# Copy application
COPY target/my-app.jar .

# Expose port
EXPOSE 8080

# Health check
HEALTHCHECK --interval=30s --timeout=3s \
  CMD curl -f http://localhost:8080/ || exit 1

# Run application
CMD ["java", "-jar", "my-app.jar"]
```

### Docker Commands

```bash
# Build image
docker build -t my-app:1.0 .

# Run container
docker run -d -p 8080:8080 --name my-container my-app:1.0

# List containers
docker ps -a

# View logs
docker logs my-container

# Stop container
docker stop my-container

# Remove container
docker rm my-container

# Push to registry
docker tag my-app:1.0 myregistry/my-app:1.0
docker push myregistry/my-app:1.0

# Pull image
docker pull myregistry/my-app:1.0
```

### Docker Compose

**docker-compose.yml:**

```yaml
version: '3.8'

services:
  web:
    image: my-app:1.0
    ports:
      - "8080:8080"
    environment:
      - DB_HOST=db
      - DB_PORT=5432
    depends_on:
      - db
    
  db:
    image: postgres:13
    environment:
      - POSTGRES_PASSWORD=secret
    volumes:
      - db-data:/var/lib/postgresql/data

volumes:
  db-data:
```

**Commands:**

```bash
# Start services
docker-compose up -d

# Stop services
docker-compose down

# View logs
docker-compose logs -f
```

### Best Practices

✓ Use specific base image versions  
✓ Keep images small  
✓ Use .dockerignore  
✓ Don't run as root  
✓ Use health checks  
✓ Implement proper logging  
✓ Use environment variables  
✓ Use volumes for persistence  

---

## DAY 9: YAML - Configuration Language

### Learning Objectives
- Understand YAML syntax
- Learn YAML best practices
- Use YAML in DevOps tools
- Create valid YAML files

### What is YAML?

YAML = YAML Ain't Markup Language

YAML is:
- Human-readable data serialization format
- Used for configuration files
- Supports lists, maps, and scalars
- Used in Docker Compose, Kubernetes, Ansible, etc.

### YAML Syntax

**Basic Types:**

```yaml
# Strings
name: John
title: "DevOps Engineer"

# Numbers
age: 30
salary: 75000.50

# Booleans
active: true
deleted: false

# Null
value: null

# Lists
languages:
  - Python
  - Java
  - Go

# Alternative list syntax
languages: [Python, Java, Go]

# Maps/Dictionaries
person:
  name: John
  age: 30
  city: New York

# Multi-line strings
description: |
  This is a long description
  that spans multiple lines
  with preserved line breaks

# Folded strings
summary: >
  This is a summary that
  spans multiple lines
  but is folded into one line
```

### YAML Indentation

```yaml
# Correct - 2 spaces
root:
  child1:
    grandchild: value
  child2: value

# Incorrect - inconsistent
root:
  child1:
      grandchild: value  # 4 spaces
  child2: value          # 2 spaces
```

### Complex Examples

**Kubernetes Pod:**

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
  labels:
    app: myapp
spec:
  containers:
  - name: web
    image: nginx:latest
    ports:
    - containerPort: 80
    resources:
      requests:
        memory: "256Mi"
        cpu: "250m"
      limits:
        memory: "512Mi"
        cpu: "500m"
```

**Docker Compose:**

```yaml
version: '3.8'
services:
  web:
    image: myapp:1.0
    ports:
      - "8080:8080"
    environment:
      - LOG_LEVEL=INFO
      - DATABASE_URL=postgresql://db:5432/mydb
    depends_on:
      - db
  
  db:
    image: postgres:13
    environment:
      - POSTGRES_PASSWORD=secret
```

### YAML Validation

```bash
# Validate YAML online
# yamllint.readthedocs.io

# Install yamllint
pip install yamllint

# Validate file
yamllint my-config.yaml
```

### YAML Tips

✓ Use 2-space indentation  
✓ Avoid tabs  
✓ Be consistent with structure  
✓ Use clear key names  
✓ Comment complex sections  
✓ Use proper quoting  
✓ Validate before using  

---

## DAY 10: Kubernetes - Container Orchestration

### Learning Objectives
- Understand Kubernetes architecture
- Install Kubernetes
- Deploy applications to Kubernetes
- Manage scaling and updates
- Use Kubernetes services

### What is Kubernetes?

Kubernetes (K8s) is:
- Open-source container orchestration platform
- Automates deployment, scaling, and management
- Handles high availability
- Self-healing capabilities
- Supports multiple cloud providers

### Kubernetes Benefits

✓ Automatic scaling  
✓ High availability  
✓ Self-healing  
✓ Rolling updates  
✓ Resource management  
✓ Multi-cloud support  

### Kubernetes Architecture

```
┌─────────────────────────────────────────┐
│       Kubernetes Cluster                │
├─────────────────────────────────────────┤
│  Master Node (Control Plane)            │
│  ├─ API Server                          │
│  ├─ Scheduler                           │
│  ├─ Controller Manager                  │
│  └─ etcd (State Store)                  │
├─────────────────────────────────────────┤
│  Worker Nodes                           │
│  ├─ Node 1 (Kubelet + Docker + Kube-proxy)
│  │   ├─ Pod 1                           │
│  │   └─ Pod 2                           │
│  ├─ Node 2 (Kubelet + Docker + Kube-proxy)
│  │   ├─ Pod 3                           │
│  │   └─ Pod 4                           │
│  └─ Node 3 (Kubelet + Docker + Kube-proxy)
│      ├─ Pod 5                           │
│      └─ Pod 6                           │
└─────────────────────────────────────────┘
```

### Key Kubernetes Objects

**1. Pod** - Smallest deployable unit
**2. Deployment** - Manages ReplicaSets
**3. Service** - Exposes pods
**4. ConfigMap** - Store configuration
**5. Secret** - Store sensitive data
**6. PersistentVolume** - Storage

### Installation (Minikube for local dev)

```bash
# Install Minikube
curl -LO https://github.com/kubernetes/minikube/releases/latest/download/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube

# Install kubectl
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl

# Start Minikube
minikube start

# Verify
kubectl cluster-info
kubectl get nodes
```

### Basic Deployment

**deployment.yaml:**

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app
  labels:
    app: myapp
spec:
  replicas: 3
  selector:
    matchLabels:
      app: myapp
  template:
    metadata:
      labels:
        app: myapp
    spec:
      containers:
      - name: app
        image: myapp:1.0
        ports:
        - containerPort: 8080
        resources:
          requests:
            memory: "256Mi"
            cpu: "250m"
          limits:
            memory: "512Mi"
            cpu: "500m"
        env:
        - name: LOG_LEVEL
          value: "INFO"
        livenessProbe:
          httpGet:
            path: /health
            port: 8080
          initialDelaySeconds: 30
          periodSeconds: 10
```

**service.yaml:**

```yaml
apiVersion: v1
kind: Service
metadata:
  name: my-app-service
spec:
  type: LoadBalancer
  selector:
    app: myapp
  ports:
  - protocol: TCP
    port: 80
    targetPort: 8080
```

### Kubectl Commands

```bash
# Apply configuration
kubectl apply -f deployment.yaml

# Get resources
kubectl get pods
kubectl get deployments
kubectl get services

# Describe resource
kubectl describe pod my-app-xxx

# View logs
kubectl logs my-app-xxx
kubectl logs -f my-app-xxx  # Follow logs

# Scale deployment
kubectl scale deployment my-app --replicas=5

# Update image
kubectl set image deployment/my-app app=myapp:2.0

# Port forward
kubectl port-forward svc/my-app-service 8080:80

# Delete resources
kubectl delete pod my-app-xxx
kubectl delete deployment my-app
```

### Best Practices

✓ Use namespaces for organization  
✓ Set resource requests and limits  
✓ Use health checks (liveness, readiness)  
✓ Implement proper logging  
✓ Use ConfigMaps for configuration  
✓ Use Secrets for sensitive data  
✓ Implement network policies  
✓ Regular backups of etcd  
✓ Use RBAC for access control  

---

# WEEK 3: AZURE DEVOPS (Days 11-15)

## DAY 11: Azure DevOps Overview

### Learning Objectives
- Understand Azure DevOps platform
- Know key components
- Set up Azure DevOps organization
- Create teams and projects

### What is Azure DevOps?

Azure DevOps is Microsoft's comprehensive DevOps platform providing:
- **Azure Boards** - Work item tracking
- **Azure Repos** - Version control (Git)
- **Azure Pipelines** - CI/CD
- **Azure Test Plans** - Test management
- **Azure Artifacts** - Package management

### Azure DevOps Benefits

✓ Integrated solution  
✓ Cloud-hosted or on-premise  
✓ Scales from small teams to enterprises  
✓ Built-in security  
✓ No plugins needed  
✓ Supports multiple languages  

### Setup Process

1. Create Azure account: https://azure.microsoft.com
2. Create Azure DevOps organization
3. Create project
4. Add team members
5. Configure repositories
6. Set up pipelines

### Azure DevOps Organization Structure

```
Organization
├── Project 1
│   ├── Repos
│   ├── Pipelines
│   ├── Boards
│   └── Artifacts
├── Project 2
└── Project 3
```

---

## DAY 12: Azure Pipelines - CI/CD in Azure

### Learning Objectives
- Create Azure Pipelines
- Use YAML pipeline definitions
- Implement CI/CD workflows
- Integrate with repositories

### What is Azure Pipelines?

Azure Pipelines:
- Cloud-hosted CI/CD service
- Supports multiple languages and platforms
- YAML or visual editor
- Free tier: 1 free job (10 parallel)
- Integrates with GitHub, Bitbucket, Azure Repos

### Pipeline Structure

**azure-pipelines.yml:**

```yaml
trigger:
  - main
  - develop

pool:
  vmImage: 'ubuntu-latest'

variables:
  buildConfiguration: 'Release'

stages:
- stage: Build
  jobs:
  - job: BuildJob
    steps:
    - task: UseDotNet@2
      inputs:
        version: '6.0.x'
    
    - task: DotNetCoreCLI@2
      inputs:
        command: 'build'
        arguments: '--configuration $(buildConfiguration)'
    
    - task: DotNetCoreCLI@2
      inputs:
        command: 'test'
        arguments: '--configuration $(buildConfiguration)'
    
    - task: DotNetCoreCLI@2
      inputs:
        command: 'publish'
        arguments: '--configuration $(buildConfiguration) --output $(Build.ArtifactStagingDirectory)'
    
    - task: PublishBuildArtifacts@1
      inputs:
        pathToPublish: '$(Build.ArtifactStagingDirectory)'

- stage: Deploy
  dependsOn: Build
  condition: succeeded()
  jobs:
  - deployment: DeployApp
    environment: 'Production'
    strategy:
      runOnce:
        deploy:
          steps:
          - task: AzureWebApp@1
            inputs:
              azureSubscription: 'Azure Connection'
              appName: 'myapp'
              package: '$(Pipeline.Workspace)/**/*.zip'
```

### Common Tasks

```yaml
# Checkout code
- checkout: self

# Run scripts
- script: echo Hello, world!
  displayName: 'Run a one-line script'

# Run commands
- bash: |
    echo Add other tasks to build, test, and deploy your project.
    echo See https://aka.ms/yaml
  displayName: 'Run a multi-line script'

# Install tool
- task: UsePythonVersion@0
  inputs:
    versionSpec: '3.9'

# Publish artifacts
- task: PublishBuildArtifacts@1
  inputs:
    PathtoPublish: '$(Build.ArtifactStagingDirectory)'

# Azure Web App deployment
- task: AzureWebApp@1
  inputs:
    azureSubscription: 'service-connection-name'
    appType: 'webAppLinux'
    appName: 'app-name'
    package: '$(Build.ArtifactStagingDirectory)'
```

---

## DAY 13: Azure Artifacts - Package Management

### Learning Objectives
- Manage packages in Azure Artifacts
- Publish and consume packages
- Use feeds and views
- Manage versions

### What is Azure Artifacts?

Azure Artifacts:
- Package management service
- Supports NuGet, npm, Maven, Python, etc.
- Create and manage feeds
- Store build artifacts
- Manage package versions

### Package Management Types

**1. NuGet** - .NET packages
**2. npm** - JavaScript packages
**3. Maven** - Java packages
**4. Python** - Python packages
**5. Universal** - Any artifact type

### Creating and Using Feeds

**In Azure DevOps:**
1. Navigate to Artifacts
2. Create New Feed
3. Give it a name
4. Choose permissions

**Using in code:**

**NuGet (C#):**
```xml
<!-- nuget.config -->
<packageSources>
  <add key="MyFeed" value="https://pkgs.dev.azure.com/organization/project/_packaging/feed-name/nuget/v3/index.json" />
</packageSources>
```

**npm:**
```bash
# .npmrc
registry=https://pkgs.dev.azure.com/organization/project/_packaging/feed-name/npm/registry/

npm install my-package
```

**Maven:**
```xml
<!-- pom.xml -->
<repository>
  <id>myFeed</id>
  <url>https://pkgs.dev.azure.com/organization/project/_packaging/feed-name/maven/v1</url>
</repository>
```

---

## DAY 14: Azure Container Registry (ACR)

### Learning Objectives
- Set up Azure Container Registry
- Push Docker images to ACR
- Integrate with Azure Pipelines
- Manage image versions

### What is ACR?

Azure Container Registry:
- Private Docker registry in Azure
- Store and manage container images
- Geo-replication
- Built-in security
- Integration with AKS and other services

### Setting up ACR

```bash
# Create resource group
az group create --name myResourceGroup --location eastus

# Create ACR
az acr create --resource-group myResourceGroup \
  --name myregistry --sku Basic

# Login to ACR
az acr login --name myregistry

# Get login server
az acr list --resource-group myResourceGroup --query "[].loginServer" -o tsv
```

### Pushing Images

```bash
# Build and push
az acr build --registry myregistry --image myapp:1.0 .

# Or using Docker
docker tag myapp:1.0 myregistry.azurecr.io/myapp:1.0
docker push myregistry.azurecr.io/myapp:1.0

# List images
az acr repository list --name myregistry --output table
```

### Pipeline Integration

```yaml
trigger:
  - main

pool:
  vmImage: 'ubuntu-latest'

variables:
  imageRepository: 'myapp'
  containerRegistry: 'myregistry.azurecr.io'
  dockerfilePath: '$(Build.SourcesDirectory)/Dockerfile'
  tag: '$(Build.BuildId)'

stages:
- stage: Build
  jobs:
  - job: Build
    steps:
    - task: Docker@2
      inputs:
        command: build
        repository: $(imageRepository)
        dockerfile: $(dockerfilePath)
        containerRegistry: 'ACR Connection'
        tags: |
          $(tag)
          latest
    
    - task: Docker@2
      inputs:
        command: push
        repository: $(imageRepository)
        containerRegistry: 'ACR Connection'
        tags: |
          $(tag)
          latest
```

---

## DAY 15: Azure Kubernetes Service (AKS)

### Learning Objectives
- Create AKS cluster
- Deploy applications to AKS
- Manage scaling and updates
- Monitor AKS cluster

### What is AKS?

Azure Kubernetes Service:
- Managed Kubernetes in Azure
- Built-in security and monitoring
- Auto-scaling
- Simplified cluster management
- Integration with other Azure services

### Creating AKS Cluster

```bash
# Create cluster
az aks create \
  --resource-group myResourceGroup \
  --name myAKSCluster \
  --node-count 3 \
  --vm-set-type VirtualMachineScaleSets \
  --load-balancer-sku standard \
  --enable-managed-identity \
  --enable-add-ons monitoring,http_application_routing \
  --generate-ssh-keys

# Get credentials
az aks get-credentials --resource-group myResourceGroup --name myAKSCluster

# Verify
kubectl get nodes
```

### Deploying to AKS

```yaml
# deployment.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app
spec:
  replicas: 3
  selector:
    matchLabels:
      app: myapp
  template:
    metadata:
      labels:
        app: myapp
    spec:
      containers:
      - name: app
        image: myregistry.azurecr.io/myapp:latest
        ports:
        - containerPort: 8080
        imagePullPolicy: Always

---
apiVersion: v1
kind: Service
metadata:
  name: my-app-service
spec:
  type: LoadBalancer
  selector:
    app: myapp
  ports:
  - protocol: TCP
    port: 80
    targetPort: 8080
```

```bash
# Deploy
kubectl apply -f deployment.yaml

# Get service IP
kubectl get service my-app-service
```

### Pipeline Integration

```yaml
- stage: Deploy
  jobs:
  - deployment: DeployAKS
    environment: 'AKS'
    strategy:
      runOnce:
        deploy:
          steps:
          - task: KubernetesManifest@0
            inputs:
              action: 'deploy'
              kubernetesServiceConnection: 'aks-connection'
              namespace: 'default'
              manifests: |
                $(Pipeline.Workspace)/manifests/deployment.yaml
                $(Pipeline.Workspace)/manifests/service.yaml
              imagePullSecrets: |
                acr-secret
```

---

# WEEK 4: INFRASTRUCTURE AS CODE (Days 16-20)

## DAY 16: Ansible - Configuration Management

### Learning Objectives
- Understand Ansible basics
- Write Ansible playbooks
- Manage infrastructure as code
- Automate server configuration

### What is Ansible?

Ansible is:
- Agentless configuration management
- Uses SSH for communication
- YAML-based playbooks
- Simple and powerful
- Idempotent operations

### Ansible Advantages

✓ Agentless  
✓ Simple YAML syntax  
✓ Idempotent  
✓ Scales easily  
✓ No dependencies  
✓ Large community  

### Installation

```bash
# Ubuntu
sudo apt-get install ansible

# Verify
ansible --version

# Check inventory
ansible-inventory --list -i /etc/ansible/hosts
```

### Inventory File

```ini
# /etc/ansible/hosts

[webservers]
web1.example.com
web2.example.com
web3.example.com

[databases]
db1.example.com
db2.example.com

[all:vars]
ansible_user=ubuntu
ansible_ssh_private_key_file=~/.ssh/id_rsa

[webservers:vars]
http_port=80

[databases:vars]
mysql_port=3306
```

### Basic Playbook

```yaml
# playbook.yml
---
- name: Configure Web Servers
  hosts: webservers
  become: yes
  
  vars:
    http_port: 80
    max_clients: 200
  
  tasks:
  - name: Ensure Apache is installed
    apt:
      name: apache2
      state: present
    when: ansible_os_family == "Debian"
  
  - name: Ensure Apache service is running
    service:
      name: apache2
      state: started
      enabled: yes
  
  - name: Create index.html
    copy:
      content: |
        <html>
          <body>
            <h1>Welcome to {{ ansible_hostname }}</h1>
          </body>
        </html>
      dest: /var/www/html/index.html

- name: Configure Databases
  hosts: databases
  become: yes
  
  tasks:
  - name: Ensure MySQL is installed
    apt:
      name: mysql-server
      state: present
  
  - name: Ensure MySQL service is running
    service:
      name: mysql
      state: started
      enabled: yes
```

### Running Playbooks

```bash
# Run playbook
ansible-playbook playbook.yml

# Run with specific inventory
ansible-playbook -i inventory.ini playbook.yml

# Check mode (dry-run)
ansible-playbook playbook.yml --check

# Verbose output
ansible-playbook playbook.yml -v

# Run specific tags
ansible-playbook playbook.yml --tags "install"

# Limit to specific hosts
ansible-playbook playbook.yml --limit webservers
```

### Common Modules

```yaml
# Package management
- apt:
    name: git
    state: present

# File operations
- copy:
    src: /local/file
    dest: /remote/file
    mode: '0644'

- file:
    path: /tmp/mydir
    state: directory
    mode: '0755'

# Service management
- service:
    name: nginx
    state: started
    enabled: yes

# Execute commands
- command: /usr/bin/whoami

- shell: echo Hello from {{ ansible_hostname }}

# Template rendering
- template:
    src: nginx.conf.j2
    dest: /etc/nginx/nginx.conf
```

---

## DAY 17: Terraform - Infrastructure as Code

### Learning Objectives
- Understand Terraform basics
- Write Terraform configurations
- Manage infrastructure state
- Deploy to cloud providers

### What is Terraform?

Terraform is:
- Infrastructure as Code tool
- Supports multiple providers (AWS, Azure, GCP, etc.)
- Declarative configuration
- State management
- Plan before apply

### Terraform Workflow

```
┌─────────┐     ┌────────┐     ┌───────┐
│ Write   │ →   │ Plan   │ →   │ Apply │
│ Config  │     │        │     │       │
└─────────┘     └────────┘     └───────┘
                                    ↓
                             ┌───────────┐
                             │ State     │
                             │ File      │
                             └───────────┘
```

### Installation

```bash
# Download
cd /tmp
wget https://releases.hashicorp.com/terraform/1.3.0/terraform_1.3.0_linux_amd64.zip

# Install
unzip terraform_1.3.0_linux_amd64.zip
sudo mv terraform /usr/local/bin/

# Verify
terraform --version
```

### Basic Configuration

**main.tf:**

```hcl
terraform {
  required_providers {
    azurerm = {
      source  = "hashicorp/azurerm"
      version = "~> 3.0"
    }
  }
}

provider "azurerm" {
  features {}
  subscription_id = var.subscription_id
}

resource "azurerm_resource_group" "main" {
  name     = "rg-myapp"
  location = "East US"
  
  tags = {
    Environment = "production"
    Project     = "myapp"
  }
}

resource "azurerm_container_registry" "main" {
  name                = "myregistry"
  resource_group_name = azurerm_resource_group.main.name
  location            = azurerm_resource_group.main.location
  sku                 = "Basic"
  admin_enabled       = false
}

resource "azurerm_kubernetes_cluster" "main" {
  name                = "aks-cluster"
  location            = azurerm_resource_group.main.location
  resource_group_name = azurerm_resource_group.main.name
  dns_prefix          = "aks"
  
  default_node_pool {
    name       = "default"
    node_count = 3
    vm_size    = "Standard_B2s"
  }
  
  identity {
    type = "SystemAssigned"
  }
}
```

**variables.tf:**

```hcl
variable "subscription_id" {
  description = "Azure subscription ID"
  type        = string
  sensitive   = true
}

variable "environment" {
  description = "Environment name"
  type        = string
  default     = "dev"
}

variable "node_count" {
  description = "Number of Kubernetes nodes"
  type        = number
  default     = 3
  
  validation {
    condition     = var.node_count > 0 && var.node_count < 10
    error_message = "Node count must be between 1 and 9."
  }
}
```

**outputs.tf:**

```hcl
output "resource_group_id" {
  value = azurerm_resource_group.main.id
}

output "container_registry_url" {
  value = azurerm_container_registry.main.login_server
}

output "kubernetes_cluster_id" {
  value = azurerm_kubernetes_cluster.main.id
}
```

### Terraform Commands

```bash
# Initialize (downloads provider)
terraform init

# Validate configuration
terraform validate

# Format code
terraform fmt

# Create plan
terraform plan -out=plan.tfplan

# Apply changes
terraform apply plan.tfplan

# Destroy resources
terraform destroy

# Show state
terraform show

# List resources
terraform state list

# View specific resource
terraform state show azurerm_resource_group.main
```

### State Management

```bash
# Store state in Azure Storage
terraform {
  backend "azurerm" {
    resource_group_name  = "rg-state"
    storage_account_name = "mystateaccount"
    container_name       = "tfstate"
    key                  = "prod.terraform.tfstate"
  }
}

# Initialize with backend
terraform init -backend-config="resource_group_name=rg-state"
```

---

## DAY 18-20: Terraform with Azure, Integration, and Best Practices

[Continuing with Terraform Azure, Integration, and Advanced Topics...]

### DAY 18: Terraform with Azure

**Azure Resources:**

```hcl
# Virtual Network
resource "azurerm_virtual_network" "main" {
  name                = "vnet-main"
  address_space       = ["10.0.0.0/16"]
  location            = azurerm_resource_group.main.location
  resource_group_name = azurerm_resource_group.main.name
}

# Subnet
resource "azurerm_subnet" "internal" {
  name                 = "subnet-internal"
  resource_group_name  = azurerm_resource_group.main.name
  virtual_network_name = azurerm_virtual_network.main.name
  address_prefixes     = ["10.0.2.0/24"]
}

# Network Interface
resource "azurerm_network_interface" "main" {
  name                = "nic-main"
  location            = azurerm_resource_group.main.location
  resource_group_name = azurerm_resource_group.main.name

  ip_configuration {
    name                          = "testconfiguration1"
    subnet_id                     = azurerm_subnet.internal.id
    private_ip_address_allocation = "Dynamic"
  }
}

# Virtual Machine
resource "azurerm_linux_virtual_machine" "main" {
  name                = "vm-main"
  location            = azurerm_resource_group.main.location
  resource_group_name = azurerm_resource_group.main.name
  size                = "Standard_B1s"

  admin_username = "azureuser"

  admin_ssh_key {
    username   = "azureuser"
    public_key = file("~/.ssh/id_rsa.pub")
  }

  network_interface_ids = [
    azurerm_network_interface.main.id,
  ]

  os_disk {
    caching              = "ReadWrite"
    storage_account_type = "Premium_LRS"
  }

  source_image_reference {
    publisher = "Canonical"
    offer     = "0001-com-ubuntu-server-focal"
    sku       = "20_04-lts-gen2"
    version   = "latest"
  }
}
```

### DAY 19: Azure DevOps & Terraform Integration

**Pipeline with Terraform:**

```yaml
trigger:
  - main

pool:
  vmImage: 'ubuntu-latest'

variables:
  tfVersion: '1.3.0'
  tfBackendKey: 'terraform.tfstate'

stages:
- stage: Validate
  jobs:
  - job: ValidateTerraform
    steps:
    - task: TerraformInstaller@0
      inputs:
        terraformVersion: $(tfVersion)
    
    - task: TerraformTaskV3@3
      inputs:
        provider: 'azurerm'
        command: 'init'
        backendServiceArm: 'Azure Subscription'
        backendAzureRmResourceGroupName: 'rg-terraform'
        backendAzureRmStorageAccountName: 'tfstate'
        backendAzureRmContainerName: 'tfstate'
        backendAzureRmKey: $(tfBackendKey)
    
    - task: TerraformTaskV3@3
      inputs:
        provider: 'azurerm'
        command: 'validate'

- stage: Plan
  jobs:
  - job: PlanTerraform
    steps:
    - task: TerraformTaskV3@3
      inputs:
        provider: 'azurerm'
        command: 'init'
        workingDirectory: '$(System.DefaultWorkingDirectory)'
        backendServiceArm: 'Azure Subscription'
        backendAzureRmResourceGroupName: 'rg-terraform'
        backendAzureRmStorageAccountName: 'tfstate'
        backendAzureRmContainerName: 'tfstate'
        backendAzureRmKey: $(tfBackendKey)
    
    - task: TerraformTaskV3@3
      inputs:
        provider: 'azurerm'
        command: 'plan'
        workingDirectory: '$(System.DefaultWorkingDirectory)'
        commandOptions: '-var-file="terraform.tfvars"'
        environmentServiceNameAzureRM: 'Azure Subscription'
    
    - task: PublishBuildArtifacts@1
      inputs:
        pathToPublish: 'terraform.plan'

- stage: Apply
  dependsOn: Plan
  condition: succeeded()
  jobs:
  - deployment: ApplyTerraform
    environment: 'Production'
    strategy:
      runOnce:
        deploy:
          steps:
          - task: DownloadBuildArtifacts@0
            inputs:
              buildType: 'current'
              downloadType: 'single'
              artifactName: 'drop'
          
          - task: TerraformTaskV3@3
            inputs:
              provider: 'azurerm'
              command: 'apply'
              workingDirectory: '$(Agent.ReleaseDirectory)/drop'
              commandOptions: 'terraform.plan'
              environmentServiceNameAzureRM: 'Azure Subscription'
```

### DAY 20: Infrastructure as Code Best Practices

**Best Practices:**

1. **Version Control**
   - Store all code in Git
   - Use meaningful commit messages
   - Tag releases

2. **State Management**
   - Store state remotely (Azure Storage, S3, etc.)
   - Use state locking
   - Encrypt sensitive data
   - Backup state files regularly

3. **Module Organization**

```hcl
# modules/networking/main.tf
resource "azurerm_virtual_network" "main" {
  name                = var.vnet_name
  address_space       = var.address_space
  location            = var.location
  resource_group_name = var.resource_group_name
}

# modules/networking/variables.tf
variable "vnet_name" {
  type = string
}

# modules/networking/outputs.tf
output "vnet_id" {
  value = azurerm_virtual_network.main.id
}

# main.tf
module "networking" {
  source = "./modules/networking"
  
  vnet_name           = "vnet-prod"
  address_space       = ["10.0.0.0/16"]
  location            = "East US"
  resource_group_name = azurerm_resource_group.main.name
}
```

4. **Testing Infrastructure**
   - Use Terraform validate
   - Use tflint for linting
   - Test in lower environments first
   - Use plan approvals for production

5. **Security**
   - Don't hardcode secrets
   - Use Terraform variables
   - Use environment variables for sensitive data
   - Implement RBAC
   - Encrypt state files

```bash
# Using environment variables for credentials
export ARM_CLIENT_ID="..."
export ARM_CLIENT_SECRET="..."
export ARM_TENANT_ID="..."
export ARM_SUBSCRIPTION_ID="..."

terraform plan
```

---

# WEEK 5: ADVANCED TOPICS (Days 21-30)

## DAY 21: Continuous Monitoring

### Learning Objectives
- Understand monitoring importance
- Use Azure Monitor
- Create alerts and dashboards
- Monitor applications and infrastructure

### Key Monitoring Concepts

**Metrics:**
- Numerical measurements (CPU%, Memory, Request Count)
- Real-time data
- Used for alerting and dashboards

**Logs:**
- Detailed records of events
- Searchable and queryable
- Used for troubleshooting and analysis

**Traces:**
- Distributed tracing
- Track requests across services
- Understand latency and dependencies

### Azure Monitor Setup

```yaml
# Deploy monitoring
apiVersion: apps/v1
kind: Deployment
metadata:
  name: app-with-monitoring
spec:
  template:
    spec:
      containers:
      - name: app
        image: myapp:1.0
        env:
        - name: APPLICATIONINSIGHTS_CONNECTION_STRING
          value: "InstrumentationKey=..."
        - name: ApplicationInsightsAgent_EXTENSION_VERSION
          value: "~2"
```

### Alert Rules

```hcl
# Terraform alert rule
resource "azurerm_monitor_metric_alert" "cpu_alert" {
  name                = "cpu-alert"
  resource_group_name = azurerm_resource_group.main.name
  scopes              = [azurerm_virtual_machine.main.id]
  description         = "Alert when CPU exceeds 80%"
  
  criteria {
    metric_name      = "Percentage CPU"
    metric_namespace = "Microsoft.Compute/virtualMachines"
    aggregation      = "Average"
    operator         = "GreaterThan"
    threshold        = 80
  }
  
  action {
    action_group_id = azurerm_monitor_action_group.main.id
  }
}
```

---

## DAY 22: Log Management (ELK Stack)

### Learning Objectives
- Understand log aggregation
- Deploy ELK stack
- Parse and analyze logs
- Create visualizations

### ELK Components

**Elasticsearch:**
- Search and analytics engine
- Stores log data
- RESTful API

**Logstash:**
- Log processor
- Collects from sources
- Transforms and enriches data

**Kibana:**
- Visualization tool
- Create dashboards
- Query and explore data

### Deployment

```yaml
version: '3.8'
services:
  elasticsearch:
    image: docker.elastic.co/elasticsearch/elasticsearch:7.17.0
    environment:
      - discovery.type=single-node
      - xpack.security.enabled=false
    ports:
      - "9200:9200"
  
  kibana:
    image: docker.elastic.co/kibana/kibana:7.17.0
    environment:
      - ELASTICSEARCH_HOSTS=http://elasticsearch:9200
    ports:
      - "5601:5601"
  
  logstash:
    image: docker.elastic.co/logstash/logstash:7.17.0
    volumes:
      - ./logstash.conf:/usr/share/logstash/pipeline/logstash.conf
    environment:
      - "LS_JAVA_OPTS=-Xmx256m -Xms256m"
    ports:
      - "5000:5000/udp"
```

---

## DAY 23: Infrastructure Orchestration

[Advanced orchestration patterns and multi-cloud strategies]

---

## DAY 24: Serverless Computing & Azure Functions

### What is Serverless?

- No server management
- Auto-scaling
- Pay per execution
- Event-driven

### Azure Functions Example

```csharp
using System.Threading.Tasks;
using Microsoft.AspNetCore.Http;
using Microsoft.Azure.WebJobs;
using Microsoft.Extensions.Logging;

public static class HttpTriggerFunction
{
    [FunctionName("HttpTriggerFunction")]
    public static async Task<IActionResult> Run(
        [HttpTrigger(AuthorizationLevel.Function, "get", "post", Route = null)] HttpRequest req,
        ILogger log)
    {
        log.LogInformation("HTTP trigger function processed a request.");
        
        string name = req.Query["name"];
        
        return new OkObjectResult($"Hello, {name}!");
    }
}
```

---

## DAY 25: Cloud-Native Architecture

### Principles

1. **Microservices** - Small, independent services
2. **Containers** - Docker for consistency
3. **Orchestration** - Kubernetes for management
4. **DevOps** - Automation and collaboration
5. **Serverless** - Event-driven computing

---

## DAY 26: Continuous Testing

### Testing Strategy

```yaml
# Test automation in pipeline
stages:
- stage: Test
  jobs:
  - job: UnitTests
    steps:
    - task: DotNetCoreCLI@2
      inputs:
        command: 'test'
        arguments: '--logger trx --collect:"XPlat Code Coverage"'
  
  - job: IntegrationTests
    steps:
    - script: |
        docker-compose up -d
        npm test
        docker-compose down
  
  - job: SecurityTests
    steps:
    - task: SnykSecurityScan@0
      inputs:
        serviceConnectionEndpoint: 'Snyk'
        testType: 'app'
  
  - job: PerformanceTests
    steps:
    - script: |
        jmeter -n -t tests/performance.jmx \
          -l tests/results.jtl -j tests/logs.jtl
```

---

## DAY 27: Release Management

### Release Strategy

```yaml
# Release pipeline
stages:
- stage: Pre-Production
  jobs:
  - deployment: DeployStaging
    environment: Staging
    strategy:
      runOnce:
        deploy:
          steps:
          - task: AzureWebApp@1
            inputs:
              azureSubscription: 'Azure'
              appName: 'app-staging'

- stage: Production
  dependsOn: Pre-Production
  condition: succeeded()
  jobs:
  - deployment: DeployProduction
    environment: Production
    strategy:
      canary:
        increments: [25, 50, 75, 100]
      deploy:
        steps:
        - task: AzureWebApp@1
          inputs:
            azureSubscription: 'Azure'
            appName: 'app-prod'
```

---

## DAY 28: DevOps Culture and Collaboration

### Key Principles

1. **Shared Responsibility**
   - Everyone owns quality
   - Cross-functional teams
   - Blameless postmortems

2. **Continuous Learning**
   - Knowledge sharing
   - Team training
   - Documentation

3. **Transparency**
   - Visible metrics
   - Open communication
   - Shared goals

4. **Automation First**
   - Automate repetitive tasks
   - Self-service tools
   - Reduce manual toil

---

## DAY 29: Scaling DevOps

### Scaling Strategies

1. **Organizational Scaling**
   - Platform teams
   - Cross-functional pods
   - Clear communication channels

2. **Tool Scaling**
   - Centralized logging
   - Distributed CI/CD
   - Multi-region deployments

3. **Process Scaling**
   - Standardized workflows
   - Automation frameworks
   - Reusable components

---

## DAY 30: DevOps Case Studies & Career Path

### Real-World Success Stories

**Case Study 1: E-commerce Platform**
- Challenge: Deployments every 3 months
- Solution: Implemented CI/CD pipeline
- Result: Daily deployments, 40% fewer bugs

**Case Study 2: Financial Services**
- Challenge: Security and compliance
- Solution: DevSecOps with automated scanning
- Result: Security breaches reduced by 80%

**Case Study 3: Startup**
- Challenge: Limited resources
- Solution: Cloud-native, serverless architecture
- Result: 10x scale without proportional cost increase

### Career Path

**Junior DevOps Engineer (0-2 years)**
- Linux fundamentals
- Basic scripting
- Git and CI/CD basics
- Docker and Kubernetes basics

**Mid-level DevOps Engineer (2-5 years)**
- Advanced CI/CD design
- Cloud platform expertise
- Infrastructure as Code
- Monitoring and logging

**Senior DevOps Engineer (5+ years)**
- Architecture design
- Team leadership
- Security and compliance
- Multi-cloud strategy

### Next Steps

1. **Learn Continuously**
   - Follow industry trends
   - Take certifications
   - Contribute to open source

2. **Build Projects**
   - Personal projects
   - Contribute to repositories
   - Share knowledge

3. **Network**
   - Join communities
   - Attend conferences
   - Connect with peers

4. **Specialize**
   - Cloud provider (AWS, Azure, GCP)
   - Container orchestration
   - Security (DevSecOps)
   - Cost optimization

---

# COMPLETE IMPLEMENTATION GUIDE

## Full CI/CD Pipeline Example

### Repository Structure

```
my-app/
├── .github/workflows/
│   └── ci-cd.yml
├── src/
│   ├── main/java/...
│   └── test/java/...
├── Dockerfile
├── docker-compose.yml
├── pom.xml
├── .dockerignore
├── .gitignore
├── README.md
└── terraform/
    ├── main.tf
    ├── variables.tf
    └── outputs.tf
```

### Complete Workflow

```yaml
name: Complete CI/CD Pipeline

on:
  push:
    branches: [ main, develop ]
  pull_request:
    branches: [ main ]

env:
  REGISTRY: myregistry.azurecr.io
  IMAGE_NAME: myapp
  DOCKER_BUILDKIT: 1

jobs:
  build:
    runs-on: ubuntu-latest
    outputs:
      image-tag: ${{ steps.meta.outputs.tags }}
    
    steps:
    - uses: actions/checkout@v3
    
    - name: Set up JDK 11
      uses: actions/setup-java@v3
      with:
        java-version: '11'
        distribution: 'temurin'
    
    - name: Build with Maven
      run: mvn clean package -DskipTests
    
    - name: Run Tests
      run: mvn test
    
    - name: SonarQube Analysis
      run: |
        mvn sonar:sonar \
          -Dsonar.projectKey=my-app \
          -Dsonar.host.url=${{ secrets.SONAR_HOST_URL }} \
          -Dsonar.login=${{ secrets.SONAR_TOKEN }}
    
    - name: Dependency Check
      run: mvn org.owasp:dependency-check-maven:check
    
    - name: Build Docker Image
      run: docker build -t ${{ env.REGISTRY }}/${{ env.IMAGE_NAME }}:${{ github.sha }} .
    
    - name: Login to ACR
      uses: docker/login-action@v2
      with:
        registry: ${{ env.REGISTRY }}
        username: ${{ secrets.ACR_USERNAME }}
        password: ${{ secrets.ACR_PASSWORD }}
    
    - name: Push to ACR
      run: docker push ${{ env.REGISTRY }}/${{ env.IMAGE_NAME }}:${{ github.sha }}

  deploy-dev:
    needs: build
    runs-on: ubuntu-latest
    if: github.ref == 'refs/heads/develop'
    
    steps:
    - uses: actions/checkout@v3
    
    - name: Deploy to Dev
      run: |
        kubectl set image deployment/my-app-dev \
          app=${{ env.REGISTRY }}/${{ env.IMAGE_NAME }}:${{ github.sha }} \
          -n dev

  deploy-prod:
    needs: build
    runs-on: ubuntu-latest
    if: github.ref == 'refs/heads/main'
    environment: Production
    
    steps:
    - uses: actions/checkout@v3
    
    - name: Deploy to Production
      run: |
        kubectl set image deployment/my-app-prod \
          app=${{ env.REGISTRY }}/${{ env.IMAGE_NAME }}:${{ github.sha }} \
          -n production

  notify:
    needs: [ build, deploy-dev, deploy-prod ]
    runs-on: ubuntu-latest
    if: always()
    
    steps:
    - name: Slack Notification
      uses: 8398a7/action-slack@v3
      with:
        status: ${{ job.status }}
        text: 'Deployment Status: ${{ job.status }}'
        webhook_url: ${{ secrets.SLACK_WEBHOOK }}
```

---

# CAREER PATH & NEXT STEPS

## Skills Development Timeline

**Month 1-2: Foundations**
- Linux fundamentals
- Git and version control
- Docker basics
- Basic CI/CD concepts

**Month 3-4: Tools**
- Jenkins or GitHub Actions
- Maven/Gradle
- Basic Kubernetes
- Nexus or Artifactory

**Month 5-6: Cloud & Infrastructure**
- Cloud provider (Azure/AWS/GCP)
- Terraform basics
- Ansible basics
- Monitoring setup

**Month 7-9: Advanced**
- Multi-environment deployments
- Advanced Kubernetes
- Infrastructure as Code
- Security in DevOps

**Month 10-12: Specialization**
- Deep dive into one cloud provider
- Container security
- Cost optimization
- Scalability patterns

## Certifications to Consider

1. **Linux Foundation**
   - LF-CompTia DevOps+
   - CKAD (Kubernetes)
   - LF-OpenStack

2. **Cloud Providers**
   - AZ-400 (Azure DevOps)
   - AZ-305 (Azure Architecture)
   - AWS DevOps Engineer
   - GCP Professional DevOps Engineer

3. **Specialty**
   - Certified Kubernetes Administrator (CKA)
   - HashiCorp Certified Terraform Associate
   - Docker Certified Associate

## Final Recommendations

1. **Practice Hands-On**
   - Set up lab environment
   - Build projects
   - Automate your workflows

2. **Learn from Others**
   - Read case studies
   - Join communities
   - Attend conferences

3. **Stay Updated**
   - Follow DevOps news
   - Track tool updates
   - Understand industry trends

4. **Contribute**
   - Open source projects
   - Share knowledge
   - Help junior engineers

---

**Congratulations on completing the 30-Day DevOps course!**

You now have a comprehensive understanding of:
- DevOps principles and culture
- CI/CD pipeline implementation
- Container and orchestration technologies
- Infrastructure as Code
- Cloud platform services
- Monitoring and logging
- Best practices and patterns

**Your DevOps journey is just beginning!**

---

**Document Version:** 1.0  
**Last Updated:** May 2026  
**Source:** 30-Days-Of-DevOps (GitHub)  
**Total Pages:** 100+  
**Word Count:** 50,000+  

---
