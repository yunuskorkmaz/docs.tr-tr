---
title: İle eşleşme büyük/küçük harf duyarsız Özellik adı etkinleştirme System.Text.Json
description: .NET 'teki JSON 'a serileştirirken ve seri durumdan çıkarılırken büyük/küçük harfe duyarsız Özellik adı eşleştirmeyi nasıl etkinleştirebileceğinizi öğrenin.
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 4bd57d32120f51ffd1ff09c9817edbafa28a3f19
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96440008"
---
# <a name="how-to-enable-case-insensitive-property-name-matching-with-no-locsystemtextjson"></a><span data-ttu-id="c31f9-103">İle eşleşme büyük/küçük harf duyarsız Özellik adı etkinleştirme System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="c31f9-103">How to enable case-insensitive property name matching with System.Text.Json</span></span>

<span data-ttu-id="c31f9-104">Bu makalede, ad alanıyla büyük/küçük harfe duyarsız Özellik adı eşleştirmeyi nasıl etkinleştireceğinizi öğreneceksiniz `System.Text.Json` .</span><span class="sxs-lookup"><span data-stu-id="c31f9-104">In this article, you will learn how to enable case-insensitive property name matching with the `System.Text.Json` namespace.</span></span>

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="c31f9-105">Büyük/küçük harfe duyarsız Özellik eşleştirme</span><span class="sxs-lookup"><span data-stu-id="c31f9-105">Case-insensitive property matching</span></span>

<span data-ttu-id="c31f9-106">Varsayılan olarak, seri durumdan çıkarma JSON ile hedef nesne özellikleri arasındaki büyük/küçük harfe duyarlı Özellik adı eşleşmelerini arar.</span><span class="sxs-lookup"><span data-stu-id="c31f9-106">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="c31f9-107">Bu davranışı değiştirmek için şu <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> şekilde ayarlayın `true` :</span><span class="sxs-lookup"><span data-stu-id="c31f9-107">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

> [!NOTE]
> <span data-ttu-id="c31f9-108">[Web Varsayılanları](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions) , büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="c31f9-108">The [web defaults](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions) is case-insensitive.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DeserializeCaseInsensitive.cs" id="Deserialize":::

<span data-ttu-id="c31f9-109">Aşağıda, ortası Case özellik adlarına sahip JSON örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c31f9-109">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="c31f9-110">Bu,, Pascal case özellik adlarına sahip olan aşağıdaki türde seri durumdan çıkarılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="c31f9-110">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

## <a name="see-also"></a><span data-ttu-id="c31f9-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c31f9-111">See also</span></span>

* [<span data-ttu-id="c31f9-112">System.Text.Json bakýþ</span><span class="sxs-lookup"><span data-stu-id="c31f9-112">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="c31f9-113">JsonSerializerOptions örneğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="c31f9-113">Instantiate JsonSerializerOptions</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="c31f9-114">Özellik adlarını ve değerlerini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="c31f9-114">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="c31f9-115">Özellikleri yoksay</span><span class="sxs-lookup"><span data-stu-id="c31f9-115">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="c31f9-116">Geçersiz JSON 'a izin ver</span><span class="sxs-lookup"><span data-stu-id="c31f9-116">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="c31f9-117">Tutamaç taşması JSON</span><span class="sxs-lookup"><span data-stu-id="c31f9-117">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="c31f9-118">Döngüsel başvuruları koru</span><span class="sxs-lookup"><span data-stu-id="c31f9-118">Preserve circular references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="c31f9-119">Değişmez türler ve genel olmayan erişimciler</span><span class="sxs-lookup"><span data-stu-id="c31f9-119">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="c31f9-120">Polimorfik serileştirme</span><span class="sxs-lookup"><span data-stu-id="c31f9-120">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="c31f9-121">[System.Text.Json API başvurusu](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="c31f9-121">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
