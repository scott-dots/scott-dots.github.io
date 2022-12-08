---
layout: home
published: true
---
<div class="home-container">
  <!-- <div class="splash-card">
    <span class="splash-icon"></span>
    <h1 class="splash-title">Stop the Permit</h1>
    <div class="splash-info">
      <p>
        Big-Wall Permits are unnecessary in Yosemite       
      </p>
      <blockquote>
        <p>
          95% of big wall climbers are good stewards ... 5% of climbers are responsible for the mess
        </p>
        <name class="fr">- Climbing Ranger Jesse McGahey</name>
      </blockquote>
      <br>
      <br>
      <p>
      Help to eliminate Yosemite’s proposed Big Wall Permit System by clicking the link below and signing the change.org petition  
      </p> 
      <table>
        <tbody>
          <tr>
            <td>Source</td>
            <td><a href="https://www.change.org/p/eliminate-yosemite-s-proposed-big-wall-permit-system">change.org</a></td>
          </tr>
        </tbody>
      </table>
    </div>
    {% include petition.html %} 
  </div> -->

  {% assign card = site.yosemite | sort: 'weight' %}
  {% for post in card %}
  {% unless post.redirect %}
  <div class="splash-card">
    <h1 class="splash-title">{{ post.title }}</h1>
      {% if post.card %}
        <img src="{{ site.url }}{{ post.card }}" />
	<br>
      {% endif %}
      {% if post.content contains site.excerpt_separator %}
        <div class="splash-info">
          {{ post.excerpt | markdownify }}
          <p>
            <a href="{{ post.url | relative_url }}"><button class="more">Read more&nbsp;&nbsp;></button></a>
            <br>
          </p>
        </div>
      {% else if post.content.size > 10 %}
        <p class="splash-info">
          {{ post.content | markdownify }}
        </p>
      {% endif %}
      {% if post.source %}
        <table>
          <tbody>
            {% for source in post.source %}
            <tr>
              <td>{{ source.title }}</td>
              <td><a href="{{ source.url }}">{{ source.alt }}</a></td>
            </tr>
            {% endfor %}
          </tbody>
        </table>
      {% endif %}
      {% if post.button %}
      {% for button in post.button %}
        {% if button.card == true %}
        {% if button.include and button.include != ‘’ %}
	{% include_relative /_includes/{{ button.include}} %}
	{% else %}
          <a href="{{ button.url }}">
            <button type="submit" style="{{ button.style }}">{{ button.text }}</button>
          </a>
        {% endif %}
        {% endif %}
      {% endfor %}
      {% endif %}
  </div>    
  {% endunless %}
  {% endfor %}
</div>
