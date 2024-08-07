---
description: Access data  using the API.
---

# Accessing Data

## Getting Started

To get data from the API you will need to access the instance of the API. \
To do this you will need to depend on Fadah. By adding it to your plugin.yml

{% code title="" %}
```yaml
name: FadahAPIExample
version: '1.0'

depend: [Fadah]
```
{% endcode %}

You will then need to get the instance of the API.

<pre class="language-java"><code class="lang-java">import org.bukkit.Bukkit;
import org.bukkit.plugin.java.JavaPlugin;

public final class FadahAPIExample extends JavaPlugin {
    private AuctionHouseAPI fadahApi;

    @Override
    public void onEnable() {
<strong>        if (Bukkit.getPluginManager().getPlugin("Fadah") != null) {
</strong><strong>            fadahApi = AuctionHouseAPI.getInstance();
</strong>        }
    }
}
</code></pre>

## Available Methods

```java
 /**
  * Get a listing
  *
  * @param uuid a valid listing uuid
  * @return the listing or null if none found
  * @since 1.0
  */
 public abstract Listing getListing(UUID uuid);

 /**
  * Get a category
  *
  * @param id a valid category id
  * @return the category or null if none found
  * @since 1.0
  */
 public abstract Category getCategory(String id);

 /**
  * Get a players collection box
  *
  * @param offlinePlayer a player
  * @return the collection box or null if no items found for that player
  * @since 1.0
  */
 public abstract List<CollectableItem> getCollectionBox(OfflinePlayer offlinePlayer);

 /**
  * Get a players collection box
  *
  * @param uuid a players uuid
  * @return the collection box or null if no items found for that player
  * @since 1.0
  */
 public abstract List<CollectableItem> getCollectionBox(UUID uuid);

 /**
  * Get a players expired items
  *
  * @param offlinePlayer a player
  * @return the expired items or null if no items found for that player
  * @since 1.0
  */
 public abstract List<CollectableItem> getExpiredItems(OfflinePlayer offlinePlayer);

 /**
  * Get a players expired items
  *
  * @param uuid a players uuid
  * @return the expired items or null if no items found for that player
  * @since 1.0
  */
 public abstract List<CollectableItem> getExpiredItems(UUID uuid);

 /**
  * Get a players history
  *
  * @param offlinePlayer a player
  * @return the players history, ordered from newest to oldest
  */
 public abstract List<HistoricItem> getHistory(OfflinePlayer offlinePlayer);

 /**
  * Get a players history
  *
  * @param uuid a player uuid
  * @return the players history, ordered from newest to oldest
  */
 public abstract List<HistoricItem> getHistory(UUID uuid);
```

## Data Objects

### Listing

```java
@NotNull UUID id;
@NotNull UUID owner;
@NotNull String ownerName;
@NotNull ItemStack itemStack;
@NotNull String categoryID;
double price;
double tax; // % of amount of price to take
long creationDate; // Epoch milli
long deletionDate; // Epoch milli
boolean biddable; // unused
@NotNull List<Bid> bids; // unused
```

### Category (For Sorting Listings)

```java
@NotNull String id
@NotNull String name
int priority
int modelData
@NotNull Material icon
@NotNull List<String> description
@Nullable Set<Material> materials
boolean isCustomItems
@Nullable CustomItemMode customItemMode
@Nullable Set<String> customItemIds
```

### CollectableItem (Collection Box & Expired Listings)

```java
ItemStack itemStack
long dateAdded // Epoch timestamp
```

### HistoricItem (History Menu)

<pre class="language-java"><code class="lang-java"><strong>@NotNull UUID ownerUUID // the person who the log belongs to
</strong>@NotNull Long loggedDate // when the action happened, in epoch millis
<strong>@NotNull LoggedAction action // the action that got logged
</strong>@NotNull ItemStack itemStack // the item that had an action happen to it
@Nullable Double price // only used for LISTING_START, LISTING_PURCHASED, LISTING_SOLD
<strong>@Nullable UUID purchaserUUID // only used for LISTING_SOLD
</strong></code></pre>

### LoggedAction (For HistoricItem)

```java
LISTING_START
LISTING_PURCHASED
LISTING_SOLD
LISTING_CANCEL
LISTING_EXPIRE
LISTING_ADMIN_CANCEL
EXPIRED_ITEM_CLAIM
EXPIRED_ITEM_ADMIN_CLAIM
COLLECTION_BOX_CLAIM
COLLECTION_BOX_ADMIN_CLAIM
```
