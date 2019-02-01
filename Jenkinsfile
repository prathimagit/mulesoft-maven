pipeline {
  agent {
        label 'master'
    }
  stages {
    stage('Deploy Standalone') { 
      steps {
        sh 'mvn deploy -P standalone'
      }
    }
    stage('Deploy ARM') { 
      environment {
        ANYPOINT_CREDENTIALS = credentials('prathi.credentials') 
      }
      steps {
        sh 'mvn deploy -P arm -Darm.target.name=local-3.9.0-ee -Viren Shah.username=${ANYPOINT_CREDENTIALS_USR}  -Viren Shah.password=${ANYPOINT_CREDENTIALS_PSW}' 
      }
    }
    stage('Deploy CloudHub') { 
      environment {
        ANYPOINT_CREDENTIALS = credentials('prathi.credentials')
      }
      steps {
        sh 'mvn deploy -P cloudhub -Dmule.version=3.9.0 -Viren Shah.username=${ANYPOINT_CREDENTIALS_USR} -Viren Shah.password=${ANYPOINT_CREDENTIALS_PSW}' 
      }
    }
  }
}
