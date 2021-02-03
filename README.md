# Whale Easy Data Discovery Demo

I really enjoy the idea of a dead simple data discovery tool, so when I discovered https://github.com/dataframehq/whale, I really wanted to show that to people.

So here it is... The repository uses batect to make it as easy as possible for you guys.

## Start With batect

You can simply list all tasks by typing

```
.\batect --list-tasks
...
```

## Overview

In this demo you get:

1.  A demo postgres DB
2.  Whale dockerized
3.  A bunch of batect tasks which help you get running without any setup!

Type `./batect --list-tasks` to see what's in it.

```
$ ./batect --list-tasks
Utility tasks:
- run_etl: Loads config file from here so you can kick off the etl process...
- run_everything: Loads config file; now create alias, then ETL and then use wh to search!
- run_init: Type through the prompt; URL is "my_postgres", everything else you can see in this config.
- shell: Start a shell in the development environment.
```

So three fun tasks to play around with whale inside docker with a postgres
whichs system tables you can search through (sorry didn't have time to
dump data into it...)

## A Quick Walk through

Use `./batect run_init` to get a feeling for the setup, and take a look at the different data sources you can add to whale.

Of course you can also store the connections in yaml, see connections/connections.yaml and the whale docs. Run `./batect run_etl` to manually kick off the ETL process (which you can also cron schedule of course).

Finally, run `./batect run_everything` to auto-load the postgres connection. Then you can kick off the ETL and use the whale cli to search through the tables of the postgres.

But that's not all, the searchindex is also written as markdown which you could now push to git.

(which I obviously haven't implemented here...)
