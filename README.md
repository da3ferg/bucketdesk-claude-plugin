# BucketDesk plugin for Claude

BucketDesk is a file workspace for the Amazon S3 buckets a business already owns. This plugin connects Claude to
your BucketDesk workspace so you can find, read, summarize and share the files in your connected buckets by asking
in plain language.

## What it contains

- **A remote MCP server**, `https://app.bucketdesk.com/mcp`, declared in `.mcp.json`. It is the same server as the
  BucketDesk connector in Claude's directory.
- **One skill**, `skills/bucketdesk/SKILL.md`, that tells Claude which BucketDesk tool to use for each kind of request.

The plugin runs no local code, hooks or scripts, and installs no packages.

## Requirements

A BucketDesk Business workspace with at least one S3 bucket connected. You sign in as a workspace admin. Answering
questions about PDFs and Office files also needs document chat turned on for that bucket's connection.

## Sign-in and data

When Claude first calls a BucketDesk tool, it opens BucketDesk's OAuth sign-in page. Claude never receives AWS keys.
Each tool call is sent to `app.bucketdesk.com` with a one-hour token for that one workspace, and runs with the same
permissions, bucket scopes and audit log as the BucketDesk app. BucketDesk reads file contents only when a tool needs
them and returns the result to Claude. Nothing else is sent anywhere by this plugin.

Read-only tools: list connections, browse folders, search file names, read text files, file details, photo and video
metadata, archive job status. Tools that ask before running: ask a question about a document, create a share link
(emails one recipient), and start an archive job (list, unpack or zip). The plugin cannot delete, upload or move files.

## Links

- Setup guide: https://bucketdesk.com/blog/connect-bucketdesk-to-claude-and-chatgpt
- Privacy notice: https://bucketdesk.com/privacy
- Terms: https://bucketdesk.com/terms
- Support: https://bucketdesk.com/contact
