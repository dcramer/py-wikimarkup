Formats text following the MediaWiki (http://meta.wikimedia.org/wiki/Help:Editing) syntax.

To return HTML from Wiki::

	from wikimarkup import parse

	html = parse(text[, show_toc=True])

To return HTML without certain "annoying" (TODO: define annoying) elements, such as headings::

	from wikimarkup import parselite

	parselite(text)