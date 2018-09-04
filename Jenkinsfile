#!/usr/bin/groovy
@Library('github.com/piyush1594/fabric8-pipeline-library@newnodejs')
def canaryVersion = "1.0.${env.BUILD_NUMBER}"
def utils = new io.fabric8.Utils()
def stashName = "buildpod.${env.JOB_NAME}.${env.BUILD_NUMBER}".replace('-', '_').replace('/', '_')
def envStage = utils.environmentNamespace('stage')
def envProd = utils.environmentNamespace('run')
def setupScript = null


osio {
    cd {
      spawn (version: "latest") {
        sh """
          which --help
          oc version
          git help -g
          tar --help
          zip -h
          unzip -h
          npm version
          node --version
        """
      }
    }
}
