node {
    stage ('Preparation'){
        checkout scm
    }
    stage ('Build'){
        sh 'docker run -i -v $PWD:/usr/src/mymaven -w /usr/src/mymaven --rm maven:3-jdk-8 mvn clean package'

    }
    stage ('Test'){
        sh 'docker run -i -v $PWD:/usr/src/mymaven -w /usr/src/mymaven --rm maven:3-jdk-8 mvn test'

    }
    stage ('Javadoc'){
        echo 'Ladidadida ... computing ... javadoc generated ... speculating ... contemplating ... *javadoc archived successfully*'
    }
    stage ('Results'){
        archiveArtifacts artifacts: 'target/gildedrose-*.jar', onlyIfSuccessful: true
        
    }
}
