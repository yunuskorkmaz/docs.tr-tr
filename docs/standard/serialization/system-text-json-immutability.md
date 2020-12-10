---
title: İle değişmez türleri ve genel olmayan erişimcileri kullanma System.Text.Json
description: .NET ' te JSON ile seri hale getirme ve serisini kaldırma sırasında değişmez türleri ve genel olmayan erişimcileri kullanmayı öğrenin.
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
ms.openlocfilehash: ff8ecec0d70c877b7cbbd0297b85f0d9578ab828
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97008831"
---
# <a name="how-to-use-immutable-types-and-non-public-accessors-with-no-locsystemtextjson"></a><span data-ttu-id="db630-103">İle değişmez türleri ve genel olmayan erişimcileri kullanma System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="db630-103">How to use immutable types and non-public accessors with System.Text.Json</span></span>

<span data-ttu-id="db630-104">Bu makalede, ad alanı ile kayıtlar gibi değişmez türlerin nasıl kullanılacağını öğreneceksiniz `System.Text.Json` .</span><span class="sxs-lookup"><span data-stu-id="db630-104">In this article, you will learn how to use immutable types, such as Records, with the `System.Text.Json` namespace.</span></span>

## <a name="immutable-types-and-records"></a><span data-ttu-id="db630-105">Sabit türler ve kayıtlar</span><span class="sxs-lookup"><span data-stu-id="db630-105">Immutable types and Records</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="db630-106">`System.Text.Json` , sabit bir sınıfın veya yapının serisini kaldırma olanağı sağlayan parametreli bir Oluşturucu kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="db630-106">`System.Text.Json` can use a parameterized constructor, which makes it possible to deserialize an immutable class or struct.</span></span> <span data-ttu-id="db630-107">Bir sınıf için, tek Oluşturucu parametreli bir ise, bu Oluşturucu kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="db630-107">For a class, if the only constructor is a parameterized one, that constructor will be used.</span></span> <span data-ttu-id="db630-108">Bir yapı veya birden çok Oluşturucu içeren bir sınıf için, [[Jsonconstructor]](xref:System.Text.Json.Serialization.JsonConstructorAttribute.%23ctor%2A) özniteliğini uygulayarak kullanılacak olanı belirtin.</span><span class="sxs-lookup"><span data-stu-id="db630-108">For a struct, or a class with multiple constructors, specify the one to use by applying the [[JsonConstructor]](xref:System.Text.Json.Serialization.JsonConstructorAttribute.%23ctor%2A) attribute.</span></span> <span data-ttu-id="db630-109">Özniteliği kullanılmazsa, varsa Ortak parametresiz bir Oluşturucu her zaman kullanılır.</span><span class="sxs-lookup"><span data-stu-id="db630-109">When the attribute is not used, a public parameterless constructor is always used if present.</span></span> <span data-ttu-id="db630-110">Özniteliği yalnızca ortak oluşturucularla birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="db630-110">The attribute can only be used with public constructors.</span></span> <span data-ttu-id="db630-111">Aşağıdaki örnek `[JsonConstructor]` özniteliğini kullanır:</span><span class="sxs-lookup"><span data-stu-id="db630-111">The following example uses the `[JsonConstructor]` attribute:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/ImmutableTypes.cs" highlight="13":::

<span data-ttu-id="db630-112">C# 9 ' da kayıtlar aşağıdaki örnekte gösterildiği gibi desteklenir:</span><span class="sxs-lookup"><span data-stu-id="db630-112">Records in C# 9 are also supported, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Records.cs":::

<span data-ttu-id="db630-113">Tüm özellik ayarlayıcıları ortak olmadığından, sabit olan türler için, [genel olmayan özellik erişimcileri](#non-public-property-accessors)hakkında aşağıdaki bölüme bakın.</span><span class="sxs-lookup"><span data-stu-id="db630-113">For types that are immutable because all their property setters are non-public, see the following section about [non-public property accessors](#non-public-property-accessors).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="db630-114">`JsonConstructorAttribute` ve C# 9 kayıt desteği .NET Core 3,1 ' de kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="db630-114">`JsonConstructorAttribute` and C# 9 Record support aren't available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="non-public-property-accessors"></a><span data-ttu-id="db630-115">Ortak olmayan özellik erişimcileri</span><span class="sxs-lookup"><span data-stu-id="db630-115">Non-public property accessors</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="db630-116">Ortak olmayan bir özellik erişimcisinin kullanımını etkinleştirmek için, aşağıdaki örnekte gösterildiği gibi [[Jsonınclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) özniteliğini kullanın:</span><span class="sxs-lookup"><span data-stu-id="db630-116">To enable use of a non-public property accessor, use the [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) attribute, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/NonPublicAccessors.cs" highlight="12,15":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="db630-117">Ortak olmayan özellik erişimcileri .NET Core 3,1 ' de desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="db630-117">Non-public property accessors are not supported in .NET Core 3.1.</span></span> <span data-ttu-id="db630-118">Daha fazla bilgi için, bkz. [ Newtonsoft.Json makaleden geçiş](system-text-json-migrate-from-newtonsoft-how-to.md#non-public-property-setters-and-getters).</span><span class="sxs-lookup"><span data-stu-id="db630-118">For more information, see [the Migrate from Newtonsoft.Json article](system-text-json-migrate-from-newtonsoft-how-to.md#non-public-property-setters-and-getters).</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="db630-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db630-119">See also</span></span>

* [<span data-ttu-id="db630-120">System.Text.Json bakýþ</span><span class="sxs-lookup"><span data-stu-id="db630-120">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="db630-121">JSON’u seri hale getirme ve seri halden çıkarma</span><span class="sxs-lookup"><span data-stu-id="db630-121">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="db630-122">JsonSerializerOptions örneklerinin örneğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="db630-122">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="db630-123">Büyük/küçük harf duyarlı eşlemeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="db630-123">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="db630-124">Özellik adlarını ve değerlerini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="db630-124">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="db630-125">Özellikleri yoksayma</span><span class="sxs-lookup"><span data-stu-id="db630-125">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="db630-126">Geçersiz JSON’a izin verme</span><span class="sxs-lookup"><span data-stu-id="db630-126">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="db630-127">Sap taşması JSON’ı</span><span class="sxs-lookup"><span data-stu-id="db630-127">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="db630-128">Başvuruları koruma</span><span class="sxs-lookup"><span data-stu-id="db630-128">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="db630-129">Polimorfik serileştirme</span><span class="sxs-lookup"><span data-stu-id="db630-129">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="db630-130">' Den ' a geçiş Newtonsoft.JsonSystem.Text.Json</span><span class="sxs-lookup"><span data-stu-id="db630-130">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="db630-131">Karakter kodlamasını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="db630-131">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="db630-132">Özel serileştiriciler ve seri hale getiriciler yazma</span><span class="sxs-lookup"><span data-stu-id="db630-132">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="db630-133">JSON serileştirme için özel dönüştürücüler yazma</span><span class="sxs-lookup"><span data-stu-id="db630-133">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="db630-134">DateTime ve DateTimeOffset desteği</span><span class="sxs-lookup"><span data-stu-id="db630-134">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="db630-135">[System.Text.Json API başvurusu](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="db630-135">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="db630-136">[System.Text.Json. Serileştirme API başvurusu](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="db630-136">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
