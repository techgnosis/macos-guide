You use the `security` CLI



security add-trusted-cert -d -p ssl -p basic mitmproxy-ca-cert.pem

security remove-trusted-cert -d mitmproxy-ca-cert.pem

security dump-trust-settings -d
