pipeline
{
agent any
stages
{
  stage('scm checkout')
    { steps {  git branch: 'master', url: 'https://github.com/prakashk0301/maven-project/'

            }
    }

   stage('compile source code')
   {   steps {  
           withMaven(jdk: 'localjava', maven: 'localmaven') 
                {
                   sh 'mvn compile'
                 }  
              } 
   } 
        stage('build source code')
     {  steps 
         {  
            withMaven(jdk: 'localjava', maven: 'localmaven') 
             {
             sh 'mvn package'
              }
         }
      } 
     stage('archive artifact')
     {
        steps
             {
              archiveArtifacts '**/*.war'	
              }
     }
       stage('deploy the container')
       { 
           steps
               {
                 deploy adapters: [tomcat7(credentialsId: 'tomcat7', path: '/var/lib/tomcat/webapps/webapp', url: 'http://54.175.88.96:8080/')], contextPath: null, war: '**/*.war'
                }
        }
    }
}
