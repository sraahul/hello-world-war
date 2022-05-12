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
      sh "pwd"
      sh "ls"
      sh "cd hello-world-war"
      sh "docker build -t sraahul/file:1.0 ."
      }
      }
       stage('publish'){
                  steps{
                        sh "docker login -u shashankvirat -p Virat@123"
                        sh "docker push sraahul/file:1.0"
                  }
            }
            stage('deploy'){
                  agent { label 'tomcat' }
                  steps{
                        sh "docker login -u shashankvirat -p Virat@123"
                        sh "docker pull sraahul/file:1.0"
                        sh "docker rm -f trail1"
                        sh "docker run -d -p 8082:8080 --name trail1 sraahul/file:1.0"
                  }
            }
      }
      }
