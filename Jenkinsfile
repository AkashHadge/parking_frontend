pipeline {
    agent any
        stages{
            stage('Git Checkout'){
                steps{
                    git 'https://github.com/AkashHadge/parking_frontend'
                }
            }
            stage('Build') {
                steps{
                    sh 'npm install'
                    sh 'npm run build'
                    sh 'npm audit fix'
                }
            }
            stage('Deploy'){
                steps{
                    sh 'cp -r $WORKSPACE/build /var/jenkins_home/workspace'
                    sh 'curl -u admin:admin http://35.192.17.97:8888/manager/reload?path=/build'
                }
            }
            }
        }
