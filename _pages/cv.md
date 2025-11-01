---
layout: page
title: CV
permalink: /cv/
---

{% assign cv_url = "/assets/cv/cmelcher_cv1025.pdf" | relative_url %}

<p><a class="btn" href="{{ cv_url }}">Download my CV (PDF)</a></p>

<object
  data="{{ cv_url }}"
  type="application/pdf"
  width="100%"
  height="1000">
  <p>Your browser can’t display PDFs inline.
     <a href="{{ cv_url }}">Download the PDF</a> instead.</p>
</object>
