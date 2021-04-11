pipeline {
    agent any
    stages {
        stage('SCM') {
            steps {
                git url: 'https://github.com/Tamilvananv/HCL'
            }
        }
     stages{
	       stage('Quality Gate Status Check'){
		    agent any{
			args '-v $HOME/.m2:/root.m2'
			}
		}
	stage('Tools Init') {
            steps {
                script {
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
               def tfHome = tool name: 'Ansible'
                env.PATH = "${tfHome}:${env.PATH}"
                 sh 'ansible --version'
                    
            }
            }
	 stage('Execute Maven') {
           steps {
             
                sh 'mvn package'             
          }
        }
        
     stage('Ansible Deploy') {
             
            steps {
                 
           sh "ansible-playbook main.yml -i inventories/dev/hosts -- user jenkins --key-file ~/.ssh/id_rsa"
}
        }
