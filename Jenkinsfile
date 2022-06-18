pipeline{
  agent {
    label {
      label 'slave1'
    }
  }
  stages{
    stage('1-git-checkout'){
      steps{
        checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'f7c765a1-e95f-44ad-9f53-7b9fc6ad20ec', url: 'https://github.com/Healthapp-org/team5-distributed-pipeline.git']]])  }
    } 
    stage('2-parallel-job by princess, uche, kanayo'){
      parallel{
        stage('sub-job1 by princess'){
          steps{
            sh 'uptime'
          }
        }
        stage('sub-job2 by uche'){
          steps{
            sh 'free -m'
          }
        }
        stage('sub-job3 by kanayo'){
            steps{
                sh 'ls -i'
            }
        }
      }
    }
    stage('3-user-info'){
      agent {
        label {
          label 'slave2'
        }
      }
      steps{
        sh 'cat /etc/passwd'
      }
    }
    stage('4-parallel-job by chinedu & ozo'){
          parallel{
            stage('sub-job4 by chinedu'){
              steps{
                  sh 'free -g'
                }
              }
              stage('sub-job5 by ozo'){
                steps{
                  sh 'du -h'
                  sh 'df -h'
                }
              }
              stage('sub-job6 by princess'){
                steps{
                  echo "deployment"
                }
              }
            }
          }
    stage('5-parallel-job by uche & ozo'){
          parallel{
            stage('sub-job7 by ozo'){
              steps{
                  sh 'uname'
                }
              }
              stage('sub-job8 by princess'){
                steps{
                  echo 'My time has come'
                }
              }
              stage('sub-job9 by princess'){
                steps{
                  echo "pipeline building"
                }
              }
            }
          }
    stage('6-Build Success'){
      agent {
        label {
          label 'slave3'
        }
      }
      steps{
        echo 'successful build'
      }    
    }
    stage('7-System Analysis'){
      agent {
        label {
          label 'slave3'
        }
      }
      steps{
        sh 'cat /etc/os-release'
      }
    }
   }
  }
