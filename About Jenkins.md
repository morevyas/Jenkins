---


---

<h1 id="jenkins">Jenkins</h1>
<h1 id="using-jenkins">Using Jenkins<a href="https://www.jenkins.io/doc/book/using/#using-jenkins"></a></h1>
<p>Chapter Sub-Sections</p>
<ul>
<li><a href="https://www.jenkins.io/doc/book/using/best-practices">Best Practices</a></li>
<li><a href="https://www.jenkins.io/doc/book/using/working-with-projects">Working with projects</a></li>
<li><a href="https://www.jenkins.io/doc/book/using/using-credentials">Using credentials</a></li>
<li><a href="https://www.jenkins.io/doc/book/using/searchbox">Command Palette</a></li>
<li><a href="https://www.jenkins.io/doc/book/using/referencing-another-project-by-name">Referencing another project by name</a></li>
<li><a href="https://www.jenkins.io/doc/book/using/aborting-a-build">Aborting a build</a></li>
<li><a href="https://www.jenkins.io/doc/book/using/fingerprints">Fingerprints</a></li>
<li><a href="https://www.jenkins.io/doc/book/using/using-local-language">Using local language</a></li>
<li><a href="https://www.jenkins.io/doc/book/using/change-time-zone">Change time zone</a></li>
<li><a href="https://www.jenkins.io/doc/book/using/remote-access-api">Remote Access API</a></li>
<li><a href="https://www.jenkins.io/doc/book/using/executor-starvation">Executor Starvation</a></li>
<li><a href="https://www.jenkins.io/doc/book/using/using-agents">Using Jenkins agents</a></li>
<li><a href="https://www.jenkins.io/doc/book/using/using-jmeter-with-jenkins">Using JMeter with Jenkins</a></li>
<li><a href="https://www.jenkins.io/doc/book/using/pluggable-storage">Pluggable Storage</a></li>
</ul>
<p>This chapter contains topics for typical Jenkins users (of all skill levels) about Jenkins Pipeline.</p>
<p>If you want to create and configure a Pipeline project through a  <code>Jenkinsfile</code>  or you wish to find out more about this core Jenkins feature, refer to the relevant topics within the  <a href="https://www.jenkins.io/doc/book/pipeline">Pipeline</a>  chapter.</p>
<p>If you are a Jenkins administrator and want to know more about managing Jenkins nodes and instances, see  <a href="https://www.jenkins.io/doc/book/managing">Managing Jenkins</a>.</p>
<p>If you are a system administrator and want to learn how to back-up, restore, maintain as Jenkins servers and nodes, see  <a href="https://www.jenkins.io/doc/book/system-administration">Jenkins System Administration</a>.</p>
<p>If you are a Jenkins user looking for some troubleshooting tips, see  <a href="https://www.jenkins.io/doc/book/troubleshooting">Troubleshooting Jenkins</a></p>
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
<h3 id="jenkins-controller">2) Jenkins Controller</h3>
<ul>
<li>Managing Jenkins jobs and pipelines</li>
<li>Scheduling builds</li>
<li>Managing users and permissions</li>
<li>Managing credentials</li>
<li>Managing plugins</li>
<li>Reading Jenkinsfiles</li>
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

