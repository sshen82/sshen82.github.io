---
layout: post
title: Submitting data to GEO with ftp
gh-repo: daattali/beautiful-jekyll
tags: [General]
comments: true
---

Recently, I submitted a dataset to GEO. It was a painful experience, since we only have "ftp" in the server, without "ncftp", "lftp", etc. I worked on it for two days, 
and finally sort out the correct procedure. This post is for keeping the record.

With the account, input ftp ftp-private.ncbi.nlm.nih.gov. Username and password will be provided by the GEO website. After logging into GEO, input "passive" and 
"prompt". The first one allows you to transfer the data, and the second one allows you to transfer multiple data without the server asking you whether to transfer each 
data. With that, using "mput *", it will work.
