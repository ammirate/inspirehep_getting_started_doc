=========================
Start with Elastic search
=========================

#. Get Elastic Search

If you have installed inspirehep via docker (if not ypu should), you can access it trough localhost:5000. Well, the same image also contains an Elastic Search (ES) instance, accessible via localhost:9200.

#. Sense Plugin

Download Chrome and install the Sense add-on (easiest way). Sense is a plugin developed by ES that allows you to query the ES instance very easily.

#. To play around, you could start looking at the ES query Language.

#. ES in inspirehep is known as `indexer`. To have an idea about how they iteract, you can look at the console (where you ran docker-compose-up to run inspirehep).
You can also look at the ES log to get some other info by typing `docker logs -f indexer`


#. Tools
--------

Monitoring tool: localhost:9200/_plugin/hq
Cluster browsing tool: localhost:9200/_plugin-head