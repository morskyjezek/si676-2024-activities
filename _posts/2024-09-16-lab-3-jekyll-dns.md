---
layout: post
title:  "Lab 3: DNS and A Jekyll Static Site"
date:   2024-09-16
categories: activities web dns jekyll serverless labs
---


This page contains the questions for Lab 03: DNS and Jekyll

## GitHub Pages & Jekyll Tasks

1. Set up a new GitHub repository and connect it to a repo on your local machine. Suggested name: `test-site-1` (or something similar)
2. Activate GitHub pages: [https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site)
3. Add a `README.md` (if you haven't already) and `index.html` so there is information in the repo, and also a published page; for this week, provide URL to repo and to published site

### Over the next two weeks (due Sep 30)

4. Initiate Jekyll in your local repo and publish your first serverless site (more details in online assignment): [https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/about-github-pages-and-jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/about-github-pages-and-jekyll)

## DNS Questions

1. Use the `dig` command to query `si.umich.edu`. What is the response and how would you explain it?
2. Use the `dig` command to query `si.umich.edu`. What is the command to return only the "answer" section of the response?  
3. Use the command for the above response, and pipe the output to a file named `mysite-dns-record.txt` (where UNIQNAME is your uniqname). Provide the command and the text file.

## Bonus

5. Note that you can ask for multiple domain names. For example: `dig +noall +answer si.umich.edu umich.edu wisc.edu education.wisc.edu`. The response is a good use case for a tool like `awk`. If you use a pipe to route the data from dig to awk, can you produce a comma-separated-values-like output of just the domain and the IP address? 
  * The `awk` command is actually a sort of mini program language, particularly useful for querying and parsing text files with columns. If you want to learn more about it, you can look at the G-AWK manual at [https://www.gnu.org/software/gawk/manual/gawk.html](https://www.gnu.org/software/gawk/manual/gawk.html). It is very useful for parsing data in columns, which is a frequent pattern seen in the command line/text interface. Variables are named with dollar signs `$1` and the output patterns are enclosed in curly braces `{}`. This should be very similar to the exmaple presented in the slack channel, but you will need to add in a comma for the output.

  ## Resources

* [Accompanying slides][slides]
* [Assignment page on canvas][canvas-link]

[slides]: https://docs.google.com/presentation/d/1iSu3lnByhIsORFVL93oMJ-zAog23SaKpj_bo5VA4V70/edit?usp=sharing
[canvas-link]: 
