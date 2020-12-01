---
title: İle JsonSerializerOptions örneği System.Text.Json
description: Mevcut örnekleri veya Web varsayılanlarını kopyalayarak JsonSerializerOptions örneklerinin örneğini oluşturmayı öğrenin.
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
ms.openlocfilehash: 0febfe15f36856f10699fd327fb17c146277eb9b
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96440032"
---
# <a name="how-to-instantiate-jsonserializeroptions-instances-with-no-locsystemtextjson"></a><span data-ttu-id="88624-103">İle JsonSerializerOptions örneklerinin örneğini oluşturma System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="88624-103">How to instantiate JsonSerializerOptions instances with System.Text.Json</span></span>

<span data-ttu-id="88624-104">Bu makalede, <xref:System.Text.Json.JsonSerializerOptions> mevcut örnekleri veya Web varsayılanlarını kopyalayarak örneklerin örneğini oluşturmayı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="88624-104">In this article, you'll learn how to instantiate <xref:System.Text.Json.JsonSerializerOptions> instances by copying existing instances or with web defaults.</span></span>

## <a name="copy-jsonserializeroptions"></a><span data-ttu-id="88624-105">JsonSerializerOptions 'ı Kopyala</span><span class="sxs-lookup"><span data-stu-id="88624-105">Copy JsonSerializerOptions</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="88624-106">[JsonSerializerOptions Oluşturucusu] (XREF:) var System.Text.Json . JsonSerializerOptions .% 23ctor ( System.Text.Json . JsonSerializerOptions)), aşağıdaki örnekte gösterildiği gibi, var olan örnekle aynı seçeneklere sahip yeni bir örnek oluşturmanıza olanak sağlar:</span><span class="sxs-lookup"><span data-stu-id="88624-106">There is a [JsonSerializerOptions constructor](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerOptions)) that lets you create a new instance with the same options as an existing instance, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CopyOptions.cs" highlight="29":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="88624-107">`JsonSerializerOptions`Mevcut bir örneği alan bir Oluşturucu .NET Core 3,1 ' de kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="88624-107">A `JsonSerializerOptions` constructor that takes an existing instance is not available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="web-defaults-for-jsonserializeroptions"></a><span data-ttu-id="88624-108">JsonSerializerOptions için Web Varsayılanları</span><span class="sxs-lookup"><span data-stu-id="88624-108">Web defaults for JsonSerializerOptions</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="88624-109">Web uygulamaları için farklı varsayılan değerlere sahip olan seçenekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="88624-109">Here are the options that have different defaults for web apps:</span></span>

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>
* <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A> = <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString>

<span data-ttu-id="88624-110">[JsonSerializerOptions Oluşturucusu] (XREF:) var System.Text.Json . JsonSerializerOptions .% 23ctor ( System.Text.Json . JsonSerializerDefaults)? View = net-5,0&Preserve-View = true), aşağıdaki örnekte gösterildiği gibi, ASP.NET Core Web Apps için kullandığı varsayılan seçeneklerle yeni bir örnek oluşturmanıza olanak sağlar:</span><span class="sxs-lookup"><span data-stu-id="88624-110">There's a [JsonSerializerOptions constructor](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerDefaults)?view=net-5.0&preserve-view=true) that lets you create a new instance with the default options that ASP.NET Core uses for web apps, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/OptionsDefaults.cs" highlight="24":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="88624-111">Web uygulamaları için farklı varsayılan değerlere sahip olan seçenekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="88624-111">Here are the options that have different defaults for web apps:</span></span>

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>

<span data-ttu-id="88624-112">`JsonSerializerOptions`Varsayılan kümesini belirten bir Oluşturucu .NET Core 3,1 ' de kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="88624-112">A `JsonSerializerOptions` constructor that specifies a set of defaults is not available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="88624-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88624-113">See also</span></span>

* [<span data-ttu-id="88624-114">System.Text.Json bakýþ</span><span class="sxs-lookup"><span data-stu-id="88624-114">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="88624-115">Büyük/küçük harfe duyarsız eşleştirmeyi etkinleştir</span><span class="sxs-lookup"><span data-stu-id="88624-115">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="88624-116">Özellik adlarını ve değerlerini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="88624-116">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="88624-117">Özellikleri yoksay</span><span class="sxs-lookup"><span data-stu-id="88624-117">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="88624-118">Geçersiz JSON 'a izin ver</span><span class="sxs-lookup"><span data-stu-id="88624-118">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="88624-119">Tutamaç taşması JSON</span><span class="sxs-lookup"><span data-stu-id="88624-119">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="88624-120">Döngüsel başvuruları koru</span><span class="sxs-lookup"><span data-stu-id="88624-120">Preserve circular references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="88624-121">Değişmez türler ve genel olmayan erişimciler</span><span class="sxs-lookup"><span data-stu-id="88624-121">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="88624-122">Polimorfik serileştirme</span><span class="sxs-lookup"><span data-stu-id="88624-122">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="88624-123">[System.Text.Json API başvurusu](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="88624-123">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
