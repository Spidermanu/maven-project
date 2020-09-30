pipeline{
    agent any
    
    tools{
        maven 'Local Maven'
    }
	stage ('Checkout') {
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '', url: 'https://github.com/Spidermanu/maven-project.git']]]) 
	}

    stages{
        stage('Build'){
            steps{
                bat 'mvn clean package'
            }
            
            post{
                success{
                    echo "Estamos haciendo el archive de los artefactos"
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
        
    }
}
