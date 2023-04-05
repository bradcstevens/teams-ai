# Teams Conversation Bot

Bot Framework v4 Conversation Bot sample for Teams.

This bot has been created using [Bot Framework](https://dev.botframework.com). This sample shows
how to incorporate basic conversational flow into a Teams application. It also illustrates a few of the Teams specific calls you can make from your bot.

## Prerequisites

-   Microsoft Teams is installed and you have an account
-   [NodeJS](https://nodejs.org/en/) (version 16.x)
-   [ngrok](https://ngrok.com/) or equivalent tunnelling solution

## To try this sample

> Note these instructions are for running the sample on your local machine; the tunnelling solution is required because the Teams service needs to call into the bot.

1. Clone the repository

    ```bash
    git clone https://github.com/Microsoft/botbuilder-m365.git
    ```

1. In the root JavaScript folder, install and build all dependencies

    ```bash
    cd botbuilder-m365/js
    yarn install
    yarn build
    ```

    - If you already ran `yarn install` and `yarn build` in the `js` folder, you are ready to get started with ngrok. Otherwise, you need to run `yarn install` and `yarn build` in the `js` folder.

1. In a terminal, navigate to `samples/js/samples/messaging/echoBot`

    ```bash
    cd samples/js/samples/messaging/echoBot
    ```

1. Run ngrok tunneling service - point to port 3978

    ```bash
    ngrok http --host-header=rewrite 3978
    ```

1. Create [Bot Framework registration resource](https://docs.microsoft.com/en-us/azure/bot-service/bot-service-quickstart-registration) in Azure

    - Use the current `https` URL you were given by running ngrok. Append with the path `/api/messages` used by this sample.
    - Ensure that you've [enabled the Teams Channel](https://docs.microsoft.com/en-us/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0)
    - **_If you don't have an Azure account_** you can use this [Bot Framework registration](https://docs.microsoft.com/en-us/microsoftteams/platform/bots/how-to/create-a-bot-for-teams#register-your-web-service-with-the-bot-framework)

1. Update the `.env` configuration for the bot to use the Microsoft App Id and App Password from the Bot Framework registration. (Note the App Password is referred to as the "client secret" in the azure portal and you can always create a new client secret anytime.)

1. **_This step is specific to Teams._**

    - **Edit** the `manifest.json` contained in the `teamsAppManifest` folder to replace your Microsoft App Id (that was created when you registered your bot earlier) _everywhere_ you see the place holder string `<<YOUR-MICROSOFT-APP-ID>>` (depending on the scenario the Microsoft App Id may occur multiple times in the `manifest.json`). If you haven't created an Azure app service yet, you can use your bot id for the above. You're bot id should be pasted in where you see `___YOUR BOTS ID___`
    - **Zip** up the contents of the `teamsAppManifest` folder to create a `manifest.zip`
    - **[Sideload the app](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/deploy-and-publish/apps-upload) (manifest zip) file** the `manifest.zip` to Teams (in the Apps view click "Upload a custom app")

1. Run your bot at the command line:

    ```bash
    yarn start
    ```

1. [Sideload the app](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/deploy-and-publish/apps-upload) (manifest zip) file in Teams.

## Interacting with the bot

You can interact with this bot by sending it a message, which will echo back to you.

## Deploy the bot to Azure

To learn more about deploying a bot to Azure, see [Deploy your bot to Azure](https://aka.ms/azuredeployment) for a complete list of deployment instructions.

## Further reading

-   [How Microsoft Teams bots work](https://docs.microsoft.com/en-us/azure/bot-service/bot-builder-basics-teams?view=azure-bot-service-4.0&tabs=javascript)