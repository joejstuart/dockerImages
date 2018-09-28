def containers = ['ansible-executor']
def version = '0.0.1'
def test_cmd = "echo testing..."
def image_name = 'fedora'
def build_root = "Dockerfiles/${image_name}"
def credentials = [usernamePassword(credentialsId: 'contra-sample-project-docker-credentials',
                                                usernameVariable: 'DOCKER_USERNAME',
                                                passwordVariable: 'DOCKER_PASSWORD')]

modifyArgs = [owner: '1000:0', items: [['blah', '/tmp'], ['test', '/tmp']]]
podTemplate = [containers: containers,
               docker_repo_url: '172.30.1.1:5000',
               openshift_namespace: 'contra-sample-project',
               podName: 'generic',
               jenkins_slave_image: 'jenkins-contra-sample-project-slave']

buildTestContainer(podTemplateProps: podTemplate,
                   version: version,
                   test_cmd: test_cmd,
                   build_root: build_root,
                   image_name: image_name,
                   send_metrics: false,
                   docker_namespace: 'jjstuart79',
                   credentials: credentials,
                   modify_args: modifyArgs)

