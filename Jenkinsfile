pipeline{

    agent any 

    environment{

        DOCKERHUB_USERNAME = "namrtasalunke"
        APP_NAME = "gitops-argo-app"
        IMAGE_TAG = "${BUILD_NUMBER}"
        IMAGE_NAME = "${DOCKERHUB_USERNAME}" + "/" + "${APP_NAME}"
        REGISTRY_CREDS = 'dockerhub'
    }
    stages{

        stage('Clenup workspace'){

            steps{
                script{

                    cleanWs()
                }
            }
        }
        stage('checkout SCM'){

            steps{
                script{
                    git credentialsId: 'github',
                    url: 'https://github.com/NamrtaSalunke/gitops-argocd_project.git',
                    branch: 'main'
                  }
               }
            }
        stage('Build Docker Image'){
            steps{
                script{

                    docker_image = docker.build "${IMAGE_NAME}"
                }
            }
        }
        
        stage('Push Docker Image'){
            steps{
                script{

                    docker.withRegistry('',REGISTRY_CREDS){
                        docker_image.push("$BUILD_NUMBER")
                        docker_image.push('latest')
                    }
                }
            }
        }  
    
        }
    }

//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