---
layout: default
title: Publications
---

<h1>Publications</h1>

<div id="publications-list">
  <!-- As publicações serão carregadas aqui -->
  <p>Loading publications...</p>
</div>

<p><a href="/publications.bib" download>📥 Download complete bibliography (BibTeX)</a></p>

<script>
// Função para formatar autores
function formatAuthors(authors) {
  return authors
    .replace(/ and /g, ', ')
    .replace(/Monteiro Nascimento, Matheus/g, '<strong>Monteiro Nascimento, Matheus</strong>');
}

// Carrega e formata as publicações
fetch('/assets/publications.bib')
  .then(response => response.text())
  .then(bibtex => {
    const entries = [];
    const blocks = bibtex.split('@');
    
    blocks.forEach(block => {
      if (block.trim()) {
        const lines = block.split('\n');
        const firstLine = lines[0];
        if (firstLine.includes('{')) {
          const [type, id] = firstLine.split('{');
          const entry = {
            type: type.trim(),
            id: id.replace(',', '').trim(),
            year: '',
            title: '',
            author: '',
            journal: '',
            volume: '',
            number: '',
            pages: '',
            doi: '',
            url: ''
          };
          
          lines.slice(1).forEach(line => {
            const match = line.match(/\s*(\w+)\s*=\s*{([^}]+)}/);
            if (match) {
              const key = match[1];
              const value = match[2];
              entry[key] = value;
            }
          });
          
          // Extrai o ano de várias formas possíveis
          if (entry.year) {
            entry.year = entry.year.replace(/[{}]/g, '').trim();
          }
          
          entries.push(entry);
        }
      }
    });
    
    // Ordena por ano (mais recente primeiro)
    entries.sort((a, b) => b.year - a.year);
    
    // Agrupa por ano
    const byYear = {};
    entries.forEach(entry => {
      if (!byYear[entry.year]) byYear[entry.year] = [];
      byYear[entry.year].push(entry);
    });
    
    // Renderiza
    const container = document.getElementById('publications-list');
    let html = '';
    
    // Ordena anos decrescente
    const years = Object.keys(byYear).sort((a, b) => b - a);
    
    years.forEach(year => {
      html += `<h2>${year}</h2>`;
      
      byYear[year].forEach(pub => {
        html += `
        <div class="publication">
          <p class="title"><strong>${pub.title || ''}</strong></p>
          <p class="authors">${formatAuthors(pub.author || '')}</p>
          <p class="journal">
            ${pub.journal ? `<em>${pub.journal}</em>` : ''}
            ${pub.volume ? `, ${pub.volume}` : ''}
            ${pub.number ? `(${pub.number})` : ''}
            ${pub.pages ? `: ${pub.pages}` : ''}
            ${pub.year ? `, ${pub.year}` : ''}
          </p>
          ${pub.doi ? `<p class="doi">DOI: <a href="https://doi.org/${pub.doi}">${pub.doi}</a></p>` : ''}
          ${pub.url ? `<p class="link"><a href="${pub.url}">🔗 Link</a></p>` : ''}
        </div>
        <hr>
        `;
      });
    });
    
    container.innerHTML = html;
  })
  .catch(error => {
    document.getElementById('publications-list').innerHTML = 
      '<p>Error loading publications. Please try again later.</p>';
    console.error('Error:', error);
  });
</script>

<style>
.publication {
  margin: 1.5rem 0;
  padding: 1rem 0;
}
.publication .title {
  margin-bottom: 0.3rem;
  font-size: 1.1rem;
}
.publication .authors {
  margin: 0.2rem 0;
  color: #555;
  font-size: 0.95rem;
}
.publication .journal {
  margin: 0.2rem 0;
  color: #666;
  font-size: 0.9rem;
}
.publication .doi, .publication .link {
  margin: 0.2rem 0;
  font-size: 0.85rem;
}
hr {
  border: none;
  border-top: 1px solid #eee;
  margin: 1rem 0;
}
</style>
