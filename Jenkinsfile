pipeline {
    agent any

    environment {
        VENV_DIR = "venv"
    }

    stages {
        stage('Setup Python') {
            steps {
                echo "Creating virtual environment..."
                sh "python3 -m venv $VENV_DIR"
            }
        }

        stage('Install dependencies') {
            steps {
                echo "Activating virtual environment and installing dependencies..."
                sh """
                source $VENV_DIR/bin/activate
                python -m pip install --upgrade pip
                if [ -f requirements.txt ]; then pip install -r requirements.txt; fi
                """
            }
        }

        stage('Run Calculator') {
            steps {
                echo "Running calculator.py..."
                sh """
                source $VENV_DIR/bin/activate
                python calculator.py
                """
            }
        }
    }

    post {
        always {
            echo "Pipeline finished."
        }
    }
}
