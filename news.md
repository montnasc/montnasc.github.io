---
layout: default
title: News
---
# News

<div class="news-intro">
  Latest announcements, publications, and updates from my research.
</div>

<div class="news-grid">
  {% for post in site.posts %}
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
        {{ post.excerpt | strip_html | truncate: 150 }}
      </p>
      
      <a class="news-read-more" href="{{ post.url }}">
        Read more →
      </a>
    </div>
  </article>
  {% endfor %}
</div>

<style>
/* Estilos para a grid de notícias */
.news-intro {
  font-size: 1.1rem;
  color: #555;
  margin-bottom: 2.5rem;
  line-height: 1.6;
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
  height: 100px;
  overflow: hidden;
}

.news-image img {
  width: 50%;
  height: 50%;
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
  font-size: 1.3rem;
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
  margin-bottom: 1rem;
  font-size: 0.9rem;
  color: #666;
}

.news-category {
  background-color: #f0f7ff;
  color: #0366d6;
  padding: 2px 8px;
  border-radius: 12px;
  font-size: 0.8rem;
  font-weight: 500;
}

.news-excerpt {
  color: #555;
  line-height: 1.6;
  margin-bottom: 1.25rem;
}

.news-read-more {
  display: inline-block;
  color: #0366d6;
  text-decoration: none;
  font-weight: 500;
  font-size: 0.95rem;
}

.news-read-more:hover {
  text-decoration: underline;
}

/* Layout responsivo */
@media (min-width: 768px) {
  .news-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (min-width: 1024px) {
  .news-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}

/* Estilos para post individual */
.post {
  max-width: 800px;
  margin: 0 auto;
}

.post-header {
  margin-bottom: 2rem;
}

.post-title {
  font-size: 2rem;
  margin-bottom: 0.5rem;
  line-height: 1.3;
}

.post-meta {
  color: #666;
  font-size: 0.95rem;
  margin-bottom: 2rem;
}

.post-image {
  margin: 2rem 0;
}

.post-image img {
  width: 50%;
  border-radius: 8px;
}

.image-caption {
  text-align: center;
  font-style: italic;
  color: #666;
  margin-top: 0.5rem;
  font-size: 0.9rem;
}

.post-content {
  line-height: 1.7;
  font-size: 1.1rem;
}

.post-content h2 {
  margin-top: 2.5rem;
}

.post-content p {
  margin-bottom: 1.5rem;
}

.post-footer {
  margin-top: 3rem;
  padding-top: 2rem;
  border-top: 1px solid #eaeaea;
}

.post-navigation {
  display: flex;
  justify-content: space-between;
  margin-bottom: 1.5rem;
}

.post-navigation a {
  color: #0366d6;
  text-decoration: none;
  max-width: 45%;
}

.post-navigation a:hover {
  text-decoration: underline;
}

.back-to-news {
  display: inline-block;
  color: #0366d6;
  text-decoration: none;
  font-weight: 500;
}

.back-to-news:hover {
  text-decoration: underline;
}
</style>
