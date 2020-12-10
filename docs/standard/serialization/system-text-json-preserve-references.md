---
title: İle başvuruları koruma System.Text.Json
description: .NET 'teki JSON 'dan serileştirilirken ve seri durumdan çıkarılırken başvuruları nasıl koruyacağınızı ve döngüsel başvuruları nasıl işleyeceğinizi öğrenin.
ms.date: 12/09/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: d358c953c0979ca097c080fcd750d5ef95b07de0
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97008740"
---
# <a name="how-to-preserve-references-and-handle-circular-references-with-no-locsystemtextjson"></a><span data-ttu-id="1d925-103">Başvuruları koruma ve ile döngüsel başvuruları işleme System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="1d925-103">How to preserve references and handle circular references with System.Text.Json</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="1d925-104">Başvuruları korumak ve döngüsel başvuruları işlemek için olarak ayarlayın <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A> .</span><span class="sxs-lookup"><span data-stu-id="1d925-104">To preserve references and handle circular references, set <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> to <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A>.</span></span> <span data-ttu-id="1d925-105">Bu ayar aşağıdaki davranışa neden olur:</span><span class="sxs-lookup"><span data-stu-id="1d925-105">This setting causes the following behavior:</span></span>

* <span data-ttu-id="1d925-106">Seri hale getirme:</span><span class="sxs-lookup"><span data-stu-id="1d925-106">On serialize:</span></span>

  <span data-ttu-id="1d925-107">Karmaşık türler yazarken serileştirici Ayrıca meta veri özellikleri ( `$id` , `$values` ve `$ref` ) yazar.</span><span class="sxs-lookup"><span data-stu-id="1d925-107">When writing complex types, the serializer also writes metadata properties (`$id`, `$values`, and `$ref`).</span></span>

* <span data-ttu-id="1d925-108">Seri durumdan çıkarma tarihi:</span><span class="sxs-lookup"><span data-stu-id="1d925-108">On deserialize:</span></span>

  <span data-ttu-id="1d925-109">Meta veriler beklenir (zorunlu olmasa da) ve seri hale getirici bunu anlamaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="1d925-109">Metadata is expected (although not mandatory), and the deserializer tries to understand it.</span></span>

<span data-ttu-id="1d925-110">Aşağıdaki kod, ayarın kullanımını gösterir `Preserve` .</span><span class="sxs-lookup"><span data-stu-id="1d925-110">The following code illustrates use of the `Preserve` setting.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferences.cs" highlight="34":::

<span data-ttu-id="1d925-111">Bu özellik değer türlerini veya sabit türleri korumak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1d925-111">This feature can't be used to preserve value types or immutable types.</span></span> <span data-ttu-id="1d925-112">Seri durumdan çıkarma sırasında, tüm yük okunduktan sonra sabit bir tür örneği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1d925-112">On deserialization, the instance of an immutable type is created after the entire payload is read.</span></span> <span data-ttu-id="1d925-113">Bu nedenle, JSON yükünün içinde bir başvuru görünürse aynı örneğin serisini kaldırma imkansızdır.</span><span class="sxs-lookup"><span data-stu-id="1d925-113">So it would be impossible to deserialize the same instance if a reference to it appears within the JSON payload.</span></span>

<span data-ttu-id="1d925-114">Değer türleri, değişmez türler ve diziler için hiçbir başvuru meta verisi serileştirilmez.</span><span class="sxs-lookup"><span data-stu-id="1d925-114">For value types, immutable types, and arrays, no reference metadata is serialized.</span></span> <span data-ttu-id="1d925-115">Seri durumdan çıkarma sırasında, veya bulunursa bir özel durum oluşturulur `$ref` `$id` .</span><span class="sxs-lookup"><span data-stu-id="1d925-115">On deserialization, an exception is thrown if `$ref` or `$id` is found.</span></span> <span data-ttu-id="1d925-116">Ancak, `$id` `$values` kullanılarak seri hale getirilen yüklerin serisini kaldırma olanağı sağlamak için değer türleri (koleksiyonlar durumunda ve ' de) yoksayar Newtonsoft.Json .</span><span class="sxs-lookup"><span data-stu-id="1d925-116">However, value types ignore `$id` (and `$values` in the case of collections) to make it possible to deserialize payloads that were serialized by using Newtonsoft.Json.</span></span>  <span data-ttu-id="1d925-117">Newtonsoft.Json Bu tür türler için meta verileri serileştirmez.</span><span class="sxs-lookup"><span data-stu-id="1d925-117">Newtonsoft.Json does serialize metadata for such types.</span></span>

<span data-ttu-id="1d925-118">Nesnelerin eşit olup olmadığını anlamak için, System.Text.Json <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType> <xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType> değer eşitlik yerine başvuru eşitlik () kullanır ( <xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> iki nesne örneği karşılaştırılırken).</span><span class="sxs-lookup"><span data-stu-id="1d925-118">To determine if objects are equal, System.Text.Json uses <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType>, which uses reference equality (<xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType>) instead of value equality (<xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> when comparing two object instances.</span></span>

<span data-ttu-id="1d925-119">Başvuruların serileştirilme ve seri durumdan çıkarıldığı hakkında daha fazla bilgi için bkz <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType> ..</span><span class="sxs-lookup"><span data-stu-id="1d925-119">For more information about how references are serialized and deserialized, see <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="1d925-120"><xref:System.Text.Json.Serialization.ReferenceResolver>Sınıfı serileştirme ve seri durumundan çıkarma için başvuruları koruma davranışını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1d925-120">The <xref:System.Text.Json.Serialization.ReferenceResolver> class defines the behavior of preserving references on serialization and deserialization.</span></span> <span data-ttu-id="1d925-121">Özel davranışı belirtmek için türetilmiş bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1d925-121">Create a derived class to specify custom behavior.</span></span> <span data-ttu-id="1d925-122">Bir örnek için bkz. [GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs).</span><span class="sxs-lookup"><span data-stu-id="1d925-122">For an example, see [GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs).</span></span>

::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="1d925-123">System.Text.Json .NET Core 3,1 yalnızca değere göre serileştirme destekler ve döngüsel başvurular için bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1d925-123">System.Text.Json in .NET Core 3.1 only supports serialization by value and throws an exception for circular references.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="1d925-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d925-124">See also</span></span>

* [<span data-ttu-id="1d925-125">System.Text.Json bakýþ</span><span class="sxs-lookup"><span data-stu-id="1d925-125">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="1d925-126">JSON’u seri hale getirme ve seri halden çıkarma</span><span class="sxs-lookup"><span data-stu-id="1d925-126">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="1d925-127">JsonSerializerOptions örneklerinin örneğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="1d925-127">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="1d925-128">Büyük/küçük harf duyarlı eşlemeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="1d925-128">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="1d925-129">Özellik adlarını ve değerlerini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="1d925-129">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="1d925-130">Özellikleri yoksayma</span><span class="sxs-lookup"><span data-stu-id="1d925-130">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="1d925-131">Geçersiz JSON’a izin verme</span><span class="sxs-lookup"><span data-stu-id="1d925-131">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="1d925-132">Sap taşması JSON’ı</span><span class="sxs-lookup"><span data-stu-id="1d925-132">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="1d925-133">Sabit türler ve genel olmayan erişimciler</span><span class="sxs-lookup"><span data-stu-id="1d925-133">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="1d925-134">Polimorfik serileştirme</span><span class="sxs-lookup"><span data-stu-id="1d925-134">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="1d925-135">' Den ' a geçiş Newtonsoft.JsonSystem.Text.Json</span><span class="sxs-lookup"><span data-stu-id="1d925-135">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="1d925-136">Karakter kodlamasını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="1d925-136">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="1d925-137">Özel serileştiriciler ve seri hale getiriciler yazma</span><span class="sxs-lookup"><span data-stu-id="1d925-137">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="1d925-138">JSON serileştirme için özel dönüştürücüler yazma</span><span class="sxs-lookup"><span data-stu-id="1d925-138">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="1d925-139">DateTime ve DateTimeOffset desteği</span><span class="sxs-lookup"><span data-stu-id="1d925-139">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="1d925-140">[System.Text.Json API başvurusu](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="1d925-140">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="1d925-141">[System.Text.Json. Serileştirme API başvurusu](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="1d925-141">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
