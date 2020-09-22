pipeline {
   agent any

   environment {
     SERVICE_NAME = "mssql-db"     
     REPOSITORY_TAG="${YOUR_DOCKERHUB_USERNAME}/${ORGANIZATION_NAME}-${SERVICE_NAME}:${BUILD_ID}"
   }

   stages {
      stage('Preparation') {
         steps {
            cleanWs()
            git credentialsId: 'GitHub', url: "https://github.com/${ORGANIZATION_NAME}/${SERVICE_NAME}"
         }
      }

      stage('Deploy to Cluster') {
          steps {
              sh 'kubectl apply -f deploy.yaml'
               }
          }
      }
   }
}