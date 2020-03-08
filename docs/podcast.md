---
layout: none
collectionType: podcast
---

{%- for collection in site.collections | where: "label", page.collectionType -%}
  {%- for post in collection.docs -%}
    {%- comment -%}Check date to determine if its published{%- endcomment -%}
      {%- capture nowunix %}{{'now' | date: '%s'}}{% endcapture -%}
      {%- capture posttime %}{{post.date | date: '%s'}}{% endcapture -%}
      {% if posttime < nowunix %} 
        {%- comment -%}Figure out episode name{%- endcomment -%}
          {%- assign postname = post.path | remove_first: '_' | remove_first: page.collectionType | remove_first: '/' | remove_first: '.md' -%}
        {%- comment %}Set the Audio file matching episode name{%- endcomment -%}
          {%- assign audio =  site.github.url | append: '/' | append: page.collectionType  | append: '/' | append: postname | append: '.mp3' -%}	
        {%- comment -%}Set the Cover Image for the Podcast Episode - default.jpg or image matching episode name{%- endcomment -%}
          {%- assign cover =  site.github.url | append: '/' | append: page.collectionType  | append: '/' | append: 'default.jpg' -%}
          {%- for image in collection.files | where: "image", true -%}
            {%- if image.basename == postname -%}
              {%- assign cover =  site.github.url | append: '/' | append: page.collectionType | append: '/' | append: postname | append: '.jpg' -%}
              {%- break -%}
            {%- endif -%}
          {%- endfor -%}
        {%- comment -%}Create Item record for Episoded{%- endcomment -%}
                              
        <div id='{{postname}}'>
          <!--
          <title>{{ post.title }}</title>
          <itunes:summary>{{ post.excerptplain }}</itunes:summary>
          <itunes:image href="{{cover}}"/>
          <media:content url="{{audio}}" type="audio/mpeg">
            <media:player url="{{ site.github.url }}{{ post.id }}/embed"/>
          </media:content>
          <pubDate>{{ site.date }}</pubDate>
          -->
          <div class="body excerpt-content">
		        <p class="excerpt" style="white-space:pre-wrap;">{{post.excerptplain}}</p>
		        <span class="action"><a class="read-more" href="{{post.url}}">Read More</a></span>
		      </div>
        </div>
     
      {%- endif -%}
  {%- endfor -%}
{%- endfor -%}
