node {
    checkout scm
    stage('Build') {
       sh "mvn -B clean package"
       archive "target/sky-launch-*.jar"
       junit 'target/surefire-reports/*.xml'
    }
}
stage ("Test") {
    parallel (
        "Code Static Analysis": {
            node {
                echo "analyze..."
            }
        },
        "Web Browser Tests": {
            node {
                echo "test..."
            }
        }
    )
}