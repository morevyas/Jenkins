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
<ul>
<li><strong>Developer writes code</strong> – The developer creates or modifies the application source code.</li>
<li><strong>Commit and Push</strong> – The developer commits the changes and pushes them to a Git repository such as GitHub, GitLab, or Bitbucket.</li>
<li><strong>Jenkins detects the change</strong> – Jenkins detects the new code using a <strong>webhook</strong> or <strong>polling</strong>.</li>
<li><strong>Pipeline starts</strong> – After detecting the change, Jenkins starts the pipeline according to the instructions written in the <strong>Jenkinsfile</strong>.</li>
<li><strong>Checkout Stage</strong> – Jenkins downloads the latest source code from the Git repository into the workspace of a Jenkins Agent.</li>
<li><strong>Build Stage</strong> – Jenkins builds or prepares the application. Depending on the technology, it may compile the code, install dependencies, create packages, or build a Docker image.</li>
<li><strong>Build validation</strong> – If the build fails, Jenkins stops the pipeline and reports the error. If the build succeeds, it moves to testing.</li>
<li><strong>Test Stage</strong> – Jenkins runs automated tests such as <strong>unit tests, integration tests, API tests, and security checks</strong> to verify that the application works correctly.</li>
<li><strong>Test result</strong> – If the tests fail, Jenkins stops the pipeline so that faulty code is not deployed. If all tests pass, Jenkins continues to deployment.</li>
<li><strong>Deploy Stage</strong> – Jenkins deploys the successfully built and tested application to an environment such as <strong>development, staging, or production</strong>.</li>
<li><strong>Application runs</strong> – After successful deployment, the application becomes available in the target environment for users or further testing.</li>
<li><strong>Notification</strong> – Jenkins can notify developers about the pipeline result, such as <strong>Build Successful</strong> or <strong>Build Failed</strong>.</li>
</ul>

