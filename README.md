[![CircleCI](https://circleci.com/gh/thebrettbarlow/forcelandia-sfdx-plugin.svg?style=svg)](https://circleci.com/gh/thebrettbarlow/forcelandia-sfdx-plugin)

# forcelandia-sfdx-plugin

_Salesforce Command Line Training Workshop at [Forcelandia](http://forcelandia.com)_

---

## Overview

This is a 40 minute workshop hosted at [Forcelandia](http://forcelandia.com) that is scheduled as follows:

* 01 - 10 Minutes: Installation and Exploring the Plugin sections
* 10 - 20 Minutes: Workshop steps 1-6
* 20 - 30 Minutes: Coding!
* 30 - 40 Minutes: Demo time

1. [Installation and Setup](#installation-and-setup)
1. [Exploring the Plugin](#exploring-the-plugin)
1. [Workshop](#workshop)

## Installation and Setup

Let's do some initial setup to prepare our computers for development. If you run 
into any strange errors, Salesforce covers some of this in their setup article [here](https://developer.salesforce.com/docs/atlas.en-us.sfdx_cli_plugins.meta/sfdx_cli_plugins/cli_plugins_generate_prepare.htm).

### 1. node and npm
Make sure `node` and `npm` is [installed](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm)

```bash
brew install node
```

### 2. Login to npm

If you don't have an npm account, Brett will provide a shared account you can use. 

If you do have npm, make sure you're logged in by running:

```bash
npm login
```

### 3. TypeScript

```bash
npm install --global typescript
```

### 4. yarn
We'll be using `yarn` as a package manager. Also get it [here](https://yarnpkg.com/lang/en/docs/install)

```bash
npm install --global yarn
```

### 5. sfdx-cli
Make sure the base `sfdx-cli` is [installed](https://developer.salesforce.com/tools/sfdxcli)

```bash
npm install --global sfdx-cli
```

### 6. Authenticate
_production authentication command_
```bash
sfdx force:auth:web:login --setalias production
```

_stage authentication command_
```bash
sfdx force:auth:web:login --setalias stage --instanceurl https://test.salesforce.com
```

### 7. forcelandia-sfdx-plugin
```bash
echo 'y' | sfdx plugins:install thebrettbarlow/forcelandia-sfdx-plugin
sfdx fl --help
```

## Exploring the Plugin
The `--help` command is your friend.

This command will display which topics and commands are available in the plugin. 
Running `--help` on a specific topic will display which commands are available 
to run.
```
$ sfdx fl:data --help
commands for all the datas

USAGE
  $ sfdx fl:data:COMMAND

COMMANDS
  fl:data:copy      copies data from production to another sfdx connection
  fl:data:setvalue  sets a value into a field for all records returned by the query
  fl:data:upsert    upsert data from a csv file
```

---

## Workshop

### 1. Clone the repo and provide a new directory name

```bash
git clone https://github.com/thebrettbarlow/forcelandia-sfdx-plugin new_directory_name
```

### 2. Create a GitHub repo

This can be done via the `hub` command below or within the GitHub UI. I recommend using `hub` for this workshop

If you don't have `hub`, try the command below or [other install methods](https://github.com/github/hub#installation)
```bash
brew install hub
```

Create a repo (will prompt for GitHub login)
```bash
# cd into your new directory from above first 
cd new_directory_name

hub create \
    --description "Salesforce Command Line Training Workshop at Forcelandia" \
    --homepage "http://bit.ly/forcelandia-sfdx-plugin"
```

### 3. Update origin's url

```bash
git remote set-url origin http://github.com/USERNAME/REPO_NAME
```

### 4. Push to new remote

```bash
git push origin master
```

### 5. Initialize and Install

```bash
yarn init
yarn install
```

### 6. Link plugin for development
```bash
sfdx plugins:link
sfdx plugins --core
```

### 7. Make a change

Time to get creative! Make a change to an existing command or add a command of your own!

### Tips on making changes

To change an existing command, directly edit the TypeScript file you would like to change.

If you would like to add a command within an existing topic (data, recordtype or user), you can create a new 
TypeScript file within the appropriate folder. It may be helpful to copy and paste an existing command over as a
starting place.

If you would like to add a command within a _new_ topic, add a folder within the `fl` directory (at the same level as
data, recordtype and user). Create a new TypeScript file within this new folder. It may be helpful to copy and paste an 
existing command over as a starting place.

### Need some inspiration? Here are a few ideas:

* Display the top 10 Opportunities by Amount
* Add a filter to `recordtype:get`
* Create a record and open that page

### 8. Publish
```bash
yarn publish --access public
```

### 9. Demo

If you have something working by the end, let Brett know and he'll demo it!

## All Available Commands

<!-- commands -->
* [`sfdx fl:data:copy -d <filepath> [-a] [-s <string>] [-l <number>] [-d <directory>] [-u <string>] [--apiversion <string>] [--json] [--loglevel trace|debug|info|warn|error|fatal|TRACE|DEBUG|INFO|WARN|ERROR|FATAL]`](#sfdx-fldatacopy--d-filepath--a--s-string--l-number--d-directory--u-string---apiversion-string---json---loglevel-tracedebuginfowarnerrorfataltracedebuginfowarnerrorfatal)
* [`sfdx fl:data:setvalue -q <string> -f <string> -v <string> [-n <string>] [-d <directory>] [-u <string>] [--apiversion <string>] [--json] [--loglevel trace|debug|info|warn|error|fatal|TRACE|DEBUG|INFO|WARN|ERROR|FATAL]`](#sfdx-fldatasetvalue--q-string--f-string--v-string--n-string--d-directory--u-string---apiversion-string---json---loglevel-tracedebuginfowarnerrorfataltracedebuginfowarnerrorfatal)
* [`sfdx fl:data:upsert -s <string> -f <filepath> [-i <string>] [-u <string>] [--apiversion <string>] [--json] [--loglevel trace|debug|info|warn|error|fatal|TRACE|DEBUG|INFO|WARN|ERROR|FATAL]`](#sfdx-fldataupsert--s-string--f-filepath--i-string--u-string---apiversion-string---json---loglevel-tracedebuginfowarnerrorfataltracedebuginfowarnerrorfatal)
* [`sfdx fl:recordtype:get [-u <string>] [--apiversion <string>] [--json] [--loglevel trace|debug|info|warn|error|fatal|TRACE|DEBUG|INFO|WARN|ERROR|FATAL]`](#sfdx-flrecordtypeget--u-string---apiversion-string---json---loglevel-tracedebuginfowarnerrorfataltracedebuginfowarnerrorfatal)
* [`sfdx fl:user:get [-a] [-n <string>] [-p <string>] [-r <string>] [-s] [-o] [-d <directory>] [-u <string>] [--apiversion <string>] [--json] [--loglevel trace|debug|info|warn|error|fatal|TRACE|DEBUG|INFO|WARN|ERROR|FATAL]`](#sfdx-fluserget--a--n-string--p-string--r-string--s--o--d-directory--u-string---apiversion-string---json---loglevel-tracedebuginfowarnerrorfataltracedebuginfowarnerrorfatal)

## `sfdx fl:data:copy -d <filepath> [-a] [-s <string>] [-l <number>] [-d <directory>] [-u <string>] [--apiversion <string>] [--json] [--loglevel trace|debug|info|warn|error|fatal|TRACE|DEBUG|INFO|WARN|ERROR|FATAL]`

copies data from production to another sfdx connection

```
USAGE
  $ sfdx fl:data:copy -d <filepath> [-a] [-s <string>] [-l <number>] [-d <directory>] [-u <string>] [--apiversion 
  <string>] [--json] [--loglevel trace|debug|info|warn|error|fatal|TRACE|DEBUG|INFO|WARN|ERROR|FATAL]

OPTIONS
  -a, --all                                                                         if true, the script gets all
                                                                                    sobjects in the `sobjectTypes` array

  -d, --destination=destination                                                     (required) sfdx connection to copy
                                                                                    places to

  -d, --directory=directory                                                         [default: .] directory where you
                                                                                    would like the output to go

  -l, --limit=limit                                                                 limit the number of records to
                                                                                    export

  -s, --sobjecttype=sobjecttype                                                     name of the sobject to get. Required
                                                                                    if --all is false

  -u, --targetusername=targetusername                                               username or alias for the target
                                                                                    org; overrides default target org

  --apiversion=apiversion                                                           override the api version used for
                                                                                    api requests made by this command

  --json                                                                            format output as json

  --loglevel=(trace|debug|info|warn|error|fatal|TRACE|DEBUG|INFO|WARN|ERROR|FATAL)  [default: warn] logging level for
                                                                                    this command invocation

EXAMPLE
  sfdx fl:data:copy --sobjecttype Account --limit 100 --targetusername production --destination stage
```

_See code: [src/commands/fl/data/copy.ts](https://github.com/thebrettbarlow/forcelandia-sfdx-plugin/blob/v1.0.0/src/commands/fl/data/copy.ts)_

## `sfdx fl:data:setvalue -q <string> -f <string> -v <string> [-n <string>] [-d <directory>] [-u <string>] [--apiversion <string>] [--json] [--loglevel trace|debug|info|warn|error|fatal|TRACE|DEBUG|INFO|WARN|ERROR|FATAL]`

sets a value into a field for all records returned by the query

```
USAGE
  $ sfdx fl:data:setvalue -q <string> -f <string> -v <string> [-n <string>] [-d <directory>] [-u <string>] [--apiversion 
  <string>] [--json] [--loglevel trace|debug|info|warn|error|fatal|TRACE|DEBUG|INFO|WARN|ERROR|FATAL]

OPTIONS
  -d, --directory=directory                                                         [default: .] directory where you
                                                                                    would like the output to go

  -f, --field=field                                                                 (required) name of the field to set

  -n, --filename=filename                                                           [default: set_value] name of the
                                                                                    backup and output files

  -q, --query=query                                                                 (required) query to get records to
                                                                                    update

  -u, --targetusername=targetusername                                               username or alias for the target
                                                                                    org; overrides default target org

  -v, --value=value                                                                 (required) value that should be set

  --apiversion=apiversion                                                           override the api version used for
                                                                                    api requests made by this command

  --json                                                                            format output as json

  --loglevel=(trace|debug|info|warn|error|fatal|TRACE|DEBUG|INFO|WARN|ERROR|FATAL)  [default: warn] logging level for
                                                                                    this command invocation

EXAMPLE
  sfdx fl:data:setvalue --query "select id, type from account where type != null limit 5" --field Type --value "Cool 
  Company" --targetusername stage
```

_See code: [src/commands/fl/data/setvalue.ts](https://github.com/thebrettbarlow/forcelandia-sfdx-plugin/blob/v1.0.0/src/commands/fl/data/setvalue.ts)_

## `sfdx fl:data:upsert -s <string> -f <filepath> [-i <string>] [-u <string>] [--apiversion <string>] [--json] [--loglevel trace|debug|info|warn|error|fatal|TRACE|DEBUG|INFO|WARN|ERROR|FATAL]`

upsert data from a csv file

```
USAGE
  $ sfdx fl:data:upsert -s <string> -f <filepath> [-i <string>] [-u <string>] [--apiversion <string>] [--json] 
  [--loglevel trace|debug|info|warn|error|fatal|TRACE|DEBUG|INFO|WARN|ERROR|FATAL]

OPTIONS
  -f, --file=file                                                                   (required) csv that contains the
                                                                                    data to upsert

  -i, --externalid=externalid                                                       [default: Id] external id to use
                                                                                    with the upsert

  -s, --sobjecttype=sobjecttype                                                     (required) sobject type to use with
                                                                                    the upsert

  -u, --targetusername=targetusername                                               username or alias for the target
                                                                                    org; overrides default target org

  --apiversion=apiversion                                                           override the api version used for
                                                                                    api requests made by this command

  --json                                                                            format output as json

  --loglevel=(trace|debug|info|warn|error|fatal|TRACE|DEBUG|INFO|WARN|ERROR|FATAL)  [default: warn] logging level for
                                                                                    this command invocation

EXAMPLE
  sfdx fl:data:upsert --sobjecttype Account --externalid Id --file accounts_to_upsert.csv
```

_See code: [src/commands/fl/data/upsert.ts](https://github.com/thebrettbarlow/forcelandia-sfdx-plugin/blob/v1.0.0/src/commands/fl/data/upsert.ts)_

## `sfdx fl:recordtype:get [-u <string>] [--apiversion <string>] [--json] [--loglevel trace|debug|info|warn|error|fatal|TRACE|DEBUG|INFO|WARN|ERROR|FATAL]`

gets record type names and ids

```
USAGE
  $ sfdx fl:recordtype:get [-u <string>] [--apiversion <string>] [--json] [--loglevel 
  trace|debug|info|warn|error|fatal|TRACE|DEBUG|INFO|WARN|ERROR|FATAL]

OPTIONS
  -u, --targetusername=targetusername                                               username or alias for the target
                                                                                    org; overrides default target org

  --apiversion=apiversion                                                           override the api version used for
                                                                                    api requests made by this command

  --json                                                                            format output as json

  --loglevel=(trace|debug|info|warn|error|fatal|TRACE|DEBUG|INFO|WARN|ERROR|FATAL)  [default: warn] logging level for
                                                                                    this command invocation

EXAMPLE
  sfdx fl:recordtype:get
```

_See code: [src/commands/fl/recordtype/get.ts](https://github.com/thebrettbarlow/forcelandia-sfdx-plugin/blob/v1.0.0/src/commands/fl/recordtype/get.ts)_

## `sfdx fl:user:get [-a] [-n <string>] [-p <string>] [-r <string>] [-s] [-o] [-d <directory>] [-u <string>] [--apiversion <string>] [--json] [--loglevel trace|debug|info|warn|error|fatal|TRACE|DEBUG|INFO|WARN|ERROR|FATAL]`

gets users based on certain parameters

```
USAGE
  $ sfdx fl:user:get [-a] [-n <string>] [-p <string>] [-r <string>] [-s] [-o] [-d <directory>] [-u <string>] 
  [--apiversion <string>] [--json] [--loglevel trace|debug|info|warn|error|fatal|TRACE|DEBUG|INFO|WARN|ERROR|FATAL]

OPTIONS
  -a, --active                                                                      only return active users

  -d, --directory=directory                                                         [default: .] directory where you
                                                                                    would like the output to go

  -n, --name=name                                                                   return users whose name contains
                                                                                    this value

  -o, --outputcsv                                                                   output the result as a csv

  -p, --profile=profile                                                             return users whose profile name
                                                                                    contains this value

  -r, --userrole=userrole                                                           return users whose user role
                                                                                    developer name contains this value

  -s, --skinny                                                                      only returns the Username and Id of
                                                                                    each result

  -u, --targetusername=targetusername                                               username or alias for the target
                                                                                    org; overrides default target org

  --apiversion=apiversion                                                           override the api version used for
                                                                                    api requests made by this command

  --json                                                                            format output as json

  --loglevel=(trace|debug|info|warn|error|fatal|TRACE|DEBUG|INFO|WARN|ERROR|FATAL)  [default: warn] logging level for
                                                                                    this command invocation

EXAMPLES
  sfdx fl:user:get
  sfdx fl:user:get --active
  sfdx fl:user:get --active --name "john smith"
  sfdx fl:user:get --active --profile admin
  sfdx fl:user:get --active --userrole sales
  sfdx fl:user:get --active --skinny
  sfdx fl:user:get --active --outputcsv
```

_See code: [src/commands/fl/user/get.ts](https://github.com/thebrettbarlow/forcelandia-sfdx-plugin/blob/v1.0.0/src/commands/fl/user/get.ts)_
<!-- commandsstop -->
<!-- debugging-your-plugin -->
# Debugging your plugin
We recommend using the Visual Studio Code (VS Code) IDE for your plugin development. Included in the `.vscode` directory of this plugin is a `launch.json` config file, which allows you to attach a debugger to the node process when running your commands.

To debug the `hello:org` command: 
1. Start the inspector
  
If you linked your plugin to the sfdx cli, call your command with the `dev-suspend` switch: 
```sh-session
$ sfdx hello:org -u myOrg@example.com --dev-suspend
```
  
Alternatively, to call your command using the `bin/run` script, set the `NODE_OPTIONS` environment variable to `--inspect-brk` when starting the debugger:
```sh-session
$ NODE_OPTIONS=--inspect-brk bin/run hello:org -u myOrg@example.com
```

2. Set some breakpoints in your command code
3. Click on the Debug icon in the Activity Bar on the side of VS Code to open up the Debug view.
4. In the upper left hand corner of VS Code, verify that the "Attach to Remote" launch configuration has been chosen.
5. Hit the green play button to the left of the "Attach to Remote" launch configuration window. The debugger should now be suspended on the first line of the program. 
6. Hit the green play button at the top middle of VS Code (this play button will be to the right of the play button that you clicked in step #5).
<br><img src=".images/vscodeScreenshot.png" width="480" height="278"><br>
Congrats, you are debugging!
