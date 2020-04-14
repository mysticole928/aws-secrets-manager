# Storing a PEM file to AWS Secrets Manager

I've found that, when using the console, getting a PEM key into Secrets Manager can be cumbersome. 

I just want to store the file as an artifact.  I don't really want a key/value store.

Using the CLI makes the process much easier.  The entire file is uploaded at once.  

There's no issue with newlines or other special characters.

```bash
aws secretsmanager create-secret --region REGION-ID --name NAME_OF_SECRET --secret-string file://YOUR_PEM_FILE.pem
```

To retrieve the PEM, use this command:

```bash
aws secretsmanager get-secret-value --secret-id NAME_OF_SECRET --region REGION --output json
```

However, if you want to store the output as a file, use jQuery.  (You might have to install it.)

Be sure that the `--output` is set to `json` and that you add the option `--raw-output`.


```bash
aws secretsmanager get-secret-value --secret-id NAME_OF_SECRET --region REGION --output json | jq '.SecretString' --raw-output > sshfile.pem
```
