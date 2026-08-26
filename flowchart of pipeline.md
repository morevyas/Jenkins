---


---

<h1 id="flowchart">Flowchart</h1>
<p><strong>Jenkins Pipeline is a collection of automated steps written as code that defines how an application is built, tested, packaged, and deployed.</strong></p>
<p><img src="https://www.jenkins.io/doc/book/resources/pipeline/realworld-pipeline-flow.png" alt="Pipeline Flow"></p>
<h3 id="basic-structure-of-pipeline--">Basic structure of Pipeline :-</h3>
<p>pipeline {<br>
agent any</p>
<pre><code>stages {

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

