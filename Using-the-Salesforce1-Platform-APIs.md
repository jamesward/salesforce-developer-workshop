---
layout: module
title: Module 12&#58; Using the Salesforce1 Platform APIs
---
In this module, you create an application that runs outside your Salesforce instance: it uses OAuth to authenticate with Salesforce, and the REST APIs to access Salesforce data.

## Requirement

You will need to [install Typesafe Activator](http://typesafe.com/platform/getstarted) to complete this module.

## Step 1: Create a New Java + Salesforce + REST App

1. Launch the Activator UI ([detailed instructions](http://typesafe.com/platform/getstarted))
1. Select **Seeds** and then select **Reactive Salesforce Seed with REST and JavaScript**
1. Select **Create** to create a new app from the seed
1. Open [localhost:9000](http://localhost:9000) in your browser and follow the instructions to setup OAuth
1. Once the setup is complete reload [localhost:9000](http://localhost:9000) in your browser and Login to Salesforce via your new app
    > Note: If you get a "error=invalid_client_id" error then wait a few minutes and try again.


## Step 2: Fetch the Sessions

1. In **Code** open `app/controllers/Application.java` and add a new method to fetch the Sessions:

    ```
    @Security.Authenticated(Secured.class)
    public static F.Promise<Result> getSessions() {
        F.Promise<JsonNode> sessions = SalesforceAPI.query(Secured.getToken(), Secured.getInstanceUrl(), "SELECT Id, Name, Session_Date__c FROM Session__c");
        return sessions.map(new F.Function<JsonNode, Result>() {
            @Override
            public Result apply(JsonNode jsonNode) throws Throwable {
                return ok(jsonNode);
            }
        });
    }
    ```

1. Open `conf/routes` and add a new route on line 8:

        GET        /sessions               controllers.Application.getSessions()

1. Test the new controller: [localhost:9000/sessions](http://localhost:9000/sessions)


## Step 3: Display the Sessions

1. In **Code** open `app/assets/javascripts/index.js` and change `contacts` on line 12 to `sessions` to fetch the new data
2. Open the `app/views/index.scala.html` file and change line 9 to:

        <li ng-repeat="contact in contacts">{{contact.Name}}</li>

3. Open the app and verify it is displaying the sessions: [localhost:9000](http://localhost:9000)


<div class="row" style="margin-top:40px;">
<div class="col-sm-12">
<a href="Batch-and-Schedule.html" class="btn btn-default"><i class="glyphicon glyphicon-chevron-left"></i> Previous</a>
<a href="next.html" class="btn btn-default pull-right">Next <i class="glyphicon glyphicon-chevron-right"></i></a>
</div>
</div>
