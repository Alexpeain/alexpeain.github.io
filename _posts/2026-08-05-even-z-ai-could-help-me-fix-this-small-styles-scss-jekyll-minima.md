---
layout: post
title: "Even Z.ai could help me fix this small styles.scss jekyll minima "
date: 2026-08-05T20:42:00.000+06:30
image: /images/screenshot_5-8-2026_191923_alexpeain.github.io.jpeg
draft: false
category: Projects
tags:
  - web-dev
  - jekyll
color: "#858b95"
---
I have been using ai to help me fix the style of my blog and it takes me over 1 hour,until i can't take it anymore search and found it on stack overflow .

Minima markdown can resize and hard force to make it smaller on styles.scss doesn't work.



```



#Raw error all it take it  from this 
<div class="avatar-container">
  <img src="../images/my-notion-face-transparent.png" alt="Alex Peain - Backend Developer" class="avatar-img" />
</div> 
#to this 
<div class="avatar-container">
    ![Alex Peain - Backend Developer](../images/my-notion-face-transparent.png){: style="width: 64px; height: 64px; border-radius: 50%; object-fit: cover; border: 1px solid #e5e5e5;" class="avatar-img"}
  </div>
```

<https://stackoverflow.com/questions/14675913/changing-image-size-in-markdown>
