pipeline {
    agent any

    tools {
        maven 'Maven3' 
    }

    stages {
        stage('Compilar y Empaquetar') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Desplegar en Tomcat') {
            steps {
                sh 'cp target/CalculadoraWeb-1.0-SNAPSHOT.war /var/jenkins_home/tomcat-deploy/CalculadoraWeb.war'
            }
        }
    }
}
