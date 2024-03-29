---
title: "{{ replace .Name "-" " " | title }}"
description: ""
summary: ""
date: {{ .Date }}
lastmod: {{ .Date }}
draft: false
menu:
  docs:
    parent: ""
    identifier: "{{ .File.ContentBaseName }}-{{ now.Unix }}"
    weight: 10
toc: true
seo:
  title: ""
  description: ""
  canonical: ""
  noindex: false
---