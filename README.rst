discord-py-darkself
===================

A modern, easy-to-use, feature-rich, and async-ready API wrapper for Discord's user API written in Python.

About the Project
-----------------

**discord-py-darkself** is a customized fork of the `discord.py-self` library. 

The primary feature of this fork is the complete isolation of its namespace. In this version, the standard ``discord`` package namespace and all its internal/external imports have been renamed to ``discord_self``.

This allows you to install and use this library concurrently alongside the official, upstream ``discord.py`` library (used for regular bot accounts) within the same Python environment without experiencing any naming conflicts or dependency collisions.

How to Use
----------

Instead of using the standard ``discord`` import, use ``discord_self`` and ``discord_self.ext`` for commands and tasks:

.. code:: py

    import discord_self
    from discord_self.ext import commands

    bot = commands.Bot(command_prefix='!', self_bot=True)

    @bot.event
    async def on_ready():
        print(f'Logged on as {bot.user} (ID: {bot.user.id})')

    @bot.command()
    async def ping(ctx):
        await ctx.send('pong')

    bot.run('YOUR_ACCOUNT_TOKEN_HERE')

Installation
------------

**Python 3.10 or higher is required.**

You can install the library directly from your GitHub repository using ``pip``:

.. code:: sh

    pip install git+https://github.com/Darknife339/discord.py-darkself.git

If you have cloned the repository locally and wish to install it in editable mode for development:

.. code:: sh

    cd discord.py-darkself
    pip install -e .

Disclaimer
----------

Automating user accounts (self-botting) is against the Discord Terms of Service (ToS). This library is a proof of concept and is intended strictly for educational and research purposes. The author of this fork assumes no responsibility for any account terminations or penalties incurred while using this software. Use it entirely at your own risk.
