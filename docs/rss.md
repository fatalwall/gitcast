---
layout: none
---
<?xml version="1.0" encoding="UTF-8" ?>
<rss version="2.0">
<channel>
  <language>en-US</language>
  <atom:link rel="self" type="application/rss+xml" href="{{ site.github.url }}/rss"/>
  <itunes:new-feed-url>{{ site.github.url }}/rss</itunes:new-feed-url>
  <title>{{ site.title }}</title>
  <link>
    {{ site.github.url }}
  </link>
  <description>
      <![CDATA[Site Description text here]]>
  </description>
  <itunes:type>episodic</itunes:type>
  <itunes:summary>Site Description text here</itunes:summary>
  <itunes:owner>
    <itunes:name>{{ site.github.author }}</itunes:name>
    <itunes:email>name@mail.com</itunes:email>
  </itunes:owner>
  <itunes:author>{{ site.github.author }}</itunes:author>
  <copyright>2020 Peter Varney</copyright>
  <itunes:explicit>yes</itunes:explicit>
  <itunes:category text="Comedy">
    <itunes:category text="Improv"/>
  </itunes:category>
  <itunes:category text="Fiction">
    <itunes:category text="Comedy Fiction"/>
  </itunes:category>
  <itunes:image href="{{ site.github.url }}/{{ site.title }}.jpg"/>
  <image>
    <url>{{ site.github.url }}/{{ site.title }}.jpg</url>
    <title>{{ site.title }}</title>
    <link>{{ site.github.url }}</link>
  </image>

{% for post in site.posts %}
<item>
  <title>{{ post.title }}</title>
  <itunes:title>{{ post.title }}</itunes:title>
  <description><![CDATA[{{ post.excerpt }}]]></description>
  <itunes:summary>{{ post.excerpt }}</itunes:summary>
  <itunes:episodeType>full</itunes:episodeType>
  <itunes:author>{{ site.github.author }}</itunes:author>
  <itunes:image href="{{ site.github.url }}{{ post.id | default: site.title }}.jpg"/>
  <media:content url="{{ site.github.url }}{{ post.id }}.mp3" type="audio/mpeg">
    <media:player url="{{ site.github.url }}{{ post.id }}/embed"/>
  </media:content>
  <media:content url="{{ site.github.url }}{{ post.id | default: site.title }}.jpg" type="image/jpeg"/>
  <pubDate>{{ site.date }}</pubDate>
  <itunes:duration>3071</itunes:duration>
  <enclosure url="{{ site.github.url }}{{ post.id }}.mp3" length="49184685" type="audio/mpeg"/>
  <link>{{ site.github.url }}{{ post.url }}</link>
</item>
{% endfor %}

</channel>
</rss>
