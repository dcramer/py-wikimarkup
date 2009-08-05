Formats text following the MediaWiki (http://meta.wikimedia.org/wiki/Help:Editing) syntax.

Usage
-----

To return HTML from Wiki::

	from wikimarkup import parse

	html = parse(text[, show_toc=True])

To return HTML without certain "annoying" (TODO: define annoying) elements, such as headings::

	from wikimarkup import parselite

	parselite(text)

Adding New Tags
---------------

You can add new tags with the `registerTagHook` method.::

	from wikimarkup import registerTagHook, parse
	import cgi
	
	def blockquoteTagHook(parser_env, body, attributes={}):
	    """<quote[ cite="Person"]>A paragraph of text.</quote>"""
	    text = ['<blockquote>']
	    if 'cite' in attributes:
	        text.append('<cite>%s</cite>' % (cgi.escape(attributes['cite']),))
	    text.append(parse(body.strip()))
	    text.append('</blockquote>')
	    return u'\n'.join(text)
	registerTagHook('quote', blockquoteTagHook)