Want to send text-messages in your Node.js application? Then you are at the right place.

The package is currently limited in features compared to the CM gateway, but if you want to get all the functionalities, go to: [ne.com API Docs](https://docs.cmtelecom.com/bulk-sms/v1.0)

### Usage
#### Node.JS
First, run `npm install @nwolisaemmenuel2/text-sdk`. Then, in your source file:
```javascript
const messagingApi = require("@nwolisaemmanuel2/text-sdk");

// Get your product token at CM.com.
const yourProductToken = "";
const myMessageApi = new messagingApi.MessageApiClient(yourProductToken);

const result = myMessageApi.sendTextMessage(["00316012345678"], "TestSender", "Hello world?!");

result.then((result) => {
    console.log(result);
}).catch((error) => {
    console.log(error);
});
```

or send multiple
```javascript
const result = myMessageApi.sendTextMessage(["00316012345678","003160000000"], "TestSender", "Hello world?!");
```

 send rich messages using the message builder
```javascript
const richMessage = {
    media: {
        mediaName: "ne.com",
        mediaUri: "https://avatars3.githubusercontent.com/u/8234794?s=200&v=4"
    },
    text: "good!"
};

const suggestion = {
    action: "openUrl",
    label: "Click me",
    url: "https://www.ne.com"
};

const response = client.createMessage()
    .setMessage(["00316012345678"], "TestSender", "Hello world?!")
    .setAllowedChannels(["Viber"])
    .setConversation([richMessage])
    .setSuggestion([suggestion])
    .send();

response.then((result) => {
    console.log(result);
}).catch((error) => {
    console.log(error);
});
```