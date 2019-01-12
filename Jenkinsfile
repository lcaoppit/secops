node{
   stage('SCM Checkout'){
     git 'https://github.com/lcaoppit/devsecops'
   }
   stage('Compile-Package'){
      // Get maven home path
      def mvnHome =  tool name: 'maven-3', type: 'maven'   
      sh "${mvnHome}/bin/mvn package"
   }
   stage('Email Notification'){
      mail bcc: '', body: '''Hi Welcome to jenkins email alerts
      Thanks
      WFoster''', cc: '', from: '', replyTo: '', subject: 'Jenkins Job', to: 'lca.luisaraujo@gmail.com'
   }
   stage('Slack Notification'){
       slackSend baseUrl: 'https://hooks.slack.com/services/', 
       channel: 'devsecops', 
       color: 'good', 
       message: 'Jenkins + SonarQube', 
       teamDomain: 'oppit', 
       tokenCredentialId: 'slack'
   }
}

