pipeline{
      agent any
      stages{
      stage('check out'){
                  steps{
                  sh "rm -rf hello-world-war"
                  sh "git clone https://github.com/sraahul/hello-world-war"
                  }
                  }
      stage('build'){
      steps{
      sh "cd hello-world-war"
      sh "docker build -t sraahul/file-1-0:${BUILD_NUMBER} ."
      }
      }
       stage('publish'){
                  steps{
                        sh "docker login -u sraahul -p Rahul@123"
                        sh "docker push sraahul/file-1-0:${BUILD_NUMBER}"
                  }
            }
            stage('deploy'){
                  agent { label 'tomcat' }
                  steps{
                        sh "docker login -u sraahul -p Rahul@123"
                        sh "docker pull sraahul/file-1-0:${BUILD_NUMBER}"
                        sh "docker rm -f trail1"
                        sh "docker run -d -p 8082:8080 --name trail1 sraahul/file-1-0:${BUILD_NUMBER}"
                  }
            }
      }
      }
