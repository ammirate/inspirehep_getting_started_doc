============
inspire-next
============ 

****************
Development tips
****************

Back-end
===============

Debugging
^^^^^^^^^
- When developing for code that runs on the worker node and you need to debug it, you need to use 
  `remote-pdb` package as described by `Riccardo Candido <https://github.com/rikirenz>`_, `here <https://github.com/inspirehep/inspire-next/pull/1946#discussion_r104183272>`_.


Front-end
===============

Debugging
^^^^^^^^^
- For developing Javascript code without rebuilding the assets each time:  
  ``cd`` into ``$DOCKER_DATA/tmp/virtualenv/var/inspirehep-instance`` and create a file called ``inspirehep.cfg`` with this content:  

  ::

      DEBUG = True  
      ASSETS_DEBUG = True
      COLLECT_STORAGE = 'flask_collect.storage.link'
  
  | Then, restart the application, so as to reflect the configuration changes. Now, rebuild the assets.
  | (For Docker users: ``docker-compose -f docker-compose.deps.yml run --rm assets``.)

|  The interesting part in the configuration above is the `COLLECT_STORAGE` which instead of copying each time the assets, it simply creates symbolic links to 
  the development files.  
|  (We're using `Invenio-Asset`, which in turn uses `Flask-Collect`. More `here <https://pythonhosted.org/invenio-assets/configuration.html>`__.)
