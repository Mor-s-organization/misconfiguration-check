withCredentials([
  string(credentialsId: 'AQUA_KEY_3', variable: 'AQUA_KEY'),
  string(credentialsId: 'AQUA_SECRET_3', variable: 'AQUA_SECRET'),
  string(credentialsId: 'GITHUB_TOKEN_3', variable: 'GITHUB_TOKEN')]        
  ) {
  sh '''
  export TRIVY_RUN_AS_PLUGIN=aqua
  export trivyVersion=0.34.0
  export AQUA_URL=https://api.dev.supply-chain.cloud.aquasec.com
  export CSPM_URL=https://stage.api.cloudsploit.com
  curl -sfL https://raw.githubusercontent.com/aquasecurity/trivy/main/contrib/install.sh | sh -s -- -b . v${trivyVersion}
  ./trivy plugin install github.com/Mor-s-organization/trivy-plugin-version
  ./trivy fs --security-checks config,vuln,secret .
  # Customizing which severities are scanned for is done by adding the following flag: --severity UNKNOWN,LOW,MEDIUM,HIGH,CRITICAL
  '''
 }