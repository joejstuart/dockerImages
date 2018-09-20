def containers = ['ansible-executor']
def version = '0.0.1'
def test_cmd = """
echo testing...
"""
def image_name = 'fedora'
def build_root = "Dockerfiles/${image_name}"

podTemplate = [containers: containers, docker_repo_url: '172.30.1.1:5000', openshift_namespace: 'contra-sample-project', podName: 'jenkins-build']

buildTestContainer(podTemplate: podTemplate,
                   version: version,
                   test_cmd: test_cmd,
                   build_root: build_root,
                   docker_registry: 'docker.io',
                   docker_namespace: 'jjstuart79')

