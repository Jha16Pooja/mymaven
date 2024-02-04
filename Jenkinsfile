node('built-in') {
   stage('ContinuosDownload') {
   git 'https://github.com/Jha16Pooja/mymaven.git'
}

stage('ContinuosBuild') {
   sh 'mvn package'
}

stage('ContinuosDeployment') {
  deploy adapters: [tomcat9(credentialsId: 'eff309f4-7b1e-4d56-b6e4-3c6385f44dd1', path: '', url: 'http://172.31.25.149:8080')], contextPath: 'testapp1', war: '**/*.war'
}

stage('ContinuosTesting') {
   git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
   sh 'java -jar  /home/ubuntu/.jenkins/workspace/ScriptivePipeline/testing.jar'
  
}
stage('ContinuosDelivery') {
    input message: '  Ready to go?     Proceed or Abort', submitter: 'pooja'
deploy adapters: [tomcat9(credentialsId: 'eff309f4-7b1e-4d56-b6e4-3c6385f44dd1', path: '', url: 'http://172.31.46.156:8080')], contextPath: 'prodapp11', war: '**/*.war'
}

}
