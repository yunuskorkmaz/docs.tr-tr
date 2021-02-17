---
title: İle başvuruları koruma System.Text.Json
description: .NET 'teki JSON 'dan serileştirilirken ve seri durumdan çıkarılırken başvuruları nasıl koruyacağınızı ve döngüsel başvuruları nasıl işleyeceğinizi öğrenin.
ms.date: 01/12/2021
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
ms.openlocfilehash: 0dda695c7e21090f68703309da03d5158fc858f1
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100584058"
---
# <a name="how-to-preserve-references-and-handle-circular-references-with-systemtextjson"></a><span data-ttu-id="63a86-103">Başvuruları koruma ve ile döngüsel başvuruları işleme System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="63a86-103">How to preserve references and handle circular references with System.Text.Json</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="63a86-104">Başvuruları korumak ve döngüsel başvuruları işlemek için olarak ayarlayın <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A> .</span><span class="sxs-lookup"><span data-stu-id="63a86-104">To preserve references and handle circular references, set <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> to <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A>.</span></span> <span data-ttu-id="63a86-105">Bu ayar aşağıdaki davranışa neden olur:</span><span class="sxs-lookup"><span data-stu-id="63a86-105">This setting causes the following behavior:</span></span>

* <span data-ttu-id="63a86-106">Seri hale getirme:</span><span class="sxs-lookup"><span data-stu-id="63a86-106">On serialize:</span></span>

  <span data-ttu-id="63a86-107">Karmaşık türler yazarken serileştirici Ayrıca meta veri özellikleri ( `$id` , `$values` ve `$ref` ) yazar.</span><span class="sxs-lookup"><span data-stu-id="63a86-107">When writing complex types, the serializer also writes metadata properties (`$id`, `$values`, and `$ref`).</span></span>

* <span data-ttu-id="63a86-108">Seri durumdan çıkarma tarihi:</span><span class="sxs-lookup"><span data-stu-id="63a86-108">On deserialize:</span></span>

  <span data-ttu-id="63a86-109">Meta veriler beklenir (zorunlu olmasa da) ve seri hale getirici bunu anlamaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="63a86-109">Metadata is expected (although not mandatory), and the deserializer tries to understand it.</span></span>

<span data-ttu-id="63a86-110">Aşağıdaki kod, ayarın kullanımını gösterir `Preserve` .</span><span class="sxs-lookup"><span data-stu-id="63a86-110">The following code illustrates use of the `Preserve` setting.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferences.cs" highlight="34":::
:::code language="vb" source="snippets/system-text-json-how-to-5-0/vb/PreserveReferences.vb" :::

<span data-ttu-id="63a86-111">Bu özellik değer türlerini veya sabit türleri korumak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="63a86-111">This feature can't be used to preserve value types or immutable types.</span></span> <span data-ttu-id="63a86-112">Seri durumdan çıkarma sırasında, tüm yük okunduktan sonra sabit bir tür örneği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="63a86-112">On deserialization, the instance of an immutable type is created after the entire payload is read.</span></span> <span data-ttu-id="63a86-113">Bu nedenle, JSON yükünün içinde bir başvuru görünürse aynı örneğin serisini kaldırma imkansızdır.</span><span class="sxs-lookup"><span data-stu-id="63a86-113">So it would be impossible to deserialize the same instance if a reference to it appears within the JSON payload.</span></span>

<span data-ttu-id="63a86-114">Değer türleri, değişmez türler ve diziler için hiçbir başvuru meta verisi serileştirilmez.</span><span class="sxs-lookup"><span data-stu-id="63a86-114">For value types, immutable types, and arrays, no reference metadata is serialized.</span></span> <span data-ttu-id="63a86-115">Seri durumdan çıkarma sırasında, veya bulunursa bir özel durum oluşturulur `$ref` `$id` .</span><span class="sxs-lookup"><span data-stu-id="63a86-115">On deserialization, an exception is thrown if `$ref` or `$id` is found.</span></span> <span data-ttu-id="63a86-116">Ancak, `$id` `$values` kullanılarak seri hale getirilen yüklerin serisini kaldırma olanağı sağlamak için değer türleri (koleksiyonlar durumunda ve ' de) yoksayar Newtonsoft.Json .</span><span class="sxs-lookup"><span data-stu-id="63a86-116">However, value types ignore `$id` (and `$values` in the case of collections) to make it possible to deserialize payloads that were serialized by using Newtonsoft.Json.</span></span>  <span data-ttu-id="63a86-117">Newtonsoft.Json Bu tür türler için meta verileri serileştirmez.</span><span class="sxs-lookup"><span data-stu-id="63a86-117">Newtonsoft.Json does serialize metadata for such types.</span></span>

<span data-ttu-id="63a86-118">Nesnelerin eşit olup olmadığını anlamak için, System.Text.Json <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType> <xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType> değer eşitlik yerine başvuru eşitlik () kullanır ( <xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> iki nesne örneği karşılaştırılırken).</span><span class="sxs-lookup"><span data-stu-id="63a86-118">To determine if objects are equal, System.Text.Json uses <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType>, which uses reference equality (<xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType>) instead of value equality (<xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> when comparing two object instances.</span></span>

<span data-ttu-id="63a86-119">Başvuruların serileştirilme ve seri durumdan çıkarıldığı hakkında daha fazla bilgi için bkz <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType> ..</span><span class="sxs-lookup"><span data-stu-id="63a86-119">For more information about how references are serialized and deserialized, see <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="63a86-120"><xref:System.Text.Json.Serialization.ReferenceResolver>Sınıfı serileştirme ve seri durumundan çıkarma için başvuruları koruma davranışını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="63a86-120">The <xref:System.Text.Json.Serialization.ReferenceResolver> class defines the behavior of preserving references on serialization and deserialization.</span></span> <span data-ttu-id="63a86-121">Özel davranışı belirtmek için türetilmiş bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="63a86-121">Create a derived class to specify custom behavior.</span></span> <span data-ttu-id="63a86-122">Bir örnek için bkz. [GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs).</span><span class="sxs-lookup"><span data-stu-id="63a86-122">For an example, see [GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs).</span></span>

## <a name="persist-reference-metadata-across-multiple-serialization-and-deserialization-calls"></a><span data-ttu-id="63a86-123">Birden çok serileştirme ve seri durumdan çıkarma çağrılarında başvuru meta verilerini kalıcı yap</span><span class="sxs-lookup"><span data-stu-id="63a86-123">Persist reference metadata across multiple serialization and deserialization calls</span></span>

<span data-ttu-id="63a86-124">Varsayılan olarak, başvuru verileri yalnızca veya için yapılan her çağrı için önbelleğe alınır <xref:System.Text.Json.JsonSerializer.Serialize%2A> <xref:System.Text.Json.JsonSerializer.Deserialize%2A> .</span><span class="sxs-lookup"><span data-stu-id="63a86-124">By default, reference data is only cached for each call to <xref:System.Text.Json.JsonSerializer.Serialize%2A> or <xref:System.Text.Json.JsonSerializer.Deserialize%2A>.</span></span> <span data-ttu-id="63a86-125">Bir çağrıdan diğerine yapılan başvuruları kalıcı hale getirmek için `Serialize` / `Deserialize` , ' <xref:System.Text.Json.Serialization.ReferenceResolver> ın çağrı sitesinde kökünü yapın `Serialize` / `Deserialize` .</span><span class="sxs-lookup"><span data-stu-id="63a86-125">To persist references from one `Serialize`/`Deserialize` call to another one, root the <xref:System.Text.Json.Serialization.ReferenceResolver> instance in the call site of `Serialize`/`Deserialize`.</span></span> <span data-ttu-id="63a86-126">Aşağıdaki kod, bu senaryo için bir örnek gösterir:</span><span class="sxs-lookup"><span data-stu-id="63a86-126">The following code shows an example for this scenario:</span></span>

* <span data-ttu-id="63a86-127">Bir listeniz vardır `Employee` ve her birini ayrı olarak serileştirmek zorunda olursunuz.</span><span class="sxs-lookup"><span data-stu-id="63a86-127">You have a list of `Employee`s and you have to serialize each one individually.</span></span>
* <span data-ttu-id="63a86-128">çözümleyicisine kaydedilen başvuruların avantajlarından yararlanmak istiyorsunuz `ReferenceHandler` .</span><span class="sxs-lookup"><span data-stu-id="63a86-128">you want to take advantage of the references saved in the `ReferenceHandler`'s resolver.</span></span>

<span data-ttu-id="63a86-129">`Employee`Sınıf şöyledir:</span><span class="sxs-lookup"><span data-stu-id="63a86-129">Here is the `Employee` class:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferencesMultipleCalls.cs" id="Employee":::

<span data-ttu-id="63a86-130">Öğesinden türetilen bir sınıf <xref:System.Text.Json.Serialization.ReferenceResolver> , başvuruları bir sözlükte depolar:</span><span class="sxs-lookup"><span data-stu-id="63a86-130">A class that derives from <xref:System.Text.Json.Serialization.ReferenceResolver> stores the references in a dictionary:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferencesMultipleCalls.cs" id="MyReferenceResolver":::

<span data-ttu-id="63a86-131">Öğesinden türetilen bir sınıf <xref:System.Text.Json.Serialization.ReferenceHandler> , bir örneğini tutar `MyReferenceResolver` ve yalnızca gerektiğinde yeni bir örnek oluşturur (Bu örnekte adlı bir yöntemde `Reset` ):</span><span class="sxs-lookup"><span data-stu-id="63a86-131">A class that derives from <xref:System.Text.Json.Serialization.ReferenceHandler> holds an instance of `MyReferenceResolver` and creates a new instance only when needed (in a method named `Reset` in this example):</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferencesMultipleCalls.cs" id="MyReferenceHandler":::

<span data-ttu-id="63a86-132">Örnek kod serileştiriciyi çağırdığında, <xref:System.Text.Json.JsonSerializerOptions> <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler> özelliğinin bir örneğine ayarlandığı bir örneği kullanır `MyReferenceHandler` .</span><span class="sxs-lookup"><span data-stu-id="63a86-132">When the sample code calls the serializer, it uses a <xref:System.Text.Json.JsonSerializerOptions> instance in which the <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler> property is set to an instance of `MyReferenceHandler`.</span></span> <span data-ttu-id="63a86-133">Bu kalıbı izlediğinizde, `ReferenceResolver` seri hale getirmeyi tamamladıktan sonra, sonsuza kadar büyümeye devam etmek için sözlüğü sıfırladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="63a86-133">When you follow this pattern, be sure to reset the `ReferenceResolver` dictionary when you're finished serializing, to keep it from growing forever.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferencesMultipleCalls.cs" id="CallSerializer" highlight = "3-4,14":::

::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="63a86-134">System.Text.Json .NET Core 3,1 yalnızca değere göre serileştirme destekler ve döngüsel başvurular için bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="63a86-134">System.Text.Json in .NET Core 3.1 only supports serialization by value and throws an exception for circular references.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="63a86-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63a86-135">See also</span></span>

* [<span data-ttu-id="63a86-136">System.Text.Json bakýþ</span><span class="sxs-lookup"><span data-stu-id="63a86-136">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="63a86-137">JSON’u seri hale getirme ve seri halden çıkarma</span><span class="sxs-lookup"><span data-stu-id="63a86-137">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="63a86-138">JsonSerializerOptions örneklerinin örneğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="63a86-138">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="63a86-139">Büyük/küçük harf duyarlı eşlemeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="63a86-139">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="63a86-140">Özellik adlarını ve değerlerini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="63a86-140">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="63a86-141">Özellikleri yoksayma</span><span class="sxs-lookup"><span data-stu-id="63a86-141">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="63a86-142">Geçersiz JSON’a izin verme</span><span class="sxs-lookup"><span data-stu-id="63a86-142">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="63a86-143">Sap taşması JSON’ı</span><span class="sxs-lookup"><span data-stu-id="63a86-143">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="63a86-144">Sabit türler ve genel olmayan erişimciler</span><span class="sxs-lookup"><span data-stu-id="63a86-144">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="63a86-145">Polimorfik serileştirme</span><span class="sxs-lookup"><span data-stu-id="63a86-145">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="63a86-146">' Den ' a geçiş Newtonsoft.JsonSystem.Text.Json</span><span class="sxs-lookup"><span data-stu-id="63a86-146">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="63a86-147">Karakter kodlamasını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="63a86-147">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="63a86-148">Özel serileştiriciler ve seri hale getiriciler yazma</span><span class="sxs-lookup"><span data-stu-id="63a86-148">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="63a86-149">JSON serileştirme için özel dönüştürücüler yazma</span><span class="sxs-lookup"><span data-stu-id="63a86-149">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="63a86-150">DateTime ve DateTimeOffset desteği</span><span class="sxs-lookup"><span data-stu-id="63a86-150">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="63a86-151">[System.Text.Json API başvurusu](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="63a86-151">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="63a86-152">[System.Text.Json. Serileştirme API başvurusu](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="63a86-152">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
