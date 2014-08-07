---
layout: module
title: Using Heroku Connect
---

## Create a new Heroku Connect App

1. Create a new app using the [salesforce-developer-workshop-java](http://typesafe.com/activator/template/salesforce-developer-workshop-java) template:

        activator new hello-heroku-connect salesforce-developer-workshop-java

2. Change to the newly created `hello-heroku-connect` directory:

        cd hello-heroku-connect

3. Initialize a git repo in your project's root directory:

        git init

4. Stage the project files to be added to the repo:

        git add .

5. Commit your files:

        git commit -m "init"

6. Create a new app on Heroku:

        heroku create

7. Deploy the app:

        git push heroku master

    Note: This pushes your source code and then builds it from scratch on Heroku so it will take a few minutes.  Subsequent deploys are faster.

8. Add the Heroku Connect Add-on:

        heroku addons:add herokuconnect

9. Setup Heroku Connect:

        ???

10. Verify the app works on Heroku:

        heroku open

    You should now see the sessions from your Salesforce app.

<!-- TODO: Add some customizations to this app. -->

<div class="row" style="margin-top:40px;">
<div class="col-sm-12">
<a href="Creating-a-Heroku-App.html" class="btn btn-default"><i class="glyphicon glyphicon-chevron-left"></i> Previous</a>
</div>
</div>
