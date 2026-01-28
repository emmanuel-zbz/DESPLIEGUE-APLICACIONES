pipeline {
    agent any

    tools {
        maven 'Maven3' 
    }

    stages {
        // ETAPA 1: Compilar (Limpia y compila el código fuente)
        stage('Compilar') {
            steps {
                // 'clean' borra target previo. 'compile' solo genera los .class
                sh 'mvn clean compile' 
            }
        }

        // ETAPA 2: Test (Reutiliza lo compilado y corre los tests)
        stage('Test Unitarios') {
            steps {
                // NO uses 'clean' aquí o borrarás lo que hizo la etapa anterior.
                sh 'mvn test' 
            }
        }

        // ETAPA 3: Empaquetar (Genera el .war sin repetir tests)
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
