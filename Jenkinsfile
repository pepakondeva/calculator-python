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
                echo "Installing dependencies..."
                sh """
                $VENV_DIR/bin/python -m pip install --upgrade pip
                if [ -f requirements.txt ]; then $VENV_DIR/bin/pip install -r requirements.txt; fi
                """
            }
        }

        stage('Run Calculator') {
            steps {
                echo "Running calculator.py..."
                sh "$VENV_DIR/bin/python calculator.py"
            }
        }
    }

    post {
        always {
            echo "Pipeline finished."
        }
    }
}
