pipeline {
    agent any

    tools {
        maven 'Maven3' 
    }

    stages {
        // ETAPA 1: Solo compilar y testear
        stage('Test Unitarios') {
            steps {
                // Ejecuta los tests. Si fallan, el pipeline se detiene aquí.
                sh 'mvn clean test' 
            }
        }

        // ETAPA 2: Empaquetar (saltando los tests porque ya pasaron)
        stage('Empaquetar') {
            steps {
                // -DskipTests evita que se corran los tests de nuevo
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
