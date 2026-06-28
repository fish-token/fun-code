# What Does it Do?

This JXA (JavaScript for Automation) script let's you automatically and repeatedly send text messages to a person or group of people. It let's you customize:

- Who to send the messages to
- What message to send
- How many times to send the message

**Clarifications:**

- Please use this responsibly (it may get you blocked by some people)
- This, like any other JXA script, will only work on macOS 10.12 Sierra or higher. For more info, please see [info.md](info.md)
- The script shouldn't drain performance, unless sending large amounts and/or many messages

## What's The Setup Process?

Follow the steps below!

- Download [this](assets/message_spam.zip) zip, and wait for it to finish
- Open your file browser, and go to `Downloads`
- Find `message_spam.zip` and extract it (double click)
- Open up the terminal by pressing `Cmd + Spacebar`, then typing `Terminal` then press enter
- Put the following commands inside

```bash
cd ~/Downloads # Navigate to the correct directory
chmod +x message_spam # Give it permissions to run
```

Now whenever you want to run this script, just double-click the executable, or put the following commands in the terminal:

```bash
cd ~/Downloads # Navigate to the correct directory
./message_spam # Run the script
```

## What's The Removal Process?

If you are looking to cancel running of the script, just press cancel on any dialog.  
If it's already running or you want to delete the script, delete the `message_spam.zip` and `message_spam` files

## Source code

```js
#!/usr/bin/env osascript -l JavaScript
// Script by Fish Token
const prompt = (text, initialText) => {
    const opts = { defaultAnswer: initialText || '' };
    try {
        return app.displayDialog(text, opts).textReturned;
    } catch (err) { return null; };
}

const app = Application.currentApplication();
app.includeStandardAdditions = true;
const targ = Application('Messages');

/* Get information about all chats
const chats = targ.chats();
chats.forEach(chat => {
    const id = chat.id();
    const name = chat.name();
    const nums = chat.participants().length;
    console.log(`Name: ${name}, ID: ${id}, # of participants: ${nums}, name: ${name}`);
});
*/

let target = null;
if (prompt('Identify by Name?', 'Yes') === 'Yes') {
    target = targ.chats.byName(prompt('Name of user/chat to send to:', 'Example User'));
} else target = targ.chats.byId(prompt('ID of user/chat to send to:', 'SMS;+;chat...'));
const message = prompt('Message to send:', 'Example!');
let amount = prompt('How many messages?', '1');
if (amount === '' || amount === null) amount = 1;

for (let i = 0; i < amount; i++) {
    try {
        targ.send(message, { to: target });
    } catch (err) { console.error('Error occured when running: ' + err); }
}
```