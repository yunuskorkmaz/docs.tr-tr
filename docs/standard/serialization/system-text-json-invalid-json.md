---
title: İle bazı geçersiz JSON türlerine izin verme System.Text.Json
description: .NET 'teki JSON 'dan serileştirirken ve seri durumdan çıkarılırken yorumlara, sondaki virgüller ve tırnak içine alınmış numaralara nasıl izin vereceğinizi öğrenin.
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
ms.openlocfilehash: 60cbb98bb65ee5c1ffdd3043e42a04004530a115
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96440010"
---
# <a name="how-to-allow-some-kinds-of-invalid-json-with-no-locsystemtextjson"></a><span data-ttu-id="5e636-103">İle bazı geçersiz JSON türlerine izin verme System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="5e636-103">How to allow some kinds of invalid JSON with System.Text.Json</span></span>

<span data-ttu-id="5e636-104">Bu makalede, JSON 'da açıklamalara, sondaki virgüller ve tırnak içine alınmış sayılara ve sayıların dize olarak nasıl yazılacağını öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="5e636-104">In this article, you will learn how to allow comments, trailing commas, and quoted numbers in JSON, and how to write numbers as strings.</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="5e636-105">Yorumlara ve sondaki virgülleri izin ver</span><span class="sxs-lookup"><span data-stu-id="5e636-105">Allow comments and trailing commas</span></span>

<span data-ttu-id="5e636-106">Varsayılan olarak, JSON 'da yorumlara ve sondaki virgüllerin kullanımına izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="5e636-106">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="5e636-107">JSON 'da açıklamalara izin vermek için <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> özelliğini olarak ayarlayın `JsonCommentHandling.Skip` .</span><span class="sxs-lookup"><span data-stu-id="5e636-107">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span>
<span data-ttu-id="5e636-108">Ve sondaki virgüllerin kullanılmasına izin vermek için <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> özelliğini olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="5e636-108">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="5e636-109">Aşağıdaki örnek, her ikisine de izin vermeyi göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="5e636-109">The following example shows how to allow both:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DeserializeCommasComments.cs" id="Deserialize":::

<span data-ttu-id="5e636-110">Yorumlar ve sondaki virgülden oluşan örnek JSON aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5e636-110">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="allow-or-write-numbers-in-quotes"></a><span data-ttu-id="5e636-111">Tırnak işaretleri halinde izin ver veya yaz</span><span class="sxs-lookup"><span data-stu-id="5e636-111">Allow or write numbers in quotes</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="5e636-112">Bazı serileştiriciler sayıları JSON dizeleri (tırnak işaretleriyle çevrelenmiş) olarak kodlayabilir.</span><span class="sxs-lookup"><span data-stu-id="5e636-112">Some serializers encode numbers as JSON strings (surrounded by quotes).</span></span>

<span data-ttu-id="5e636-113">Örnek:</span><span class="sxs-lookup"><span data-stu-id="5e636-113">For example:</span></span>

```json
{
    "DegreesCelsius": "23"
}
```

<span data-ttu-id="5e636-114">Onun yerine:</span><span class="sxs-lookup"><span data-stu-id="5e636-114">Instead of:</span></span>

```json
{
    "DegreesCelsius": 23
}
```

<span data-ttu-id="5e636-115">Tırnak işaretleri içindeki sayıları seri hale getirmek veya giriş nesnesi grafiğinin tamamına tırnak içinde kabul etmek için <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A?displayProperty=nameWithType> Aşağıdaki örnekte gösterildiği gibi ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="5e636-115">To serialize numbers in quotes or accept numbers in quotes across the entire input object graph, set <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A?displayProperty=nameWithType> as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/QuotedNumbers.cs" highlight="27-29":::

<span data-ttu-id="5e636-116">`System.Text.Json`ASP.NET Core aracılığıyla dolaylı olarak kullandığınızda, ASP.NET Core [Web varsayılan seçeneklerini](xref:System.Text.Json.JsonSerializerDefaults.Web)belirttiğinden, serisi kaldırılırken tırnak işaretli sayılara izin verilir.</span><span class="sxs-lookup"><span data-stu-id="5e636-116">When you use `System.Text.Json` indirectly through ASP.NET Core, quoted numbers are allowed when deserializing because ASP.NET Core specifies [web default options](xref:System.Text.Json.JsonSerializerDefaults.Web).</span></span>

<span data-ttu-id="5e636-117">Belirli özellikler, alanlar veya türler için tırnak işaretli sayılara izin vermek veya yazmak için [[Jsonnumberhandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute) özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="5e636-117">To allow or write quoted numbers for specific properties, fields, or types, use the [[JsonNumberHandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute) attribute.</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="5e636-118">`System.Text.Json` .NET Core 3,1, tırnak işaretleriyle çevrelenen sayıları serileştirmek veya seri durumdan çıkarmayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="5e636-118">`System.Text.Json` in .NET Core 3.1 doesn't support serializing or deserializing numbers surrounded by quotation marks.</span></span> <span data-ttu-id="5e636-119">Daha fazla bilgi için bkz. [tekliflere Izin verme veya yazma numaraları](system-text-json-migrate-from-newtonsoft-how-to.md#allow-or-write-numbers-in-quotes).</span><span class="sxs-lookup"><span data-stu-id="5e636-119">For more information, see [Allow or write numbers in quotes](system-text-json-migrate-from-newtonsoft-how-to.md#allow-or-write-numbers-in-quotes).</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="5e636-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e636-120">See also</span></span>

* [<span data-ttu-id="5e636-121">System.Text.Json bakýþ</span><span class="sxs-lookup"><span data-stu-id="5e636-121">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="5e636-122">JsonSerializerOptions örneğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="5e636-122">Instantiate JsonSerializerOptions</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="5e636-123">Büyük/küçük harfe duyarsız eşleştirmeyi etkinleştir</span><span class="sxs-lookup"><span data-stu-id="5e636-123">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="5e636-124">Özellik adlarını ve değerlerini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="5e636-124">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="5e636-125">Özellikleri yoksay</span><span class="sxs-lookup"><span data-stu-id="5e636-125">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="5e636-126">Tutamaç taşması JSON</span><span class="sxs-lookup"><span data-stu-id="5e636-126">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="5e636-127">Döngüsel başvuruları koru</span><span class="sxs-lookup"><span data-stu-id="5e636-127">Preserve circular references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="5e636-128">Değişmez türler ve genel olmayan erişimciler</span><span class="sxs-lookup"><span data-stu-id="5e636-128">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="5e636-129">Polimorfik serileştirme</span><span class="sxs-lookup"><span data-stu-id="5e636-129">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="5e636-130">[System.Text.Json API başvurusu](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="5e636-130">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
