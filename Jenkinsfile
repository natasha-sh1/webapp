pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                bat """
                    set JAVA_HOME=C:\\Users\\ISHITA SHARMA\\AppData\\Local\\Programs\\Eclipse Adoptium\\jdk-17.0.16.8-hotspot
                    set PATH=%JAVA_HOME%\\bin;%PATH%

                    echo After override, JAVA_HOME=%JAVA_HOME%
                    mvn -version
                    mvn -B -DskipTests clean package
                """
            }
        }

        stage('Test') {
            steps {
                bat """
                    set JAVA_HOME=C:\\Users\\ISHITA SHARMA\\AppData\\Local\\Programs\\Eclipse Adoptium\\jdk-17.0.16.8-hotspot
                    set PATH=%JAVA_HOME%\\bin;%PATH%

                    mvn test
                """
            }
        }

        stage('Sonar-Report') {
            steps {
                bat """
                    set JAVA_HOME=C:\\Users\\ISHITA SHARMA\\AppData\\Local\\Programs\\Eclipse Adoptium\\jdk-17.0.16.8-hotspot
                    set PATH=%JAVA_HOME%\\bin;%PATH%

                    mvn sonar:sonar
                """
            }
        }
    }
}
