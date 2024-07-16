Pipeline {
    agent { label 'new_node' }
    triggers { pollSCM('H/10 * * * *') }
    stages {
        stage('vcn') {
            steps {
                git url: 'https://github.com/wakaleo/game-of-life.git'
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