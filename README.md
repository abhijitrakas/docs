easyengine/docs
====================

⚠️ _**WIP:** This repo is currently work in progress!_  🚧

The purpose of this repo is to hold EasyEngine v4 documentation as of now. Over the time, we hope to make all tutorials published on EasyEngine.io available here.

## V4 Docs

EasyEngine v4 documentation is divided into two parts.

### Commands reference 

This part is automatically generated by parsing PHP docblock. Please do not edit markdown files in `commands` folder as they may get overwritten any time. 

If you want to send a fix for a command documentation, the best way to do is send a pull request with changes to PHP docblock on its respective repo. 

Alternatively, is to create a new issue in this repo with details such as:

1. EE Command for which you are sending a fix
2. Mention the wrong part (screenshot is also fine)
3. Mention the correct part (optional)

### Handbook  

EasyEngine v4 has a lot to it. The docker magic, new filesystem layouts a lot more. This is a part which is independent of any command.

For now, we are [creating issues labeled `documentation`](https://github.com/EasyEngine/docs/issues?q=is%3Aissue+is%3Aopen+label%3Adocumentation) for each such aspect which we feel needs documentation.

You can help in the following ways:

#### Write a new documentation

If you are familiar with EasyEngine v4

1. Pick an [issue labeled `documentation`](https://github.com/EasyEngine/docs/issues?q=is%3Aissue+is%3Aopen+label%3Adocumentation). 
2. Please post a comment on the issue saying something like "working on this". So others will not pick the same issue.
3. [Fork this repo](https://github.com/EasyEngine/docs/fork)!
3. Create a new markdown file for the issue in folder `handbook/`. Please avoid spaces in filename. Use `-` as a separator. Keep all characters lowercase. 
4. Once you are done writing markdown file, submit it via pull request (PR). 

If for some reason, you can't send PR, you can write down documentation as comment on relevant issue. Please use markdown. We will copy your comment manually! 

#### Update existing documentation

You can help with documentation update in two ways:

1. English is not a primary language of any core team member. So if you can improve _langauge_ of the documentation so it becomes easy to understand, that would be a great help.
2. Send updates to improve accuracy, add more information or even fix typos! 


## Documentation Hosting

We are not using Github pages or any static site generator. Instead another team at rtCamp is working on a solution which will seamlessly publish these markdown files in a WordPress site as pages. 

Their WordPress custom code will take care of all the bells & whistles a documentation sites need such as:

- [ ] stylining (theming), 
- [ ] table of content
- [ ] listing subpages
- [ ] breadcrumb
- [ ] search
- [ ] related pages
- [ ] meta data such as title, discription, slug

We will be open sourcing WordPress custom code also so that any other project which wish to make use of such documentation flow will benefit from this. We are using some codes from wp-cli. wp-cli project documenation is also built like this.

Once we have documentation site ready, we will add its URL here. 

The good part is - we are writing in markdown files which if nothing else works _(by Nov 15, 2018)_, can be quickly converted into Github Pages! 😉

### The proposed build process

1. All EasyEngine comamnds repos and this docs repo will have CI/CD setup.
2. Whenever something changes, a build process will run which will invoke a wp-cli command (WordPress custom code). 
3. That wp-cli command will take care of updating WordPress sites in appropriate way.

## Legacy flow

The documentation is located in GitHub to enable a pull request-based editing workflow. Long-form documentation can be edited directly. Command pages are generated dynamically from the EasyEngine codebase using the `ee handbook gen_commands` series of commands. `ee handbook gen-all` will regenerate all of the command pages and handbook pages.

All documentation is imported automatically into docs.easyengine.io in a two step process:

1. WordPress reads `commands-manifest.json` and `handbook-manifest.json` to understand all pages that need to be created.
2. Each WordPress page has a `markdown_source` attribute specifying a Markdown file to be fetched, converted to HTML, and saved in the database.

For docs.easyengine.io, the import process is running a WP Cron job on every push to github repo.
