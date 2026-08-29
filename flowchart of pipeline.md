---


---

<h1 id="flowchart">Flowchart</h1>
<p><strong>Jenkins Pipeline is a collection of automated steps written as code that defines how an application is built, tested, packaged, and deployed.</strong></p>
<p><img src="https://www.jenkins.io/doc/book/resources/pipeline/realworld-pipeline-flow.png" alt="Pipeline Flow"></p>
<h3 id="basic-structure-of-pipeline--">Basic structure of Pipeline :-</h3>
<pre><code>pipeline {
agent any

    stages {

    stage('Build') {
        steps {
            sh 'mvn clean package'
        }
    }

    stage('Test') {
        steps {
            sh 'mvn test'
        }
    }

    stage('Deploy') {
        steps {
            sh 'docker compose up -d'
        }
    }
}
}
</code></pre>
<h2 id="jenkins-pipeline-flow">jenkins pipeline flow</h2>
<pre><code>Developer
│
│  git push
▼
Git Repository
(GitHub / GitLab / Bitbucket)
│
│ Webhook / Poll SCM
▼
Jenkins Controller
│
│ Assigns job
▼
Jenkins Agent / Worker
│
├── 1. Checkout Code
│
├── 2. Build
│
├── 3. Test
│
├── 4. Code Quality / Scan
│
├── 5. Package
│
├── 6. Docker Build
│
├── 7. Push Image
│
└── 8. Deploy
        │
        ▼
   Server / AWS / Kubernetes
</code></pre>

