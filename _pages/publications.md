---
layout: page
permalink: /publications/
title: Publications
description: See also <a href=https://dblp.org/pid/307/3268.html> dblp</a> for a complete list. </i>
nav: true
nav_order: 4
---

<!-- _pages/publications.md -->

<!-- Bibsearch Feature -->

{% include bib_search.liquid %}


<div class="tag-filter">
  <span class="tag-pill tag-blockchain active" data-tag="blockchain">blockchain</span>
  <span class="tag-pill tag-networks active" data-tag="networks">networks</span>
  <span class="tag-pill tag-security active" data-tag="security">security</span>
  <span class="tag-pill tag-privacy active" data-tag="privacy">privacy</span>
  <span class="tag-pill tag-resilience active" data-tag="resilience">resilience</span>
  <span class="tag-pill inactive" data-tag="all" style="background:#f5f5f5;color:#bbb;">all</span>
</div>


<div class="publications">
  {% bibliography %}
</div>

<script>
(function() {
  const filters = document.querySelectorAll('.tag-filter .tag-pill');
  filters.forEach(btn => {
    btn.addEventListener('click', () => {
      const tag = btn.dataset.tag;
      if (tag === 'all') {
        filters.forEach(b => b.classList.toggle('active', b.dataset.tag === 'all'));
        document.querySelectorAll('.bibliography li').forEach(p => p.style.display = '');
        return;
      }
      btn.classList.toggle('active');
      const active = [...filters]
        .filter(b => b.classList.contains('active') && b.dataset.tag !== 'all')
        .map(b => b.dataset.tag);
      document.querySelectorAll('.bibliography li').forEach(paper => {
        const inner = paper.querySelector('[data-keywords]');
        const pills = inner
          ? (inner.dataset.keywords || '').split(',').map(s => s.trim()).filter(Boolean)
          : [];
        const show = active.length === 0 || active.some(t => pills.includes(t));
        paper.style.display = show ? '' : 'none';
      });
    });
  });
})();
</script>

