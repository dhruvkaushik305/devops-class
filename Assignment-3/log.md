Started by an SCM change
Running as SYSTEM
Building in workspace /var/lib/jenkins/workspace/assignment-3
The recommended git tool is: NONE
No credentials specified
 > git rev-parse --resolve-git-dir /var/lib/jenkins/workspace/assignment-3/.git # timeout=10
Fetching changes from the remote Git repository
 > git config remote.origin.url https://github.com/dhruvkaushik305/spring3hibernate.git # timeout=10
Fetching upstream changes from https://github.com/dhruvkaushik305/spring3hibernate.git
 > git --version # timeout=10
 > git --version # 'git version 2.34.1'
 > git fetch --tags --force --progress -- https://github.com/dhruvkaushik305/spring3hibernate.git +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git rev-parse refs/remotes/origin/master^{commit} # timeout=10
Checking out Revision e6401d1eb452466c0bfc7010f062397caec60974 (refs/remotes/origin/master)
 > git config core.sparsecheckout # timeout=10
 > git checkout -f e6401d1eb452466c0bfc7010f062397caec60974 # timeout=10
Commit message: "Update README.md"
 > git rev-list --no-walk 82d59771f414e2ea2583b200e688d2878c98cb29 # timeout=10
[assignment-3] $ /bin/sh -xe /tmp/jenkins9993317864671558946.sh
+ wc -w README.md
272 README.md
Finished: SUCCESS

