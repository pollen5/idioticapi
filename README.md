# Idiotic-Wrapper (Python edition)
This is an API wrapper for the [idiot's guide api](https://api.anidiots.guide)
The wrapper is asynchronous and is hightly compatible with [discord.py](https://github.com/Rapptz/discord.py) Being built with aiohttp that comes with discord.py you don't have to add extra dependencies!

## Example
Retrieving image in a regular code
```python
import idioticapi
import asyncio

client = idioticapi.Client("Your api key", dev=True)

async def main():
    img = open("test.png", "wb")
    img.write(await client.blame("This person"))
    # untested though that's just what i think how it works shrug, its recommended to use it as a discord.py cog
    
asyncio.get_event_loop().run_until_complete(main())
```
Discord.py example
```python
import idioticapi
# you want easy access to it so maybe attach it to your bot # object, this allowes access to cogs as well and you don't have to remake the class everywhere.
bot.api = idioticapi.Client("Your api key", dev=True)

@bot.command()
async def blame(ctx, *, text):
    await ctx.send(file=discord.File(await bot.api.blame(text), "blame.png"))
# a simple example, change it to whatever you like to fit in a cog etc, also works with old d.py 0.16.x just change the way i sent things, i didn't test though but SHOULD work
```
More info
Client takes a session as third argument, which you can reuse another session if you have one or leave it to create a new aiohttp.ClientSession()

## Requirements.
Python Minimum version: 3.5
Dependencies:
- aiohttp

## Contributing
Contributing is allowed anytime just open a Pull Request with your changes, pretty straight forward right?

## License
Released under MIT License.