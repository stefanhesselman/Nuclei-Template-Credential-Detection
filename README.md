# Nuclei-Template - Credential Detection

**I'm aware it does not cover ALL types of secrets. Just the ones I come across most often.**

A nuclei template that looks for specific credentials or secrets in the front-end markup of web applications. It looks for hardcoded credentials, API keys, authorization bearer tokens, cloud credentials and more.

A few years back, I've written this template as a result from past experience with credential detection - these are the most common secrets and credentials I have found. Since Nuclei has a more up-to-date database with Nuclei templates regarding this type of exposure, this is now here for learning purposes.

Cloud, payment, VCS and CI, messaging apps, private keys, JWTs, Firebase are supported. It also looks for secrets based on phrases such as 'secret','accessToken', 'apikey' and 'password'.

## Usage

```bash
# Single host
nuclei -t hardcoded-credentials-frontend.yaml -u https://your-target-host.com

# List of hosts
nuclei -t hardcoded-credentials-frontend.yaml -l targets.txt

# JSON output with extracted secrets
nuclei -t hardcoded-credentials-frontend.yaml -u https://your-target-host.com -json
```

## Sidenotes

- set `stop-at-first-match: false` so it keeps looking for secrets and credentials.
- Firebase API keys aren't really a security issue on their own. It depends on your context, so verify manually.
- Generic matchers (password, apiKey, etc.) require quoted values to reduce false positives.
