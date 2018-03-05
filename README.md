# Hello World React :crescent_moon:

A simple `create-react-app` skeleton app used to test Google App Engine (GAE) deployment, along with Travis CI

# Steps

1. Run `create-react-app hello-world-react`
2. Install `google cloud sdk` if you prefer deploying using CLI compared to Travis or GAE Dashboard. [instructions here!](https://cloud.google.com/appengine/docs/flexible/nodejs/download)
3. Create app.yaml for configuring your GAE settings. [It can run with minimal settings, no worries!](https://cloud.google.com/appengine/docs/flexible/nodejs/configuring-your-app-with-app-yaml)
4. Install `travis-cli` if you haven't. [The ever fantabulous github repo](https://github.com/travis-ci/travis.rb)
5. Download your GAE *App*'s credential key from Dashboard > API & Services > create credential
6. Encrypt GAE *App*'s credential into Travis's .travis.yml using the command `travis encrypt secretCredential.json --add`
    - Do **NOT** commit the original credential file
    - **COMMIT ONLY** the generated secretCredential.json.enc file *(ignore .enc extension when configuring .travis.yml)*
7. Log into your Travis Account and link your Github Repository.
8. Commit and push your code to automation greatness.

# Fun fact and takeaways

1. `gcloud init` is not a per-project command. It's a global command used to init a new project in GAE, similar to creating a new repository in Git. Once you have created an *App* using the command, you may build multiple projects in it. *(Look at it like a server instance)* 
2. Once your service is deployed on GAE using Travis, the old version will be stopped.
    - This can be prevented by using `no_stop_previous_version` flag in Travis
    - If you have two versions of the same service running, you can split traffic in GAE's Dashboard, under *Versions*. Can be useful for non-demographically targeted AB Testing
3. GAE is PaaS, while Google Compute Engine (GCE) is Iaas. [What are the differences?](https://www.bmc.com/blogs/saas-vs-paas-vs-iaas-whats-the-difference-and-how-to-choose/)
4. For some reason Travis build process is a lot longer than simply running `gcloud app deploy`. It needs to be looked into.
5. Node JS can only use flexible environment on GAE, which will [incur higher cost!](https://cloud.google.com/appengine/docs/the-appengine-environments)
