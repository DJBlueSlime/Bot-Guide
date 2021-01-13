So, now that we can listen for messages, let's do things based on that messages

```js
if (message.content === `${prefix}ping`) {
	message.channel.send('Pong.');
} else if (message.content === `${prefix}beep`) {
	message.channel.send('Boop.');
}
```

So, that if statement, is for doing something based on the message content, that block of code, should be placed in your `client.on('message')` event.

But for that to work, let's make a small modification in the config file import
```js
const { prefix, token } = require('./config.json')
```

That's it, now, if you want to add a command, just do like this:
```js
if (message.content === `${prefix}servername`) {
    message.channel.send(`This's server's name is: ${message.guild.name}`)
}
```

The `message.channel.send()` method, is for sending a message to the channel, the message was sent.

And the `message.guild.name` is a value that contains the server's name, note that is guild not server, in the code, we refer to a server, as "guild"