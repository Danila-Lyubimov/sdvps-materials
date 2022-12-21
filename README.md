# 8.2. Что такое DevOps. СI/СD_ Любимов

## Задание 1.
 1. https://github.com/Danila-Lyubimov/testrepos/blob/b01f6d768368e6becd6f166d317c536f6bb2b9f0/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%20%D0%BE%D1%82%202022-12-10%2000-16-32.png
 2. https://github.com/Danila-Lyubimov/testrepos/blob/b01f6d768368e6becd6f166d317c536f6bb2b9f0/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%20%D0%BE%D1%82%202022-12-10%2000-48-07.png
 3. https://github.com/Danila-Lyubimov/testrepos/blob/b01f6d768368e6becd6f166d317c536f6bb2b9f0/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%20%D0%BE%D1%82%202022-12-10%2000-48-32.png

## Задание 2.
 1. https://github.com/Danila-Lyubimov/testrepos/blob/b01f6d768368e6becd6f166d317c536f6bb2b9f0/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%20%D0%BE%D1%82%202022-12-10%2011-51-06.png
 2. https://github.com/Danila-Lyubimov/testrepos/blob/b01f6d768368e6becd6f166d317c536f6bb2b9f0/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%20%D0%BE%D1%82%202022-12-12%2020-57-13.png

## Задание 3. pipe
```
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
    sh 'CGO_ENABLED=0 GOOS=linux go build -o outfile.go'
   }
  }
  stage('Push') {
   steps {
    sh 'curl -v -u admin:admin http://192.168.1.57:8081/repository/reponew/ --upload-file outfile.go'
    }
  }
 }
}
```
