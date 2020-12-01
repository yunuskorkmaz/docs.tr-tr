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
ms.openlocfilehash: d3e61d44ce22b7f50838b6d3ba9cf64004bd3725
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96440014"
---
# <a name="how-to-use-immutable-types-and-non-public-accessors-with-no-locsystemtextjson"></a><span data-ttu-id="b1b7d-103">İle değişmez türleri ve genel olmayan erişimcileri kullanma System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="b1b7d-103">How to use immutable types and non-public accessors with System.Text.Json</span></span>

<span data-ttu-id="b1b7d-104">Bu makalede, ad alanı ile kayıtlar gibi değişmez türlerin nasıl kullanılacağını öğreneceksiniz `System.Text.Json` .</span><span class="sxs-lookup"><span data-stu-id="b1b7d-104">In this article, you will learn how to use immutable types, such as Records, with the `System.Text.Json` namespace.</span></span>

## <a name="immutable-types-and-records"></a><span data-ttu-id="b1b7d-105">Sabit türler ve kayıtlar</span><span class="sxs-lookup"><span data-stu-id="b1b7d-105">Immutable types and Records</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="b1b7d-106">`System.Text.Json` , sabit bir sınıfın veya yapının serisini kaldırma olanağı sağlayan parametreli bir Oluşturucu kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="b1b7d-106">`System.Text.Json` can use a parameterized constructor, which makes it possible to deserialize an immutable class or struct.</span></span> <span data-ttu-id="b1b7d-107">Bir sınıf için, tek Oluşturucu parametreli bir ise, bu Oluşturucu kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="b1b7d-107">For a class, if the only constructor is a parameterized one, that constructor will be used.</span></span> <span data-ttu-id="b1b7d-108">Bir yapı veya birden çok Oluşturucu içeren bir sınıf için, [[Jsonconstructor]](xref:System.Text.Json.Serialization.JsonConstructorAttribute.%23ctor%2A) özniteliğini uygulayarak kullanılacak olanı belirtin.</span><span class="sxs-lookup"><span data-stu-id="b1b7d-108">For a struct, or a class with multiple constructors, specify the one to use by applying the [[JsonConstructor]](xref:System.Text.Json.Serialization.JsonConstructorAttribute.%23ctor%2A) attribute.</span></span> <span data-ttu-id="b1b7d-109">Özniteliği kullanılmazsa, varsa Ortak parametresiz bir Oluşturucu her zaman kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b1b7d-109">When the attribute is not used, a public parameterless constructor is always used if present.</span></span> <span data-ttu-id="b1b7d-110">Özniteliği yalnızca ortak oluşturucularla birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b1b7d-110">The attribute can only be used with public constructors.</span></span> <span data-ttu-id="b1b7d-111">Aşağıdaki örnek `[JsonConstructor]` özniteliğini kullanır:</span><span class="sxs-lookup"><span data-stu-id="b1b7d-111">The following example uses the `[JsonConstructor]` attribute:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/ImmutableTypes.cs" highlight="13":::

<span data-ttu-id="b1b7d-112">C# 9 ' da kayıtlar aşağıdaki örnekte gösterildiği gibi desteklenir:</span><span class="sxs-lookup"><span data-stu-id="b1b7d-112">Records in C# 9 are also supported, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Records.cs":::

<span data-ttu-id="b1b7d-113">Tüm özellik ayarlayıcıları ortak olmadığından, sabit olan türler için, [genel olmayan özellik erişimcileri](#non-public-property-accessors)hakkında aşağıdaki bölüme bakın.</span><span class="sxs-lookup"><span data-stu-id="b1b7d-113">For types that are immutable because all their property setters are non-public, see the following section about [non-public property accessors](#non-public-property-accessors).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="b1b7d-114">`JsonConstructorAttribute` ve C# 9 kayıt desteği .NET Core 3,1 ' de kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b1b7d-114">`JsonConstructorAttribute` and C# 9 Record support aren't available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="non-public-property-accessors"></a><span data-ttu-id="b1b7d-115">Ortak olmayan özellik erişimcileri</span><span class="sxs-lookup"><span data-stu-id="b1b7d-115">Non-public property accessors</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="b1b7d-116">Ortak olmayan bir özellik erişimcisinin kullanımını etkinleştirmek için, aşağıdaki örnekte gösterildiği gibi [[Jsonınclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) özniteliğini kullanın:</span><span class="sxs-lookup"><span data-stu-id="b1b7d-116">To enable use of a non-public property accessor, use the [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) attribute, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/NonPublicAccessors.cs" highlight="12,15":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="b1b7d-117">Ortak olmayan özellik erişimcileri .NET Core 3,1 ' de desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="b1b7d-117">Non-public property accessors are not supported in .NET Core 3.1.</span></span> <span data-ttu-id="b1b7d-118">Daha fazla bilgi için, bkz. [ Newtonsoft.Json makaleden geçiş](system-text-json-migrate-from-newtonsoft-how-to.md#non-public-property-setters-and-getters).</span><span class="sxs-lookup"><span data-stu-id="b1b7d-118">For more information, see [the Migrate from Newtonsoft.Json article](system-text-json-migrate-from-newtonsoft-how-to.md#non-public-property-setters-and-getters).</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="b1b7d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1b7d-119">See also</span></span>

* [<span data-ttu-id="b1b7d-120">System.Text.Json bakýþ</span><span class="sxs-lookup"><span data-stu-id="b1b7d-120">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="b1b7d-121">JsonSerializerOptions örneğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="b1b7d-121">Instantiate JsonSerializerOptions</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="b1b7d-122">Büyük/küçük harfe duyarsız eşleştirmeyi etkinleştir</span><span class="sxs-lookup"><span data-stu-id="b1b7d-122">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="b1b7d-123">Özellik adlarını ve değerlerini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="b1b7d-123">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="b1b7d-124">Özellikleri yoksay</span><span class="sxs-lookup"><span data-stu-id="b1b7d-124">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="b1b7d-125">Geçersiz JSON 'a izin ver</span><span class="sxs-lookup"><span data-stu-id="b1b7d-125">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="b1b7d-126">Tutamaç taşması JSON</span><span class="sxs-lookup"><span data-stu-id="b1b7d-126">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="b1b7d-127">Döngüsel başvuruları koru</span><span class="sxs-lookup"><span data-stu-id="b1b7d-127">Preserve circular references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="b1b7d-128">Polimorfik serileştirme</span><span class="sxs-lookup"><span data-stu-id="b1b7d-128">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="b1b7d-129">[System.Text.Json API başvurusu](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="b1b7d-129">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
