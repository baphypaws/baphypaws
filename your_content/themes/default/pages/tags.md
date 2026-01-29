{# This template is the base for all other templates, meaning that all other templates will be adding to the blocks

&nbsp;  in this template, before they're used to create HTML files. #}

{{ autogenerate\_warning|safe }}

<!DOCTYPE html>

<html lang="en" prefix="og: http://ogp.me/ns#">

<head>

&nbsp;   {%- if google\_analytics\_id %}

&nbsp;   <!-- Global site tag (gtag.js) - Google Analytics -->

&nbsp;   {# When text is surrounded by {{ these double curly braces }}, it's representing a variable that's passed in by

&nbsp;      the Python script that generates the HTML file. That value is dropped into the existing HTML with no changes.

&nbsp;      For example, if the value passed in to `google\_analytics\_id` is `UA-123456789-0`, then

&nbsp;      `id={{ google\_analytics\_id }}` becomes `id=UA-123456789-0` #}

&nbsp;   <script async src="https://www.googletagmanager.com/gtag/js?id={{ google\_analytics\_id }}"></script>

&nbsp;   <script>

&nbsp;     window.dataLayer = window.dataLayer || \[];

&nbsp;     function gtag(){dataLayer.push(arguments);}

&nbsp;     gtag('js', new Date());



&nbsp;     gtag('config', '{{ google\_analytics\_id }}');

&nbsp;   </script>

&nbsp;   {%- endif %}

&nbsp;   {# Naming the blocks like this lets other templates either replace or add onto this block by referencing it by

&nbsp;      name. #}

&nbsp;   {%- block head %}

&nbsp;   <meta charset="UTF-8">

&nbsp;   <link rel="preconnect" href="https://fonts.gstatic.com">

&nbsp;   <link rel="stylesheet" type="text/css" href="{{ base\_dir }}/your\_content/themes/{{ theme }}/css/fonts.css">

&nbsp;   <link rel="stylesheet" type="text/css" href="{{ base\_dir }}/comic\_git\_engine/css/base.css">

&nbsp;   <link rel="stylesheet" type="text/css" href="{{ base\_dir }}/comic\_git\_engine/css/{{ template\_name }}.css">

&nbsp;   <link rel="stylesheet" type="text/css" href="{{ base\_dir }}/your\_content/themes/{{ theme }}/css/stylesheet.css">

&nbsp;   <link rel="stylesheet" type="text/css" href="{{ base\_dir }}/your\_content/themes/{{ theme }}/css/base.css">

&nbsp;   <link rel="stylesheet" type="text/css" href="{{ base\_dir }}/your\_content/themes/{{ theme }}/css/{{ template\_name }}.css">

&nbsp;   {%- if comic\_folder != "" %}

&nbsp;   {# Allows for setting specific CSS for an extra comic. #}

&nbsp;   <link rel="stylesheet" type="text/css" href="{{ base\_dir }}/your\_content/themes/{{ theme }}/css/{{ comic\_folder.strip('/') }}.css">

&nbsp;   {%- endif %}

&nbsp;   <link rel="icon" href="{{ base\_dir }}/favicon.ico" type="image/x-icon" />

&nbsp;   <meta property="og:title" content="{{ comic\_title }}" />

&nbsp;   <meta property="og:description" content="{{ comic\_description }}" />

&nbsp;   <meta property="og:type" content="website" />

&nbsp;   <meta property="og:url" content="{{ comic\_url }}/" />

&nbsp;   <meta property="og:image" content="{{ comic\_url + '/your\_content/images/preview\_image.png' }}" />

&nbsp;   <meta property="og:image:width" content="200" />

&nbsp;   <meta property="og:image:height" content="200" />

&nbsp;   <meta name="viewport" content="width=device-width, initial-scale=1">

&nbsp;   <title>{{ \_title }} - {{ comic\_title }}</title>

&nbsp;   {%- endblock %}

</head>

<body>

{# This is the start of the `body` block. This is where all the visible parts of the website show up. #}

{% block body %}

<div id="container">

&nbsp;   <div id="banner">

&nbsp;       <a id="banner-img-link" href="{{ base\_dir }}/">

&nbsp;           <img id="banner-img" alt="banner" src="{{ banner\_image }}">

&nbsp;       </a>

&nbsp;   </div>

&nbsp;   {%- if links %}

&nbsp;   <div id="links-bar">

&nbsp;   {# For loops let you take a list of values and do something for each of those values. In this case,

&nbsp;      it runs through list of all the links provided by the \[Links Bar] section of your comic\_info.ini file,

&nbsp;      and it generates a link for each of them. #}

&nbsp;   {%- for link in links %}

&nbsp;       <a class="link-bar-link" href="{{ link.url }}" {{ 'target="\_blank"' if link.open\_in\_new\_tab else "" }}>

&nbsp;           {%- if link.image\_url %}

&nbsp;               <img class="link-bar-link-image" src="{{ link.image\_url }}">

&nbsp;           {%- else %}

&nbsp;               {{ link.name }}

&nbsp;           {%- endif %}

&nbsp;       </a>

&nbsp;       {% if not loop.last %}<span class="link-bar-separator">|</span>{% endif %}

&nbsp;   {%- endfor %}

&nbsp;   </div>

&nbsp;   {%- endif %}



&nbsp;  <div> 

&nbsp;	<p><h2> test </h2> </p>
	<p> pee pee </p>

</div>

&nbsp;	

&nbsp;   {% block content %}{% endblock %}



&nbsp;   {%- if enable\_webring  %}

&nbsp;   {% include "webring.tpl" %}

&nbsp;   {%- endif %}



&nbsp;   <div id="powered-by">

&nbsp;       Powered by <a id="powered-by-link" href="https://www.comic-git.com">comic\_git</a> v{{ version }}

&nbsp;   </div>

</div>

{% endblock %}

{# This is the start of the `script` block. Most pages don't need any javascript, so by default it's blank, but some

&nbsp;  pages like infinite\_scroll.tpl will fill this in with a <script> tag. #}

{% block script %}{% endblock %}

</body>

</html>



