Pipeline {
    agent { label 'new_node' }
    triggers { pollSCM('H/5 * * * *') }
    stages {
        stage('vcn') {
            steps {
                git url: 'https://github.com/wakaleo/game-of-life.git',
                    branch: 'declarative'
            }
        }
        stage('build') {
            steps {
                sh 'mvn package'
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