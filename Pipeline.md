---


---

<h1 id="pipeline">Pipeline</h1>
<h2 id="jenkins-pipeline">Jenkins pipeline</h2>
<p>Jenkins Pipeline is a suite of plugins which supports <strong>implementing and integrating _continuous delivery pipelines</strong>_ into Jenkins.</p>
<p>A <em>continuous delivery (CD) pipeline</em> is an automated expression of your process for getting software from version control right through to your users and customers. Every change to your software (committed in source control) goes through a complex process on its way to being released. This process involves building the software in a reliable and repeatable manner, as well as progressing the built software (called a “build”) through multiple stages of testing and deployment.</p>
<p>The definition of a Jenkins Pipeline is written into a text file (called a <a href="https://www.jenkins.io/doc/book/pipeline/jenkinsfile"><code>Jenkinsfile</code></a>) which in turn can be committed to a project’s source control repository.<br>
This is the foundation of “Pipeline-as-code”; treating the CD pipeline as a part of the application to be versioned and reviewed like any other code.</p>
<h3 id="jenkinsfile">Jenkinsfile</h3>
<pre><code>pipeline {
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
<h2 id="why-pipeline">Why Pipeline</h2>
<p><strong>Pipeline:</strong> Jenkins manages the <strong>entire software delivery workflow as code</strong>.</p>
<p>Jenkins Pipeline is important because it <strong>automates the entire software delivery process</strong>—from getting code from GitHub to testing, building, and deploying the application.</p>
<pre><code>Developer → GitHub → Jenkins Pipeline → Build → Test → Docker → Deploy
</code></pre>
<ul>
<li><strong>Code:</strong> A Pipeline is written as code, usually in a <code>Jenkinsfile</code>, and stored in a source-code repository such as GitHub. This means the pipeline can be reviewed, modified, and version-controlled just like application code.</li>
<li><strong>Durable:</strong> A Pipeline can continue working even if the Jenkins controller is restarted, whether the restart is planned or caused by an unexpected issue.</li>
<li><strong>Pausable:</strong> A Pipeline can pause when human approval is required. For example, Jenkins can build and test an application automatically but wait for someone to approve it before deploying to production.</li>
<li><strong>Versatile:</strong> Pipelines can handle complex CI/CD workflows. Tasks can run sequentially, in parallel, or conditionally. You can also use loops, branches, and other logic when needed.</li>
<li><strong>Extensible:</strong> Jenkins Pipeline can be extended using plugins and custom Pipeline functionality. This allows Jenkins to integrate with tools such as GitHub, Docker, Maven, SonarQube, AWS, Kubernetes, and many others.</li>
</ul>

