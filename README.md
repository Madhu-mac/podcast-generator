# Podcast Feed Generator

This GitHub Action generates a podcast feed from a YAML file. YAML is much easier to read and write than XML, and this action will convert your YAML file into a valid podcast feed.

## Usage

### Turn on GitHub Pages

1. In your repository, navigate to **Settings > Pages**.
2. Select the main branch as the source.
3. This will create a link to your page and give all content in the main branch a URL. Note the URL for the next step.

### Create a YAML file

Create a YAML file in your repository with the following format:

```yaml
title: <Podcast Title>
subtitle: <Podcast Subtitle>
author: <Author Name>
description: <Podcast Description>
link: <GitHub Pages URL>
image: <Artwork Location>
language: <Podcast Language e.g., en-us>
category: <Podcast Category e.g., Technology https://podcasters.apple.com/support/1691-apple-podcasts-categories>
format: <format of files e.g., audio/mpeg>
item:
  - title: <Podcast Episode Title>
    description: <Podcast Episode Description>
    published: <Date Published - e.g., Thu, 12 Jan 2023 18:00:00 GMT>
    file: <Filename e.g., /audio/TFIT01.mp3>
    duration: <duration e.g., 00:00:36>
    length: <length e.g., 576,324 (Get Info on your files)>
  ... Repeat for each episode
```

### Sample Workflow

You're also going to need your own workflow file. Here's a sample:

```yaml
name: Generate Feed
on: [push]
jobs:
  generate-feed:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Repo
        uses: actions/checkout@v3
      - name: Run Feed Generator
        uses: planetoftheweb/podcast-feed-generator@main
```
### License

This project is licensed under the MIT License 
