# GitCast
GitCast is how you can use GitHub to host a posdcast as a free or cheap alternative to a podcast host when your first getting started hopefully lowering the cost of entry. You can have one or more podcasts hosted within the same repository.

Example Web View: https://vshed.us/gitcast/podcast

Example Feed: https://vshed.us/gitcast/podcast.rss


## Adding a podcast 
1. Add collection settings to the _config.yml
1. Create a folder in you GitHub Pages folder starting with an underscore followed by the follection name
    1. You will want to create a default.png file with a minimum size of 1400x1400 that is smaller than 250KB
1. Add /addet/css/github.css to your /asset/css folder
1. Add github.json file to your GitHub Pages folder
1. Copy the web view file 'podcast.md' to your GitHub Pages folder. Its recomended that you rename this to your collection name
    1. Note: You will need to update the header details of this file to match your colleciton and podcast details
1. Copy the feed file 'podcast.rss.xml' to your GitHub Pages folder. Its recomended that you rename this to your collection name
    1. Note: You will need to update the header details of this file to match your colleciton and podcast details
1. Create your first podcast episode using the following file requirements
    1. YYYY-dd-mm-Episode Title.md (Required)
    1. YYYY-dd-mm-Episode Title.mp3 (Required)
    1. YYYY-dd-mm-Episode Title.png (Optional minimum dimentions 1400x1400 maximum size 250KB)
  

## _config.yml Settings
This file should be located at the root of your GitHub Pages folder. This is typically the rood directory or the docs directory.
### Repository wide author details
This can be accomplished by adding the following into your _config.yml file
```markdown
author:
  name             : "John Doe"
  email            : "email@address.com"
```
### Add a single podcast
```markdown
collections:
  podcast:
    gitcast: true
    output: true
    permalink: /:collection/:year-:month-:day-:title/
````
### Add multiple podcasts
```markdown
collections:
  kneetalk:
    gitcast: true
    output: true
    permalink: /:collection/:year-:month-:day-:title/
   elbotalk:
    gitcast: true
    output: true
    permalink: /:collection/:year-:month-:day-:title/   
```

## Web view 'podcast.md' file heading
Items starting with # are optional. Removed the comment tag to use.
```markdown
---
layout: default
cast:
  name: podcast
#style: assets/css/gitcast.css
---
```

## Feed 'podcast.rss.xml' file heading
Items starting with # are optional. Removed the comment tag to use.
```markdown
---
layout: none
cast:
  title: "Cast Collextion Example"
  collection: podcast
  #type: 'episodic'
  #explicit: 'no'
  #author:
  #  name: "Jane Doe"
  #  email: "email@address.com"
  #copyright: "2020 Doe LLC"
---
```

## Episode file heading
```markdown
---
layout: default
title:  "Today I Learned"
excerpt_separator: <!--more-->
duration: 7                     #play time in seconds
length: 115774                  #size in bytes
#author:
#  name:
#  email:
excerptplain: "tis is a random test soemting something adding more text tothe test"
---
```
