
# Github actions commands

* To executes the github actions we have following steps
1. workflow/pipline
2. jobs
3. steps
4. commands

* till so far in the command parts we are seeing the linux command also we can use windows or macos command but now we will see the github actions command provided by the github.

** Github actions commad is a predefined operaton that is done as a step in a job.
Example : 

        * suppose we have a runner machine hosted by github somewhere on cluod and inside this there is a linux operating system(OS), and we want to setup or ruby & rails project on this runner machine

        - ruby ---> language
        - rails ---> framework

        1. we have to install ruby
        2. and install rails

**Problem**

* Suppose in our organisation we have 20 different-different nodejs or ruby & rails projects and if we want to setup it on the linux machine through the command in each project then it will take time and also the project setup may be changes with time if any changes happen then on that time we have to change in all the project manually, so it's not a good where we have several projets.

**solution**

* To solve this problem there is some github actions available which setup these types of projcet in single command like the to setup the : 
1. nodejs mono repo we use command ---> encore-mieux/setup-monorepo-node-app
2. ruby & rails setup ----> ruby/setup-ruby-pkgs@v1
3. python setup uses: actions/checkout@v5

* actually these are in below format but only we have to use the uses command :
```yml
steps:
- uses: actions/checkout@v5
- uses: actions/setup-python@v6
  with:
    python-version: '3.13' 
- run: python my_script.py
```

* for node js
```yml
- name: ejson action
  uses: Drafteame/node-cache-action@main
  with:
    node-version: '20' # nodejs version
    working-directory: cmd # path where the npm install command is run.
    cache-key-suffix: suffix # Optional cache key suffix
```

* So in future if any project setup configuration settings changes then we don't have to mind jus we have to use the above command.

* github actions : it's the whole workflow/jobs/steps
* github action : predefiend operation 