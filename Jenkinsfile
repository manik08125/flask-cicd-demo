pipeline {
agent any

```
environment {
    IMAGE_NAME = "flask-cicd-demo"
}

stages {
    stage('Clone Repository') {
        steps {
            git branch: 'main', url: 'https://github.com/manik08125/flask-cicd-demo.git'
        }
    }

    stage('Build Docker Image') {
        steps {
            sh 'docker build -t $IMAGE_NAME .'
        }
    }

    stage('Run Container') {
        steps {
            sh 'docker run -d -p 5000:5000 --name flask_app $IMAGE_NAME'
        }
    }
}

post {
    always {
        echo 'Pipeline execution completed.'
    }
}
```

}
