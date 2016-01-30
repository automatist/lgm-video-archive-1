# Import

Some notes about methods for importing talk data into the archive.

Since the current website runs in WordPress, we import data using the  WordPress eXtended RSS file format (used by native WordPress import / export).

To export such a file from an existing website: in wp-admin, go into Tools > Export.

To import such a file, it is needed to install the [WordPress Importer](https://wordpress.org/plugins/wordpress-importer/) plugin.

## Import FAQ

**Q:** Is it ok to define only the visible name of a term (Example: speaker name, without defining the "nicename")? Will existing terms be correctly linked?
**A:** NO! if the "nicename" isn't defined, the taxonomy term won't be imported.

**Q:** What to do when several talks start at the same time (in different rooms)? 
**A:** Add a difference of 10 seconds - this allows the "next / previous" links to work correctly in WordPress.

## Notes on exporting from WordPress with Formidable

Method used to export from LGM 2015:

Created two custom Formidable views:

1) for the Speakers: Speaker list XML

- Use entries from : LGM 2015 proposal submissions
- View format: all entries
- Content: 
 
```<wp:term><wp:term_taxonomy><![CDATA[speaker]]></wp:term_taxonomy><wp:term_slug><![CDATA[[86] [87]]]></wp:term_slug><wp:term_name><![CDATA[[86] [87]]]></wp:term_name><wp:term_description><![CDATA[[92][if 93]<div class="speaker-website">[93]</div>[/if 93]]]></wp:term_description></wp:term>```

Keys: 86 = first name, 87 = last name, 92 = biography, 93 = website

NOTE: the output needs a little bit of search-replace: Formidable replaces > with &gt;

2) For the talks: Talks as XML


