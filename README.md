# coderhubK8s
Team JupyterHub instance that provides Code-Server image.

Based on the work of [@nils-braun](https://github.com/nils-braun/codehub), I tweaked the chart values a bit, and added support for docker-in-docker

In an ideal world, you would grant your team the ability to create PRs against this repo to:
- Create their own containers
- Create their own Profiles
You could use coder directly, if most of your team only needs to consume vs create their own custom environment... this works better:
    - "If you have access to our github org, you can pull up an IDE"
___

I'm using this as a teaching aid - the hardest part of any course is Day One - Setup your Environment. This absctracts all those problems away for me.

Workflows could use some tuning, but this works for me. All I need to do is:
- Configure an ARC runner for the repo
- Create a cloudflared tunnel
- Update ./podspec/cloudflared.yaml to have correct endpoint + tunnel name
- Create secrets in the namespace I'll be deploying to
    - cloudflared.json
    - Github Container Registry Token
- Configure Github Actions Secrets
    - chp random seed
    - GithubApp credentials
    - kube.config
- Run the deploy actions
---

#TODO - Cleanup the default workspace action so that instead of loading the home directory, we open a "projects" directory. This de-clutters the explorer view
