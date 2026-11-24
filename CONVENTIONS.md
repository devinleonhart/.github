# Conventions

How my repositories are laid out and changed. A repository may differ where it has a reason; it says so in its own README.

## README

Sections in this order. Leave out one that does not apply; add none.

1. **Title** and one sentence saying what the project is.
2. **Features**: what it does. Commands for a bot, pages and addresses for an application.
3. **Development**: prerequisites, how to run it, and the one command that runs every check.
4. **Environment**: a table of variables and their purpose.
5. **MCP**: for an application that serves it. What the tools offer and how tokens are issued.
6. **Deployment**: how a change reaches production.
7. **Architecture**: a few lines on how the code is laid out.

Write plain statements of fact. No badges, no paths of one machine, no secrets, and no version numbers that a file in the repository already states.

## Branches and commits

- Work on a branch and merge it to `master`. Delete the branch when it is merged; only `master` stays.
- A commit's subject is one imperative sentence without a full stop: `Serve MCP at /mcp`.
- The body, if any, says why.

## Pull requests

`PULL_REQUEST_TEMPLATE.md` here applies to every repository without its own. Fill in its three sections and add no others:

- **Summary**: what changes, and why.
- **Changes**: the notable changes, one per line.
- **Verification**: commands run or steps taken, with their actual results.

Keep each to a sentence or a few short lines.

## Deployment

- A merge to `master` runs CI. When the checks pass, CI publishes the image `devleo/<project>:latest` to Docker Hub.
- The server runs `latest`. Deploying is `docker compose pull <service>`, then `docker compose up -d <service>`.
- A Rails application with a new migration runs `bin/rails db:migrate` between the two. Migrations never run at boot.
