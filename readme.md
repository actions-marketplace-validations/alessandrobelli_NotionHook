# Notion Hook

This action syncronize your Repository commits into a Notion Database.

📽️ Video Explanation: https://youtu.be/hARJlFH5MDE

## Setup

1. Create a new private Notion integration here: https://www.notion.so/my-integrations.
2. Copy the "Internal Integration Token" and create a new Repository secret called `NOTION_SECRET`.
3. [You need to create a new Notion Database that looks like this, or just duplicate this](https://alessandrobelli.notion.site/618655fb8e924216a5bc8b85cfd12274?v=eda6bbef2108493c9f1c0f9772a58549).
4. Click on Share -> Add people, emails, groups or integrations and select your Integration.
5. Navigate to your Notion database in a browser and get the Database Id.
![Database ID example](https://user-images.githubusercontent.com/3796324/126894870-e81d2831-9ac2-404a-bc07-a2d9d4014a39.png)
6. Create a new secret called `NOTION_DATABASE` with the database ID.
7. if you want a list of files, [create a github personal access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).
   1. then setup a files-format. the only avaliable value for now is "text-list".

## Inputs

Every input has its own default value. Check if they correspond to yours in the database.

### `commit_description`
**text**

Name of the Database column for the description field: this is the commit message after a `\n` or `\r`.


### `commit_url`
**url**

Name of the Database column for the commit url.


### `commit_id`
**Text**

Name of the Database column for the commit ID.


### `commit_project`
**Multiselect**

Name of the Database column for the project. 

### `files_format`

For now, the only possible value text-list.

### `token`
[Create a github personal access token for GitHub](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token)

## Example usage

```
on: [push]

jobs:
  Notion_Hook_job:
    runs-on: ubuntu-latest
    name: A job to connect to Notion
    steps:
      - name: Connect to Notion step
        id: notion
        uses: alessandrobelli/NotionHook@1.0
        with:
          notion_secret: ${{ secrets.NOTION_SECRET }}
          notion_database: ${{ secrets.NOTION_DATABASE }}
```
