# GBF-Banner-Data
Stores banner data for Granblue Fantasy.

## Schema
> [!NOTE]
> - Banner Data JSON files contain an object with a bannerInfo (object) property and an items (array) property.
> - Properties containing `rate1` in their name refer to draw rates for single draws or the first 9 draws of a 10-Part Draw.
> - Properties containing `rate2` in their name refer to draw rates the last draw of a 10-Part Draw (which excludes R items and guarantees an SR or better).

### bannerInfo
| Property                   | Type     | Description                                                                                                                                                                                                                                                             |
|:---------------------------|:---------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| id                         | string   | 6-digit numeric ID for the banner.                                                                                                                                                                                                                                      |
| key                        | string   | 8-digit alphanumeric key which can be used to find the banner background, info text, and some promotional images.                                                                                                                                                       |
| start <br> end             | string   | The time at which the banner starts or ends in Japan Standard Time.                                                                                                                                                                                                     |
| featuredItemIDs            | string[] | List of IDs for items that are featured. Note: this only includes items with images appearing on the [draw page](https://game.granbluefantasy.jp/#gacha), and may not include everything on the [included items page](https://game.granbluefantasy.jp/#gacha/selected). |
| totalRate1 <br> totalRate2 | number   | The total combined draw rate of all items in the first or second group of items.                                                                                                                                                                                        |
| drawRates                  | object   | Contains the rates for each rarity. Format: <pre lang="yaml">{SS Rare: string, S Rare: string, Rare: string}</pre>|

### items
| Property                 | Type                     | Description                                                                                                                                                            |
|:-------------------------|:-------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| name                     | string                   | The name of the weapon or summon.                                                                                                                                      |
| id                       | string                   | The ID of the weapon or summon.                                                                                                                                        |
| rarity                   | string                   | The rarity of the weapon or summon.                                                                                                                                    |
| element                  | string                   | The element of the weapon or summon.                                                                                                                                   |
| type                     | string                   | The type of the weapon (sabre, dagger, etc). If the item is a summon, the value will be "summon".                                                                      |
| rate1 <br> rate2         | number                   | The draw rate for the item in the first or second group of items.                                                                                                      |
| cum_rate1 <br> cum_rate2 | number                   | The cumulative draw rate for the item in the first or second group of items. This property is included to make it easy to use a random number generator to draw items. |
| rate_up                  | boolean                  | Whether the item is on rate up.                                                                                                                                        |
| character                | string&nbsp;\|&nbsp;null | The character associated with the weapon. If the item does not come with a character or is a summon, the value will be null.                                           |
