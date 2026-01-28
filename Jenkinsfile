pipeline {
    agent any

    tools {
        maven 'Maven3' 
    }

    stages {
        stage('Compilar') {
            steps {
                // 'clean' borra target previo. 'compile' solo genera los .class
                sh 'mvn clean compile' 
            }
        }

        stage('Test Unitarios') {
            steps {
                sh 'mvn test' 
            }
        }

        stage('Empaquetar') {
            steps {
                // -DskipTests evita repetir lo de la etapa 2
                sh 'mvn package -DskipTests' 
            }
        }

        stage('Desplegar en Tomcat') {
            steps {
                sh 'cp target/CalculadoraWeb-1.0-SNAPSHOT.war /var/jenkins_home/tomcat-deploy/CalculadoraWeb.war'
            }
        }
    }
}

