pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "maven_new"
    }

    stages {
        stage('Build') {
            steps {
                git branch: 'main', url: 'https://github.com/anshuk6469/nodejs-app.git'
                sh "mvn -DskipTests=true clean package"
                archive 'target/*.jar'
              
            }

        }
    }
}
