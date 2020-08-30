node {
    def app

    stage(Clone repository){
        git  'https://github.com/drsureshbrathod/web_login_automation.git'
    }

    stage('Build image')   {
                app = docker.build("drsureshbrathod/myrepo:${env.BUILD_NUMBER}")
            }
    stage("Test image"){
        
        app.inside{
            sh.echo ' "Test passed'
        }
    stage('Push image'){
            docker.WithRegistry('registry.hub.docker.com','363c3585-5530-4e49-8f8d-7b012c604bef'){
            app.push()
            }
    }
    }
           
        
}
