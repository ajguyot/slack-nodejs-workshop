# Slack SmartThings Integration

### Local Setup

* Git
    * [Install git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
    * Clone this repo or a fork locally
        * `git clone git@github.com:SmartThingsCommunity/slack-nodejs-workshop.git`
    * Checkout the start branch
        * `git checkout start`
* Node
    * [Install node](https://nodejs.org)

### AWS Setup

* Create [AWS Account](https://portal.aws.amazon.com/billing/signup?redirect_url=https%3A%2F%2Faws.amazon.com%2Fregistration-confirmation#/)
* Install and configure [aws-cli](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html)
    * Credit card is required, but we will be using services offered in the free tier
        * S3 isn't free, but is optional and rather cheap

### SmartThings Setup in Browser

* Create a Simulated RGB Bulb
    * Navigate to the [legacy developer portal](https://graph-na04-useast2.api.smartthings.com/location/list)
    * Enter `Simulated RGB Bulb` for `Name`
    * Enter  `Simulated RGB Bulb` for `Device Network Id`
    * Select `Simulated RGB Bulb` for `Type`
    * Select one of your locations to install the device on
       * If no locations navigate to [location list](https://graph-na04-useast2.api.smartthings.com/location/list), this will redirect you to the correct shard
    * Click `Create`
    
> You should be able to modify the state (on/off, color) of this
simulated device through the UI in the mobile application.
This will be useful for testing your integration

### SmartThings Setup in App

* Download and open the iOS/Android SmartThings Mobile App
    * Log into your Samsung Account
        * [Create one](https://account.samsung.com/accounts/v1/MBR/terms#) if you haven't already
    * [Enable Developer Mode](https://smartthings.developer.samsung.com/docs/guides/testing/developer-mode.html) (required for running custom automations)

### Slack Setup
* Navigate to your [Slack Apps](https://api.slack.com/apps)
    * If you don't have a Slack workspace yet, click `sign in to your Slack account` and then `Create a new workspace` ([here](https://slack.com/create#email))
    * Input an email for your workspace, then input the 6 digit code that Slack will email to you
    * Give your workspace a name, like `SmartThings IoT Fuse`
    * For a project name, go with something like `SmartThings-Slack`
    * Skip adding teammates
    * Your workspace is created! You can log into it in the Slack app for desktop or just keep it open in a browser tab
* Click `sign into your Slack account`
    * After signing in you'll need to navigate back to https://api.slack.com/apps
* Click `Create New App`
    * Name the app `ThingsBot`
    * For Development Slack Workspace, select the workspace you just logged into from the drop down
    * Create the app
* Scroll to the bottom of the Basic Information section for your app
    * Under Display Information, click `Add app icon`
        * Upload [this bot icon image](etc/ThingsBot.png) from this repo to give your ThingsBot some identity
        (feel free to find your own bot face image if you'd prefer)
* Navigate to `Install App` in the Slack API website sidebar
    * Click Install App to Workspace
    * Authorize the app
* Navigate to `OAuth & Permissions` in the Slack API website sidebar
    * Click "Add New Redirect URL"
    * Add your API Gateway URL as a redirect URL
    * Click `Save URLs`
* Navigate to `Interactive Components` in the Slack API website sidebar
    * Flip the Interactivity switch to On
    * For the Request URL, input `<YOUR_API_GATEWAY_URL>/slack/receive`
    * Click `Save Changes`

[cd lambda](lambda/README.md)
