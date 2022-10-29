pipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload')
        {
            steps
            {
                git 'https://github.com/azmeeranaveen/DevOps-Maven-code.git'
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
               git 'https://github.com/azmeeranaveen/FunctionalTesting.git'
               sh 'java -jar /var/lib/jenkins/workspace/job-2/testing.jar'
            }
        }
        stage('Contnuos Delpoy')
        {
            steps
            {
                input 'go ....'
                deploy adapters: [tomcat9(credentialsId: 'cda00675-86e1-4f1b-a8f6-0e12a6051a7e', path: '', url: 'http://54.81.225.19:8080')], contextPath: 'prodapp', war: '**/*.war'
            }
        }
       
    }    
}
