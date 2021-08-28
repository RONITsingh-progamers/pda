pda.py
==========

.. image:: https://pda.com/api/guilds/789911027932200961/embed.png
   :target: https://pda.gg/r3sSKJJ
   :alt: pda server invite
.. image:: https://img.shields.io/pypi/v/pda.py.svg
   :target: https://pypi.python.org/pypi/pda.py
   :alt: PyPI version info
.. image:: https://img.shields.io/pypi/pyversions/pda.py.svg
   :target: https://pypi.python.org/pypi/pda.py
   :alt: PyPI supported Python versions

A modern, easy to use, feature-rich, and async ready API wrapper for discord written in Python.

Key Features
-------------

- Modern Pythonic API using ``async`` and ``await``.
- Proper rate limit handling.
- Optimised in both speed and memory.

Installing
----------

**Python 3.8 or higher is required**

To install the library without full voice support, you can just run the following command:

.. code:: sh

    # Linux/macOS
    python3 -m pip install -U pda.py

    # Windows
    py -3 -m pip install -U pda.py

Otherwise to get voice support you should run the following command:

.. code:: sh

    # Linux/macOS
    python3 -m pip install -U "pda.py[voice]"

    # Windows
    py -3 -m pip install -U pda.py[voice]


To install the development version, do the following:

.. code:: sh

    $ git clone https://github.com/SangamBot/pda.git
    $ cd pda.py
    $ python3 -m pip install -U .[voice]


Optional Packages
~~~~~~~~~~~~~~~~~~

* `PyNaCl <https://pypi.org/project/PyNaCl/>`__ (for voice support)

Please note that on Linux installing voice you must install the following packages via your favourite package manager (e.g. ``apt``, ``dnf``, etc) before running the above commands:

* libffi-dev (or ``libffi-devel`` on some systems)
* python-dev (e.g. ``python3.6-dev`` for Python 3.6)

Quick Example
--------------

.. code:: py

    import pda

    class MyClient(pda.Client):
        async def on_ready(self):
            print('Logged on as', self.user)

        async def on_message(self, message):
            # don't respond to ourselves
            if message.author == self.user:
                return

            if message.content == 'ping':
                await message.channel.send('pong')

    client = MyClient()
    client.run('token')

Bot Example
~~~~~~~~~~~~~

.. code:: py

    import pda
    from pda.ext import commands

    bot = commands.Bot(command_prefix='>')

    @bot.command()
    async def ping(ctx):
        await ctx.send('pong')

    bot.run('token')

You can find more examples in the examples directory.

Links
------

- `Documentation <https://pdapy.readthedocs.io/en/latest/index.html>`_
- `Official pda Server <https://pda.gg/r3sSKJJ>`_
- `pda API <https://pda.gg/pda-api>`_
