---
description: >-
  The Developer API for Fadah is very extensive, these docs aim to cover it
  fully!
---

# Developer API

## Getting Started

To get started with the API you must add it to your Maven / Gradle Project.

Replace LATEST-VERSION with the version found below.

<div align="left">

<figure><img src="https://jitpack.io/v/ProdPreva1l/Fadah.svg" alt="" width="188"><figcaption></figcaption></figure>

</div>

{% tabs %}
{% tab title="Maven" %}
```xml
<repositories>
    <repository>
        <id>jitpack</id>
        <url>https://jitpack.io</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>com.github.ProdPreva1l.Fadah</groupId>
        <artifactId>API</artifactId>
        <version>LATEST-VERSION</version>
        <scope>provided</scope>
    </dependency>
</dependencies>
```
{% endtab %}

{% tab title="Gradle (Groovy)" %}
```gradle
repositories {
    maven { url 'https://jitpack.io' }
}

dependencies {
    compileOnly 'com.github.ProdPreva1l.Fadah:API:LATEST-VERSION'
}
```
{% endtab %}

{% tab title="Gradle (Kotlin)" %}
```gradle
repositories {
    maven("https://jitpack.io")
}

dependencies {
    compileOnly("com.github.ProdPreva1l.Fadah:API:LATEST-VERSION")
}
```
{% endtab %}
{% endtabs %}



## Using the API

{% content-ref url="accessing-data.md" %}
[accessing-data.md](accessing-data.md)
{% endcontent-ref %}

{% content-ref url="events.md" %}
[events.md](events.md)
{% endcontent-ref %}
