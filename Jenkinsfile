node {
    def mvnHome
   stage('Preparation') { // for display purposes
      // Get some couar ede from a GitHub repository
      git 'https://github.com/QASymphony/cucumber-sample.git'
      // Get the Maven tool.
      // ** NOTE: This 'M3' Maven tool must be configured
      // **       in the global configuration.           
      mvnHome = tool 'maven-3.6.1'
   }
   stage('Build') {
      // Run the maven build
      if (isUnix()) {
         sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean test"
      } else {
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean test/)
      }
   }
   stage('Results') {
      junit '**/target/**/*.xml'
      archive 'target/*.jar'
   }
    stage('qTestLog') {
      submitJUnitTestResultsToqTest([apiKey: '1358c9c4-1cb6-48a6-b535-ca557e3448fd', containerID: 465292, containerType: 'release', createTestCaseForEachJUnitTestClass: true, createTestCaseForEachJUnitTestMethod: false, environmentID: 52214, overwriteExistingTestSteps: true, parseTestResultsFromTestingTools: false, projectID: 93854, qtestURL: 'https://qas.qtestnet.com', submitToAReleaseAsSettingFromQtest: true, submitToExistingContainer: false, utilizeTestResultsFromCITool: true])
    }
}
