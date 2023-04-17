pipeline {
    agent any 
    
    stages {
        stage('Build') { 
            steps {
                withMaven(
                    maven: 'jenkins-maven',
                    jdk: 'JDK8',
                    mavenLocalRepo: '$WORKSPACE/jdk8/.repository'
                    ) {
                        sh 'export JENKINS_MAVEN_AGENT_DISABLED=true'
                        sh 'echo "Building....."'
                        sh '''
                            mvn clean package -DskipTests=true
                        '''
                    }
            }
        }
        stage('Test') { 
                steps {
                    withMaven(
                        maven: 'jenkins-maven',
                        jdk: 'JDK8',
                        mavenLocalRepo: '$WORKSPACE/jdk8/.repository'
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