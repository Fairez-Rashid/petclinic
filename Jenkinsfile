pipeline {
    agent any

    stages {
        stage('Checkout SCM') {
            steps {
                git branch: 'master', url: 'https://github.com/Fairez-Rashid/PetClinic'
            }
        }

        stage('Maven compile') {
            steps {
                sh "mvn clean compile"
            }
        }

        stage('Maven package') {
            steps {
                sh "mvn package -Dmaven.test.skip=true"
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
