---
layout: single
title: CV
permalink: /cv/
author_profile: true
---

{% assign cv_url = "/assets/cv/cmelcher_cv1025.pdf" | relative_url %}

<style>
  /* keep the footer from crowding the embed */
  .page__content { padding-bottom: 2.5rem; }
  /* fixed viewport for the PDF so toolbars don’t change page height */
  .pdf-container { height: min(85vh, 900px); border: 1px solid #eaeaea; border-radius: 6px; overflow: hidden; }
  .pdf-container object, .pdf-container iframe, .pdf-container embed { width: 100%; height: 100%; display: block; }
</style>

<div class="pdf-container">
  <object
    data="{{ cv_url }}#view=FitH&toolbar=0"
    type="application/pdf">
  </object>
</div>

<p class="text-small"><a href="{{ cv_url }}">Download my CV</a></p>
