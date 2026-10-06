# TeamSpeak Extension Information

This file aims to provide information for extension authors to build extensions
for the TeamSpeak client.

> Note: This is currently alpha state and subject to change.  
> This also applies to this documentation, which is probably not as thorough as
> you might want.  
> Please report issues and shortcomings of this documentation
> on the usual channels.

> Please note that remote content is **not allowed** to be loaded or accessed
> by extensions.

## General information

Extensions consist of a folder that must contain all the files necessary for
your extension to work properly.  
This folder needs to contain a `package.json` file that must follow a specific
format.  
The format and content of the package.json is verified to match the
`extensions.json` [schema](https://json-schema.org/) that accompanies this
documentation. You may use [a validator](https://www.jsonschemavalidator.net/)
to verify that your package.json is valid. The client will also log validation
failures in the log.  
In the future the json schema will also be available online (location TBD).

### Naming conventions

The folder name of your extension is supposed to follow standard identifier naming.
For example `com.teamspeak.dark` or `com.teamspeak.themes.dark`
would be reasonable identifiers for the default Dark theme included in the client.  
The folder name must match your extension identifier in the package.json, and both
must be all lowercase.

### Package Information File

The package.json contains information about your extension, such as the content of
the extension, a unique identifier, a public repository containing the source code
and author information. It may optionally contain additional links to community and
support information, as well as a TeamSpeak server address and a public chat room.

## Themes

Themes consists of:

- One CSS file, containing all the CSS rules you wish to apply to the client
- One image file, showing a preview of your Theme displayed in the client
- Additional files you require (such as images)

An extension may optionally contain multiple variations of the same theme, if you
wish to provide several different versions (with different accent colors for
example).  
However if your themes are vastly different we would strongly suggest to package
them as separate extensions instead.

## Example

A sort of minimal example package.json might look as follows:

```json
{
    "name": "Example Theme",
    "description": "This is an example theme, making everything purple",
    "version": "1.0.0",
    "identifier": "invalid.example.theme",
    "engines": {
        "teamspeak": 1
    },
    "repository": {
        "url": "https://github.com/bestDudeEver/themes/",
        "directory": "purple",
        "type": "git"
    },
    "image": "preview.png",
    "license": "MIT",
    "author": {
        "name": "Joe Doe",
        "email": "joe@example.net",
        "url": "https://example.net",
        "userTag": "TeamSpeak@myteamspeak.com"
    },
    "content": {
        "themes": [
            {
                "name": "Purple Theme",
                "source": "purple.css",
                "image": "purple-preview.png",
                "apiVersion": 1
            }
        ]
    }
}
```

Please note that the repository could also just be the link itself, if you don't
need the other information.  
Similarly the author can just be `"author": "Joe Doe"` in case you don't want to
provide the additional details.
