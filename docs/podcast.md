---
layout: default
cast:
  name: podcast
#style: assets/css/gitcast.css
---
<link rel="stylesheet" type="text/css" href="{{ page.style | default: 'assets/css/gitcast.css' }}">

{%- for collection in site.collections | where: "label", page.cast.name -%}
  {%- assign sorted = collection.docs | sort: 'date' | reverse -%}
  {%- for post in sorted -%}
    {%- comment -%}Check date to determine if its published{%- endcomment -%}
      {%- capture nowunix %}{{'now' | date: '%s'}}{% endcapture -%}
      {%- capture posttime %}{{post.date | date: '%s'}}{% endcapture -%}
      {% if posttime < nowunix %} 
        {%- comment -%}Figure out episode name{%- endcomment -%}
          {%- assign postname = post.path | remove_first: '_' | remove_first: page.cast.name | remove_first: '/' | remove_first: '.md' -%}
        {%- comment %}Set the Audio file matching episode name{%- endcomment -%}
          {%- assign audio =  site.baseurl | append: '/' | append: page.cast.name  | append: '/' | append: postname | append: '.mp3' -%}	
        {%- comment -%}Set the Cover Image for the Podcast Episode - default.png or image matching episode name{%- endcomment -%}
          {%- assign cover =  page.cast.name  | append: '/' | append: 'default.png' -%}
          {%- for image in collection.files -%}{%- if image.extname == '.png' -%}{%- if image.basename == postname -%}
            {%- assign cover =  page.cast.name | append: '/' | append: image.name -%}
            {%- break -%}
	  {%- endif -%}{%- endif -%}{%- endfor -%}
        {%- comment -%}Create Item record for Episoded{%- endcomment -%}
                               
<article class='gitcast-artical' id='{{post.title}}'>
  <div class='gitcast-content'>
    <div class='gitcast-cover'>
      <img src="{{site.baseurl}}/{{cover}}" alt="ImageDescription" />
    </div>  
    <div class='gitcast-body'>
      <div class="gitcast-header">
        <div class="gitcast-title">
          <h1>
            <a href="{{site.baseurl}}{{post.url}}">{{post.title}}</a>
          </h1>
          <div class='gitcast-date'>
            <a href="{{site.baseurl}}{{post.url}}">
              <time class="published" datetime="{{post.date}}">{{ post.date | date: "%B %d, %Y" }}</time>
            </a>
          </div>
        </div>
        <div class="gitcast-audiocontrol">
          <audio controls controlsList="nodownload">
            <source src="{{audio}}" type="audio/mpeg">
          </audio>
        </div>
      </div>		
      <div class='gitcast-excerpt'>
        <p class="excerpt">{{post.excerptplain}}</p>
      </div>
      <div class="gitcast-action">
        <a class="read-more" href="{{site.baseurl}}{{post.url}}">Read More</a>
      </div>
    </div>
  </div>
</article>
     
      {%- endif -%}
  {%- endfor -%}
{%- endfor -%}
