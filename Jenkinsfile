pipeline {
  agent any 
  tools {
    maven 'Maven'
  }
  stages {
    stage ('Initialize') {
      steps {
        sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
            ''' 
         }
     }
    
    stage('Check-Git-Secrets') {
      steps {
        sh 'docker pull gesellix/trufflehog'
        sh 'sudo docker run gesellix/trufflehog --json https://github.com/Bharath-Kandukoori/webapp.git > trufflehog'
        sh 'cat trufflehog'
      }
    }

     stage ('Build') {
       steps {
       sh 'mvn clean package'
    }
     }
   }
}
