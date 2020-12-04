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
ms.openlocfilehash: 2d663ac8c1c15d61959a62c40d9a3b0993484032
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599082"
---
# <a name="how-to-enable-case-insensitive-property-name-matching-with-no-locsystemtextjson"></a><span data-ttu-id="df78b-103">İle eşleşme büyük/küçük harf duyarsız Özellik adı etkinleştirme System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="df78b-103">How to enable case-insensitive property name matching with System.Text.Json</span></span>

<span data-ttu-id="df78b-104">Bu makalede, ad alanıyla büyük/küçük harfe duyarsız Özellik adı eşleştirmeyi nasıl etkinleştireceğinizi öğreneceksiniz `System.Text.Json` .</span><span class="sxs-lookup"><span data-stu-id="df78b-104">In this article, you will learn how to enable case-insensitive property name matching with the `System.Text.Json` namespace.</span></span>

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="df78b-105">Büyük/küçük harfe duyarsız Özellik eşleştirme</span><span class="sxs-lookup"><span data-stu-id="df78b-105">Case-insensitive property matching</span></span>

<span data-ttu-id="df78b-106">Varsayılan olarak, seri durumdan çıkarma JSON ile hedef nesne özellikleri arasındaki büyük/küçük harfe duyarlı Özellik adı eşleşmelerini arar.</span><span class="sxs-lookup"><span data-stu-id="df78b-106">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="df78b-107">Bu davranışı değiştirmek için şu <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> şekilde ayarlayın `true` :</span><span class="sxs-lookup"><span data-stu-id="df78b-107">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

> [!NOTE]
> <span data-ttu-id="df78b-108">[Web varsayılanı](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions) , büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="df78b-108">The [web default](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions) is case-insensitive.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DeserializeCaseInsensitive.cs" id="Deserialize":::

<span data-ttu-id="df78b-109">Aşağıda, ortası Case özellik adlarına sahip JSON örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="df78b-109">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="df78b-110">Bu,, Pascal case özellik adlarına sahip olan aşağıdaki türde seri durumdan çıkarılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="df78b-110">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

## <a name="see-also"></a><span data-ttu-id="df78b-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df78b-111">See also</span></span>

* [<span data-ttu-id="df78b-112">System.Text.Json bakýþ</span><span class="sxs-lookup"><span data-stu-id="df78b-112">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="df78b-113">JsonSerializerOptions nesne örneği oluşturma</span><span class="sxs-lookup"><span data-stu-id="df78b-113">Instantiate JsonSerializerOptions</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="df78b-114">Özellik adlarını ve değerlerini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="df78b-114">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="df78b-115">Özellikleri yoksayma</span><span class="sxs-lookup"><span data-stu-id="df78b-115">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="df78b-116">Geçersiz JSON’a izin verme</span><span class="sxs-lookup"><span data-stu-id="df78b-116">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="df78b-117">Sap taşması JSON’ı</span><span class="sxs-lookup"><span data-stu-id="df78b-117">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="df78b-118">Döngüsel başvuruları koru</span><span class="sxs-lookup"><span data-stu-id="df78b-118">Preserve circular references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="df78b-119">Sabit türler ve genel olmayan erişimciler</span><span class="sxs-lookup"><span data-stu-id="df78b-119">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="df78b-120">Polimorfik serileştirme</span><span class="sxs-lookup"><span data-stu-id="df78b-120">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="df78b-121">[System.Text.Json API başvurusu](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="df78b-121">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
