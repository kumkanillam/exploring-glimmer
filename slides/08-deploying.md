## Deploying a Glimmer App

Uses exact same tooling as Ember,<br>
can deploy application via EmberCLI

Note: 
Showing steps for deployment to `gh-pages`

----

### Setup

Install deployment packages

```
ember install ember-cli-deploy  
ember install ember-cli-deploy-build  
ember install ember-cli-deploy-git 
```

----

### Update Configuration

Update `config/deploy.js` to add a the `git` key

```
ENV.git = {  
  repo: 'git@github.com:username/repo.git',
  branch: 'gh-pages',
  worktreePath: '/tmp/deploy'
};
```

----

### Initialize `gh-pages` branch

```
git checkout --orphan gh-pages  
git rm -rf .  
git commit --allow-empty --message="Initial commit"  
```

----

### Deploy!

```
ember deploy production 
```

<span class="small">Thanks for [Robert Jackson](https://twitter.com/rwjblue) for the [quick writeup](http://rwjblue.com/2017/04/18/deploying-glimmer-apps/), and for pointing out that it was the exact same method used for Ember apps</span>