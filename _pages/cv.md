---
layout: single
title: CV
permalink: /cv/
author_profile: true
---

{% assign cv_url = "/assets/cv/cmelcher_cv1025.pdf" | relative_url %}

<p><a class="btn btn--primary" href="{{ cv_url }}">Download my CV (PDF)</a></p>

<!-- Embedded PDF viewer -->
<div>
  <object
    data="{{ cv_url }}#view=FitH"
    type="application/pdf"
    style="width:100%; height:820px; border:1px solid #eaeaea; border-radius:6px;">
  </object>
</div>

<p class="text-small">
  If the PDF doesn’t display, <a href="{{ cv_url }}">open it in a new tab</a>.
</p>
