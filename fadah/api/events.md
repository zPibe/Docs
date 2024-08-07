---
description: Listen for Events via the API.
---

# Events

## Getting started

To get started listening for events you must setup your project to do so.

Depend on Fadah

```yaml
name: FadahAPIExample
version: '1.0'

depend: [Fadah]
```

Setup your Main class and Listener class.

<pre class="language-java"><code class="lang-java">import org.bukkit.plugin.java.JavaPlugin;
import org.bukkit.Bukkit;
<strong>
</strong><strong>public final class FadahAPIExample extends JavaPlugin {
</strong>
    @Override
    public void onEnable() {
        if (Bukkit.getPluginManager().getPlugin("Fadah") != null) {
            Bukkit.getPluginManager().registerEvents(new FadahAPIExampleListener(), this);
        }
    }
}
</code></pre>

```java
import org.bukkit.event.Listener;
import org.bukkit.event.EventHandler;

public class FadahAPIExampleListener implements Listener {
    // Add listeners here.
}
```

Now you can add your listeners!

## ListingCreateEvent

This event is cancellable and accepts a reason to show the player.

```java
public class FadahAPIExampleListener implements Listener {
    @EventHandler
    public void onListingStart(ListingCreateEvent e) {
        if (e.getPlayer().getName().equalsIgnoreCase("IhateFadah")) {
            e.setCancelReason("Nuh uh!");
            e.setCancelled(true);
        }
    }
}
```

## ListingEndEvent

This event is called asyncronously.

<pre class="language-java"><code class="lang-java"><strong>public class FadahAPIExampleListener implements Listener {
</strong>    @EventHandler
    public void onListingEnd(ListingEndEvent e) {
        if (e.getReason() == ListingEndReason.CANCELLED_ADMIN) {
            Player player = Bukkit.getPlayer(e.getListing().getOwner());
            if (player == null) return;
            player.sendMessage("An admin has cancelled your listing!");
        }
    }
}
</code></pre>

## ListingPurchaseEvent

```java
public class FadahAPIExampleListener implements Listener {
    @EventHandler
    public void onListingPurchase(ListingPurchaseEvent e) {
        Player player = Bukkit.getPlayer(e.getListing().getOwner());
        if (player == null) return;
        player.sendMessage("%s has purchased your listing!"
                .formatted(e.getBuyer().getName()));
    }
}
```
