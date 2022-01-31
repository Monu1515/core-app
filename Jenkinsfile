pipeline {
    agent {label "cloud-build"}

    tools {
        maven "maven-build"
    }

    stages {
        stage('Build') {
            steps {
                git branch: 'master', url: 'https://github.com/Monu1515/core-app.git'
                sh "mvn -Dmaven.test.failure.ignore=true clean install"  
            }

            post {
                success {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.jar'
                }
            }
        }
    }
}
