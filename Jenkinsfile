pipeline {
   agent any

   tools {
      maven "M2_HOME"
      jdk "JAVA_HOME"
   }

   stages {
      stage('Build') {
         steps {
            checkout scm
            sh "mvn -Dmaven.test.failure.ignore=true install -X"

         }

         post {
            success {
               junit '**/target/surefire-reports/TEST-*.xml'
               archiveArtifacts '**/*.war'
            }
         }
      }
   }
}
