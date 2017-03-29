=========================
Start with Elastic search
=========================

Get Elastic Search
=====================

1. **Installation**

   If you have installed InspireHEP via `docker` (if don't, you should), you can access it trough ``localhost:5000``. Well, the same image also contains an Elastic Search (**ES**) instance, accessible via ``localhost:9200``.



2. **Sense Plugin**

   Download Chrome and install the `Sense` add-on (easiest way). Sense is a plugin developed by ES that allows you to                 query the ES instance very easily.

3. **Getting familiar**

   Get familiar with ES playing around. Maybe you could start looking at the ES `query language <https://www.elastic.co/guide/en/elasticsearch/reference/current/_introducing_the_query_language.html>`_.

4. **ES in inspire**

   ES, in the inspire development environment, is known as **indexer**. In order to have an idea about how they interact together, you can look at the console (where you ran docker-compose-up to run inspirehep), which displays queries and results. You can also look at the ES log to get some other info by typing ``docker-compose logs indexer``.

Tools
=====

**Monitoring tool:** ``localhost:9200/_plugin/hq``

**Cluster browsing tool:** ``localhost:9200/_plugin-head``