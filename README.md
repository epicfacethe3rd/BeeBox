# BeeBox
### NOT THE BEES
#### AAAAAAAA
Conceptualization of a coordinate exploit for minecraft using, you guessed it, bees (lmao)

Note: this information is primarily relevant to the anarchy minecraft server [Constantiam](https://constantiam.net/) (website is still down as of writing, so here's a [link](https://www.reddit.com/r/constantiam/) to the subreddit)

## What the fuck, Bees????
No, this isn't a joke, you read that right, bees. Bees are the source of the current cordinate exploit currently being used en masse on constantiam. Here's how it was (and still is, at times!) executed, in breif.
1. A trade ad is put up looking for beehives or bee nests, with bees still in them. Generally at outragous margins with the requirement that it be as fast as possible.
2. The victim gathers beehives from around their base, stash, or other builds
3. The attacker completes the trade successfully, and uses `.nbt` or a similar command to view the NBT data of the bees inside the hive
4. The attacker extracts all coordinate information from the bees inside the hive, and uses said information to hunt for a base with much greater accuracy than would otherwise be possible
5. The attacker locates the base. Profit.

As you can see, this is a very simple attack. It requires no special mods or clients, as to my knowledge almost all utility clients currently available for 1.19.2 offer a way to view NBT data in game with little to no hassle, albiet generally horribly formatted. For that reason i have attached some *readable* NBT data so you can get a better understanding of how easy this is to actually do. Here is part of the NBT data from a real hive on Constantiam that shows some of the critical information available in it, albiet censored.
```java
{
BlockEntityTag:
{
Bees:[
    {
    EntityData:
        {
        AbsorptionAmount:0.0f,
        Age:-20339,
        AgeLocked:0b,
        AngerTime:0,
        Attributes:
            [
                {Name:"minecraft:generic.max_health",Base:10.0d},
                {Name:"minecraft:generic.movement_speed",Base:0.30000001192092896d}
            ],
            Bukkit.Aware:1b,Bukkit.updateLevel:2,
            FlowerPos:
                {X:-1500,Y:69,Z:-1500}, //not real cords nothing ever happened here look away
            ForcedAge:0,
            HasNectar:0b,
            HasStung:0b,
            Health:10.0f,
            InLove:0,
            Invulnerable:0b,
            Paper.Origin:
                [CENSORED], //Redacted information
            Paper.OriginWorld:
                [CENSORED], //Redacted information
            Paper.SpawnReason:"BREEDING",
            PersistenceRequired:0b,
            Spigot.ticksLived:7265,
            WorldUUIDLeast:CENSORED, //Redacted information
            WorldUUIDMost:CENSORED, //Redacted information
            id:"minecraft:bee"
        },
        MinOccupationTicks:600,
        TicksInHive:479
    },
```
Some things to note:

1. There are __multiple__ sources of coordinate information available in the bee NBT data. Some of these are not vanilla sources! This means testing in singleplayer is not adequate to determine if any "bee laundering" methood works
2. The multipile sources include not only where the bee was made, but also the last flower said bee touched.
3. There *appears* to be no viable methood to "launder" existing bees on Paper servers such as Constantiam, as they have origin coordinates stored in `Paper.Origin`, which states the exact location that the bee was first spawned. `Paper.OriginWorld` may also have similar information but is a four-datum variable, which looks more like a UUID. that said, I don't know what it does aside from the name.
4. the *only* place location data seems to show up, contrary to what the minecraft wiki says, is in the bee NBT data. I could be wrong on this, of course, but it SEEMS that if you trade beehives that currently do not have bees in them, there will be no location data.
5. If you are really, really, *really* paranoid but still want to trade beehives, you can avoid all this fuss and concern by just crafting new beehives and not placing them. Any hives that don't have bees in them currently should be safe though.
6. Explorer maps (Buried treasure, woodland mansion, etc), according to the minecraft wiki, MIGHT have similar information in them as well, so don't share those either if you can help it. Honestly not sure why you would in the first place?

### Am I safe?
Maybe. Ask yourself the following questions:
1. Have I traded any beehives?
	1. If no, You're 100% safe
2. Did those beehives have bees in them?
	1. If no, i'm 99% sure you're safe
3. Were those bees bred or generated at (or near) a sensitive location?
	1. If yes, that location is compromised
4. Where was the last place those bees were let out and might have seen a flower?
	1. Those locations are all potentially compromised, but could possibly be "laundered"

## This seems really stupid
I mean, yeah. Kinda is lmao
## Will Mojang fix this?
Probably not. For one this is a very niche issue. It has 100% existed since 1.16 when bees were introduced, and seeming hasn't been seen as a problem since then. It's likely they don't see it as a real issue as they are not worried about the anarchy community.
## Will PaperMC fix this??
~~Maybe? They're certainly the best equipped. That said, this is, again, a very niche issue, and I don't see it at the top of their priority list. After all, you kinda have to... yknow... give the attacker a beehive with bees in it.~~
Update: another player has told me that this is a wontfix from PaperMC, so this almost certainly will not be fixed by them.
## Will Phantom fix this???
Possibly. I'm not sure of exactly how to do so, but feasibly you could hide all sensitive NBT data from the minecraft client and things would still be completely fine. That said knowing Phantom, its likely he would break something in the process, and i would rather not him try. Just don't trade beehives with bees in them lmao.
## What NBT data should I look for?
You should 100% look at the following data to confirm things for your own saftey. that said there may be other bits of data in the NBT data that i'm missing because i'm an idiot
- `FlowerPos`
- `Paper.Origin`
- `Paper.OriginWorld`
## Full NBT data for me to read pls?
Here you go!
```java
{
BlockEntityTag:
{
Bees:[
    {
    EntityData:
        {
        AbsorptionAmount:0.0f,
        Age:-20339,
        AgeLocked:0b,
        AngerTime:0,
        Attributes:
            [
                {Name:"minecraft:generic.max_health",Base:10.0d},
                {Name:"minecraft:generic.movement_speed",Base:0.30000001192092896d}
            ],
            Bukkit.Aware:1b,Bukkit.updateLevel:2,
            FlowerPos:
                {X:-1500,Y:69,Z:-1500}, //not real cords nothing ever happened here look away
            ForcedAge:0,
            HasNectar:0b,
            HasStung:0b,
            Health:10.0f,
            InLove:0,
            Invulnerable:0b,
            Paper.Origin:
                [CENSORED], //Redacted information
            Paper.OriginWorld:
                [CENSORED], //Redacted information
            Paper.SpawnReason:"BREEDING",
            PersistenceRequired:0b,
            Spigot.ticksLived:7265,
            WorldUUIDLeast:CENSORED, //Redacted information
            WorldUUIDMost:CENSORED, //Redacted information
            id:"minecraft:bee"
        },
        MinOccupationTicks:600,
        TicksInHive:479
    },
    {
    EntityData:
        {
        AbsorptionAmount:0.0f,
        Age:-20339,
        AgeLocked:0b,
        AngerTime:0,
        Attributes:
            [
                {Name:"minecraft:generic.max_health",Base:10.0d},
                {Name:"minecraft:generic.movement_speed",Base:0.30000001192092896d}
            ],
            Bukkit.Aware:1b,
            Bukkit.updateLevel:2,
            ForcedAge:0,
            HasNectar:0b,
            HasStung:0b,
            Health:10.0f,
            InLove:0,
            Invulnerable:0b,
            Paper.Origin:
                [CENSORED], //Redacted information
            Paper.OriginWorld:
                [CENSORED], //Redacted information
            Paper.SpawnReason:"BREEDING",
            PersistenceRequired:0b,Spigot.ticksLived:3662,
            WorldUUIDLeast:CENSORED, //Redacted information
            WorldUUIDMost:CENSORED, //Redacted information
            id:"minecraft:bee"
        },
        MinOccupationTicks:600,
        TicksInHive:241
    },
    {
    EntityData:
        {
        AbsorptionAmount:0.0f,
        Age:-20339,
        AgeLocked:0b,
        AngerTime:0,
        Attributes:
            [
                {Name:"minecraft:generic.max_health",Base:10.0d},
                {Name:"minecraft:generic.movement_speed",Base:0.30000001192092896d}
            ],
            Bukkit.Aware:1b,
            Bukkit.updateLevel:2,
            ForcedAge:0,
            HasNectar:0b,
            HasStung:0b,
            Health:10.0f,
            InLove:0,
            Invulnerable:0b,
            Paper.Origin:
                [CENSORED], //Redacted information
            Paper.OriginWorld:
                [CENSORED], //Redacted information
            Paper.SpawnReason:"BREEDING",
            PersistenceRequired:0b,
            Spigot.ticksLived:4070,
            WorldUUIDLeast:CENSORED, //Redacted information
            WorldUUIDMost:CENSORED, //Redacted information
            id:"minecraft:bee"
        },
        MinOccupationTicks:600,
        TicksInHive:42
    }
    ]
}
BlockStateTag:
    {honey_level:"5"}
}
```

## Why did you censor UUIDs?
Idk i'm paranoid IG

Credit to:

Yoko99 for pointing this out to the community

[Meteor](https://meteorclient.com/) devs for making Meteor

PhantomCaptain for running my personal minecraft addition and ruining my life by convincing me to mine thousands on thousands of blocks of cobblestone because why not

All the people who were hit by this exploit (Does this really qualify as an exploit? its arguably built into the game) and published their experiences for us to learn from. RIP to your stashes and builds, HMU if you need anything and I'll do my best to help you out.

Yes, Cuboyd asked to use this stuff in his video
