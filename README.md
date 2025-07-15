# star-wars-galaxy-data
[![License: CC BY-NC 4.0](https://img.shields.io/badge/License-CC%20BY--NC%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc/4.0/)

> 🛸 This is a **fan-made**, non-commercial Star Wars™ data archive.  
> Not affiliated with or endorsed by Lucasfilm or Disney.  
> Shared under [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/).

---

> Impossible. Perhaps the archives are incomplete.

Well, now they're not (mostly at least).

**SWGD** (in short) is a simple approach at structurizing as much information from the data pool of star systems, star sectors and their administrative divisions or assignation within the SW galaxy. You may ask yourself, why would anyone do it? Well, simply put it's too much time, boredom and a simple fascination with the SW universe in general.

## General info
SWGD is divided into four distinct categories of data, all of which are provided in two formats: **CSV and JSON**:
```
star-wars-galaxy-data/
├─ planets
    ├─ planets_data_csv / .json
    ├─ planets_unknown_data_csv / .json
├─ regions
    ├─ regions_data_csv / .json
├─ sectors
    ├─ sector_data_csv / .json
├─ systems
    ├─ system_data_csv / .json

```

**All entries can be distinguished by their UUID.**

The data has been compiled from publicly available sources such as:

- [StarWars.com Databank](https://www.starwars.com/databank)
- [StarWars.com Galaxy Map](https://www.starwars.com/star-wars-galaxy-map)
- [Wookieepedia](https://starwars.fandom.com/wiki/Main_Page)

And also Git repos:

- [StarWarsMap](https://github.com/Wason1797/StarWarsMap?tab=readme-ov-file)

## Regions
The regions category holds information about the basic division of the SW galaxy. It consists of:
* Colonies
* Core Worlds
* Deep Core
* Expansion Region
* Inner Rim
* Mid Rim
* Outer Rim
* Unknown Regions

Also included in this category are regions like **Extragalactic** (as a method to categorize systems or planets outside of the galaxy in general), **Wild Space**, and also **Hutt Space**, which is also distinct in where it's sometimes considered a part of the Mid or Outer Rim regions (depending on the source), but in practice is often times considered a seperate entity because of its size.

>**All data entries have one region assigned to them** (with the exepction of the `planets_unknown_data`).

### Data structure
CSV format:
```
| id                                   | region   |
|--------------------------------------|----------|
| d95cbc5c-a8df-461b-940e-f7eddf9b5cfd | Colonies |
```

JSON format:
```
{
    "id":"d95cbc5c-a8df-461b-940e-f7eddf9b5cfd",
    "region":"Colonies"
}
```

### Exeptions
For data consistency, you will not find here any of the more "common" names of some parts of the galaxy, like The Slice, Western Reaches, etc., because these are often mixed up with the more general region in which they're located in.

Worth mentioning is also the fact, that the **Corporate Sector** and **Bothan Space** are even with their distinctivness considered as sectors, mostly because of the size of the star systems they hold.

## Sectors
Sectors are second in line when it comes to dividing the galaxy. All of the sectors are, of course, **assigned to one region only** and multiple sectors can be assigned to one region.

It may happen that you stumble across a sector name followed by a second name in brackets. These are alternative names for these sectors, that happen to be simply inconsistencies in the lore.

<ins>*Example*:</ins> Tungra (Fand), where Fand is the second name of the sector

Star systems and planets follow this *double* nomenclature within their sector assignment.

><ins>*Note*:</ins> Some sectors have two or more names given, but are used alternately.

><ins>*Example*:</ins> the Tunka sector is sometimes reffered to as Dalnan. **These incosistencies are most likely to be in the data in a greater number.**

### Data structure
CSV format:
```
| id                                   | sector | region  |
|--------------------------------------|--------|---------|
| 750d48a0-9c7e-40f1-bafb-ec4131cced1f | Abaar  | Mid Rim |
```

JSON format:
```
{
    "id":"750d48a0-9c7e-40f1-bafb-ec4131cced1f",
    "sector":"Abaar",
    "region":"Mid Rim"
}
```
### Exeptions
Both Hutt Space and Extragalactic regions are not divided into sectors, and therefore the sector data lacks any mention about them. This stems mostly from the fact that information about sectors for star systems in these regions are either incoherent or are simply missing.

## Systems
Star systems are considered the next level of the galaxy's division hierarchy after sectors. This is actually the bulk of all the data gathered.

> <ins>*Note*:</ins> Some systems have two or more names given, but are used alternately. 

><ins>*Example*:</ins> the Tatooine system is sometimes reffered to as Tatoo. **These incosistencies are most likely to be in the data in a greater number.**

### Data structure
CSV format:
```
| id                                   | system  | sector  | region    |
|--------------------------------------|---------|---------|-----------|
| 5a1acfc8-a8c8-43b9-b539-23d38f418366 | 5251977 | Quence  | Outer Rim |
```

JSON format:
```
{
    "id":"5a1acfc8-a8c8-43b9-b539-23d38f418366",
    "system":"5251977",
    "sector":"Quence",
    "region":"Outer Rim"
}
```

### Exeptions
As mentioned, Hutt Space and Extragalactic regions are not divided into sectors. Therefore, none of the system found in this data have a sector assigned to them.

Also, a lot of the systems lack any sector assignement, simply because of the lore's inconsistency.

## Planets
The name for this data may be confusing, because besides planets themselves you can also find here nebulas, space stations, as well as cosmic objects.

> <ins>*Note*:</ins> Like before, some planet entries can have two or more names given, but are used alternately. 

><ins>*Example*:</ins> the planet Korriban is sometimes reffered to as Moraband, but also as Pesagam. **These incosistencies are most likely to be in the data in a greater number.**

### Data structure
CSV format:
```
| id       | name    | region   | sector | system  | capital_city | climate | inhabitants |
|----------|---------|----------|--------|---------|--------------|---------|-------------|
| ca090... | 23 Mere | Colonies | Tapani | 23 Mere | null         | null    | Humans      |
```

JSON format:
```
{
    "id":"ca090ac6-e559-4522-b084-3dc09e4ef56f",
    "name":"23 Mere",
    "region":"Colonies",
    "sector":null,
    "system":"23 Mere",
    "capital_city":null,
    "climate":null,
    "inhabitants":"Humans"
}
```

Moreover, you can find here a dataset called `planets_unknown_data_csv / .json`. These are planets and objects that couldn't be assigned to any particular sector, system or region, and therefore remain in a seperate dataset. Feel free to submit missing data!

### Exeptions
Of course, there're inconsistencies, mostly regarding lore-accurate names of planets, but these need to be addressed in a future update.

## Legal disclaimer

> This is a **non-commercial, fan-made project**.  
> Star Wars™, its characters, planets, and terminology are trademarks of **Lucasfilm Ltd.**, a subsidiary of **The Walt Disney Company**.  
> This project is **not affiliated with, sponsored by, or endorsed by Lucasfilm or Disney**.

No logos, images, or copyrighted assets are redistributed.

If you are a rights holder and have concerns, please [open an issue](../../issues) or contact the maintainer for prompt action.

## License

This work is licensed under the **Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)** License.

You may:
- Use, remix, and share the data for **non-commercial** purposes with proper attribution.

You may not:
- Use this dataset for commercial gain.
- Misrepresent it as official Star Wars content.

Full license text available in [`LICENSE`](./LICENSE) or [here](https://creativecommons.org/licenses/by-nc/4.0/)

## Contributing

Contributions are welcome! Feel free to:

- Submit missing data
- Correct inaccuracies
- Suggest structure improvements