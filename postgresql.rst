..
    This file is part of INSPIRE.
    Copyright (C) 2017 CERN.

    INSPIRE is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    INSPIRE is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with INSPIRE. If not, see <http://www.gnu.org/licenses/>.

    In applying this licence, CERN does not waive the privileges and immunities
    granted to it by virtue of its status as an Intergovernmental Organization
    or submit itself to any jurisdiction.


How to Connect to the PostgreSQL Database
=========================================

1. About
--------

This document specifies how to connect and query the inspire PostgreSQL database


2. Run the web container
------------------------

The first step is run the web container

.. code-block:: bash

    $ docker-compose run --rm web bash


3. Connect to the PostgresSQL Database
--------------------------------------

When the container is up you can run the following `psql` command line:

.. code-block:: bash

    (virtualenv)[inspirehep_web]$ psql -h inspirenext_database_1 inspirehep inspirehep
    Password for user inspirehep: dbpass123
    psql (9.2.18, server 9.4.5)
    WARNING: psql version 9.2, server version 9.4.
             Some psql features might not work.
    Type "help" for help.

    inspirehep=#


Now you have an interactive console to query the inspire SQL database
