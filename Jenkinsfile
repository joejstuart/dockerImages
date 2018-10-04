def linchpin_version = env.TAG_NAME

def containers = ['ansible-executor']
def test_cmd = "echo testing..."
def image_name = 'fedora'
def build_root = "Dockerfiles/${image_name}"
def credentials = [usernamePassword(credentialsId: 'contra-sample-project-joejstuart-github',
                                                usernameVariable: 'USERNAME',
                                                passwordVariable: 'PASSWORD')]


podTemplate = [containers: containers,
               docker_repo_url: '172.30.1.1:5000',
               openshift_namespace: 'contra-sample-project',
               podName: 'generic',
               jenkins_slave_image: 'jenkins-contra-sample-project-slave']




deployOpenShiftTemplate(podTemplate) {
    ciPipeline(sendMetrics: false, decorateBuild: decoratePRBuild()) {


        def release = 'latest'
        if (linchpin_version) {
            testRelease(installCmd: "echo installing...",
                        verifyCmd: "echo verifying...",
                        repo: 'joejstuart/dockerImages',
                        version: linchpin_version,
                        credentials: credentials)
            release = linchpin_version
        }

        // add linchpin version
        // linchpin version will either be latest/source/version number
        // on every run, build latest with the PR version
        buildTestContainer(test_cmd: test_cmd,
                           build_root: build_root,
                           image_name: image_name,
                           docker_namespace: 'jjstuart79',
                           credentials: credentials,
                           buildContainer: 'ansible-executor',
                           release: release)

        // call linchpin test job
        // review 
        // [merge] to develop, push container to latest


    }
}

