8.2. Что такое DevOps. СI/СD_ Любимов

Задание 1.
https://github.com/Danila-Lyubimov/testrepos/blob/main/Снимок экрана от 2022-12-10 00-16-32.png
https://github.com/Danila-Lyubimov/testrepos/blob/main/Снимок экрана от 2022-12-10 00-48-07.png
https://github.com/Danila-Lyubimov/testrepos/blob/main/Снимок экрана от 2022-12-10 00-48-32.png

Задание 2.
https://github.com/Danila-Lyubimov/testrepos/blob/main/Снимок экрана от 2022-12-10 11-51-06.png
https://github.com/Danila-Lyubimov/testrepos/blob/main/Снимок экрана от 2022-12-12 20-57-13.png

Задание 3.
pipeline {
 agent any
 stages {
  stage('Git') {
   steps {git 'https://github.com/netology-code/sdvps-materials.git'}
  }
  stage('Test') {
   steps {
    sh '/usr/local/go/bin/go test .'
   }
  }
   stage('Build') {
   steps {
    sh 'CGO_ENABLED=0 GOOS=linux go build -a -installsuffix nocgo -o /app'
   }
  }
  stage('Push') {
   steps {
    sh 'docker login ubuntu-bionic:8082 -u admin -p admin && docker push ubuntu-bionic:8082/hello-world:v$BUILD_NUMBER && docker logout'   }
  }
 }
}
