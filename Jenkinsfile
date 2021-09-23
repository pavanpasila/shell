pipeline {
 agent any

  stages {
    stage ("check in shell script") {
      steps {
        sh "mkdir target"
        sh "chmod 777 -R target"
        sh "find -L ./target -type f > delfile.txt"
        sh " sed -i 's/.\\/target\\//\\//g' delfile.txt"
        sh " sed -i 's/\\///'  delfile.txt"
      }
    }
  }
}
