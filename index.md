---
layout: default
title: Home
---
![Photo of Matheus Monteiro Nascimento](/assets/images/Screenshot.png){: .profile-left style="width: 140px; height: 140px; object-fit: cover; border-radius: 50%; float: left; margin-right: 1.5rem;"}

Welcome — I am a Postdoctoral Research Associate in the Institute of Sustainable Chemistry at Leuphana University Lüneburg. I hold a PhD in Physics Education from the Federal University of Rio Grande Do Sul (UFRGS) in Brazil, and was a Professor in their Physics Department prior to my current leave. The central focus of my research is on equity, diversity, and identity in Science Education.

---

## Latest News

<div class="home-news">
  {% for post in site.posts limit:3 %}
  <article class="news-preview">
    <div class="news-preview-content">
      <h3 class="news-preview-title">
        <a href="{{ post.url }}">{{ post.title }}</a>
      </h3>
      <div class="news-preview-meta">
        <time datetime="{{ post.date | date_to_xmlschema }}">
          {{ post.date | date: "%B %d, %Y" }}
        </time>
      </div>
      <p class="news-preview-excerpt">
        {{ post.excerpt | strip_html | truncate: 120 }}
      </p>
      <a class="news-preview-link" href="{{ post.url }}">Read more →</a>
    </div>
  </article>
  {% endfor %}
</div>

<p class="all-news-link">
  <a href="/news">View all news →</a>
</p>

<style>
.home-news {
  margin: 2rem 0;
}

.news-preview {
  margin-bottom: 2rem;
  padding-bottom: 1.5rem;
  border-bottom: 1px solid #eaeaea;
}

.news-preview:last-child {
  border-bottom: none;
  margin-bottom: 1rem;
}

.news-preview-title {
  margin: 0 0 0.5rem 0;
  font-size: 1.2rem;
  font-weight: 600;
  line-height: 1.4;
}

.news-preview-title a {
  color: #111;
  text-decoration: none;
}

.news-preview-title a:hover {
  color: #0366d6;
}

.news-preview-meta {
  color: #666;
  font-size: 0.9rem;
  margin-bottom: 0.75rem;
}

.news-preview-excerpt {
  color: #555;
  line-height: 1.5;
  margin-bottom: 1rem;
  font-size: 0.95rem;
}

.news-preview-link {
  color: #0366d6;
  text-decoration: none;
  font-size: 0.9rem;
  font-weight: 500;
}

.news-preview-link:hover {
  text-decoration: underline;
}

.all-news-link {
  text-align: right;
  margin-top: 1.5rem;
}

.all-news-link a {
  color: #0366d6;
  text-decoration: none;
  font-weight: 500;
}

.all-news-link a:hover {
  text-decoration: underline;
}

/* Clearfix para a imagem flutuante */
.profile-left {
  clear: both;
}

/* Responsividade */
@media (max-width: 600px) {
  .profile-left {
    float: none;
    display: block;
    margin: 0 auto 1.5rem;
  }
  
  .news-preview-title {
    font-size: 1.1rem;
  }
}
</style>
