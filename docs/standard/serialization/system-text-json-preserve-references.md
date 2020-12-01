---
title: İle başvuruları koruma System.Text.Json
description: .NET 'teki JSON 'dan serileştirilirken ve seri durumdan çıkarılırken başvuruları nasıl koruyacağınızı ve döngüsel başvuruları nasıl işleyeceğinizi öğrenin.
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
ms.openlocfilehash: 9254ca261c7d748c04c311fa56359014f752ff31
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96440016"
---
# <a name="how-to-handle-circular-references-with-no-locsystemtextjson"></a><span data-ttu-id="d3704-103">İle döngüsel başvuruları işleme System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="d3704-103">How to handle circular references with System.Text.Json</span></span>

<span data-ttu-id="d3704-104">Bu makalede, ad alanıyla döngüsel başvuruları nasıl işleyeceğinizi öğreneceksiniz `System.Text.Json` .</span><span class="sxs-lookup"><span data-stu-id="d3704-104">In this article, you will learn how to handle circular references with the `System.Text.Json` namespace.</span></span>

## <a name="preserve-references-and-handle-circular-references"></a><span data-ttu-id="d3704-105">Başvuruları koru ve döngüsel başvuruları işle</span><span class="sxs-lookup"><span data-stu-id="d3704-105">Preserve references and handle circular references</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="d3704-106">Başvuruları korumak ve döngüsel başvuruları işlemek için olarak ayarlayın <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A> .</span><span class="sxs-lookup"><span data-stu-id="d3704-106">To preserve references and handle circular references, set <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> to <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A>.</span></span> <span data-ttu-id="d3704-107">Bu ayar aşağıdaki davranışa neden olur:</span><span class="sxs-lookup"><span data-stu-id="d3704-107">This setting causes the following behavior:</span></span>

* <span data-ttu-id="d3704-108">Seri hale getirme:</span><span class="sxs-lookup"><span data-stu-id="d3704-108">On serialize:</span></span>

  <span data-ttu-id="d3704-109">Karmaşık türler yazarken serileştirici Ayrıca meta veri özellikleri ( `$id` , `$values` ve `$ref` ) yazar.</span><span class="sxs-lookup"><span data-stu-id="d3704-109">When writing complex types, the serializer also writes metadata properties (`$id`, `$values`, and `$ref`).</span></span>

* <span data-ttu-id="d3704-110">Seri durumdan çıkarma tarihi:</span><span class="sxs-lookup"><span data-stu-id="d3704-110">On deserialize:</span></span>

  <span data-ttu-id="d3704-111">Meta veriler beklenir (zorunlu olmasa da) ve seri hale getirici bunu anlamaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="d3704-111">Metadata is expected (although not mandatory), and the deserializer tries to understand it.</span></span>

<span data-ttu-id="d3704-112">Aşağıdaki kod, ayarın kullanımını gösterir `Preserve` .</span><span class="sxs-lookup"><span data-stu-id="d3704-112">The following code illustrates use of the `Preserve` setting.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferences.cs" highlight="34":::

<span data-ttu-id="d3704-113">Bu özellik değer türlerini veya sabit türleri korumak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d3704-113">This feature can't be used to preserve value types or immutable types.</span></span> <span data-ttu-id="d3704-114">Seri durumdan çıkarma sırasında, tüm yük okunduktan sonra sabit bir tür örneği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d3704-114">On deserialization, the instance of an immutable type is created after the entire payload is read.</span></span> <span data-ttu-id="d3704-115">Bu nedenle, JSON yükünün içinde bir başvuru görünürse aynı örneğin serisini kaldırma imkansızdır.</span><span class="sxs-lookup"><span data-stu-id="d3704-115">So it would be impossible to deserialize the same instance if a reference to it appears within the JSON payload.</span></span>

<span data-ttu-id="d3704-116">Değer türleri, değişmez türler ve diziler için hiçbir başvuru meta verisi serileştirilmez.</span><span class="sxs-lookup"><span data-stu-id="d3704-116">For value types, immutable types, and arrays, no reference metadata is serialized.</span></span> <span data-ttu-id="d3704-117">Seri durumdan çıkarma sırasında, veya bulunursa bir özel durum oluşturulur `$ref` `$id` .</span><span class="sxs-lookup"><span data-stu-id="d3704-117">On deserialization, an exception is thrown if `$ref` or `$id` is found.</span></span> <span data-ttu-id="d3704-118">Ancak, `$id` `$values` kullanılarak seri hale getirilen yüklerin serisini kaldırma olanağı sağlamak için değer türleri (koleksiyonlar durumunda ve ' de) yoksayar Newtonsoft.Json .</span><span class="sxs-lookup"><span data-stu-id="d3704-118">However, value types ignore `$id` (and `$values` in the case of collections) to make it possible to deserialize payloads that were serialized by using Newtonsoft.Json.</span></span>  <span data-ttu-id="d3704-119">Newtonsoft.Json Bu tür türler için meta verileri serileştirmez.</span><span class="sxs-lookup"><span data-stu-id="d3704-119">Newtonsoft.Json does serialize metadata for such types.</span></span>

<span data-ttu-id="d3704-120">Nesnelerin eşit olup olmadığını anlamak için, System.Text.Json <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType> <xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType> değer eşitlik yerine başvuru eşitlik () kullanır ( <xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> iki nesne örneği karşılaştırılırken).</span><span class="sxs-lookup"><span data-stu-id="d3704-120">To determine if objects are equal, System.Text.Json uses <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType>, which uses reference equality (<xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType>) instead of value equality (<xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> when comparing two object instances.</span></span>

<span data-ttu-id="d3704-121">Başvuruların serileştirilme ve seri durumdan çıkarıldığı hakkında daha fazla bilgi için bkz <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType> ..</span><span class="sxs-lookup"><span data-stu-id="d3704-121">For more information about how references are serialized and deserialized, see <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="d3704-122"><xref:System.Text.Json.Serialization.ReferenceResolver>Sınıfı serileştirme ve seri durumundan çıkarma için başvuruları koruma davranışını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d3704-122">The <xref:System.Text.Json.Serialization.ReferenceResolver> class defines the behavior of preserving references on serialization and deserialization.</span></span> <span data-ttu-id="d3704-123">Özel davranışı belirtmek için türetilmiş bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d3704-123">Create a derived class to specify custom behavior.</span></span> <span data-ttu-id="d3704-124">Bir örnek için bkz. [GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs).</span><span class="sxs-lookup"><span data-stu-id="d3704-124">For an example, see [GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs).</span></span>

::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="d3704-125">System.Text.Json .NET Core 3,1 yalnızca değere göre serileştirme destekler ve döngüsel başvurular için bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d3704-125">System.Text.Json in .NET Core 3.1 only supports serialization by value and throws an exception for circular references.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="d3704-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3704-126">See also</span></span>

* [<span data-ttu-id="d3704-127">System.Text.Json bakýþ</span><span class="sxs-lookup"><span data-stu-id="d3704-127">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="d3704-128">JsonSerializerOptions örneğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="d3704-128">Instantiate JsonSerializerOptions</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="d3704-129">Büyük/küçük harfe duyarsız eşleştirmeyi etkinleştir</span><span class="sxs-lookup"><span data-stu-id="d3704-129">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="d3704-130">Özellik adlarını ve değerlerini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="d3704-130">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="d3704-131">Özellikleri yoksay</span><span class="sxs-lookup"><span data-stu-id="d3704-131">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="d3704-132">Geçersiz JSON 'a izin ver</span><span class="sxs-lookup"><span data-stu-id="d3704-132">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="d3704-133">Tutamaç taşması JSON</span><span class="sxs-lookup"><span data-stu-id="d3704-133">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="d3704-134">Değişmez türler ve genel olmayan erişimciler</span><span class="sxs-lookup"><span data-stu-id="d3704-134">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="d3704-135">Polimorfik serileştirme</span><span class="sxs-lookup"><span data-stu-id="d3704-135">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="d3704-136">[System.Text.Json API başvurusu](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="d3704-136">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
