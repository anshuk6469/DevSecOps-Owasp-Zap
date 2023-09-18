pipeline {
    agent any
    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "maven_new"
    }

    stages {
        stage('Build') {
            steps {
                echo "This is ${WORKSPACE}"
                git branch: 'main', url: 'https://github.com/anshuk6469/nodejs-app2.git'
                sh "mvn clean package -DskipTests=true"
                archive 'target/*.jar'
            }
        }
           stage('Test') {
            steps {
                sh "ls ; mvn test"
            }
            post{
                always {
                    junit 'target/surefire-reports/*.xml'
                    jacoco (execPattern: '**/target/jacoco.exec')
                  }
             }
        }
    }   
}