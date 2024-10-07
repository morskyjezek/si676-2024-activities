---
layout: post
title:  "Lab 5: Requests and Adding Content to Your CB Collection Site"
date:   2024-10-07
assigned: 2024-10-07
due: 2024-10-20
categories: activities web collectionbuilder http requests python jekyll labs
---


This page contains the information for *{{ page.title }}*.

## Part One: Python Requests Lab

### 1. URL / URI Formulation

The Library of Congress provides a standard "permalink" structure,
which is intended to be a stable identifier that can provide a consistent
URI for any item in the Library's collections.
The pattern for these URIs is `https://lccn.loc.gov/ + LCCN`.

Find the pages for the following item URIs, identify the LCCN, and provide the matching LCCN permalinks:

```
1. /resource/cph.3f05183/
2. /resource/fsa.8d24709/
3. /resource/highsm.64003/
```

### 2. Retrieve JSON data for items

The `loc.gov` website allows for responses to be requested in a data format, like JSON.
Using the same three items as above, request and restrieve the data about the items and save them in local files.

### 3. Use a different parameter

Assume that the LOC website can also receive search requests as a parameter.
This parameter is `q` for "query".
Create a Python script that asks for a query string as an input,
then append that query to a URI, send the request using python requests,
and return the results. The script should print out the results to the terminal.

## Part Two: Adding Content to Your CB Collection Site

The second part of this assignment builds on the collection sites you created last week.
You should use the site you created in [last week's lab]({% link _posts/2024-10-01-lab-4-collectionbuilder.md %}).

Your task is to gather the components for the five digital items represented by
the following URIs located at the Library of Congress's namespace (i.e., `loc.gov`):

```
resource/ds.06560/
resource/ppmsca.18016/
resource/hhh.ok0012.sheet/?sp=8&q=hhh.ok0012
resource/cph.3f05183/
resource/highsm.20336/
```

You will need: a digital image file for each one, and as much metadata about each as you can find. Your goal is to restructure all of this into information
that CollectionBuilder can use, then republish it on your site.

### Decide on an identifier scheme

To link together the metadata and files comprising the digital objects,
you will need to create a standard naming scheme.
I suggest some combination of letters and numbers, joined together in a standard pattern.
For example, you could use some abbreviation of your collection, an underscore, and an item number, such as `nc_001` where `nc` is "new collection" with an appended iterated number after the underscore.
Another possibility would be to use the LCCN numbers for each object.

### Find and organize the digital objects

In some cases, the files may not be immediately downloadable.
In others, they will be easy to find.
In either case, you are looking for a high resolution digital image
in a jpeg or tif format. Once you locate the file, save it and rename it
according to the identifier scheme you created above.
Once the file is downloaded and renamed, move it to your site's `objects` directory.
Make sure the file's name matches the `objectid` column in your metadata spreadsheet.

### Record the metadata for each item

CollectionBuilder supports standard DublinCore elements for digital objects.
Consult each of the above resources, and complete the metadata entry for each one.
To do this, you may use the [sample CSV template provided in the course data repository][csv-template]

**Note**: to use the template, you can upload to GoogleSheets, edit there, then download a CSV copy to add to your collection site. Or, you can create in Python or another editor. Note that the CollectionBuilder docs suggest that editing the CSV in Excel will cause problems (due to the way that Excel encodes the CSV files, particularly line endings).

## Deliverables

* Answers to the requests lab (upload via Canvas)
* Link to your updated and working CollectionBuilder site,
  now populated with the five items you created metadata for
  (all still publishing from your GitHub repo)
* Invite the course instructor to collaborate on the repo

## Resources

* [Collection Builder Guide]({% link _posts/2024-10-06-collectionbuilder-guide.md %})
* [Jekyll Guide]({% link _posts/2024-09-27-jekyll-starter-guide.md %})
* [Assignment page on canvas][canvas-link]

[canvas-link]: https://umich.instructure.com/courses/698670/assignments/2515067
[csv-template]: https://github.com/morskyjezek/si676-2024-data/blob/main/cb-metadata-template.csv