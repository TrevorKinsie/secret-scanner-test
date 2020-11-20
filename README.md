# secret-scanner-test
Test of Secret-Scanner

## installation of secret-scanner

### prerequisites 

you will need to have go installed

`brew install go`

### installation

clone the repository

`git clone git@github.com:grab/secret-scanner.git`

change into the correct directory: `cd cmd/secret-scanner`

build: `go build`

you can then copy the finished binary to wherever you'd like (somewhere on your PATH is best):

`cp secret-scanner /usr/local/bin/secret-scanner`

create a personal token with no privileges: https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github/creating-a-personal-access-token

export it: `GITHUB_TOKEN=<yourpersonalaccesstoken>`

## results

### running the command
run the command on any repo you have access to (including public)

`secret-scanner -repos TrevorKinsie/WebGoat`

### output
```
Github Scanning Started at 2020-11-20T08:47:47-05:00
Loaded 121 signatures
 Retrieved repository: TrevorKinsie/WebGoat
 Retrieved 1 repository from github
Analyzing 1 repository...
 PATH SCAN: Contains OAuth token
  Path........: webgoat-lessons/jwt/src/main/resources/images/logs.txt
  Repo........: TrevorKinsie/WebGoat
  Author......:
  Comment.....:
  File URL....: https://api.github.com/repos/TrevorKinsie/WebGoat/blob/develop/webgoat-lessons/jwt/src/main/resources/images/logs.txt
  Line........: 2
 ------------------------------------------------

 PATH SCAN: Potential cryptographic key bundle
  Path........: webgoat-container/src/main/resources/goatkeystore.pkcs12
  Repo........: TrevorKinsie/WebGoat
  Author......:
  Comment.....:
  File URL....: https://api.github.com/repos/TrevorKinsie/WebGoat/blob/develop/webgoat-container/src/main/resources/goatkeystore.pkcs12
  Line........: 0
 ------------------------------------------------

 PATH SCAN: Contains OAuth token
  Path........: webgoat-lessons/jwt/src/main/resources/html/JWT.html
  Repo........: TrevorKinsie/WebGoat
  Author......:
  Comment.....:
  File URL....: https://api.github.com/repos/TrevorKinsie/WebGoat/blob/develop/webgoat-lessons/jwt/src/main/resources/html/JWT.html
  Line........: 248
 ------------------------------------------------

Gitlab Scanning Finished at 2020-11-20T08:48:12-05:00

Findings....: 3
Files.......: 0
Commits.....: 0
Repositories: 1
Targets.....: 1
```

1. https://github.com/TrevorKinsie/WebGoat/blob/b6aa6775947b842803841cdbade8400bf81c07cf/webgoat-lessons/jwt/src/main/resources/images/logs.txt#L2
2. https://github.com/TrevorKinsie/WebGoat/blob/develop/webgoat-container/src/main/resources/goatkeystore.pkcs12
3. https://github.com/TrevorKinsie/WebGoat/blob/b6aa6775947b842803841cdbade8400bf81c07cf/webgoat-lessons/jwt/src/main/resources/html/JWT.html#L248
