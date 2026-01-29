---
layout: default
title: Home
---
![Photo of Matheus Monteiro Nascimento](/assets/images/Screenshot.png){: .profile-left style="width: 140px; height: 140px; object-fit: cover; border-radius: 50%; float: left; margin-right: 1.5rem;"}

Welcome — I am a Postdoctoral Research Associate in the Institute of Sustainable Chemistry at Leuphana University Lüneburg. I hold a PhD in Physics Education from the Federal University of Rio Grande Do Sul (UFRGS) in Brazil, and was a Professor in their Physics Department prior to my current leave. The central focus of my research is on equity, diversity, and identity in Science Education.

---

## Latest News

<div class="news-grid home-news-grid">
  {% for post in site.posts limit:3 %}
  <article class="news-card">
    {% if post.image %}
    <div class="news-image">
      <a href="{{ post.url }}">
        <img src="{{ post.image }}" alt="{{ post.title }}">
      </a>
    </div>
    {% endif %}
    
    <div class="news-content">
      <h2 class="news-title">
        <a href="{{ post.url }}">{{ post.title }}</a>
      </h2>
      
      <div class="news-meta">
        <time datetime="{{ post.date | date_to_xmlschema }}">
          {{ post.date | date: "%B %d, %Y" }}
        </time>
        {% if post.categories %}
          <span class="news-category">
            {{ post.categories | first }}
          </span>
        {% endif %}
      </div>
      
      <p class="news-excerpt">
        {{ post.excerpt | strip_html | truncate: 120 }}
      </p>
      
      <a class="news-read-more" href="{{ post.url }}">
        Read more →
      </a>
    </div>
  </article>
  {% endfor %}
</div>

<div class="view-all-news">
  <a href="/news" class="view-all-button">
    View all news
    <svg width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg">
      <path d="M8 0L6.59 1.41L12.17 7H0V9H12.17L6.59 14.59L8 16L16 8L8 0Z" fill="currentColor"/>
    </svg>
  </a>
</div>

<style>
/* Clearfix para a imagem de perfil */
.profile-left {
  clear: both;
}

/* Grid de notícias na home */
.home-news-grid {
  margin: 2.5rem 0;
}

.news-grid {
  display: grid;
  gap: 2rem;
}

.news-card {
  border: 1px solid #eaeaea;
  border-radius: 8px;
  overflow: hidden;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
  background: white;
}

.news-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.1);
}

.news-image {
  height: 180px;
  overflow: hidden;
}

.news-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.3s ease;
}

.news-card:hover .news-image img {
  transform: scale(1.05);
}

.news-content {
  padding: 1.5rem;
}

.news-title {
  margin: 0 0 0.75rem 0;
  font-size: 1.25rem;
  line-height: 1.4;
}

.news-title a {
  color: #111;
  text-decoration: none;
}

.news-title a:hover {
  color: #0366d6;
}

.news-meta {
  display: flex;
  align-items: center;
  gap: 1rem;
  margin-bottom: 0.75rem;
  font-size: 0.85rem;
  color: #666;
}

.news-category {
  background-color: #f0f7ff;
  color: #0366d6;
  padding: 2px 8px;
  border-radius: 12px;
  font-size: 0.75rem;
  font-weight: 500;
}

.news-excerpt {
  color: #555;
  line-height: 1.6;
  margin-bottom: 1.25rem;
  font-size: 0.95rem;
}

.news-read-more {
  display: inline-block;
  color: #0366d6;
  text-decoration: none;
  font-weight: 500;
  font-size: 0.9rem;
}

.news-read-more:hover {
  text-decoration: underline;
}

/* Botão para ver todas as notícias */
.view-all-news {
  text-align: center;
  margin: 2.5rem 0 1rem 0;
}

.view-all-button {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  color: #0366d6;
  text-decoration: none;
  font-weight: 500;
  padding: 10px 20px;
  border: 1px solid #0366d6;
  border-radius: 6px;
  transition: all 0.2s ease;
  font-size: 0.95rem;
}

.view-all-button:hover {
  background-color: #0366d6;
  color: white;
  text-decoration: none;
}

/* Layout responsivo */
@media (min-width: 768px) {
  .news-grid {
    grid-template-columns: repeat(3, 1fr);
  }
  
  .home-news-grid .news-image {
    height: 160px;
  }
  
  .home-news-grid .news-title {
    font-size: 1.1rem;
  }
  
  .home-news-grid .news-excerpt {
    font-size: 0.9rem;
  }
}

@media (max-width: 767px) {
  .news-grid {
    grid-template-columns: 1fr;
  }
  
  .profile-left {
    float: none;
    display: block;
    margin: 0 auto 1.5rem;
  }
}

@media (max-width: 600px) {
  .home-news-grid .news-image {
    height: 150px;
  }
  
  .news-content {
    padding: 1.25rem;
  }
}
</style>
  .news-preview-title {
    font-size: 1.1rem;
  }
}
</style>
