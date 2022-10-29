pipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload')
        {
            steps
            {
                git 'https://github.com/Ersandeep977/DevOps-Maven-code.git'
            }
        }
        stage('ContinuousBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('ContinuousDeployment')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: 'cda00675-86e1-4f1b-a8f6-0e12a6051a7e', path: '', url: 'http://35.173.233.22:8080')], contextPath: 'testapp', war: '**/*.war'
                }
        }
       stage('ContinuousTesting')
        {
            steps
            {
               git 'https://github.com/Ersandeep977/FunctionalTesting.git'
               sh 'java -jar /var/lib/jenkins/workspace/job-2/testing.jar'
            }
        }
        stage('testing')
        {
            steps
            {
               sh 'date'
            }
        }
       
    }    
}
