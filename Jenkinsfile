pipeline {
 agent any

  stages {
    stage ("check in shell script") {
      steps {
        sh "mkdir -p target/a.b.c"
        sh "touch target/a.b.c/test.sql"
        sh "chmod 777 -R target/"
        sh "find -L ./target -type f > delfile.txt"
        sh "cat delfile.txt"
        sh " sed -i 's/.\\/target\\//\\//g' delfile.txt"
        sh "cat delfile.txt"
        sh " sed -i 's/\\///'  delfile.txt"
        sh "cat delfile.txt"
      }
    }
   stage ("delete lower branch files") {
    steps {
     sh label: '', script: '''echo \'while  read -r line
					do
                    find . -name "$line" -delete
					done <delfile.txt \' > del.sh'''
				
				sh "sh del.sh"
				sh "rm -rf delfile.txt del.sh"
    }
   }
  }
}
