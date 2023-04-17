pipeline {
    agent any 
    
    stages {
        stage('Build') { 
            steps {
                withMaven(
                    maven: 'jenkins-maven',
                    jdk: 'JDK11v2',
                    mavenLocalRepo: '$WORKSPACE/jdk11/.repository'
                    ) {
                        sh 'export JENKINS_MAVEN_AGENT_DISABLED=true'
                        sh 'echo "Building....."'
                        sh '''
                            mvn clean package
                        '''
                    }
            }
        }
        stage('Test') { 
                steps {
                    withMaven(
                        maven: 'jenkins-maven',
                        jdk: 'JDK11v2',
                        mavenLocalRepo: '$WORKSPACE/jdk11/.repository'
                    ) {
                        echo "Testing......" 
                        // sh 'mvn test'
                    }
            }
        }
        stage('Deploy') { 
            steps {
                sh '''
                    if [ lsof -t -i:8081 ] 
                    then
                        kill -9 $(lsof -t -i:8081)
                    fi
                    java -jar target/*.jar
                '''
            }
        }
        
    }
    
}