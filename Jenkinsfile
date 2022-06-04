pipeline {
  agent {label 'tomcat'}
  stages {
    stage ('checkout') {
      steps {
              sh 'whoami'
              sh 'rm -rf hello-world-war'
              sh 'git clone https://github.com/sraahul/hello-world-war'
              sh 'pwd'
              sh 'ls'
      }
    }
    stage ('build') {
      steps {
              sh 'docker build -t sraahul/file-1-0:${BUILD_NUMBER} .'
      }
    }
    stage ('publish') {
      steps {               
              sh "docker login -u sraahul -p Rahul@123"
              sh "docker push sraahul/file-1-0:${BUILD_NUMBER}"
              sh 'pwd'
              sh 'ls'
              sh "helm package --version ${BUILD_NUMBER} helm/mytomcat/ "
              sh "curl -rinsane15@gmail.com:Rahul@123 -T mytomcat-${BUILD_NUMBER}.tgz \"https://srahul.jfrog.io/artifactory/mytomcat-helm/mytomcat-${BUILD_NUMBER}.tgz\""
      }
    }
      
    stage ('deploy') {
      agent {label 'eksslave'}
      steps {
              sh "helm repo add mytomcat-helm https://srahul.jfrog.io/artifactory/api/helm/mytomcat-helm --username rinsane15@gmail.com --password Rahul@123"
              sh "helm repo update"
              sh "helm upgrade --install tomcat mytomcat-helm/mytomcat --set image_tag=${BUILD_NUMBER} --version ${BUILD_NUMBER}"
      }
    }
  }         
}

