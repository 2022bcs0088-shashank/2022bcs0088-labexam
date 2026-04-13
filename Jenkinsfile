pipeline {
    agent any
    
    stages {
        stage('Setup') {
            steps {
                sh '''
                python3 -m venv .venv
                . .venv/bin/activate
                pip install -r requirements.txt
                '''
            }
        }
        
        stage('Train') {
            steps {
                sh '''
                . .venv/bin/activate
                python3 train.py
                '''
            }
        }
        
        stage('Identity') {
            steps {
                echo "Student: [Insert Your Name] | Roll No: 2022BCS0088"
            }
        }
        
        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'model.pkl, metrics.json', allowEmptyArchive: false
            }
        }
    }
}