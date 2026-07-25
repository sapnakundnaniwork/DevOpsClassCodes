pipeline {
    agent any
    tools {
        maven 'mymaven'
    }
stages {
    stage('CloneRepo') {
        steps {
            git changelog: false, poll: false, url: 'https://github.com/bhasker-manikyala/DevOpsClassCodes.git'
        }
    }
    stage('Build') {
        steps {
            sh 'mvn compile'
        }
    }
}
}
