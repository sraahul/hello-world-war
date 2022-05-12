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
      sh "sudo docker build -t sraahul/file-1-0 ."
      }
      }
       stage('publish'){
                  steps{
                        sh "sudo docker login -u sraahul -p Rahul@123"
                        sh "sudo docker push sraahul/file-1-0"
                  }
            }
            stage('deploy'){
                  agent { label 'tomcat' }
                  steps{
                        sh "sudo docker -S login -u sraahul -p Rahul@123"
                        sh "sudo docker pull sraahul/file-1-0"
                        sh "sudo docker run -d -p 8082:8080 --name trail1 sraahul/file-1-0"
                  }
            }
      }
      }
