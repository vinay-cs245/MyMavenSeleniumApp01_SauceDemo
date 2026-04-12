pipeline {
    agent any

    tools {
        maven 'Maven'   // Must match Jenkins Global Tool Configuration
        jdk 'JDK'       // Must match Jenkins Global Tool Configuration
    }

    environment {
        APP_NAME = 'MyMavenSeleniumApp01_SauceDemo'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/vinay-cs245/MyMavenSeleniumApp01_SauceDemo'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Run Selenium Script') {
            steps {
                sh 'mvn exec:java -Dexec.mainClass="com.example.App"'
            }
        }
    }

    post {
        success {
            echo 'Selenium script executed successfully!'
        }
        failure {
            echo 'Execution failed!'
        }
        always {
            echo 'Pipeline execution completed.'
        }
    }
}
