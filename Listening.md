# Listening for messages

So now we will listen for messages and do things accordingly

For that, we listen for an event:
```js
client.on('message', message => {
	console.log(message.content);
});
```

And that will log to the console the content of the new message     
A message, is an object, an object that contains some things, such as:

- The author user, things like the username, discriminator (Username **#9999**, that last 4 numbers are the discriminator), and other things
- The message, like, the content, the channel it was sent, the mentions (Mentioning is when you tag a user: @User)

For reference, here's a message object:
```
Message {
  channel: <ref *1> TextChannel {
    type: 'text',
    deleted: false,
    id: '798181668102996012',
    name: 'general',
    rawPosition: 0,
    parentID: '798181668102996010',
    permissionOverwrites: Collection(0) [Map] {},
    topic: null,
    lastMessageID: '798937071015428157',
    rateLimitPerUser: 0,
    lastPinTimestamp: null,
    guild: Guild {
      members: [GuildMemberManager],
      channels: [GuildChannelManager],
      roles: [RoleManager],
      presences: [PresenceManager],
      voiceStates: [VoiceStateManager],
      deleted: false,
      available: true,
      id: '798181668102996009',
      shardID: 0,
      name: 'My Server',
      icon: null,
      splash: null,
      discoverySplash: null,
      region: 'us-south',
      memberCount: 2,
      large: false,
      features: [],
      applicationID: null,
      afkTimeout: 300,
      afkChannelID: null,
      systemChannelID: '798181668102996012',
      embedEnabled: undefined,
      premiumTier: 0,
      premiumSubscriptionCount: 0,
      verificationLevel: 'NONE',
      explicitContentFilter: 'DISABLED',
      mfaLevel: 0,
      joinedTimestamp: 1610371920376,
      defaultMessageNotifications: 'ALL',
      systemChannelFlags: [SystemChannelFlags],
      maximumMembers: 100000,
      maximumPresences: null,
      approximateMemberCount: null,
      approximatePresenceCount: null,
      vanityURLCode: null,
      vanityURLUses: null,
      description: null,
      banner: null,
      rulesChannelID: null,
      publicUpdatesChannelID: null,
      preferredLocale: 'en-US',
      ownerID: '748881839686418482',
      emojis: [GuildEmojiManager]
    },
    messages: MessageManager {
      cacheType: [class LimitedCollection extends Collection],
      cache: [LimitedCollection [Map]],
      channel: [Circular *1]
    },
    nsfw: false,
    _typing: Map(0) {}
  },
  deleted: false,
  id: '798937071015428157',
  type: 'DEFAULT',
  system: false,
  content: 'Hello world!',
  author: User {
    id: '748881839686418482',
    system: false,
    locale: null,
    flags: UserFlags { bitfield: 0 },
    username: 'Alyx',
    bot: false,
    discriminator: '7092',
    avatar: 'ea14dc80a7ba44fed6b89d1b5ecf25b6',
    lastMessageID: '798937071015428157',
    lastMessageChannelID: '798181668102996012'
  },
  pinned: false,
  tts: false,
  nonce: '798937070578958336',
  embeds: [],
  attachments: Collection(0) [Map] {},
  createdTimestamp: 1610551841263,
  editedTimestamp: 0,
  reactions: ReactionManager {
    cacheType: [class Collection extends Collection],
    cache: Collection(0) [Map] {},
    message: [Circular *2]
  },
  mentions: MessageMentions {
    everyone: false,
    users: Collection(0) [Map] {},
    roles: Collection(0) [Map] {},
    _members: null,
    _channels: null,
    crosspostedChannels: Collection(0) [Map] {}
  },
  webhookID: null,
  application: null,
  activity: null,
  _edits: [],
  flags: MessageFlags { bitfield: 0 },
  reference: null
}
```

Yeah, it is a long object				

Now, before we continue, let's create some config files		
	
Inside the bot directory, create a config.json, then, write the following code in there:
```json
{
	"prefix": "!",
	"token": "your-token-goes-here"
}
```

The prefix is for our bot to listen to commands, and the token, is for not having the token in the index.js file

Then go back to your main bot file, locate the `const client = new Discord.Client()` line, and add this above it:
```js
const config = require('./config.json');
```

Next, copy your token from the client.login('your-token-goes-here') line and paste into the config.json file. Make sure to keep it between the double quotes.

Now you can simply do `client.login(config.token)` to login! If you want to use a different prefix than !, you can change that as well.

Now, if you want to store additional data, you can add that in the config.json file, in a line like this
```json
"key": "key-value"
```

And you can use that in your main file just by doing like this:
```js
console.log(config.key)
```

## Next up: [Commands](Commands.md)