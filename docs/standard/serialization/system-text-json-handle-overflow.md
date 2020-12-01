---
title: İle taşma JSON ile işleme System.Text.Json
description: .NET 'teki JSON 'a serileştirirken ve seri durumdan çıkarılırken taşma JSON işlemesini öğrenin.
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 2c40d42b26bc5bd05f592cc51c6b5b9b4c6bbd9e
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96440020"
---
# <a name="how-to-handle-overflow-json-with-no-locsystemtextjson"></a><span data-ttu-id="a65f8-103">İle taşma JSON ile işleme System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="a65f8-103">How to handle overflow JSON with System.Text.Json</span></span>

<span data-ttu-id="a65f8-104">Bu makalede, ad alanıyla taşma JSON 'u nasıl işleyeceğinizi öğreneceksiniz `System.Text.Json` .</span><span class="sxs-lookup"><span data-stu-id="a65f8-104">In this article, you will learn how to handle overflow JSON with the `System.Text.Json` namespace.</span></span>

## <a name="handle-overflow-json"></a><span data-ttu-id="a65f8-105">Tutamaç taşması JSON</span><span class="sxs-lookup"><span data-stu-id="a65f8-105">Handle overflow JSON</span></span>

<span data-ttu-id="a65f8-106">Seri durumdan çıkarma sırasında, JSON 'da hedef türünün özellikleriyle temsil edilmeyen verileri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a65f8-106">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="a65f8-107">Örneğin, hedef türünün bu olduğunu varsayalım:</span><span class="sxs-lookup"><span data-stu-id="a65f8-107">For example, suppose your target type is this:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

<span data-ttu-id="a65f8-108">Ve seri durumdan çıkarılacak JSON şu şekilde yapılır:</span><span class="sxs-lookup"><span data-stu-id="a65f8-108">And the JSON to be deserialized is this:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "Summary": "Hot",
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

<span data-ttu-id="a65f8-109">Gösterilen türde gösterilen JSON serisini kaldırırsanız, `DatesAvailable` ve `SummaryWords` özellikleri nonereye gidebileceği ve kaybediliyor.</span><span class="sxs-lookup"><span data-stu-id="a65f8-109">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="a65f8-110">Bu özellikler gibi ek verileri yakalamak için, [[Jsonextensiondata]](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) özniteliğini türü bir özelliğe uygulayın `Dictionary<string,object>` `Dictionary<string,JsonElement>` :</span><span class="sxs-lookup"><span data-stu-id="a65f8-110">To capture extra data such as these properties, apply the [[JsonExtensionData]](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithExtensionData":::

<span data-ttu-id="a65f8-111">Daha önce Bu örnek türünde gösterilen JSON serisini kaldırdığınızda, ek veri özelliğin anahtar-değer çiftleri haline gelir `ExtensionData` :</span><span class="sxs-lookup"><span data-stu-id="a65f8-111">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

| <span data-ttu-id="a65f8-112">Özellik</span><span class="sxs-lookup"><span data-stu-id="a65f8-112">Property</span></span> | <span data-ttu-id="a65f8-113">Değer</span><span class="sxs-lookup"><span data-stu-id="a65f8-113">Value</span></span> | <span data-ttu-id="a65f8-114">Notlar</span><span class="sxs-lookup"><span data-stu-id="a65f8-114">Notes</span></span> |
|--|--|--|
| `Date` | `"8/1/2019 12:00:00 AM -07:00"` |  |
| `TemperatureCelsius` | `0` | <span data-ttu-id="a65f8-115">Büyük/küçük harfe duyarlı uyuşmazlık ( `temperatureCelsius` JSON 'da), bu nedenle özellik ayarlanmadı.</span><span class="sxs-lookup"><span data-stu-id="a65f8-115">Case-sensitive mismatch (`temperatureCelsius` in the JSON), so the property isn't set.</span></span> |
| `Summary` | `"Hot"` |  |
| `ExtensionData` | `temperatureCelsius: 25` | <span data-ttu-id="a65f8-116">Büyük/küçük harf eşleşmediğinden, bu JSON özelliği çok fazla olur ve sözlükte anahtar-değer çifti olur.</span><span class="sxs-lookup"><span data-stu-id="a65f8-116">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span> |
| `DatesAvailable` | `[ "8/1/2019 12:00:00 AM -07:00", "8/2/2019 12:00:00 AM -07:00" ]` | <span data-ttu-id="a65f8-117">JSON 'dan fazladan özellik, değer nesnesi olarak bir dizi ile anahtar-değer çifti haline gelir.</span><span class="sxs-lookup"><span data-stu-id="a65f8-117">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span> |
| `SummaryWords` | `[ "Cool", "Windy", "Humid" ]` | <span data-ttu-id="a65f8-118">JSON 'dan fazladan özellik, değer nesnesi olarak bir dizi ile anahtar-değer çifti haline gelir.</span><span class="sxs-lookup"><span data-stu-id="a65f8-118">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span> |

<span data-ttu-id="a65f8-119">Hedef nesne serileştirildiğinde, uzantı veri anahtarı değer çiftleri, gelen JSON 'da olduğu gibi JSON özellikleri olur:</span><span class="sxs-lookup"><span data-stu-id="a65f8-119">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 0,
  "Summary": "Hot",
  "temperatureCelsius": 25,
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

<span data-ttu-id="a65f8-120">`ExtensionData`Özellik ADıNıN JSON içinde görünmediğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="a65f8-120">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="a65f8-121">Bu davranış, JSON 'nin seri durumdan çıkarılmazsız ek verileri kaybetmeden bir gidiş dönüş yapmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a65f8-121">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="see-also"></a><span data-ttu-id="a65f8-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a65f8-122">See also</span></span>

* [<span data-ttu-id="a65f8-123">System.Text.Json bakýþ</span><span class="sxs-lookup"><span data-stu-id="a65f8-123">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="a65f8-124">JsonSerializerOptions örneğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="a65f8-124">Instantiate JsonSerializerOptions</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="a65f8-125">Büyük/küçük harfe duyarsız eşleştirmeyi etkinleştir</span><span class="sxs-lookup"><span data-stu-id="a65f8-125">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="a65f8-126">Özellik adlarını ve değerlerini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="a65f8-126">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="a65f8-127">Özellikleri yoksay</span><span class="sxs-lookup"><span data-stu-id="a65f8-127">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="a65f8-128">Geçersiz JSON 'a izin ver</span><span class="sxs-lookup"><span data-stu-id="a65f8-128">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="a65f8-129">Döngüsel başvuruları koru</span><span class="sxs-lookup"><span data-stu-id="a65f8-129">Preserve circular references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="a65f8-130">Değişmez türler ve genel olmayan erişimciler</span><span class="sxs-lookup"><span data-stu-id="a65f8-130">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="a65f8-131">Polimorfik serileştirme</span><span class="sxs-lookup"><span data-stu-id="a65f8-131">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="a65f8-132">[System.Text.Json API başvurusu](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="a65f8-132">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
