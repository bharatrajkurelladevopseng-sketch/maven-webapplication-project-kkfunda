node
{
    def mavenhome = tool "maven-3.9.16"
       stage('git checkout')
    {
       git 'https://github.com/bharatrajkurelladevopseng-sketch/maven-webapplication-project-kkfunda.git'
    }

        stage('compile')
    {
        sh "${mavenhome}/bin/mvn compile"
    }
        stage('build')
    {
        sh "${mavenhome}/bin/mvn clean package"
    }
        stage('SonarQube report')
    {
        sh "${mavenhome}/bin/mvn sonar:sonar"
    }
            stage('nexus')
    {
        sh "${mavenhome}/bin/mvn deploy"
    }
    stage('Deploy to Tomcat')
    {
    sh """
        curl -u bharat:bharat \
        --upload-file target/maven-web-application.war \
        "http://44.222.203.122:8080/manager/text/deploy?path=/maven-web-application&update=true"
    """
     }
}
