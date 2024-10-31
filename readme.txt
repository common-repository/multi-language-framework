=== Multi-Language Framework ===
Contributors: BIREME, HackLab
Donate link: http://reddes.bvsalud.org/projects/multi-language-framework/
Tags: multilanguage, translation, cms
Requires at least: 3.0
Tested up to: 3.0.1
Stable tag: Not available

Handles creation of multilingual content.


== Description ==

Handles creation of multilingual content.

This plugin is a work in progress and an effort to be an alternative for handling with multiple languages in a single WordPress translation.

Here is a description of how it works:

1. Current solutions and why I dont like them:

Q-Translate -> saves the content of the post int the same post_content field of the database, separating the languages with html comments.. When the theme outputs the content of a post, it gets filtered and displays only one language. Appart from that, this is an excelent plugin. But I junt cant sleep well at night knowing my database is like this...

WPML -> creates a lot of extra tables in a complex database structure and is associated with a translating service. In the top of that, the plugin does a lot more than juts adding the multi language support and claims itself as a cms solution for wordpress... I like plugin that do only one thing very well done.

2. How do I think that can be done?

2.1 translating posts

First, I think it can be done without adding any extra table or doing anything out of the database structure.

The approach Im using is to treat translations as post types. So, for instance, if I would translate my posts to spanish, there would be the native "post" post type and the plugin would add the "post_translation_es" post type.

In the edit posts screen, there would be an extra column called 'translations' that would show for each post if it already have the spanish translation. If it has, there is a button 'edit', if it dont, 'add'. If you go to the edit screen of the spanish posts, you would see the same thing, the other way round. 

This part is already coded and working fine.

2.2 translating everything else (appart from taxonomies)

I think its nice to be able to translate everything on the site (The site title, te text of a text widget, etc). So what Im trying to do is to add a filter in get_option() and update/add_option() to allways check which language are we visiting right now (int the front end or the admin, does not matter) and allways look for a corresponding option in the current language.

For instance.. if you do a get_option('option_name') and are visiting the spanish site, it will try to find an option called 'option_name_es'. If there is not, it will get the default. Same thing when saving.

== Installation ==

1. Download the package
2. Upload to the plugins folder
3. Activate it

== FAQ ==

1. I have placed some widgets in the sidebar but they wont show up!

All the options you set in the admin are language-independent. So you can have a different set of wigets for each language of your site. If you want a widget to allways appear you have to edit the widgets settings for all the languages.

== Known Issues ==

Will not work with Post types with a name bigger than 15 chars 
