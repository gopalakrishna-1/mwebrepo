pipeline{
    agent any
            environment {
        PATH = "/opt/maven/bin:$PATH"
    }
    stages{
        stage('code checkout') {
            steps{
                git credentialsId: 'git_credentials', url: 'https://github.com/gopalakrishna-1/mwebrepo.git'
                echo"code checkout successfully done"
            }
        }
        stage('code build') {
            steps{
                sh 'mvn clean package'
                echo 'code build successfully done'
            }
        }
        stage('code deploy') {
            steps{
             sshagent(['ssh-agent']) {
               sh 'scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/pjob-1/webapp/target/webapp.war ec2-user@54.159.2.213:/opt/apache-tomcat-9.0.75'
              }     
            }
            
        }
        
    }
}
	
