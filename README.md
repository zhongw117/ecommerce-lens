# ecommerce-lens

# For issues not showing local pictures: 
Check the sample urls.py below

from django.conf.urls import patterns, include, url
from django.contrib import admin
from oscar.app import application
from django.conf import settings
from django.conf.urls.static import static

urlpatterns = patterns('',
    url(r'^admin/', include(admin.site.urls)),
    url(r'^i18n/', include('django.conf.urls.i18n')),
    url(r'', include(application.urls)),
)+ static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)
And in your settings.py file, make sure you define media_root and media_url

location = lambda x: os.path.join(
os.path.dirname(os.path.realpath(__file__)), x)

TEMPLATE_DIRS = (
    location('templates'),
    OSCAR_MAIN_TEMPLATE_DIR,
)
STATIC_URL = '/static/'
STATIC_ROOT = location('static')
MEDIA_URL = '/media/'
MEDIA_ROOT = location('media')
THUMBNAIL_DEBUG = True
THUMBNAIL_KEY_PREFIX = 'oscar-sandbox'
