pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                bat """
                    echo ===== BUILD STAGE =====

                    rem Set Java for this pipeline
                    set JAVA_HOME=C:\\Program Files\\jdk-21.0.8
                    set PATH=%JAVA_HOME%\\bin;%PATH%

                    echo JAVA_HOME=%JAVA_HOME%
                    echo ---- java -version ----
                    java -version

                    echo ---- mvn -version ----
                    mvn -version

                    echo ---- mvn clean package (skip tests) ----
                    mvn -B -DskipTests clean package
                """
            }
        }

        stage('Test') {
            steps {
                bat """
                    echo ===== TEST STAGE =====

                    rem Set Java again for safety
                    set JAVA_HOME=C:\\Program Files\\jdk-21.0.8
                    set PATH=%JAVA_HOME%\\bin;%PATH%

                    echo JAVA_HOME=%JAVA_HOME%
                    echo ---- running mvn test ----
                    mvn test
                """
            }
        }

        stage('Sonar-Report') {
            steps {
                bat """
                    echo ===== SONAR STAGE =====

                    rem Set Java again for safety
                    set JAVA_HOME=C:\\Program Files\\jdk-21.0.8
                    set PATH=%JAVA_HOME%\\bin;%PATH%

                    echo JAVA_HOME=%JAVA_HOME%
                    echo ---- sonar analysis (this will fail if SonarQube not configured) ----

                    rem Replace this with your actual sonar command when ready
                    mvn sonar:sonar
                """
            }
        }
    }
}
