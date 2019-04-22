node('linux'){
    stage('Build'){
        git 'https://github.com/codeistheway/java-project.git'
        sh "ant -f build.xml -v"
    }
    
    stage('Unit Tests'){
        sh "ant -buildfile test.xml"
    }
    
    stage('Report'){
        junit 'reports/*.xml'
    }
}
