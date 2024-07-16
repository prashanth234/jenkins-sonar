pipeline {
    agent any

    stages {
        
        stage('Checkout') {
            steps {
                git branch: 'main', credentialsId: 'FYP_Github', url: 'git@github.com:prashanth234/FYP.git'
            }
        }
        
        stage('Scan Code') {
            steps {
                script {
                    echo "Scanning code"
                    def sonarProperties = """
                        sonar.projectKey=fyp
                    """
                    writeFile file: 'sonar-project.properties', text: sonarProperties
                    def scannerHome = tool 'SonarQubeScanner'; 
                    withSonarQubeEnv('SonarQubeInstance') { 
                      sh "${scannerHome}/bin/sonar-scanner"
                    }
                }
            }
        }
    }
}
