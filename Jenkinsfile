Pipeline {
    agent { label 'JDK_17' }
    triggers { pollSCM('* * * * *') }
    stages {
        stage('vcn') {
            steps {
                git url: 'https://github.com/wakaleo/game-of-life.git',
                    branch: 'new1'
            }
        }
        stage('build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('post bulid actions')  {
            steps {
                archiveArtifacts artifacts: '**/gameoflife.war'
                junit testResults: '**/Test-*.xml'
            }
        }
    }
}