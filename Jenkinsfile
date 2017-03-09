node {
    stage("build & unit tests") {
        node('build') {
            echo "build & tests"
            sleep 5
        }
    }
    stage("static-analysis") {
        node('build') {
            echo "analysis"
            sleep 2
        }
    }
    stage("acceptance-test") {

        parallel "chrome": {
            node {
                sleep 5
            }
        }, "edge": {
            node {
                sleep 5
            }
        }, "firefox": {
            node {
                sleep 5
            }
        }, failFast: true
    }
    stage ("staging"){
        node('build') {
            echo "Staging"
            sleep 5
        }
    }
    stage ("manual-approval"){
        input "Déploiement en production ?"
    }
    stage ("deploy"){
        node('build') {
            echo "deploy"
            sleep 5
        }
    }
}
