pipeline{
  agent {
     label 'JAVA'
  }

  stages{

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
       cp target/*.jar user.jar
       zip -r user.zip user.jar
       '''
     }
   }
   stage('Upload Artifacts'){
     steps{
       sh '''
       curl -f -v -u admin:admin123 --upload-file user.zip http://192.168.0.84:8081/repository/user/user.zip
       '''
     }
   }
  }
}