# Infrastructure security in Amazon OpenSearch Service<a name="infrastructure-security"></a>

As a managed service, Amazon OpenSearch Service is protected by the AWS global network security procedures that are described in [Amazon Web Services: Overview of Security Processes](https://d0.awsstatic.com/whitepapers/Security/AWS_Security_Whitepaper.pdf)

You use AWS published API calls to access the OpenSearch Service configuration API through the network\. Clients must support Transport Layer Security \(TLS\) 1\.0 or later\. We recommend TLS 1\.2 or later\. To configure the minimum required TLS version to accept, specify the `TLSSecurityPolicy` value in the domain endpoint options\. For details, see the [AWS CLI Command Reference](https://docs.aws.amazon.com/cli/latest/reference/opensearch/create-domain.html)\.

Clients must also support cipher suites with perfect forward secrecy \(PFS\) such as Ephemeral Diffie\-Hellman \(DHE\) or Elliptic Curve Ephemeral Diffie\-Hellman \(ECDHE\)\. Most modern systems such as Java 7 and later support these modes\.

Additionally, requests to the configuration API must be signed by using an access key ID and a secret access key that is associated with an IAM principal\. Or you can use the [AWS Security Token Service](https://docs.aws.amazon.com/STS/latest/APIReference/Welcome.html) \(AWS STS\) to generate temporary security credentials to sign requests\.

Depending on your domain configuration, you might also need to sign requests to the OpenSearch APIs\. For more information, see [Making and signing OpenSearch Service requests](ac.md#managedomains-signing-service-requests)\.

OpenSearch Service supports public access domains, which can receive requests from any internet\-connected device, and [VPC access domains](vpc.md), which are isolated from the public internet\.