{# This template is the base for all other templates, meaning that all other templates will be adding to the blocks
   in this template, before they're used to create HTML files. #}
{{ autogenerate_warning|safe }}
<!DOCTYPE html>
<html lang="en" prefix="og: http://ogp.me/ns#">
<head>
    {# If blocks let you check the value of a variable and then generate different HTML depending on that variable.
       The if block below will check if the `google_analytics_id` variable is defined (set in the Python script by
       the "Tracking ID" value of the "Google Analytics" section in the comic_info.ini file). If so, it then
       includes all the text between the `{% if ... %}` and `{% endif %}` blocks. #}
    {%- if google_analytics_id %}
    <!-- Global site tag (gtag.js) - Google Analytics -->
    {# When text is surrounded by {{ these double curly braces }}, it's representing a variable that's passed in by
       the Python script that generates the HTML file. That value is dropped into the existing HTML with no changes.
       For example, if the value passed in to `google_analytics_id` is `UA-123456789-0`, then
       `id={{ google_analytics_id }}` becomes `id=UA-123456789-0` #}
    <script async src="https://www.googletagmanager.com/gtag/js?id={{ google_analytics_id }}"></script>
    <script>
      window.dataLayer = window.dataLayer || [];
      function gtag(){dataLayer.push(arguments);}
      gtag('js', new Date());

      gtag('config', '{{ google_analytics_id }}');
    </script>
    {%- endif %}
    {# Naming the blocks like this lets other templates either replace or add onto this block by referencing it by
       name. #}
    {%- block head %}
    <meta charset="UTF-8">
    <link rel="preconnect" href="https://fonts.gstatic.com">
    <link rel="stylesheet" type="text/css" href="{{ base_dir }}/your_content/themes/{{ theme }}/css/fonts.css">
    <link rel="stylesheet" type="text/css" href="{{ base_dir }}/comic_git_engine/css/base.css">
    <link rel="stylesheet" type="text/css" href="{{ base_dir }}/comic_git_engine/css/{{ template_name }}.css">
    <link rel="stylesheet" type="text/css" href="{{ base_dir }}/your_content/themes/{{ theme }}/css/stylesheet.css">
    <link rel="stylesheet" type="text/css" href="{{ base_dir }}/your_content/themes/{{ theme }}/css/base.css">
    <link rel="stylesheet" type="text/css" href="{{ base_dir }}/your_content/themes/{{ theme }}/css/{{ template_name }}.css">
    {%- if comic_folder != "" %}
    {# Allows for setting specific CSS for an extra comic. #}
    <link rel="stylesheet" type="text/css" href="{{ base_dir }}/your_content/themes/{{ theme }}/css/{{ comic_folder.strip('/') }}.css">
    {%- endif %}
    <link rel="icon" href="{{ base_dir }}/favicon.ico" type="image/x-icon" />
    <meta property="og:title" content="{{ comic_title }}" />
    <meta property="og:description" content="{{ comic_description }}" />
    <meta property="og:type" content="website" />
    <meta property="og:url" content="{{ comic_url }}/" />
    <meta property="og:image" content="{{ comic_url + '/your_content/images/preview_image.png' }}" />
    <meta property="og:image:width" content="200" />
    <meta property="og:image:height" content="200" />
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>{{ _title }} - {{ comic_title }}</title>
    {%- endblock %}
</head>
<body>
{# This is the start of the `body` block. This is where all the visible parts of the website show up. #}
{% block body %}
<div id="container">
    <div id="banner">
        <a id="banner-img-link" href="{{ base_dir }}/">
            <img id="banner-img" alt="banner" src="{{ banner_image }}">
        </a>
    </div>
    {%- if links %}
    <div id="links-bar">
    {# For loops let you take a list of values and do something for each of those values. In this case,
       it runs through list of all the links provided by the [Links Bar] section of your comic_info.ini file,
       and it generates a link for each of them. #}
    {%- for link in links %}
        <a class="link-bar-link" href="{{ link.url }}" {{ 'target="_blank"' if link.open_in_new_tab else "" }}>
            {%- if link.image_url %}
                <img class="link-bar-link-image" src="{{ link.image_url }}">
            {%- else %}
                {{ link.name }}
            {%- endif %}
        </a>
        {% if not loop.last %}<span class="link-bar-separator">|</span>{% endif %}
    {%- endfor %}
    </div>
    {%- endif %}

    {# This is the start of the `content` block. Nothing is here now because other templates are expected to fill it
       in on their own. It will contain everything on a webpage after the links bar and before the
       "Powered by comic_git" footer. #}
    {% block content %}




<h1 style="text-align: center;"><span style="font-weight: 400;">🐾 BAPHYPAWS&nbsp; 🐾</span><span style="font-weight: 400;"><br /></span><span style="font-weight: 400;">Commissions Info</span></h1>
<h2 style="text-align: center;"><a href="https://forms.gle/HhJFjtusFZN3pAxW6"><strong>COMMISSIONS </strong></a><strong>CLOSED!&nbsp;</strong></h2>
<p style="text-align: center;"><span style="font-weight: 400;">Contact : </span><a href="mailto:baphypaws@gmail.com"><span style="font-weight: 400;">baphypaws@gmail.com</span><span style="font-weight: 400;"><br /></span><span style="font-weight: 400;"><br /></span></a><span style="font-weight: 400;">_______________________________________________________________________</span><span style="font-weight: 400;"><br /><br /></span></p>
<h3 style="text-align: center;"><strong>All commissions are artistic freedom, </strong><strong><br /></strong><strong>and priced $125 per hour. </strong><strong><br /></strong><span style="font-weight: 400;">As a rule of thumb, I recommend one hour per character, </span><span style="font-weight: 400;"><br /></span><span style="font-weight: 400;">with involved backgrounds being another hour. </span><span style="font-weight: 400;"><br /></span><span style="font-weight: 400;">Comic pages require a minimum of three hours. </span><span style="font-weight: 400;"><br /></span><span style="font-weight: 400;"><br /></span><a href="https://forms.gle/HhJFjtusFZN3pAxW6"><strong>CLICK HERE for the COMMISSION REQUEST FORM</strong><span style="font-weight: 400;"><br /></span><span style="font-weight: 400;"><br /></span></a><a href="https://www.dropbox.com/scl/fo/bsygao8g39sm53uox5jb7/AGk8MmCDI0HByXbXWXsjrmo?rlkey=idebld8340gpofeausugs6o4t&amp;dl=0"><span style="font-weight: 400;">Examples of Previous Commissions, Organized by Hour</span></a><span style="font-weight: 400;">&nbsp;</span></h3>
<p style="text-align: center;">&nbsp;</p>
<table style="margin-left: auto; margin-right: auto;" cellpadding="25">
<tbody>
<tr>
<td>
<p><span style="font-weight: 400;">😀💖😊I LIKE TO DRAW😻💗💌</span></p>
</td>
<td>
<p><span style="font-weight: 400;">👎🚫🙅DO NOT DRAW❌😞🫸</span></p>
</td>
</tr>
<tr>
<td style="background-color: #ccffcc;">
<h5 style="text-align: center;"><strong>🌶️ Bodies and Types 🌶️</strong><span style="font-weight: 400;"><br /></span></h5>
<p style="text-align: center;"><span style="font-weight: 400;">Thick thighs | Fat ass | Tummy</span></p>
<p style="text-align: center;"><span style="font-weight: 400;">Exotic genitalia | Size Difference | Big</span></p>
<br />
<h5 style="text-align: center;"><strong>🌶️ Situations 🌶️</strong></h5>
<p style="text-align: center;"><span style="font-weight: 400;">Threesomes, Groups | Anon / Freeuse</span></p>
<p style="text-align: center;"><span style="font-weight: 400;">Transformation | Pet Play | Demon Worship</span></p>
<p style="text-align: center;"><span style="font-weight: 400;">Breeding | Monsterfucking | Public Play</span></p>
<p style="text-align: center;"><span style="font-weight: 400;">Objectification (Plush, Pool Toy, etc.)&nbsp;</span></p>
<br /><br />
<p style="text-align: center;"><strong>🌶️ People and Things 🌶️</strong></p>
<p><span style="font-weight: 400;">Cum / Gooey or Slimy Textures | Smoking</span></p>
<p><span style="font-weight: 400;">Pokemon | DILFs/GILFs | Sex Cults | Masks</span><span style="font-weight: 400;"><br /><br /></span></p>
</td>
<td style="background-color: #ffcccc; text-align: center;">
<p><span style="font-weight: 400;">Anything that is not&nbsp;<br /></span><span style="font-weight: 400;">or cannot give consent</span></p>
<br />
<p><span style="font-weight: 400;">Piss, scat, vomit</span></p>
<br />
<p><span style="font-weight: 400;">Feederism/Gaining</span></p>
<br />
<p><span style="font-weight: 400;">Symbols of hate, <br />prejudice or discrimination</span></p>
<br />
<p><span style="font-weight: 400;">Anything that I would have to&nbsp;<br /></span><span style="font-weight: 400;">explain to law enforcement</span><span style="font-weight: 400;">&nbsp;<br />or my therapist&nbsp;</span></p>
<br />
<p><span style="font-weight: 400;">I will be so mad<br />if you make me&nbsp;</span><span style="font-weight: 400;">talk <br />to the fucking cops</span></p>
</td>
</tr>
</tbody>
</table>
<p style="text-align: center;">&nbsp;</p>
<p style="text-align: center;"><span style="font-weight: 400;">This is an incomplete list, please feel free to reach out and ask! I do not judge.</span></p>
<p style="text-align: center;"><br /><br /><br /></p>
<table cellpadding="25">
<tbody>
<tr style="text-align: center;">
<td>
<h3><span style="font-weight: 400;">ToS</span></h3>
</td>
<td>
<h3><span style="font-weight: 400;">Method</span></h3>
</td>
</tr>
<tr>
<td style="text-align: center;"><br />
<p><em><span style="font-weight: 400;">By commissioning me, you acknowledge having read and agree to follow the following Terms of Service.&nbsp;</span></em></p>
<p><em><span style="font-weight: 400;"><br /></span></em><em><span style="font-weight: 400;">&mdash;------------------------------------</span></em><span style="font-weight: 400;"><br /></span><span style="font-weight: 400;"><br /></span><span style="font-weight: 400;">Commissioned artwork is for personal use only. </span><strong>Above listed commission prices do NOT include commercial rights. </strong><span style="font-weight: 400;">Any profit-making ventures on the part of the client involving the commissioned artwork is strictly forbidden. At my sole discretion I may sell print or electronic copies of any commission, without prior approval from the client. </span><span style="font-weight: 400;">If the client does NOT want their commission sold as a print or in a digital format, it is the client's responsibilty to inform me.&nbsp;<br /></span><span style="font-weight: 400;"><br /></span><span style="font-weight: 400;">Commissioned artwork may </span><strong>NOT</strong><span style="font-weight: 400;">, under </span><strong>ANY</strong><span style="font-weight: 400;"> circumstances, be used as a source for AI learning, or utilized as an NFT. No exceptions.&nbsp;</span></p>
<p><strong><br />Editing, manipulating, reworking or any alterations of my work is strictly forbidden. </strong><span style="font-weight: 400;">For example, cropping an image to use as an icon on social media is totally fine; tracing or painting over my work is not. Please reach out for clarification if need be.&nbsp;</span></p>
<p><br /><strong>Disappearance Clause</strong>&nbsp;<br /><br />if the client has not been in communication for over a year, the commission is considered forfiet and no refunds will be given. This is a last resort clause and I will do everything in my power to avoid it.&nbsp;<br /><br />Note : this only applies when the <span style="text-decoration: underline;"><em>client</em></span>&nbsp;has not responded to communications from&nbsp;<em><span style="text-decoration: underline;">me,</span></em> NOT the other way around. If you have been waiting on a response from me for over a year, something has gone terribly wrong, please reach out immediately.</p>
<p>&nbsp;</p>
<p><strong>Edits</strong></p>
<p><span style="font-weight: 400;">I will accommodate as many requests for revisions as possible, and always when it&rsquo;s due to an error on my part. 99% of the requests I receive for revisions are no problem. </span><strong>In circumstances where more in depth or structural edits are needed, I may ask for an additional fee</strong><span style="font-weight: 400;">, depending on the complexity of the request.&nbsp;</span></p>
<br />
<p><strong>Sharing</strong></p>
<p><strong>Posting your commission on socials is encouraged!</strong><span style="font-weight: 400;">&nbsp; Don&rsquo;t forget to tag me. :) I always appreciate credit/a link back to my website on gallery sites like FurAffinity.</span><span style="font-weight: 400;">&nbsp;</span></p>
<br />
<p><span style="font-weight: 400;">Last Updated : January 2026</span></p>
</td>
<td>
<p style="text-align: center;"><strong>Step 1 : Contact</strong></p>
<p style="text-align: center;"><span style="font-weight: 400;">The client reaches out to the artist via the above linked Google Forms. The artist reviews the information and references given and asks for more information if necessary. Communication primarily occurs through Bluesky DMs, Discord or email. </span><strong><br /></strong></p>
<p style="text-align: center;"><strong><br /></strong><strong>Step 2 : Payment</strong></p>
<p style="text-align: center;"><span style="font-weight: 400;">An invoice is sent to the requested service, for the agreed upon amount. Payment plans are available. Once payment is received, the commission will be placed on the </span><a href="https://trello.com/b/yJO6YQy4"><span style="font-weight: 400;">work trello</span></a><span style="font-weight: 400;">. </span><strong><br /></strong></p>
<p style="text-align: center;"><strong><br /></strong><strong>Step 3 : Drawing!</strong></p>
<p style="text-align: center;"><span style="font-weight: 400;">All commissions are artistic freedom. This gives the artist the flexibility to make minor changes to the character or the style to best fit the project&rsquo;s needs and budget. Examples of these kinds of edits might be painting a character a very dark grey instead of flat black, or slightly moving a marking to better aid composition or clarity. The goal of these edits, if they are made at all, is to be an invisible support working towards the best possible version of the commission. Clients are encouraged to include in their commission request the style preferred, and the artist will make every attempt to fulfill said requests. </span></p>
<p style="text-align: center;"><strong><br /></strong><strong><br /></strong><strong>Step 3a (3+h comms only) Sketch</strong></p>
<p style="text-align: center;"><span style="font-weight: 400;">In the case of longer commissions or comic pages, a sketch or WIP is sent to the client for approval. Edits requested at this stage will count towards the paid hourly rate.</span></p>
<p style="text-align: center;"><strong><br /></strong><strong><br /></strong><strong>Step 3b (3+h comms only) Sketch Revisions</strong></p>
<p style="text-align: center;"><span style="font-weight: 400;">See Step 5</span><strong><br /></strong></p>
<p style="text-align: center;"><strong><br /></strong><strong>Step 4 : Delivery</strong></p>
<p style="text-align: center;"><span style="font-weight: 400;">The artist delivers the finished low resolution (lores) version of the image for approval. Upon approval of the client, the artist will then send the high resolution (hires) version. </span><strong><br /></strong></p>
<p style="text-align: center;"><strong><br /></strong><strong>Step 5 : Revisions</strong></p>
<p style="text-align: center;"><span style="font-weight: 400;">If needed, revisions occur at this stage. If the requested edits are due to oversight from the artist, a thirty minute unpaid grace period is allotted to address said revisions. The thirty minutes are au graits, and NOT a part of the time already paid for. This would be edits like adjusted markings, missing glasses/piercings, and other errors.</span></p>
<p style="text-align: center;"><span style="font-weight: 400;">&nbsp;If the edits requested are more structural, or require more than the allotted half hour of revisions, additional charges of the hourly rate will be requested.&nbsp;</span></p>
<br />
<p style="text-align: center;"><strong>Step 6 : Post</strong></p>
<p style="text-align: center;"><span style="font-weight: 400;">The artist reserves the right to post the commission itself, as well as WIPs or progress videos, to their Discord server and social media/gallery websites. The client may post themselves before or after the artist, at their discretion. A link back is always appreciated. :) </span><span style="font-weight: 400;"><br /></span><span style="font-weight: 400;">In the case of the client NOT wanting the art posted (Usually for gift giving surprise reasons) simply let the artist know.&nbsp;</span></p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>

{% endblock %}

    {%- if enable_webring  %}
    {% include "webring.tpl" %}
    {%- endif %}

    <div id="powered-by">
        Powered by <a id="powered-by-link" href="https://www.comic-git.com">comic_git</a> v{{ version }}
    </div>
</div>
{% endblock %}
{# This is the start of the `script` block. Most pages don't need any javascript, so by default it's blank, but some
   pages like infinite_scroll.tpl will fill this in with a <script> tag. #}
{% block script %}{% endblock %}
</body>
</html>

