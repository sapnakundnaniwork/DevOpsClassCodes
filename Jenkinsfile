pipeline {
    agent any

    tools {
        maven 'Mymaven'
    }

    stages {

        stage('CloneRepo') {
            steps {
                git 'https://github.com/bhasker-manikyala/DevOpsClassCodes.git'
            }
        }

        stage('Compile') {
            steps {
                sh 'mvn compile'
            }
        }

        stage('CodeReview') {
            steps {
                sh 'mvn pmd:pmd'
            }
            post {
                success {
                    recordIssues(
                        tools: [pmdParser(pattern: 'target/pmd.xml')]
                    )
                }
            }
        }

        stage('UnitTesting') {
            steps {
                sh 'mvn test'
            }
            post {
                always {   // better than success
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }

        stage('Package') {   // capitalize for consistency
            steps {
                sh 'mvn package'
            }
        }
    }
}
