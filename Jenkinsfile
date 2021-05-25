pipeline{
  agent {
     label 'JAVA'
  }

  stages{

   stage('clean code'){
     steps{
        sh '''
          mvn clean
        '''
     }
   }
   stage('compile code'){
        steps{
           sh '''
             mvn compile
           '''
        }
      }
   stage('Make Package'){
     steps{
       sh '''
         mvn package
       '''
     }
   }
   stage('Preparing Artifacts'){
     steps{
       sh '''
       cp target/*.jar users.jar
       zip -r users.zip users.jar
       '''
     }
   }
   stage('Upload Artifacts'){
     steps{
       sh '''
       curl -f -v -u admin:admin123 --upload-file user.zip http://192.168.0.84:8081/repository/user/users.zip
       '''
     }
   }
  }
}