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
}
}
