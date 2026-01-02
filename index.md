---
layout: single
author_profile: true
permalink: /
title: "Hi, I'm Ronald."
excerpt: "Principal Applied Scientist | AI Agents | Builder"
---

I build proactive AI teammates and scalable agent systems. Currently, I'm a Principal Applied Scientist at Oracle. Outside of work, I also...

* **[Write](/writing/)** about agentic workflows, system architecture, and my journey to ...
* **[Prototype](/prototyping/)** new tools like "Nexus Foundation" and personal productivity bots.

---

## ✍️ Latest Writing
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