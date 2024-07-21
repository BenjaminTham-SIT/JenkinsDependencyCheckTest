pipeline {
    agent any
    stages {
        stage('Checkout SCM') {
            steps {
                git url: 'https://github.com/BenjaminTham-SIT/JenkinsDependencyCheckTest.git', branch: 'master'
            }
        }
        stage('OWASP Dependency-Check Vulnerabilities') {
            steps {
                dependencyCheck additionalArguments: ''' 
                    -o "./" 
                    -s "./"
                    -f "ALL" 
                    --prettyPrint''', odcInstallation: 'OWASP-DC'
            }
        }   
    }
    post {
        success {
            dependencyCheckPublisher pattern: 'dependency-check-report.xml'
        }
    }
}
