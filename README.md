# Edge Delivery Services - WKND Demo
Codebase for the fictional WKND site, showcasing the capabilities of Adobe's Edge Delivery Services. Highlights include:

- Experimentation capabilities 
- Conversion tracking
- Slack Bot integration for monitoring Lighthouse score and conversions 
- Document based content authoring

## Environments
- Preview: https://main--wknd--hlxsites.hlx.page/
- Live: https://main--wknd--hlxsites.hlx.live/

## Installation

```sh
npm i
```

## Tests

```sh
npm tst
```

## Capabilities

Before you begin, ensure you have the [AEM Sidekick Chrome extension](https://chrome.google.com/webstore/detail/aem-sidekick/ccfggkjabjahcjoljmgmklhpaccedipo) installed.

### Experimentation
[Experimentation docs](https://www.hlx.live/docs/experimentation)

- Load the site's Preview URL (above)
- Note the green "Experiment" pill-shaped button in the bottom right corner
- Click the button to open the Experimentation UI
- Click the "Simulate" button next to an experiment to view how that variant will render for the end user

<img src="/docs/images/experiment-simulate.png" width="300" alt="Experimentation UI opened from the green pill-shaped button">

- To see how this experiment is configured, right-click on the AEM Sidekick extension and select "View document source"
- Scroll down to the Metadata block at the bottom of the document
- Note the Experiment, and Instant Experiment properties
- The Instant Experiment property defines the pages used for the "challenger" variants in the Experimentation UI

<img src="/docs/images/experiment-metadata.png" width="500" alt="The document source which configures the experiments">

### Conversion Tracking
[RUM docs](https://www.hlx.live/developer/rum)

- You will need to fork this repository in order to access "Real User Monitoring" (RUM) data, including conversion data, via the Slack Bot
- In your fork, point fstab.yaml to a SharePoint or Google Drive folder that you own. Extract and upload documents.zip to seed this folder with content
- Install the Github bot on your forked repository using this link: https://github.com/apps/helix-bot/installations/new
- Using the AEM sidekick, publish the content that you would like to track conversions for (at minimum, the index and adventures documents)
- For details on project setup, reference the [Developer Tutorial](https://www.hlx.live/developer/tutorial)
- Follow the [Slack Bot installation docs](https://www.hlx.live/docs/slack) to set up the bot in your own channel
- To generate some traffic data for your forked site, you can use the included Puppeteer script (/test/puppeteer/generate-traffic.mjs):

```sh
# Set the value of TEST_URL to your forked site's Preview URL
TEST_URL=https://main--wknd--<YOUR-GITHUB-USERNAME-OR-ORG>.hlx.page npm run generate-traffic

# For example, using the WKND Demo repository, and running 100 iterations:
TEST_URL=https://main--wknd--hlxsites.hlx.page ITERATIONS=100 npm run generate-traffic
```

### Slack Bot
[Slack Bot docs](https://www.hlx.live/docs/slack)

- Follow the "Conversion Tracking" steps above to enable the Slack Bot
- Refer to the [Slack Bot Skills](https://www.hlx.live/docs/slack#slack-bot-skills) section for details on querying the underlying data from Slack

### Document based content authoring
[Authoring docs](https://www.hlx.live/docs/authoring)

- Follow the "Conversion Tracking" steps above, ensuring that fstab.yaml in your fork points to a SharePoint or Google Drive folder that you own
- Refer to the [Authoring docs](https://www.hlx.live/docs/authoring) for details on authoring functionality
- Modify and "Preview" the documents in your SharePoint or Google Drive folder to see the changes reflected on the Preview environment
- To go deeper, refer to the [Anatomy of a Project doc](https://www.hlx.live/developer/anatomy-of-a-franklin-project), and check out the [Block Collection](https://www.hlx.live/developer/block-collection)

## Local development

1. Clone this repository to your machine
1. Add the [helix-bot](https://github.com/apps/helix-bot) to the repository
1. Install the [Helix CLI](https://github.com/adobe/helix-cli): `npm install -g @adobe/helix-cli`
1. Start Helix Pages Proxy: `hlx up` (opens your browser at `http://localhost:3000`)
1. Open the `{repo}` directory in your favorite IDE and start coding :)
