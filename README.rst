discord-py-darkself
===================

A modern, easy-to-use, feature-rich, and async-ready API wrapper for Discord's user API, specifically modified for hassle-free integration alongside the official Discord bot library.

⚡ The Problem & The Solution
----------------------------

The Problem
~~~~~~~~~~~
Normally, you cannot install both ``discord.py`` (for official bots) and ``discord-py-self`` (for self-bots) in the same Python environment. Both libraries claim the ``discord`` namespace, leading to import collisions, broken dependencies, and forcing you to use separate virtual environments or processes.

The Solution
~~~~~~~~~~~~
``discord-py-darkself`` solves this by completely isolating its namespace.

Every internal and external import has been renamed from ``discord`` to ``discord_self`` (including ``discord_self.ext.commands``, etc.).

Now, you can seamlessly run both regular bots and self-bots in the exact same Python script or environment without any conflicts.

🚀 How to Use
-------------

Instead of importing ``discord``, simply use ``discord_self`` and ``discord_self.ext``:

.. code:: python

    import discord_self
    from discord_self.ext import commands

    bot = commands.Bot(command_prefix='!', self_bot=True)

    @bot.event
    async def on_ready():
        print(f'Logged on as self-bot: {bot.user} (ID: {bot.user.id})')

    @bot.command()
    async def ping(ctx):
        await ctx.send('pong')

    bot.run('YOUR_ACCOUNT_TOKEN_HERE')

🤝 Coexistence Example (The Magic Part)
---------------------------------------

Here is how you can run a standard bot and a self-bot in the same environment:

.. code:: python

    import discord       # Official discord.py library
    import discord_self  # This fork (discord-py-darkself)

    # Both can now be used in the same project without naming collisions!
    print(discord.__version__)
    print(discord_self.__version__)

📥 Installation
---------------

**Python 3.10 or higher is required.**

Standard Installation (PyPI)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The easiest way to install the library is directly via PyPI:

.. code:: sh

    pip install discord-py-darkself

From GitHub (Development version)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
If you want the latest updates directly from the repository:

.. code:: sh

    pip install git+https://github.com/Darknife339/discord.py-darkself.git

Local / Editable Installation
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
If you are developing or want to modify the library locally:

.. code:: sh

    git clone https://github.com/Darknife339/discord.py-darkself.git
    cd discord.py-darkself
    pip install -e .

⚠️ Disclaimer
-------------

Automating user accounts (self-botting) is against the Discord Terms of Service (ToS). This library is a proof of concept and is intended strictly for educational and research purposes. The author of this fork assumes no responsibility for any account terminations, bans, or penalties incurred while using this software. Use it entirely at your own risk.
