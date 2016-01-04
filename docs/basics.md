# Basic Structure

This document explains the basic content structure of the [LGM Video Archive](http://libregraphicsmeeting.org/video/) website.

The archive is - as of fall 2015 - built with WordPress. However, it should be possible to migrate the data into any other system in the future.

## Main content types

The main content types of the archive are:

1. **Talks** : since this is the most important content, we use the "post", the default content type in WordPress. We simply [rename it](../plugins/lgm-video/lgm-talks.php) as "Talks".
2. **Speakers** : a custom taxonomy, [defined](../plugins/lgm-video/lgm-speakers.php) in our functionality plugin.
3. **Topics** : a taxonomy - for simplicity, we use the built-in "tags" functionality, and [rename it](../plugins/lgm-video/lgm-topics.php) as "Topics".

### Talks : content metadata

The content metadata we want to attach to Talks. They are implemented as WordPress [custom fields](https://codex.wordpress.org/Custom_Fields).

- Video URL: `talk_video` - can be a direct link to video file, for example: http://video.constantvzw.org/LGM15/day-04/38-Snelting-Conversations.ogv ... or a link to Youtube or Archive.org
- Slides URL: `talk_slides` - can be a direct link to the slides, or to a web page displaying them. 
- Audio URL: `talk_audio` - audio recording

Other metadata we could add at some moment: 

- transcript
- <del>audio recording</del> (added)
- language : there were talks in French at LGM 2007
- licence : some talks in the 2007 have licence information: CC-BY, CC-BY-SA, Public Domain...

Note: Should we use specific fields for Youtube and Archive.org? This doesn't seem helpful. The ElementJS media player (included in WordPress) can handle Youtube links as well as direct links to OGV or MP4 files. So let's keep it simple and use one custom field for all video formats and providers.

#### Talks: Categories

The default *categories* taxonomy could be used to identify the event: LGM 2006, LGM 2007, etc. We could bypass the category and identify the the event by the year ... but we could also decide to open the video archive to related events (such as LGRU, Relearn, etc...) - in that case, it will be necessary to identify the events by a taxonomy.

This taxonomy could hold further metadata:

- `event_location`: the city where the event takes place.

### Speakers: content metadata

The speakers are handled as a custom taxonomy. There are three default content fields for a taxonomy: Name, Slug, Description.

1. **Name:** the name of the speaker
2. **Slug:** how the name will be rendered in the URL
3. **Description:** the speaker biography

**Additional fields:** implemented as Custom Fields. Since WordPress 4.4, taxonomies offer support for custom metadata. 

- **URL:** personal homepage of the speaker. Field ID: `speaker_url` - could also be used for social media profiles, WikiPedia page, etc.

## Miscellaneous

In a first iteration, we defined the Speaker as a *Post Type* (in order to have more flexibility, such as adding custom fields, images, URL, etc). However, with the new native support for *Term Metadata* in WordPress 4.4 (released December 2015), we consider that the archive will be more future-proof if we define the Speaker as a *[Custom Taxomony](https://codex.wordpress.org/Custom_Taxonomies#Custom_Taxonomies)*.

Some motivations behind that decision:
- posts2posts relationships cannot be easily "imported" with the WordPress eXtended RSS file format - taxonomy terms can.
- posts2posts isn't core WordPress functionality and may become a maintenance issue in the future.
