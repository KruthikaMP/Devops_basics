pipeline {
    agent{
        label 'ubuntuagent'
    }


    stages {
        stage('Build') {
            steps {
                // Get some code from a GitHub repository
                 checkout poll: false, scm: [$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], gitTool: 'ubuntugit', userRemoteConfigs: [[url: 'https://github.com/KruthikaMP/node-hello_Lab_Exam_Batch_2.git']]]

               
            }

        }
        
        stage('Build docker image') {
            steps {
                script {
                    
                    sh 'sudo docker build -t labtest10:v2 .'
                }
                
            }
        }
         
         stage('Push to DockerHub') {
            steps {
                script {
                     
                        sh 'sudo docker login -u maya2212 -p deehan@2822'
                        sh 'sudo docker push maya2212/labtest1'
                        sh 'sudo docker pull maya2212/labtest1'
                    
                }
            }
        }
        stage('Run docker container') {
            steps {
                script {
                    
                    sh 'sudo docker rm -f ourwebpulled1'
                    sh 'sudo docker run -itd --name ourwebpulled1 -p 3016:3000 maya2212/labtest1'
                }
                
            }
        }
    }
}
