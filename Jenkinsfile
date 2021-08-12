pipeline {
   agent {
        docker {
            image 'node:6-alpine'
            args '-p 3000:3000'
        }
   }

   environment {
       DEMO='1.3'
   }
   

   stages {
      stage('stage-1') {
         steps {
            echo "This is build number $BUILD_NUMBER of demo $DEMO"
            sh '''
               echo "Using a multi-line shell step"
               chmod +x test.sh
               ./test.sh
            '''
         }
      }
      stage ('build') {
        steps {
          sh 'npm run build'
        }
      }
      stage('test') {
         steps {
            echo "it undergoes the ttest"
            sh '''
              npm run test

            '''
         }
      }
   }
}
