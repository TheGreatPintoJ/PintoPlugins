# PintoChat
A spigot plugin to customize all thing about chat!

## Features
- Custom chat message formats
- Adds support for color codes in chat and /msg
- SQL Database support for cross-server chat and messages

## Commands
- `/msg` - Overrides default /msg command, only with improvements!

## Permissions
- `pintochat.msg` - Permission to use custom /msg command

## Config
### Database
- `type` - The type of the SQL database (known compatability: mysql - theoretical compatibility: all)
- `enabled` - Whether to use the database or not
#### MySql/Similar
- `host` - The host that the SQL server is running on
- `port` - The port that the SQL server is accessible by
- `name` - The name of the database to access
- `user` - The username to access with
- `password` - The password to acccess with

#### SQLite
- `path` - The path of the SQL database, full path from / or C:

### Chat Options
- `chatmessageformat` - The format to put chat messages in (placeholders are %player%, %message%)

## Errors/Bugs
Make an issue on this project's repository
