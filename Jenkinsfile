#!groovy

node('soapuislave') {

	    currentBuild.result = "SUCCESS"

	try{
		stage 'Checkout'
		checkout scm
		echo "Checked out the project"

		//stage 'Start Bol Rest Test'
		//sh "curl --form \"project=@Bol-soapui-project.xml\" --form \"suite=Bolsuite\" http://soapui:3000"

		//stage 'Start Soap Test'
		//sh "curl --form \"project=@BLZ-soapui-project.xml\" --form \"suite=Banksuite\" http://soapui:3000"

		stage 'Archive Results'
		//step([$class: 'JUnitResultArchiver', testResults: 'TEST-*.xml'])

	}
	   catch (InterruptedException x) {
      currentBuild.result = "ABORTED"
  } catch (e) {
      currentBuild.result = "FAILED"
      throw e
  }
}