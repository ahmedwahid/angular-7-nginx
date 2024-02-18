pipeline{
           agent any
           environment {
                      DOCKERHUB_CREDENTIALS=credentials('dockerhub ')
           }
           stages {
                      stage('Build') {
                                    steps {
                                                sh 'docker build -t ahmedwahid/angular-7-nginx:latest .'
                                          }
                      }
                      stage('Login') {
                                    steps {
                                                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                                          }
                      }
                      stage('Push') {
                                    steps {
                                                sh 'docker push ahmedwahid/angular-7-nginx:latest'
                                          }
                      }
           }
           post {
                      always {
                                                sh 'docker logout'
                             }
                }
}
