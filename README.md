# PartyLib
PartyLib is a simple library that you can use in your ChatTriggers modules to get the current members of a player's party

## Importing
Import the module into your code using
```js
import getPartyMembers from "../PartyLib"
```

## Usage
The `getPartyMembers()` function has a boolean parameter, `deletePartyMessages`, which allows you to choose whether or not to clear the messages from /party list from the player's chat. The function returns a promise containing an array of all the names of the players in the party, including the user. If the player is not in a party, the function returns an empty array. 

## Example
Here is a simple example of a command that uses this function to display the current size of the party without showing the result of the /p list command:
```js
import getPartymembers from "../PartyLib"

register("command", (...args) => {
    getPartyMembers(true).then((members) => {
        //This code runs once the module has gotten the list of party members
        ChatLib.chat("Party Size: " + members.length);
    }).catch((error) => {
        //Just in case something goes wrong
        ChatLib.chat(error);
    });
}).setName("getPartyMembers");
```