pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh '''pwd
date'''
      }
    }

    stage('Test') {
      parallel {
        stage('Test') {
          steps {
            echo 'test step'
          }pipeline{
    agent any
    tools {
        maven 'Maven' 
    }
    stages{
        stage("Test"){
            steps{
                //mvn test
                sh "mvn test"
            }
        }
        stage("Build"){
            steps{
                // mvn package
                sh "mvn package"
            }
        }
        stage("Deploy on test"){
            steps{
                //deploy on continair -> plugin
                deploy adapters: [tomcat9(credentialsId: 'c82cca90-95b8-4195-87e8-610eac8bfe2f', path: '', url: 'http://192.168.122.206:8088')], contextPath: '/app', war: '**/*.war'
            }
        }
        stage("Deploy on prod"){
            steps{
                //deploy on continair -> plugin
                deploy adapters: [tomcat9(credentialsId: 'c82cca90-95b8-4195-87e8-610eac8bfe2f', path: '', url: 'http://192.168.122.3:8080')], contextPath: '/app', war: '**/*.war'
                
            }
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}
