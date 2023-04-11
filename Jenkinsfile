pipeline{
    agent any
    tools {
        maven 'Maven' 
    }
    stages{
        stage("Test"){
            steps{
                //mvn test
                sh "mvn test"
                echo "========executing A========"
            }
        }
        stage("Build"){
            steps{
                // mvn package
                sh "mvn package"
                echo "========executing A========"
            }
        }
        stage("Deploy on test"){
            steps{
                //deploy on continair -> plugin
                deploy adapters: [tomcat9(credentialsId: 'c82cca90-95b8-4195-87e8-610eac8bfe2f', path: '', url: 'http://192.168.122.206:8088')], contextPath: '/app', war: '**/*.war'
                echo "========executing A========"
            }
        }
        stage("Deploy on prod"){
            steps{
                //deploy on continair -> plugin
                deploy adapters: [tomcat9(credentialsId: 'c82cca90-95b8-4195-87e8-610eac8bfe2f', path: '', url: 'http://192.168.122.3:8080')], contextPath: '/app', war: '**/*.war'
                echo "========executing A========"
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
