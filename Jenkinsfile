node {
    stage('Checkout SCM') {
        git branch: 'master', url: 'https://github.com/Fairez-Rashid/PetClinic'
    }

    stage('Maven compile') {
        sh "mvn clean compile"
    }

    stage('Maven package') {
        sh "mvn package -Dmaven.test.skip=true"
    }


    // stage('Deploy To Windows Server') {
    //     withCredentials([usernamePassword(credentialsId: 'windows-server-credentials', passwordVariable: 'PASSWORD', usernameVariable: 'USERNAME')]) {
    //         sh "scp -o StrictHost

}
