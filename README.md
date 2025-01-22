# prootlist_test
Test prootlist implementation.

## What is a prootlist?
- A prootlist defines a read-only list of protogen software packages and their authors over URLs. Thats it. Simple.
- This specification does not define how to edit, create, or delete records. Implementations of this specification may add such functionality.
- The intent is to allow different philosophies and opinions exist on how to manage protogen plugins and their authorship. For example, one impementation may be a dynamic site that allows authors to manage their plugins, another implementation may just be a static site with vetted, curated plugins.
- This specification does not use any JSON. It is designed to be used in environments where json parsing may not be avaliable or is inconvenient.

## prootlist specification
- A "prootlist" is defined as a set of URLs that a domain can serve over HTTP(S).
- This specification details how to read these details. It does not define any method of editing, creating, or deleting such records.
- Each URL in this specification is called with the GET HTTP method.

### prootlist URLs
Let `origin` refer to the origin of the web server. This is the scheme, domain, and optional port. For example, `http://example.com`, `https://example.com`, `https://example.com:1234`, and `https://test.com` are all different origins.
| URL Full Path | Content returned with GET call |
| --- | --- |
| `<origin>/plugins` | List of plugin ids seperated by newlines. |
| `<origin>/plugins/<id>/git_repo_url` | Full URL to the git repository where the plugin is located. |
| `<origin>/plugins/<id>/name` | Name of the plugin. |
| `<origin>/plugins/<id>/description` | Description of the plugin. This is usually plaintext. |
| `<origin>/plugins/<id>/image` | Full URL to the thumbnail or image that represents this plugin. Recommended that the image is 256 by 256 pixels and is either PNG, WEBP, or JPEG. |
| `<origin>/plugins/<id>/author` | Id of the author. |
| `<origin>/plugins/<id>/funding_url` | May be blank or return 404. A full URL to the funding page for this plugin. |
| `<origin>/plugins/<id>/websites` | May be blank or return 404. A list of full URLs that relate to this plugin seperated by newlines. |
| `<origin>/plugins/<id>/tags` | A list of tags that describe this plugin seperated by newline. |
| --- | --- |
| `<origin>/authors` | List of author ids seperated by newline. |
| `<origin>/authors/<id>/name` | Name of the author. |
| `<origin>/authors/<id>/bio` | Description of the author. This is usually plaintext. |
| `<origin>/authors/<id>/websites` | A list of full URLs to websites related to the author seperated by newlines. |
| `<origin>/authors/<id>/image` | Full URL to the thumbnail or image that represents this author. Recommended that the image is 256 by 256 pixels and is either PNG, WEBP, or JPEG. |
