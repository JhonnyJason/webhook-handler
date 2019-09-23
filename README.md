# webhook-handler
This is the standard webhook-handler for a machine thingy.

The webhook-handler itself is implemented as a thingy.

This means we have the usable service ready to deploy in he output submodule.
Also we have a sources submodule for all the interesting stuff, how it is implemented.

This service can just be cloned/pulled and used.

## Important:

- It expects to be able to read a configuration file from `../webhook-config.js`. 
- It is expected to be used as a oneshot service invoked over a socket. As it will terminate after every request.
- It will write the appropriate commands into the specified socket.

As how it is done on a machine thingy - we have a oneshot service which runs as root to apply predefined update instruction for the specific command.

The commands are simply numbers.

## Sample configuration:
```javascript
{
    "uri": "/webhook",
    "secret": "shittysecret",
    "socketPath": "/run/commander.sk",
    "port": 65531,
    "branchReactionMap": {
        "repository-1": ["release", "test"]
        ,"repository-2":["master", "deploy"]
        ...
    },
    "commandMap": {
        "repository-1": [1, 2]
        ,"repository-2":[3, 4]
        ...
    }
}```