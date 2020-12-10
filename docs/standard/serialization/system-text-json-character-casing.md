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
ms.openlocfilehash: 3e2fb8cbdd35e772b5e97c731199f69aa834bd0a
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009748"
---
# <a name="how-to-enable-case-insensitive-property-name-matching-with-no-locsystemtextjson"></a><span data-ttu-id="22eeb-103">İle eşleşme büyük/küçük harf duyarsız Özellik adı etkinleştirme System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="22eeb-103">How to enable case-insensitive property name matching with System.Text.Json</span></span>

<span data-ttu-id="22eeb-104">Bu makalede, ad alanıyla büyük/küçük harfe duyarsız Özellik adı eşleştirmeyi nasıl etkinleştireceğinizi öğreneceksiniz `System.Text.Json` .</span><span class="sxs-lookup"><span data-stu-id="22eeb-104">In this article, you will learn how to enable case-insensitive property name matching with the `System.Text.Json` namespace.</span></span>

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="22eeb-105">Büyük/küçük harfe duyarsız Özellik eşleştirme</span><span class="sxs-lookup"><span data-stu-id="22eeb-105">Case-insensitive property matching</span></span>

<span data-ttu-id="22eeb-106">Varsayılan olarak, seri durumdan çıkarma JSON ile hedef nesne özellikleri arasındaki büyük/küçük harfe duyarlı Özellik adı eşleşmelerini arar.</span><span class="sxs-lookup"><span data-stu-id="22eeb-106">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="22eeb-107">Bu davranışı değiştirmek için şu <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> şekilde ayarlayın `true` :</span><span class="sxs-lookup"><span data-stu-id="22eeb-107">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

> [!NOTE]
> <span data-ttu-id="22eeb-108">[Web varsayılanı](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions) , büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="22eeb-108">The [web default](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions) is case-insensitive.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DeserializeCaseInsensitive.cs" id="Deserialize":::

<span data-ttu-id="22eeb-109">Aşağıda, ortası Case özellik adlarına sahip JSON örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="22eeb-109">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="22eeb-110">Bu,, Pascal case özellik adlarına sahip olan aşağıdaki türde seri durumdan çıkarılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="22eeb-110">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

## <a name="see-also"></a><span data-ttu-id="22eeb-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="22eeb-111">See also</span></span>

* [<span data-ttu-id="22eeb-112">System.Text.Json bakýþ</span><span class="sxs-lookup"><span data-stu-id="22eeb-112">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="22eeb-113">JSON’u seri hale getirme ve seri halden çıkarma</span><span class="sxs-lookup"><span data-stu-id="22eeb-113">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="22eeb-114">JsonSerializerOptions örneklerinin örneğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="22eeb-114">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="22eeb-115">Özellik adlarını ve değerlerini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="22eeb-115">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="22eeb-116">Özellikleri yoksayma</span><span class="sxs-lookup"><span data-stu-id="22eeb-116">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="22eeb-117">Geçersiz JSON’a izin verme</span><span class="sxs-lookup"><span data-stu-id="22eeb-117">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="22eeb-118">Sap taşması JSON’ı</span><span class="sxs-lookup"><span data-stu-id="22eeb-118">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="22eeb-119">Başvuruları koruma</span><span class="sxs-lookup"><span data-stu-id="22eeb-119">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="22eeb-120">Sabit türler ve genel olmayan erişimciler</span><span class="sxs-lookup"><span data-stu-id="22eeb-120">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="22eeb-121">Polimorfik serileştirme</span><span class="sxs-lookup"><span data-stu-id="22eeb-121">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="22eeb-122">' Den ' a geçiş Newtonsoft.JsonSystem.Text.Json</span><span class="sxs-lookup"><span data-stu-id="22eeb-122">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="22eeb-123">Karakter kodlamasını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="22eeb-123">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="22eeb-124">Özel serileştiriciler ve seri hale getiriciler yazma</span><span class="sxs-lookup"><span data-stu-id="22eeb-124">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="22eeb-125">JSON serileştirme için özel dönüştürücüler yazma</span><span class="sxs-lookup"><span data-stu-id="22eeb-125">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="22eeb-126">DateTime ve DateTimeOffset desteği</span><span class="sxs-lookup"><span data-stu-id="22eeb-126">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="22eeb-127">[System.Text.Json API başvurusu](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="22eeb-127">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="22eeb-128">[System.Text.Json. Serileştirme API başvurusu](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="22eeb-128">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
