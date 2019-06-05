pipeline { 
    agent any
    parameters {
        string(name: 'jenkins_branch', defaultValue: 'jenkins', description: 'Jenkins Branch')
        string(name: 'git_repo', defaultValue: 'git@github.com:moongs1/sa.it.git', description: 'Git repository')
    } 

    stages {
       stage('Clone repository') { 
            steps { 
                git url: "${params.git_repo}", branch: "${params.jenkins_branch}"
            }
        }


       stage('Checking  repository'){
            steps { 
                sh "ls -l"
            }
        }

       stage('Date') {
            steps {
                sh '''
                
                echo "date" >date.txt
                '''
            }
       }


       stage('Git push Date'){
            steps {
                sh "git add --all"
                sh "git commit -m 'System date'"         
                sh "git push origin ${params.jenkins_branch}" 
               }
            
        }
       stage('delete Date'){
            steps {
                sh "git rm date.txt "
                sh "git commit -m 'delete date'"         
                sh "git push origin ${params.jenkins_branch}" 
               }
            
        }
        
        
    }
    

    
}
