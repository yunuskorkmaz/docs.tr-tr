---
title: İle değişmez türleri ve genel olmayan erişimcileri kullanma System.Text.Json
description: .NET ' te JSON ile seri hale getirme ve serisini kaldırma sırasında değişmez türleri ve genel olmayan erişimcileri kullanmayı öğrenin.
ms.date: 02/08/2021
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 9fe1e6e96703ba404308c758eca49be6e196ad61
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100438170"
---
# <a name="how-to-use-immutable-types-and-non-public-accessors-with-systemtextjson"></a><span data-ttu-id="b7bb6-103">İle değişmez türleri ve genel olmayan erişimcileri kullanma System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="b7bb6-103">How to use immutable types and non-public accessors with System.Text.Json</span></span>

<span data-ttu-id="b7bb6-104">Bu makalede, ad alanıyla değişmez türlerin, genel parametreli oluşturucuların ve genel olmayan erişimcilerinin nasıl kullanılacağı gösterilmektedir `System.Text.Json` .</span><span class="sxs-lookup"><span data-stu-id="b7bb6-104">This article shows how to use immutable types, public parameterized constructors, and non-public accessors with the `System.Text.Json` namespace.</span></span>

## <a name="immutable-types-and-records"></a><span data-ttu-id="b7bb6-105">Sabit türler ve kayıtlar</span><span class="sxs-lookup"><span data-stu-id="b7bb6-105">Immutable types and Records</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="b7bb6-106">`System.Text.Json` , sabit bir sınıfın veya yapının serisini kaldırmak mümkün kılan ortak parametreli bir Oluşturucu kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="b7bb6-106">`System.Text.Json` can use a public parameterized constructor, which makes it possible to deserialize an immutable class or struct.</span></span> <span data-ttu-id="b7bb6-107">Bir sınıf için, tek Oluşturucu parametreli bir ise, bu Oluşturucu kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="b7bb6-107">For a class, if the only constructor is a parameterized one, that constructor will be used.</span></span> <span data-ttu-id="b7bb6-108">Bir yapı veya birden çok Oluşturucu içeren bir sınıf için, [[Jsonconstructor]](xref:System.Text.Json.Serialization.JsonConstructorAttribute) özniteliğini uygulayarak kullanılacak olanı belirtin.</span><span class="sxs-lookup"><span data-stu-id="b7bb6-108">For a struct, or a class with multiple constructors, specify the one to use by applying the [[JsonConstructor]](xref:System.Text.Json.Serialization.JsonConstructorAttribute) attribute.</span></span> <span data-ttu-id="b7bb6-109">Özniteliği kullanılmazsa, varsa Ortak parametresiz bir Oluşturucu her zaman kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b7bb6-109">When the attribute is not used, a public parameterless constructor is always used if present.</span></span> <span data-ttu-id="b7bb6-110">Özniteliği yalnızca ortak oluşturucularla birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b7bb6-110">The attribute can only be used with public constructors.</span></span> <span data-ttu-id="b7bb6-111">Aşağıdaki örnek `[JsonConstructor]` özniteliğini kullanır:</span><span class="sxs-lookup"><span data-stu-id="b7bb6-111">The following example uses the `[JsonConstructor]` attribute:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/ImmutableTypes.cs" highlight="13":::

<span data-ttu-id="b7bb6-112">Parametreli bir oluşturucunun parametre adları, özellik adlarıyla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="b7bb6-112">The parameter names of a parameterized constructor must match the property names.</span></span> <span data-ttu-id="b7bb6-113">Eşleştirme büyük/küçük harfe duyarlıdır ve bir özelliği yeniden adlandırmak için [[Jsonpropertyname]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) kullanıyor olsanız bile, Oluşturucu parametresi gerçek özellik adıyla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="b7bb6-113">Matching is case-insensitive, and the constructor parameter must match the actual property name even if you use [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) to rename a property.</span></span> <span data-ttu-id="b7bb6-114">Aşağıdaki örnekte, `TemperatureC` özelliğinin adı `celsius` JSON içinde olarak değiştirilir, ancak Oluşturucu parametresi hala adlandırılmaktadır `temperatureC` :</span><span class="sxs-lookup"><span data-stu-id="b7bb6-114">In the following example, the name for the `TemperatureC` property is changed to `celsius` in the JSON, but the constructor parameter is still named `temperatureC`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/ImmutableTypesCtorParms.cs" highlight="10,14-16":::

<span data-ttu-id="b7bb6-115">`[JsonPropertyName]`Aşağıdaki özniteliklerin yanı sıra parametreli oluşturucularla serisini kaldırma desteği de vardır:</span><span class="sxs-lookup"><span data-stu-id="b7bb6-115">Besides `[JsonPropertyName]` the following attributes support deserialization with parameterized constructors:</span></span>

* <span data-ttu-id="b7bb6-116">[[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute)</span><span class="sxs-lookup"><span data-stu-id="b7bb6-116">[[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute)</span></span>
* <span data-ttu-id="b7bb6-117">[[Jsonıgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute)</span><span class="sxs-lookup"><span data-stu-id="b7bb6-117">[[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute)</span></span>
* <span data-ttu-id="b7bb6-118">[[Jsonınclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute)</span><span class="sxs-lookup"><span data-stu-id="b7bb6-118">[[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute)</span></span>
* <span data-ttu-id="b7bb6-119">[[JsonNumberHandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute)</span><span class="sxs-lookup"><span data-stu-id="b7bb6-119">[[JsonNumberHandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute)</span></span>

<span data-ttu-id="b7bb6-120">C# 9 ' da kayıtlar aşağıdaki örnekte gösterildiği gibi desteklenir:</span><span class="sxs-lookup"><span data-stu-id="b7bb6-120">Records in C# 9 are also supported, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Records.cs":::

<span data-ttu-id="b7bb6-121">Tüm özellik ayarlayıcıları ortak olmadığından, sabit olan türler için, [genel olmayan özellik erişimcileri](#non-public-property-accessors)hakkında aşağıdaki bölüme bakın.</span><span class="sxs-lookup"><span data-stu-id="b7bb6-121">For types that are immutable because all their property setters are non-public, see the following section about [non-public property accessors](#non-public-property-accessors).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="b7bb6-122">`JsonConstructorAttribute` ve C# 9 kayıt desteği .NET Core 3,1 ' de kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b7bb6-122">`JsonConstructorAttribute` and C# 9 Record support aren't available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="non-public-property-accessors"></a><span data-ttu-id="b7bb6-123">Ortak olmayan özellik erişimcileri</span><span class="sxs-lookup"><span data-stu-id="b7bb6-123">Non-public property accessors</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="b7bb6-124">Ortak olmayan bir özellik erişimcisinin kullanımını etkinleştirmek için, aşağıdaki örnekte gösterildiği gibi [[Jsonınclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) özniteliğini kullanın:</span><span class="sxs-lookup"><span data-stu-id="b7bb6-124">To enable use of a non-public property accessor, use the [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) attribute, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/NonPublicAccessors.cs" highlight="12,15":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="b7bb6-125">Ortak olmayan özellik erişimcileri .NET Core 3,1 ' de desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="b7bb6-125">Non-public property accessors are not supported in .NET Core 3.1.</span></span> <span data-ttu-id="b7bb6-126">Daha fazla bilgi için, bkz. [ Newtonsoft.Json makaleden geçiş](system-text-json-migrate-from-newtonsoft-how-to.md#non-public-property-setters-and-getters).</span><span class="sxs-lookup"><span data-stu-id="b7bb6-126">For more information, see [the Migrate from Newtonsoft.Json article](system-text-json-migrate-from-newtonsoft-how-to.md#non-public-property-setters-and-getters).</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="b7bb6-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7bb6-127">See also</span></span>

* [<span data-ttu-id="b7bb6-128">System.Text.Json bakýþ</span><span class="sxs-lookup"><span data-stu-id="b7bb6-128">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="b7bb6-129">JSON’u seri hale getirme ve seri halden çıkarma</span><span class="sxs-lookup"><span data-stu-id="b7bb6-129">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="b7bb6-130">JsonSerializerOptions örneklerinin örneğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="b7bb6-130">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="b7bb6-131">Büyük/küçük harf duyarlı eşlemeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="b7bb6-131">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="b7bb6-132">Özellik adlarını ve değerlerini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="b7bb6-132">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="b7bb6-133">Özellikleri yoksayma</span><span class="sxs-lookup"><span data-stu-id="b7bb6-133">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="b7bb6-134">Geçersiz JSON’a izin verme</span><span class="sxs-lookup"><span data-stu-id="b7bb6-134">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="b7bb6-135">Sap taşması JSON’ı</span><span class="sxs-lookup"><span data-stu-id="b7bb6-135">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="b7bb6-136">Başvuruları koruma</span><span class="sxs-lookup"><span data-stu-id="b7bb6-136">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="b7bb6-137">Polimorfik serileştirme</span><span class="sxs-lookup"><span data-stu-id="b7bb6-137">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="b7bb6-138">' Den ' a geçiş Newtonsoft.JsonSystem.Text.Json</span><span class="sxs-lookup"><span data-stu-id="b7bb6-138">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="b7bb6-139">Karakter kodlamasını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="b7bb6-139">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="b7bb6-140">Özel serileştiriciler ve seri hale getiriciler yazma</span><span class="sxs-lookup"><span data-stu-id="b7bb6-140">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="b7bb6-141">JSON serileştirme için özel dönüştürücüler yazma</span><span class="sxs-lookup"><span data-stu-id="b7bb6-141">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="b7bb6-142">DateTime ve DateTimeOffset desteği</span><span class="sxs-lookup"><span data-stu-id="b7bb6-142">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="b7bb6-143">[System.Text.Json API başvurusu](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="b7bb6-143">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="b7bb6-144">[System.Text.Json. Serileştirme API başvurusu](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="b7bb6-144">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
