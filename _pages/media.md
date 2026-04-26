---
layout: page
title: Media
permalink: /media/
description:
nav: true
nav_order: 2
papers: ["Commercial Persuasion in AI-Mediated Conversations", On the conversational persuasiveness of GPT-4", "MEDITRON-70B: Scaling Medical Pretraining for Large Language Models", "Personal"]
---


<!-- pages/media.md -->
<!-- Side navigation - positioned outside main content -->
<nav id="media-toc" data-toggle="toc" class="media-sidebar">
  <ul class="nav nav-pills flex-column">
    {%- for paper in page.papers %}
    {%- assign paper_id = paper | slugify -%}
    <li class="nav-item">
      <a class="nav-link" href="#{{ paper_id }}">{{ paper }}</a>
    </li>
    {%- endfor %}
  </ul>
</nav>

<!-- Main content -->
<div class="media" style="margin-top: 24px; flex-direction: column">

{%- for paper in page.papers %}
  {%- assign categorized_media = site.media | where: "related_paper", paper -%}
  {%- assign sorted_media = categorized_media | sort: "importance" -%}
  {%- assign paper_id = paper | slugify -%}

<div class="container" id="{{ paper_id }}">
  <h2 class="category" style="color: #c5c5c5; border-bottom: 1px solid #ffffff; margin-top: 24px">{{ paper }}</h2>
<!-- Generate cards for each media -->
   <div class="row row-cols-1 row-cols-md-3">
   {%- for media in sorted_media -%}
       {% include media.html %}
   {%- endfor %}
   </div>
</div>

{%- endfor %}

</div>

<script>
  // Wait for jQuery to be loaded
  (function checkJQuery() {
    if (typeof jQuery !== 'undefined') {
      // Smooth scrolling for anchor links
      $('#media-toc a[href^="#"]').on('click', function(e) {
        e.preventDefault();
        var target = $(this.getAttribute('href'));
        if (target.length) {
          $('html, body').stop().animate({
            scrollTop: target.offset().top - 100
          }, 500);
        }
      });

      // Highlight active section in navigation based on scroll position
      function updateActiveSection() {
        var scrollPos = $(window).scrollTop() + 200;
        var sections = [];
        
        // Collect all sections with their positions
        $('#media-toc a').each(function() {
          var href = $(this).attr('href');
          var section = $(href);
          if (section.length) {
            sections.push({
              link: $(this),
              href: href,
              top: section.offset().top,
              bottom: section.offset().top + section.outerHeight()
            });
          }
        });
        
        // Find the current section
        var currentSection = null;
        for (var i = sections.length - 1; i >= 0; i--) {
          if (scrollPos >= sections[i].top) {
            currentSection = sections[i].link;
            break;
          }
        }
        
        // Update active state
        $('#media-toc a').removeClass('active');
        if (currentSection) {
          currentSection.addClass('active');
        } else if (sections.length > 0) {
          sections[0].link.addClass('active');
        }
      }

      // Update on scroll with throttling
      var scrollTimeout;
      $(window).on('scroll', function() {
        if (scrollTimeout) {
          clearTimeout(scrollTimeout);
        }
        scrollTimeout = setTimeout(updateActiveSection, 10);
      });
      
      // Initial update
      $(document).ready(function() {
        updateActiveSection();
      });
    } else {
      // jQuery not loaded yet, check again in 50ms
      setTimeout(checkJQuery, 50);
    }
  })();
</script>
