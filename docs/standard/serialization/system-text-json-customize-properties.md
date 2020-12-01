---
title: İle özellik adlarını ve değerleri özelleştirme System.Text.Json
description: .NET ' te ile serileştirilirken özellik adlarını ve değerlerini özelleştirmeyi öğrenin System.Text.Json .
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 28f7d03ae9f794f6e5ea34a95082a059451daec6
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96440021"
---
# <a name="how-to-customize-property-names-and-values-with-no-locsystemtextjson"></a><span data-ttu-id="4f8c3-103">İle özellik adlarını ve değerleri özelleştirme System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="4f8c3-103">How to customize property names and values with System.Text.Json</span></span>

<span data-ttu-id="4f8c3-104">Varsayılan olarak, özellik adları ve sözlük anahtarları, büyük/küçük harf gibi JSON çıktısında değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="4f8c3-104">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="4f8c3-105">Sabit listesi değerleri sayı olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="4f8c3-105">Enum values are represented as numbers.</span></span> <span data-ttu-id="4f8c3-106">Bu makalede şunları yapmayı öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="4f8c3-106">In this article, you'll learn how to:</span></span>

> [!NOTE]
> <span data-ttu-id="4f8c3-107">[Web Varsayılanları](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions) , ortası durumdur.</span><span class="sxs-lookup"><span data-stu-id="4f8c3-107">The [web defaults](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions) is camel case.</span></span>

* [<span data-ttu-id="4f8c3-108">Bireysel özellik adlarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="4f8c3-108">Customize individual property names</span></span>](#customize-individual-property-names)
* [<span data-ttu-id="4f8c3-109">Tüm özellik adlarını ortası durumuna Dönüştür</span><span class="sxs-lookup"><span data-stu-id="4f8c3-109">Convert all property names to camel case</span></span>](#use-camel-case-for-all-json-property-names)
* [<span data-ttu-id="4f8c3-110">Özel özellik adlandırma ilkesi uygulama</span><span class="sxs-lookup"><span data-stu-id="4f8c3-110">Implement a custom property naming policy</span></span>](#use-a-custom-json-property-naming-policy)
* [<span data-ttu-id="4f8c3-111">Sözlük anahtarlarını ortası örneğine Dönüştür</span><span class="sxs-lookup"><span data-stu-id="4f8c3-111">Convert dictionary keys to camel case</span></span>](#camel-case-dictionary-keys)
* [<span data-ttu-id="4f8c3-112">Numaralandırmaları dizelere ve ortası örneğine Dönüştür</span><span class="sxs-lookup"><span data-stu-id="4f8c3-112">Convert enums to strings and camel case</span></span>](#enums-as-strings)

<span data-ttu-id="4f8c3-113">JSON özellik adlarını ve değerlerini özel olarak işleme gerektiren diğer senaryolar için [özel dönüştürücüler uygulayabilirsiniz](system-text-json-converters-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="4f8c3-113">For other scenarios that require special handling of JSON property names and values, you can [implement custom converters](system-text-json-converters-how-to.md).</span></span>

## <a name="customize-individual-property-names"></a><span data-ttu-id="4f8c3-114">Bireysel özellik adlarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="4f8c3-114">Customize individual property names</span></span>

<span data-ttu-id="4f8c3-115">Ayrı özelliklerin adını ayarlamak için [[Jsonpropertyname]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="4f8c3-115">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="4f8c3-116">Serileştirme ve sonuç JSON için örnek bir tür aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="4f8c3-116">Here's an example type to serialize and resulting JSON:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPropertyNameAttribute":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="4f8c3-117">Bu öznitelik tarafından ayarlanan özellik adı:</span><span class="sxs-lookup"><span data-stu-id="4f8c3-117">The property name set by this attribute:</span></span>

* <span data-ttu-id="4f8c3-118">Serileştirme ve seri durumundan çıkarma için her iki yönde de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4f8c3-118">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="4f8c3-119">Özellik adlandırma ilkelerine göre önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="4f8c3-119">Takes precedence over property naming policies.</span></span>

## <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="4f8c3-120">Tüm JSON Özellik adları için ortası Case kullanın</span><span class="sxs-lookup"><span data-stu-id="4f8c3-120">Use camel case for all JSON property names</span></span>

<span data-ttu-id="4f8c3-121">Tüm JSON Özellik adları için ortası durumunu kullanmak için, <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> `JsonNamingPolicy.CamelCase` Aşağıdaki örnekte gösterildiği gibi olarak ayarlanır:</span><span class="sxs-lookup"><span data-stu-id="4f8c3-121">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundTripCamelCasePropertyNames.cs" id="Serialize":::

<span data-ttu-id="4f8c3-122">Seri hale getirmek ve JSON çıktısı için örnek bir sınıf aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="4f8c3-122">Here's an example class to serialize and JSON output:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPropertyNameAttribute":::

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="4f8c3-123">Ortası durum özelliği adlandırma ilkesi:</span><span class="sxs-lookup"><span data-stu-id="4f8c3-123">The camel case property naming policy:</span></span>

* <span data-ttu-id="4f8c3-124">Serileştirme ve seri durumdan çıkarma için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4f8c3-124">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="4f8c3-125">Öznitelikleri tarafından geçersiz kılınır `[JsonPropertyName]` .</span><span class="sxs-lookup"><span data-stu-id="4f8c3-125">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="4f8c3-126">Bu nedenle, örnekteki JSON Özellik adının `Wind` ortası durum olmaması neden olur.</span><span class="sxs-lookup"><span data-stu-id="4f8c3-126">This is why the JSON property name `Wind` in the example is not camel case.</span></span>

## <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="4f8c3-127">Özel bir JSON Özellik adlandırma ilkesi kullanma</span><span class="sxs-lookup"><span data-stu-id="4f8c3-127">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="4f8c3-128">Özel bir JSON Özellik adlandırma ilkesi kullanmak için, <xref:System.Text.Json.JsonNamingPolicy> <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> Aşağıdaki örnekte gösterildiği gibi yönteminden türeten bir sınıf oluşturun ve yöntemi geçersiz kılın:</span><span class="sxs-lookup"><span data-stu-id="4f8c3-128">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/UpperCaseNamingPolicy.cs":::

<span data-ttu-id="4f8c3-129">Daha sonra <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> özelliği, adlandırma ilkesi sınıfınızın bir örneğine ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="4f8c3-129">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripPropertyNamingPolicy.cs" id="Serialize":::

<span data-ttu-id="4f8c3-130">Seri hale getirmek ve JSON çıktısı için örnek bir sınıf aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="4f8c3-130">Here's an example class to serialize and JSON output:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPropertyNameAttribute":::

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATURECELSIUS": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="4f8c3-131">JSON özelliği adlandırma ilkesi:</span><span class="sxs-lookup"><span data-stu-id="4f8c3-131">The JSON property naming policy:</span></span>

* <span data-ttu-id="4f8c3-132">Serileştirme ve seri durumdan çıkarma için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4f8c3-132">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="4f8c3-133">Öznitelikleri tarafından geçersiz kılınır `[JsonPropertyName]` .</span><span class="sxs-lookup"><span data-stu-id="4f8c3-133">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="4f8c3-134">Bu, örnekteki JSON Özellik adının `Wind` büyük harfle değil.</span><span class="sxs-lookup"><span data-stu-id="4f8c3-134">This is why the JSON property name `Wind` in the example is not upper case.</span></span>

## <a name="camel-case-dictionary-keys"></a><span data-ttu-id="4f8c3-135">Camel durum sözlüğü anahtarları</span><span class="sxs-lookup"><span data-stu-id="4f8c3-135">Camel case dictionary keys</span></span>

<span data-ttu-id="4f8c3-136">Seri hale getirilecek bir nesnenin özelliği tür ise `Dictionary<string,TValue>` , `string` anahtarlar ortası duruma dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="4f8c3-136">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="4f8c3-137">Bunu yapmak için, <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> `JsonNamingPolicy.CamelCase` Aşağıdaki örnekte gösterildiği gibi öğesini olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="4f8c3-137">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCamelCaseDictionaryKeys.cs" id="Serialize":::

<span data-ttu-id="4f8c3-138">Anahtar-değer çiftlerine sahip adlı bir sözlük ile bir nesneyi serileştirmek `TemperatureRanges` `"ColdMinTemp", 20` ve `"HotMinTemp", 40` Aşağıdaki örnekte olduğu gibi JSON çıktısına neden olur:</span><span class="sxs-lookup"><span data-stu-id="4f8c3-138">Serializing an object with a dictionary named `TemperatureRanges` that has key-value pairs `"ColdMinTemp", 20` and `"HotMinTemp", 40` would result in JSON output like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "coldMinTemp": 20,
    "hotMinTemp": 40
  }
}
```

<span data-ttu-id="4f8c3-139">Sözlük anahtarları için ortası örnek adlandırma ilkesi yalnızca serileştirme için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4f8c3-139">The camel case naming policy for dictionary keys applies to serialization only.</span></span> <span data-ttu-id="4f8c3-140">Bir sözlüğün serisini kaldırırsanız, için belirtseniz bile anahtarlar JSON dosyasıyla eşleşir `JsonNamingPolicy.CamelCase` `DictionaryKeyPolicy` .</span><span class="sxs-lookup"><span data-stu-id="4f8c3-140">If you deserialize a dictionary, the keys will match the JSON file even if you specify `JsonNamingPolicy.CamelCase` for the `DictionaryKeyPolicy`.</span></span>

## <a name="enums-as-strings"></a><span data-ttu-id="4f8c3-141">Dizeler dize olarak numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="4f8c3-141">Enums as strings</span></span>

<span data-ttu-id="4f8c3-142">Varsayılan olarak, numaralandırmalar sayı olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="4f8c3-142">By default, enums are serialized as numbers.</span></span> <span data-ttu-id="4f8c3-143">Sabit listesi adlarını dizeler olarak seri hale getirmek için öğesini kullanın <xref:System.Text.Json.Serialization.JsonStringEnumConverter> .</span><span class="sxs-lookup"><span data-stu-id="4f8c3-143">To serialize enum names as strings, use the <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span></span>

<span data-ttu-id="4f8c3-144">Örneğin, bir sabit listesi olan aşağıdaki sınıfı seri hale getirmeniz gerektiğini varsayalım:</span><span class="sxs-lookup"><span data-stu-id="4f8c3-144">For example, suppose you need to serialize the following class that has an enum:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithEnum":::

<span data-ttu-id="4f8c3-145">Özet ise `Hot` , varsayılan olarak SERILEŞTIRILMIŞ JSON sayısal değer 3 ' ü içerir:</span><span class="sxs-lookup"><span data-stu-id="4f8c3-145">If the Summary is `Hot`, by default the serialized JSON has the numeric value 3:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

<span data-ttu-id="4f8c3-146">Aşağıdaki örnek kod, sayısal değerler yerine enum adlarını seri hale getirir ve adları ortası örneğine dönüştürür:</span><span class="sxs-lookup"><span data-stu-id="4f8c3-146">The following sample code serializes the enum names instead of the numeric values, and converts the names to camel case:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs" id="Serialize":::

<span data-ttu-id="4f8c3-147">Elde edilen JSON aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="4f8c3-147">The resulting JSON looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

<span data-ttu-id="4f8c3-148">Aşağıdaki örnekte gösterildiği gibi, sabit listesi dize adları da seri durumdan çıkarılmış olabilir:</span><span class="sxs-lookup"><span data-stu-id="4f8c3-148">Enum string names can be deserialized as well, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs" id="Deserialize":::

## <a name="see-also"></a><span data-ttu-id="4f8c3-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f8c3-149">See also</span></span>

* [<span data-ttu-id="4f8c3-150">System.Text.Json bakýþ</span><span class="sxs-lookup"><span data-stu-id="4f8c3-150">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="4f8c3-151">JsonSerializerOptions örneğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="4f8c3-151">Instantiate JsonSerializerOptions</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="4f8c3-152">Büyük/küçük harfe duyarsız eşleştirmeyi etkinleştir</span><span class="sxs-lookup"><span data-stu-id="4f8c3-152">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="4f8c3-153">Özellikleri yoksay</span><span class="sxs-lookup"><span data-stu-id="4f8c3-153">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="4f8c3-154">Geçersiz JSON 'a izin ver</span><span class="sxs-lookup"><span data-stu-id="4f8c3-154">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="4f8c3-155">Tutamaç taşması JSON</span><span class="sxs-lookup"><span data-stu-id="4f8c3-155">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="4f8c3-156">Döngüsel başvuruları koru</span><span class="sxs-lookup"><span data-stu-id="4f8c3-156">Preserve circular references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="4f8c3-157">Değişmez türler ve genel olmayan erişimciler</span><span class="sxs-lookup"><span data-stu-id="4f8c3-157">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="4f8c3-158">Polimorfik serileştirme</span><span class="sxs-lookup"><span data-stu-id="4f8c3-158">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="4f8c3-159">[System.Text.Json API başvurusu](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="4f8c3-159">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
