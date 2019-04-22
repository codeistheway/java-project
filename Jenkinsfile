node('linux'){
    stage('Build'){
        git 'https://github.com/codeistheway/java-project.git'
        sh "ant -f build.xml -v"
    }
    
    stage('Unit Tests'){
        sh "ant -f test.xml -v"
        junit 'reports/result.xml'
    }
    
    stage('Report'){
        sh "aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins"
    }
}
