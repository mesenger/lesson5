node('master') {
    stage("Fetch Source Code") {
    	cleanWs()
        git 'https://github.com/mesenger/lesson5.git'
    }
    
    dir('.') {
        printMessage('Running Pipeline')
        stage("Testing") {
	    sh 'ls -la'
	    sh 'apk add python'
            sh 'python test_functions.py'
        }
        stage("Deployment") {
            if (env.BRANCH_NAME == 'master') {
                printMessage('Deploying the master branch')
            } else {
                printMessage("No deployment for branch [${env.BRANCH_NAME}]")
            }
            
        }
        printMessage('Pipeline Complete')
    }
}

def printMessage(message) {
    echo "${message}"
}
