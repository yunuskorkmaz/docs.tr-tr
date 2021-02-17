---
title: İle bazı geçersiz JSON türlerine izin verme System.Text.Json
description: .NET 'teki JSON 'dan serileştirirken ve seri durumdan çıkarılırken yorumlara, sondaki virgüller ve tırnak içine alınmış numaralara nasıl izin vereceğinizi öğrenin.
ms.date: 12/03/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
dev_langs:
- csharp
- vb
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 19ceaeb882e8126826e7928122c25027bcb12275
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100581465"
---
# <a name="how-to-allow-some-kinds-of-invalid-json-with-systemtextjson"></a><span data-ttu-id="b08bd-103">İle bazı geçersiz JSON türlerine izin verme System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="b08bd-103">How to allow some kinds of invalid JSON with System.Text.Json</span></span>

<span data-ttu-id="b08bd-104">Bu makalede, JSON 'da açıklamalara, sondaki virgüller ve tırnak içine alınmış sayılara ve sayıların dize olarak nasıl yazılacağını öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="b08bd-104">In this article, you will learn how to allow comments, trailing commas, and quoted numbers in JSON, and how to write numbers as strings.</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="b08bd-105">Yorumlara ve sondaki virgülleri izin ver</span><span class="sxs-lookup"><span data-stu-id="b08bd-105">Allow comments and trailing commas</span></span>

<span data-ttu-id="b08bd-106">Varsayılan olarak, JSON 'da yorumlara ve sondaki virgüllerin kullanımına izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="b08bd-106">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="b08bd-107">JSON 'da açıklamalara izin vermek için <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> özelliğini olarak ayarlayın `JsonCommentHandling.Skip` .</span><span class="sxs-lookup"><span data-stu-id="b08bd-107">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span>
<span data-ttu-id="b08bd-108">Ve sondaki virgüllerin kullanılmasına izin vermek için <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> özelliğini olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="b08bd-108">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="b08bd-109">Aşağıdaki örnek, her ikisine de izin vermeyi göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="b08bd-109">The following example shows how to allow both:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DeserializeCommasComments.cs" id="Deserialize":::
:::code language="vb" source="snippets/system-text-json-how-to/vb/DeserializeCommasComments.vb" id="Deserialize":::

<span data-ttu-id="b08bd-110">Yorumlar ve sondaki virgülden oluşan örnek JSON aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="b08bd-110">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
  // Comments on
  /* separate lines */
}
```

## <a name="allow-or-write-numbers-in-quotes"></a><span data-ttu-id="b08bd-111">Tırnak işaretleri halinde izin ver veya yaz</span><span class="sxs-lookup"><span data-stu-id="b08bd-111">Allow or write numbers in quotes</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="b08bd-112">Bazı serileştiriciler sayıları JSON dizeleri (tırnak işaretleriyle çevrelenmiş) olarak kodlayabilir.</span><span class="sxs-lookup"><span data-stu-id="b08bd-112">Some serializers encode numbers as JSON strings (surrounded by quotes).</span></span>

<span data-ttu-id="b08bd-113">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b08bd-113">For example:</span></span>

```json
{
    "DegreesCelsius": "23"
}
```

<span data-ttu-id="b08bd-114">Onun yerine:</span><span class="sxs-lookup"><span data-stu-id="b08bd-114">Instead of:</span></span>

```json
{
    "DegreesCelsius": 23
}
```

<span data-ttu-id="b08bd-115">Tırnak işaretleri içindeki sayıları seri hale getirmek veya giriş nesnesi grafiğinin tamamına tırnak içinde kabul etmek için <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A?displayProperty=nameWithType> Aşağıdaki örnekte gösterildiği gibi ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="b08bd-115">To serialize numbers in quotes or accept numbers in quotes across the entire input object graph, set <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A?displayProperty=nameWithType> as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/QuotedNumbers.cs" highlight="27-29":::
:::code language="vb" source="snippets/system-text-json-how-to-5-0/vb/QuotedNumbers.vb" :::

<span data-ttu-id="b08bd-116">`System.Text.Json`ASP.NET Core aracılığıyla dolaylı olarak kullandığınızda, ASP.NET Core [Web varsayılan seçeneklerini](xref:System.Text.Json.JsonSerializerDefaults.Web)belirttiğinden, serisi kaldırılırken tırnak işaretli sayılara izin verilir.</span><span class="sxs-lookup"><span data-stu-id="b08bd-116">When you use `System.Text.Json` indirectly through ASP.NET Core, quoted numbers are allowed when deserializing because ASP.NET Core specifies [web default options](xref:System.Text.Json.JsonSerializerDefaults.Web).</span></span>

<span data-ttu-id="b08bd-117">Belirli özellikler, alanlar veya türler için tırnak işaretli sayılara izin vermek veya yazmak için [[Jsonnumberhandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute) özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b08bd-117">To allow or write quoted numbers for specific properties, fields, or types, use the [[JsonNumberHandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute) attribute.</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="b08bd-118">`System.Text.Json` .NET Core 3,1, tırnak işaretleriyle çevrelenen sayıları serileştirmek veya seri durumdan çıkarmayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="b08bd-118">`System.Text.Json` in .NET Core 3.1 doesn't support serializing or deserializing numbers surrounded by quotation marks.</span></span> <span data-ttu-id="b08bd-119">Daha fazla bilgi için bkz. [tekliflere Izin verme veya yazma numaraları](system-text-json-migrate-from-newtonsoft-how-to.md#allow-or-write-numbers-in-quotes).</span><span class="sxs-lookup"><span data-stu-id="b08bd-119">For more information, see [Allow or write numbers in quotes](system-text-json-migrate-from-newtonsoft-how-to.md#allow-or-write-numbers-in-quotes).</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="b08bd-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b08bd-120">See also</span></span>

* [<span data-ttu-id="b08bd-121">System.Text.Json bakýþ</span><span class="sxs-lookup"><span data-stu-id="b08bd-121">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="b08bd-122">JSON’u seri hale getirme ve seri halden çıkarma</span><span class="sxs-lookup"><span data-stu-id="b08bd-122">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="b08bd-123">JsonSerializerOptions örneklerinin örneğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="b08bd-123">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="b08bd-124">Büyük/küçük harf duyarlı eşlemeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="b08bd-124">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="b08bd-125">Özellik adlarını ve değerlerini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="b08bd-125">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="b08bd-126">Özellikleri yoksayma</span><span class="sxs-lookup"><span data-stu-id="b08bd-126">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="b08bd-127">Sap taşması JSON’ı</span><span class="sxs-lookup"><span data-stu-id="b08bd-127">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="b08bd-128">Başvuruları koruma</span><span class="sxs-lookup"><span data-stu-id="b08bd-128">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="b08bd-129">Sabit türler ve genel olmayan erişimciler</span><span class="sxs-lookup"><span data-stu-id="b08bd-129">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="b08bd-130">Polimorfik serileştirme</span><span class="sxs-lookup"><span data-stu-id="b08bd-130">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="b08bd-131">' Den ' a geçiş Newtonsoft.JsonSystem.Text.Json</span><span class="sxs-lookup"><span data-stu-id="b08bd-131">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="b08bd-132">Karakter kodlamasını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="b08bd-132">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="b08bd-133">Özel serileştiriciler ve seri hale getiriciler yazma</span><span class="sxs-lookup"><span data-stu-id="b08bd-133">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="b08bd-134">JSON serileştirme için özel dönüştürücüler yazma</span><span class="sxs-lookup"><span data-stu-id="b08bd-134">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="b08bd-135">DateTime ve DateTimeOffset desteği</span><span class="sxs-lookup"><span data-stu-id="b08bd-135">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="b08bd-136">[System.Text.Json API başvurusu](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="b08bd-136">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="b08bd-137">[System.Text.Json. Serileştirme API başvurusu](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="b08bd-137">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
