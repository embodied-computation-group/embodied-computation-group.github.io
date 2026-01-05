---
title: Publications
permalink: /publication/
---

For a complete list, see Dr. Micah Allen's [Google Scholar profile](https://scholar.google.com/citations?user=C49AeHAAAAAJ&hl=en).

We try to include links for all of our papers. If you cannot access one of our papers, please let us know.

<hr>

<div id="publications-loading">Loading publications from Zotero...</div>
<div id="publications-error" style="display:none; color: red;"></div>
<div id="publications-list"></div>

<script>
(function() {
  const ZOTERO_USER_ID = '5500260';
  const API_URL = `https://api.zotero.org/users/${ZOTERO_USER_ID}/publications/items?format=json&sort=date&direction=desc&limit=100`;

  fetch(API_URL)
    .then(response => {
      if (!response.ok) throw new Error('Failed to fetch publications');
      return response.json();
    })
    .then(items => {
      document.getElementById('publications-loading').style.display = 'none';

      if (items.length === 0) {
        document.getElementById('publications-list').innerHTML = '<p>No publications found.</p>';
        return;
      }

      // Extract year from various date formats
      function extractYear(dateStr) {
        if (!dateStr) return 'Unknown';
        // Try to find a 4-digit year anywhere in the string
        const match = dateStr.match(/\b(19|20)\d{2}\b/);
        return match ? match[0] : 'Unknown';
      }

      // Group by year
      const byYear = {};
      items.forEach(item => {
        const data = item.data;
        if (data.itemType === 'attachment' || data.itemType === 'note') return;

        const year = extractYear(data.date);
        if (!byYear[year]) byYear[year] = [];
        byYear[year].push(data);
      });

      // Sort years descending
      const years = Object.keys(byYear).sort((a, b) => b.localeCompare(a));

      let html = '';
      years.forEach(year => {
        html += `<h3>${year}</h3>\n`;
        byYear[year].forEach(pub => {
          // Format authors
          let authors = '';
          if (pub.creators && pub.creators.length > 0) {
            authors = pub.creators
              .filter(c => c.creatorType === 'author')
              .map(c => c.lastName ? `${c.lastName}, ${c.firstName ? c.firstName.charAt(0) + '.' : ''}` : c.name)
              .join(', ');
          }

          // Format title with link if available
          let title = pub.title || 'Untitled';
          if (pub.url) {
            title = `<a href="${pub.url}" target="_blank">${title}</a>`;
          } else if (pub.DOI) {
            title = `<a href="https://doi.org/${pub.DOI}" target="_blank">${title}</a>`;
          }

          // Format publication info
          let venue = '';
          if (pub.publicationTitle) venue = pub.publicationTitle;
          else if (pub.journalAbbreviation) venue = pub.journalAbbreviation;
          else if (pub.proceedingsTitle) venue = pub.proceedingsTitle;
          else if (pub.bookTitle) venue = pub.bookTitle;

          let details = [];
          if (venue) details.push(`<em>${venue}</em>`);
          if (pub.volume) details.push(`${pub.volume}${pub.issue ? '(' + pub.issue + ')' : ''}`);
          if (pub.pages) details.push(pub.pages);

          html += `<p style="margin-bottom: 1em;">`;
          html += `<strong>${title}</strong><br>`;
          if (authors) html += `${authors}<br>`;
          if (details.length > 0) html += `${details.join(', ')}`;
          html += `</p>\n`;
        });
      });

      document.getElementById('publications-list').innerHTML = html;
    })
    .catch(error => {
      document.getElementById('publications-loading').style.display = 'none';
      document.getElementById('publications-error').style.display = 'block';
      document.getElementById('publications-error').textContent = 'Error loading publications: ' + error.message;
      console.error('Zotero API error:', error);
    });
})();
</script>

<hr>

### Copyright Notice

The documents listed here are available for downloading and have been provided as a means to ensure timely dissemination of scholarly and technical work on a noncommercial basis. Copyright and all rights therein are maintained by the authors or by other copyright holders, notwithstanding that they have offered their works here electronically. It is understood that all persons copying this information will adhere to the terms and constraints invoked by each author's copyright. These works may not be re-posted without the explicit permission of the copyright holder.
