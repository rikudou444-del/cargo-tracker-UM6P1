pipeline {
    agent any

    triggers {
        githubPush()   
    }

    tools {
    maven 'Maven'  // This name must match the name you configured in Jenkins
}

    stages {

        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/rikudou444-del/cargo-tracker-UM6P1.git'
            }
        }

        stage('Build & Test with Coverage') {
            steps {
                bat 'mvn clean verify'
            }
        }

       /* stage('SonarQube Analysis') {
            environment {
                SONAR_TOKEN = credentials('sonar-token-id')
            }
            steps {
                withSonarQubeEnv('SonarQube Local') {
                    bat """
                        mvn sonar:sonar ^
                        -Dsonar.projectKey=cargo-tracker ^
                        -Dsonar.projectName="Cargo Tracker" ^
                        -Dsonar.coverage.jacoco.xmlReportPaths=target/site/jacoco/jacoco.xml ^
                        -Dsonar.host.url=http://localhost:9000 ^
                        -Dsonar.token=%SONAR_TOKEN%
                    """
                }
            }
        }*/
    }
//
// test for webhooks YEEEEEEEEEEEEEEEEEEEEEEEEESSSSSSSSSSSSSSSSSSSSSSSSSSSSSS
    post {
        success {
            echo 'Build et analyse terminés avec succès !'
        }
        failure {
            echo 'Échec du build ou des tests.'
        }
    }

    // new test
}// new2
