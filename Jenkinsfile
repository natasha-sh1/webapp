pipeline {
    agent any

    environment {
        JAVA_HOME = 'C:\\Program Files\\jdk-21.0.8'
        PATH = "${JAVA_HOME}\\bin;${env.PATH}"
        SONAR_HOST_URL = 'http://localhost:9000'  // Replace with your SonarQube server
    }

    stages {
        stage('Build') {
            steps {
                bat """
                    echo ===== BUILD STAGE =====
                    echo JAVA_HOME=%JAVA_HOME%
                    java -version
                    mvn -version
                    mvn -B -DskipTests clean package
                """
            }
        }

        stage('Test') {
            steps {
                bat """
                    echo ===== TEST STAGE =====
                    mvn test
                """
            }
        }

        stage('Sonar-Report') {
            steps {
                withCredentials([string(credentialsId: 'SONAR_TOKEN', variable: 'SONAR_TOKEN')]) {
                    bat """
                        echo ===== SONAR STAGE =====
                        mvn sonar:sonar -Dsonar.host.url=%SONAR_HOST_URL% -Dsonar.login=squ_35c91fe06aa1effb59bd286a389e3f61d40a1ba2 
                    """
                }
            }
        }
    }
}
