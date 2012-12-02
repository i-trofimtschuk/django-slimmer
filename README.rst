==============
django-slimmer
==============

This module is a wrapper around Peter Bengtssons great slimmer module ::

    https://github.com/peterbe/slimmer
    http://pypi.python.org/pypi/slimmer

The slimmer is taken directly from the slimmer package on PyPI, with django middleware
and a view decorator added.

The slimming process takes html and removes whitespace, optimizes inline css,
removes oneline comments.  The end result can be a significant file size
reduction even after the page is served with gzip compression.

Installation ::

    pip install -e git+git://github.com/i-trofimtschuk/django-slimmer.git#egg=django-slimmer


Install middleware ::

    'django_slimmer.middleware.CompressHtmlMiddleware',

Or you can use a view decorator to compress specific views ::

    from django_slimmer.decorator import compress_html

    @compress_html
    def browse(request):
        context = RequestContext(request,{})
        return render_to_response('browse.html',context)

Using the slimmer directly ::

    from slimmer import slimmer
    compressed = slimmer.xhtml_slimmer(html)

