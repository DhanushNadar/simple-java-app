# ☕ Hello Java Maven - Jenkins Build Project

This project demonstrates how to build a simple Java application using **Maven** inside **Jenkins** — fulfilling **Task 8: Run a Simple Java Maven Build Job in Jenkins**.

---

## 🎯 Objective

> Learn how to use Jenkins to build a Java application using Maven — your first step into CI/CD.

---

## 📁 Project Structure




---

## 🛠 Tools Used

- Jenkins
- Maven (3.8.x)
- Java JDK 11
- Git 

---

## 🧱 Setup Guide

### 1. Create Java Application

**`HelloWorld.java`**

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, Jenkins + Maven!");
    }
}

```

#### 2. Create Maven Build File

**`pom.xml`**

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
         http://maven.apache.org/xsd/maven-4.0.0.xsd">

    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>hello</artifactId>
    <version>1.0</version>

    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.8.1</version>
                <configuration>
                    <source>11</source>
                    <target>11</target>
                </configuration>
            </plugin>
        </plugins>
    </build>

</project>

```

# 🛠 Jenkins Pipeline Setup

- Start Jenkins.

- Install Maven and JDK tools in Jenkins Global Tool Configuration.

- Create a New Pipeline Job.

- Connect to Git repository (optional) or upload code manually.

- Use this Jenkinsfile:

```grovvy
pipeline {
    agent any

    tools {
        maven 'Maven-3.8.6'    
        jdk 'JDK-11'           
    }

    stages {
        stage('Checkout Code') {
            steps {
                echo 'Checking out code...'
                checkout scm
                git branch: 'main', url: 'https://github.com/DhanushNadar/simple-java-app.git'
            }
        }

        stage('Build with Maven') {
            steps {
                echo 'Running Maven clean package...'
                sh 'mvn clean package'
            }
        }

        stage('Run Application') {
            steps {
                echo 'Running the HelloWorld program...'
                sh 'java -cp target/classes HelloWorld'
            }
        }
    }

    post {
        success {
            echo '🎉 Build and Run Successful!'
        }
        failure {
            echo '❌ Build Failed!'
        }
    }
}

```

# 📜 Maven Build Commands (Manual)

``` bash
# Compile and build the application
mvn clean package

# Run the application
java -cp target/classes HelloWorld
```

## ✅ Deliverables

 - Java HelloWorld application
 - Maven pom.xml created
 - Jenkins Freestyle/Pipeline Job created
 - Successful Console Output with BUILD SUCCESS


# 📸 Example Console Output

[pipeline screenshot](images/pipeline.png)
[Output screenshot](images/output.png)

> Made with ❤️ by Dhanush Nadar.
