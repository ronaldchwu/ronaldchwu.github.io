---
layout: single
author_profile: true
permalink: /
title: "Ronald Wu."
excerpt: "Building AI Agents & Scalable Systems."
---

My focus is on creating proactive AI teammates and scalable agent systems. Currently, I'm a Principal Applied Scientist at Oracle. Outside of work, I also...

* **[Sharing thoughts on](/writing/)** agentic workflows, system architecture, and my journey to ...
* **[Building experiments like](/prototyping/)** "Nexus Foundation" and personal productivity bots.

---

## ✍️ Articles
<ul>
  {% for post in site.tags['Writing'] limit:5 %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      <small style="color: #888;">{{ post.date | date: "%B %d, %Y" }}</small>
    </li>
  {% endfor %}
</ul>

## 🛠 Prototyping
<ul>
  {% for post in site.tags['Prototyping'] limit:5 %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      <small style="color: #888;">{{ post.date | date: "%B %d, %Y" }}</small>
    </li>
  {% endfor %}
</ul>