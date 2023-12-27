pipeline{
    agent any 

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
    }
}
    //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