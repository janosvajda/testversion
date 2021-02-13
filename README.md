How to create bugfix/feature and deploy it?

We use the semantic versioning.

https://semver.org/

We use these versions:

major | minor | patch

1. create a new branch from the master branch:

git checkout -b"JIRA-TICKET-NUMBER-short-description"

2. If you think you are done and it is QA tested, and unit tests and UI tests are ok. Then you must create a PR. 

3. If it approved and merged into master then you should do these steps:

- Delete your develop branch (because it is in master branch now) git branch -D JIRA-TICKET-NUMBER-short-description and delete its remote version on GitHub as well.
- git checkout master
- git pull
- Go to AWS s3 and download the latest version of pre-production version of the app. It is in the "qtoolbar-installer-pre-prod" bucket. Install it. (Pre production is NOT a staging. It is exactly the same like the prod build. It uses the prod Q doctor API server. It is just deployed to a different S3 bucket: "qtoolbar-installer-pre-prod")
-  
- Build a new pre-production release of the app.