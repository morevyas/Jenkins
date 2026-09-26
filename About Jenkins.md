---


---

<h1 id="jenkins">Jenkins</h1>
<h1 id="using-jenkins">Using Jenkins</h1>
<h2 id="jenkins-architecture">Jenkins Architecture</h2>
<p>Jenkins follows a <strong>controller-agent architecture</strong>. The Jenkins Controller manages the CI/CD process, while Agents execute the actual build, test, and deployment tasks.</p>
<h3 id="basic-architecture">1) Basic Architecture</h3>
<pre><code>                Developer
                    │
                    │ git push
                    ▼
             ┌─────────────┐
             │   GitHub /  │
             │    GitLab   │
             └──────┬──────┘
                    │ Webhook / Polling
                    ▼
          ┌─────────────────────┐
          │   Jenkins Controller │
          │                     │
          │ • Manage pipelines  │
          │ • Schedule jobs     │
          │ • Manage plugins    │
          │ • Credentials       │
          │ • Build management  │
          └──────────┬──────────┘
                     │
          Assigns tasks to Agents
                     │
      ┌──────────────┼──────────────┐
      ▼              ▼              ▼
   ┌────────────┐ ┌────────────┐ ┌────────────┐
   │ Jenkins    │ │ Jenkins    │ │ Jenkins    │
   │ Agent 1    │ │ Agent 2    │ │ Agent 3    │
   │            │ │            │ │            │
   │ Java/Maven │ │ Docker     │ │ Node.js    │
   │ Build/Test │ │ Build/Push │ │ Build/Test │
   └────────────┘ └─────┬──────┘ └────────────┘
                    │
                    ▼
              ┌───────────┐
              │ Deployment│
              │ Server    │
              └───────────┘
</code></pre>
<h3 id="a-basic-workflow">A basic workflow</h3>
<pre><code>Developer
   ↓
GitHub
   ↓
Jenkins Pipeline
   ↓
Checkout Code
   ↓
Install Dependencies
   ↓
Run Tests
   ↓
Build Docker Image
   ↓
Stop/Update Application
   ↓
Run Docker Container
   ↓
Application Live
</code></pre>
<h3 id="jenkins-controller">2) Jenkins Controller</h3>
<ul>
<li>Managing Jenkins jobs and pipelines</li>
<li>Scheduling builds</li>
<li>Managing users and permissions</li>
<li>Managing credentials</li>
<li>Managing plugins</li>
<li>Reading Jenkinfiles</li>
<li>Maintaining build history</li>
<li>Assigning work to agents</li>
<li>Providing the Jenkins web interface</li>
</ul>
<h3 id="jenkins-agent">3) Jenkins Agent</h3>
<p><strong>A <strong>Jenkins Agent</strong> is a machine that performs the actual work.</strong></p>
<p>ex.:</p>
<pre><code>	Agent
	 ├── Git
	 ├── Java 21
	 ├── Maven
	 ├── Docker
	 └── Linux
</code></pre>
<h3 id="cicd-flow">4) CI/CD Flow</h3>
<pre><code>Developer
│
│ git push
▼
GitHub Repository
│
│ Webhook
▼
Jenkins Controller
│
│ Trigger Pipeline
▼
Jenkins Agent
│
├── Checkout Code
│
├── Maven Build
│
├── Run Tests
│
├── Build Docker Image
│
├── Push Image
│
└── Deploy Application
         │
         ▼
   Docker Container
         │
         ▼
  Spring Boot App
</code></pre>
<h2 id="why-is-jenkins-used.">Why is jenkins used.</h2>
<p>Jenkins is used to <strong>automate the software development and delivery process</strong>. It helps DevOps teams automatically take source code from a repository, build it, test it, package it, create Docker images, and deploy the application.</p>
<p>Jenkins reduces manual work by automatically executing the steps required to build, test, and deliver an application.</p>
<p><strong>Jenkins is used to automate, standardize, and monitor the process of converting source code into a tested and deployable application.</strong></p>
<h2 id="basic-pipeline-structure---">Basic Pipeline Structure : -</h2>
<pre><code>	pipeline {
agent any

stages {

    stage('Hello') {
        steps {
            echo 'Hello from Jenkins!'
        }
    }

    stage('Build') {
        steps {
            sh '''
                echo "Building the application..."
                echo "Build completed successfully!"
            '''
        }
    }

    stage('Test') {
        steps {
            sh '''
                echo "Running tests..."
                echo "Tests passed!"
            '''
        }
    }

    stage('Deploy') {
        steps {
            echo 'Deploying application...'
        }
    }
}

post {
    success {
        echo 'Jenkins Pipeline completed successfully!'
    }

    failure {
        echo 'Jenkins Pipeline failed!'
    }
}
}
</code></pre>
<h2 id="cicd-workflow-">CI/CD Workflow :</h2>
<pre><code>                       Developer
                       │
                       │ git push
                       ↓
                    GitHub
                       │
                       │ Webhook
                       ↓
                Jenkins Controller
                       │
                       ↓
                Jenkins Pipeline
                       │
    ┌──────────────────┴──────────────────┐
    │                                     │
    ↓                                     │
   1. Checkout                                │
    ↓                                     │
   2. Build                                   │
    ↓                                     │
   3. Unit Test                               │
    ↓                                     │
   4. Test Report                             │
    ↓                                     │
   5. Code Quality                            │
    ↓                                     │
   6. Docker Build                            │
    ↓                                     │
   7. Docker Push                             │
    ↓                                     │
   8. Deployment Approval                     │
    ↓                                     │
   9. Docker Swarm                            │
    ↓                                     │
   10. Verification                           │
    ↓                                     │
   Application Running                        │
    │                                     │
    └──────────────→ Monitoring ←─────────┘
                       │
                Prometheus + Grafana
</code></pre>

