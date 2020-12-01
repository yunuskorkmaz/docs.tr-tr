---
title: İle özellikleri yoksayma System.Text.Json
description: .NET ' te ile serileştirilirken özellikleri nasıl yoksaymayı öğrenin System.Text.Json .
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: ed7ef8509d6660bbbbaf194a87aa9d4815143507
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96440011"
---
# <a name="how-to-ignore-properties-with-no-locsystemtextjson"></a><span data-ttu-id="fc7ed-103">İle özellikleri yoksayma System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="fc7ed-103">How to ignore properties with System.Text.Json</span></span>

<span data-ttu-id="fc7ed-104">C# nesnelerini JavaScript Nesne Gösterimi (JSON) olarak serileştirilirken, varsayılan olarak tüm ortak özellikler serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="fc7ed-104">When serializing C# objects to JavaScript Object Notation (JSON), by default, all public properties are serialized.</span></span> <span data-ttu-id="fc7ed-105">Sonuçta ortaya çıkan JSON 'da görünmesini istemiyorsanız, birkaç seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="fc7ed-105">If you don't want some of them to appear in the resulting JSON, you have several options.</span></span> <span data-ttu-id="fc7ed-106">Bu makalede, çeşitli ölçütlere göre özellikleri yok saymayı öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="fc7ed-106">In this article you learn how to ignore properties based on various criteria:</span></span>

::: zone pivot="dotnet-5-0"

* [<span data-ttu-id="fc7ed-107">Bireysel Özellikler</span><span class="sxs-lookup"><span data-stu-id="fc7ed-107">Individual properties</span></span>](#ignore-individual-properties)
* [<span data-ttu-id="fc7ed-108">Tüm salt okunurdur özellikleri</span><span class="sxs-lookup"><span data-stu-id="fc7ed-108">All read-only properties</span></span>](#ignore-all-read-only-properties)
* [<span data-ttu-id="fc7ed-109">Tüm null değerli özellikler</span><span class="sxs-lookup"><span data-stu-id="fc7ed-109">All null-value properties</span></span>](#ignore-all-null-value-properties)
* [<span data-ttu-id="fc7ed-110">Tüm varsayılan değer özellikleri</span><span class="sxs-lookup"><span data-stu-id="fc7ed-110">All default-value properties</span></span>](#ignore-all-default-value-properties)
::: zone-end

::: zone pivot="dotnet-core-3-1"

* [<span data-ttu-id="fc7ed-111">Bireysel Özellikler</span><span class="sxs-lookup"><span data-stu-id="fc7ed-111">Individual properties</span></span>](#ignore-individual-properties)
* [<span data-ttu-id="fc7ed-112">Tüm salt okunurdur özellikleri</span><span class="sxs-lookup"><span data-stu-id="fc7ed-112">All read-only properties</span></span>](#ignore-all-read-only-properties)
* [<span data-ttu-id="fc7ed-113">Tüm null değerli özellikler</span><span class="sxs-lookup"><span data-stu-id="fc7ed-113">All null-value properties</span></span>](#ignore-all-null-value-properties)
::: zone-end

## <a name="ignore-individual-properties"></a><span data-ttu-id="fc7ed-114">Tek tek özellikleri yoksay</span><span class="sxs-lookup"><span data-stu-id="fc7ed-114">Ignore individual properties</span></span>

<span data-ttu-id="fc7ed-115">Ayrı özellikleri yoksaymak için [[Jsonıgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="fc7ed-115">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="fc7ed-116">Seri hale getirmek ve JSON çıktısı için örnek bir tür aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="fc7ed-116">Here's an example type to serialize and JSON output:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithIgnoreAttribute":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

::: zone pivot="dotnet-5-0"
<span data-ttu-id="fc7ed-117">[[Jsonıgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) özniteliğinin özelliğini ayarlayarak koşullu dışlama belirtebilirsiniz `Condition` .</span><span class="sxs-lookup"><span data-stu-id="fc7ed-117">You can specify conditional exclusion by setting the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute's `Condition` property.</span></span> <span data-ttu-id="fc7ed-118"><xref:System.Text.Json.Serialization.JsonIgnoreCondition>Sabit listesi aşağıdaki seçenekleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="fc7ed-118">The <xref:System.Text.Json.Serialization.JsonIgnoreCondition> enum provides the following options:</span></span>

* <span data-ttu-id="fc7ed-119">`Always` -Özellik her zaman yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="fc7ed-119">`Always` - The property is always ignored.</span></span> <span data-ttu-id="fc7ed-120">Hayır `Condition` belirtilmişse, bu seçenek kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="fc7ed-120">If no `Condition` is specified, this option is assumed.</span></span>
* <span data-ttu-id="fc7ed-121">`Never` -Özelliği `DefaultIgnoreCondition` ,, `IgnoreReadOnlyProperties` ve genel ayarlarından bağımsız olarak her zaman serileştirilmiş ve seri durumdan çıkarılmış olur `IgnoreReadOnlyFields` .</span><span class="sxs-lookup"><span data-stu-id="fc7ed-121">`Never` - The property is always serialized and deserialized, regardless of the `DefaultIgnoreCondition`, `IgnoreReadOnlyProperties`, and `IgnoreReadOnlyFields` global settings.</span></span>
* <span data-ttu-id="fc7ed-122">`WhenWritingDefault` -Bir başvuru türü `null` , null yapılabilir bir değer türü `null` veya değer türü ise, bu özellik serileştirme üzerinde yok sayılır `default` .</span><span class="sxs-lookup"><span data-stu-id="fc7ed-122">`WhenWritingDefault` - The property is ignored on serialization if it's a reference type `null`, a nullable value type `null`, or a value type `default`.</span></span>
* <span data-ttu-id="fc7ed-123">`WhenWritingNull` -Bir başvuru türü `null` veya null yapılabilir bir değer türü ise, bu özellik serileştirme üzerinde yok sayılır `null` .</span><span class="sxs-lookup"><span data-stu-id="fc7ed-123">`WhenWritingNull` - The property is ignored on serialization if it's a reference type `null`, or a nullable value type `null`.</span></span>

<span data-ttu-id="fc7ed-124">Aşağıdaki örnek, [[Jsonıgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) özniteliğinin özelliğinin kullanımını gösterir `Condition` :</span><span class="sxs-lookup"><span data-stu-id="fc7ed-124">The following example illustrates use of the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute's `Condition` property:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/JsonIgnoreAttributeExample.cs" highlight="10,13,16":::
::: zone-end

## <a name="ignore-all-read-only-properties"></a><span data-ttu-id="fc7ed-125">Tüm salt okunurdur özellikleri yoksay</span><span class="sxs-lookup"><span data-stu-id="fc7ed-125">Ignore all read-only properties</span></span>

<span data-ttu-id="fc7ed-126">Bir özellik, genel bir alıcı içeriyorsa ancak genel bir ayarlayıcı içermiyorsa salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="fc7ed-126">A property is read-only if it contains a public getter but not a public setter.</span></span> <span data-ttu-id="fc7ed-127">Serileştirilirken tüm salt okunurdur özellikleri yok saymak için <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> `true` Aşağıdaki örnekte gösterildiği gibi öğesini olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="fc7ed-127">To ignore all read-only properties when serializing, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeExcludeReadOnlyProperties.cs" id="Serialize":::

<span data-ttu-id="fc7ed-128">Seri hale getirmek ve JSON çıktısı için örnek bir tür aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="fc7ed-128">Here's an example type to serialize and JSON output:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithROProperty":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="fc7ed-129">Bu seçenek yalnızca serileştirme için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="fc7ed-129">This option applies only to serialization.</span></span> <span data-ttu-id="fc7ed-130">Seri durumdan çıkarma sırasında salt okuma özellikleri varsayılan olarak yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="fc7ed-130">During deserialization, read-only properties are ignored by default.</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="fc7ed-131">Bu seçenek yalnızca özellikler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="fc7ed-131">This option applies only to properties.</span></span> <span data-ttu-id="fc7ed-132">[Alanları serileştirilirken](system-text-json-how-to.md#include-fields)salt okunurdur alanları yok saymak için <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> genel ayarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="fc7ed-132">To ignore read-only fields when [serializing fields](system-text-json-how-to.md#include-fields), use the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> global setting.</span></span>
::: zone-end

## <a name="ignore-all-null-value-properties"></a><span data-ttu-id="fc7ed-133">Tüm null değer özelliklerini yoksay</span><span class="sxs-lookup"><span data-stu-id="fc7ed-133">Ignore all null-value properties</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="fc7ed-134">Tüm null değer özelliklerini yok saymak için, <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingNull> Aşağıdaki örnekte gösterildiği gibi özelliğini olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="fc7ed-134">To ignore all null-value properties, set the <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> property to <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingNull>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreNullOnSerialize.cs" highlight="28":::

::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="fc7ed-135">Serileştirilirken tüm null değer özelliklerini yok saymak için, <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> `true` Aşağıdaki örnekte gösterildiği gibi özelliğini olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="fc7ed-135">To ignore all null-value properties when serializing, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeExcludeNullValueProperties.cs" id="Serialize":::

<span data-ttu-id="fc7ed-136">Seri hale getirmek ve JSON çıktısı için örnek bir nesne aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="fc7ed-136">Here's an example object to serialize and JSON output:</span></span>

| <span data-ttu-id="fc7ed-137">Özellik</span><span class="sxs-lookup"><span data-stu-id="fc7ed-137">Property</span></span>             | <span data-ttu-id="fc7ed-138">Değer</span><span class="sxs-lookup"><span data-stu-id="fc7ed-138">Value</span></span>                         |
|----------------------|-------------------------------|
| `Date`               | `8/1/2019 12:00:00 AM -07:00` |
| `TemperatureCelsius` | `25`                          |
| `Summary`            | `null`                        |

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

::: zone-end

## <a name="ignore-all-default-value-properties"></a><span data-ttu-id="fc7ed-139">Tüm varsayılan değer özelliklerini yoksay</span><span class="sxs-lookup"><span data-stu-id="fc7ed-139">Ignore all default-value properties</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="fc7ed-140">Değer türü özelliklerindeki varsayılan değerlerin serileştirmesini engellemek için, <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault> Aşağıdaki örnekte gösterildiği gibi özelliğini olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="fc7ed-140">To prevent serialization of default values in value type properties, set the <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> property to <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreValueDefaultOnSerialize.cs" highlight="28":::
::: zone-end

<span data-ttu-id="fc7ed-141">Bu <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault> ayar aynı zamanda null değer başvuru türü ve null yapılabilir değer türü özelliklerinin serileştirmesini önler.</span><span class="sxs-lookup"><span data-stu-id="fc7ed-141">The <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault> setting also prevents serialization of null-value reference type and nullable value type properties.</span></span>

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="fc7ed-142">.NET Core 3,1 ' deki değer türü varsayılanlarına sahip özelliklerin serileştirmesini önleyen yerleşik bir yol yoktur `System.Text.Json` .</span><span class="sxs-lookup"><span data-stu-id="fc7ed-142">There is no built-in way to prevent serialization of properties with value type defaults in `System.Text.Json` in .NET Core 3.1.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="fc7ed-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc7ed-143">See also</span></span>

* [<span data-ttu-id="fc7ed-144">System.Text.Json bakýþ</span><span class="sxs-lookup"><span data-stu-id="fc7ed-144">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="fc7ed-145">JsonSerializerOptions örneğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="fc7ed-145">Instantiate JsonSerializerOptions</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="fc7ed-146">Büyük/küçük harfe duyarsız eşleştirmeyi etkinleştir</span><span class="sxs-lookup"><span data-stu-id="fc7ed-146">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="fc7ed-147">Özellik adlarını ve değerlerini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="fc7ed-147">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="fc7ed-148">Geçersiz JSON 'a izin ver</span><span class="sxs-lookup"><span data-stu-id="fc7ed-148">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="fc7ed-149">Tutamaç taşması JSON</span><span class="sxs-lookup"><span data-stu-id="fc7ed-149">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="fc7ed-150">Döngüsel başvuruları koru</span><span class="sxs-lookup"><span data-stu-id="fc7ed-150">Preserve circular references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="fc7ed-151">Değişmez türler ve genel olmayan erişimciler</span><span class="sxs-lookup"><span data-stu-id="fc7ed-151">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="fc7ed-152">Polimorfik serileştirme</span><span class="sxs-lookup"><span data-stu-id="fc7ed-152">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="fc7ed-153">[System.Text.Json API başvurusu](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="fc7ed-153">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
