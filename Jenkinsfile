pipeline
{
    agent any
    stages
    {
        stage('continuousDwonload')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/maven.git'
            }
        }
        stage('continuousBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('continuousDeployment')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '0038fb52-bf8d-4e86-ac1d-883fd4bfab41', path: '', url: 'http://172.31.11.172:8080')], contextPath: 'testapp', war: '**/*.war'
            }
        }
        stage('continuousTesting')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar  /home/ubuntu/.jenkins/workspace/declarativepipeline2/testing.jar'     
           }
        }
        stage('continuousDelivery')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '0038fb52-bf8d-4e86-ac1d-883fd4bfab41', path: '', url: 'http://172.31.0.222:8080')], contextPath: 'prodapp', war: '**/*.war'
            }
        }
    }

}








node('built-in') 
{
    stage('continuousDwonload') 
    {
      git 'https://github.com/intelliqittrainings/maven.git'
}
 stage('continuousBuild') 
    {
      sh 'mvn package'
}
stage('continuousDeployment') 
    {
      deploy adapters: [tomcat9(credentialsId: '0038fb52-bf8d-4e86-ac1d-883fd4bfab41', path: '', url: 'http://172.31.11.172:8080')], contextPath: 'testapp', war: '**/*.war'
}
stage('continuousTesting') 
    {
       git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
}
stage('continuousDelivery') 
    {
       deploy adapters: [tomcat9(credentialsId: '0038fb52-bf8d-4e86-ac1d-883fd4bfab41', path: '', url: 'http://172.31.0.222:8080')], contextPath: 'prodapp', war: '**/*.war'
}
}














