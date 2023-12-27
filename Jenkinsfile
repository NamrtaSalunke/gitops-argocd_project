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
    }
}
    //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