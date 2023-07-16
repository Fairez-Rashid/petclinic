pipeline {
    agent any

    stages {
        stage('Checkout SCM') {
            steps {
                git 'https://github.com/Fairez-Rashid/jenkins-docker-maven-java-webapp.git'
                bat "echo source code downloaded "
                
            }
        }

        stage('Maven compile') {
            steps {
                bat "mvn clean compile"
                bat "echo maven compile completed"
            }
        }

        stage('Maven package') {
            steps {
                bat "mvn package -Dmaven.test.skip=true"
                bat "echo %CD%"
            }
        }
         stage('Deploy Artifact to remote Windows server') {
             steps {
         withCredentials([usernamePassword(usernameVariable: 'tomcat', passwordVariable: 'Tomcat@123456')]) {
          script {
            def sourceFilePath = 'C:\data\jenkins_home\workspace\jenkins_ci_pipeline\target\java-web-app-1.0.war'
            def targetServer = '20.24.71.63'
            def targetUser = env.USERNAME
            def targetPassword = env.PASSWORD

            // Copy the WAR file to the remote server using SCP
            sshCommand remote: targetServer, user: targetUser, password: targetPassword, command: "scp ${sourceFilePath} ${targetUser}@${targetServer}:C:\Program Files\Apache Software Foundation\Tomcat 8.5\webapps"
          }
        }
      }
        }        

        

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
