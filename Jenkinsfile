pipeline {
    agent any

    stages {
        stage('Checkout SCM') {
            steps {
                git 'https://github.com/Fairez-Rashid/jenkins-docker-maven-java-webapp.git'
                
            }
        }

        stage('Maven compile') {
            steps {
                bat "mvn clean compile"
            }
        }

        stage('Maven package') {
            steps {
                bat "mvn package -Dmaven.test.skip=true"
                bat "%CD%"
            }
        }
      //   stage('Deploy Artifact to remote Windows server') {
      //       steps {
      //   withCredentials([usernamePassword(credentialsId: 'YOUR_SSH_CREDENTIALS_ID', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
      //     script {
      //       def sourceFilePath = 'path/to/your/war/file.war'
      //       def targetServer = 'TARGET_SERVER_IP'
      //       def targetUser = env.USERNAME
      //       def targetPassword = env.PASSWORD

      //       // Copy the WAR file to the remote server using SCP
      //       sshCommand remote: targetServer, user: targetUser, password: targetPassword, command: "scp ${sourceFilePath} ${targetUser}@${targetServer}:C:/path/on/target/server"
      //     }
      //   }
      // }
      //   }        

        

        // stage('Archive artifacts') {
        //     steps {
        //         archiveArtifacts artifacts: '**/*.war', onlyIfSuccessful: true
        //     }
        // }

        // stage('Archive Test Results') {
        //     steps {
        //         junit allowEmptyResults: true, testResults: '**/surefire-reports/*.xml'
        //     }
        // }

        // stage('Deploy') {
        //     steps {
        //         withCredentials([[
        //             $class: 'UsernamePasswordMultiBinding',
        //             credentialsId: 'your-credentials-id',
        //             usernameVariable: 'USERNAME',
        //             passwordVariable: 'PASSWORD'
        //         ]]) {
        //             sh 'scp -o StrictHostKeyChecking=no -r target/*.war USERNAME:PASSWORD@remote-server:/path/to/deploy/'
        //         }
        //     }
        // }
    }
}
