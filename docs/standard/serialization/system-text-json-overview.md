---
title: C#-.NET kullanarak JSON serisini serileştirme ve serisini kaldırma
description: Bu genel bakışta, System.Text.Json .net 'TEKI JSON 'a serileştirmek ve seri durumdan çıkarmak için ad alanı işlevselliği açıklanmaktadır.
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 28f2b78de2533c659ea0fcf9d4990694dbfd411c
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100584870"
---
# <a name="json-serialization-and-deserialization-marshalling-and-unmarshalling-in-net---overview"></a><span data-ttu-id="4d117-103">.NET 'te JSON serileştirme ve seri durumundan çıkarma (sıralama ve kaldırma)-genel bakış</span><span class="sxs-lookup"><span data-stu-id="4d117-103">JSON serialization and deserialization (marshalling and unmarshalling) in .NET - overview</span></span>

<span data-ttu-id="4d117-104">`System.Text.Json`Ad alanı, JavaScript nesne gösterimi (JSON) öğesinden serileştirmek ve seri durumdan çıkarmak için işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="4d117-104">The `System.Text.Json` namespace provides functionality for serializing to and deserializing from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="4d117-105">Kitaplık tasarımı, kapsamlı bir özellik kümesi üzerinden yüksek performans ve düşük bellek ayırmayı vurgular.</span><span class="sxs-lookup"><span data-stu-id="4d117-105">The library design emphasizes high performance and low memory allocation over an extensive feature set.</span></span> <span data-ttu-id="4d117-106">Yerleşik UTF-8 desteği, UTF-8 olarak kodlanmış JSON metnini okuma ve yazma sürecini en iyi duruma getirir. Bu, Web ve disk üzerindeki dosyalardaki veriler için en yaygın kodlama olur.</span><span class="sxs-lookup"><span data-stu-id="4d117-106">Built-in UTF-8 support optimizes the process of reading and writing JSON text encoded as UTF-8, which is the most prevalent encoding for data on the web and files on disk.</span></span>

<span data-ttu-id="4d117-107">Kitaplık Ayrıca, bellek içi belge nesne modeli (DOM) ile çalışmak için sınıflar sağlar.</span><span class="sxs-lookup"><span data-stu-id="4d117-107">The library also provides classes for working with an in-memory document object model (DOM).</span></span> <span data-ttu-id="4d117-108">Bu özellik bir JSON dosyası veya dizesindeki öğelerin rastgele salt okunurdur erişimine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="4d117-108">This feature enables random read-only access of the elements in a JSON file or string.</span></span>

<span data-ttu-id="4d117-109">Kitaplığın Visual Basic koddan kullanabileceğiniz bölümlerine ilişkin bazı sınırlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="4d117-109">There are some limitations on what parts of the library that you can use from Visual Basic code.</span></span> <span data-ttu-id="4d117-110">Daha fazla bilgi için bkz. [Visual Basic desteği](system-text-json-how-to.md#visual-basic-support).</span><span class="sxs-lookup"><span data-stu-id="4d117-110">For more information, see [Visual Basic support](system-text-json-how-to.md#visual-basic-support).</span></span>

## <a name="how-to-get-the-library"></a><span data-ttu-id="4d117-111">Kitaplığı alma</span><span class="sxs-lookup"><span data-stu-id="4d117-111">How to get the library</span></span>

* <span data-ttu-id="4d117-112">Kitaplık, .NET Core 3,0 ve üzeri sürümler için paylaşılan Framework 'ün bir parçası olarak yerleşik olarak bulunur.</span><span class="sxs-lookup"><span data-stu-id="4d117-112">The library is built-in as part of the shared framework for .NET Core 3.0 and later versions.</span></span>
* <span data-ttu-id="4d117-113">Önceki Framework sürümleri için [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet paketini yüklersiniz.</span><span class="sxs-lookup"><span data-stu-id="4d117-113">For earlier framework versions, install the [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet package.</span></span> <span data-ttu-id="4d117-114">Paket şunları destekler:</span><span class="sxs-lookup"><span data-stu-id="4d117-114">The package supports:</span></span>

  * <span data-ttu-id="4d117-115">.NET Standard 2,0 ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="4d117-115">.NET Standard 2.0 and later versions</span></span>
  * <span data-ttu-id="4d117-116">.NET Framework 4.7.2 ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="4d117-116">.NET Framework 4.7.2 and later versions</span></span>
  * <span data-ttu-id="4d117-117">.NET Core 2,0, 2,1 ve 2,2</span><span class="sxs-lookup"><span data-stu-id="4d117-117">.NET Core 2.0, 2.1, and 2.2</span></span>

## <a name="additional-resources"></a><span data-ttu-id="4d117-118">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="4d117-118">Additional resources</span></span>

* [<span data-ttu-id="4d117-119">Kitaplığı kullanma</span><span class="sxs-lookup"><span data-stu-id="4d117-119">How to use the library</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="4d117-120">JsonSerializerOptions örneklerinin örneğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="4d117-120">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="4d117-121">Büyük/küçük harf duyarlı eşlemeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="4d117-121">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="4d117-122">Özellik adlarını ve değerlerini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="4d117-122">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="4d117-123">Özellikleri yoksayma</span><span class="sxs-lookup"><span data-stu-id="4d117-123">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="4d117-124">Geçersiz JSON’a izin verme</span><span class="sxs-lookup"><span data-stu-id="4d117-124">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="4d117-125">Sap taşması JSON’ı</span><span class="sxs-lookup"><span data-stu-id="4d117-125">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="4d117-126">Başvuruları koruma</span><span class="sxs-lookup"><span data-stu-id="4d117-126">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="4d117-127">Sabit türler ve genel olmayan erişimciler</span><span class="sxs-lookup"><span data-stu-id="4d117-127">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="4d117-128">Polimorfik serileştirme</span><span class="sxs-lookup"><span data-stu-id="4d117-128">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="4d117-129">' Den ' a geçiş Newtonsoft.JsonSystem.Text.Json</span><span class="sxs-lookup"><span data-stu-id="4d117-129">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="4d117-130">Karakter kodlamasını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="4d117-130">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="4d117-131">Özel serileştiriciler ve seri hale getiriciler yazma</span><span class="sxs-lookup"><span data-stu-id="4d117-131">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="4d117-132">JSON serileştirme için özel dönüştürücüler yazma</span><span class="sxs-lookup"><span data-stu-id="4d117-132">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="4d117-133">DateTime ve DateTimeOffset desteği</span><span class="sxs-lookup"><span data-stu-id="4d117-133">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* [<span data-ttu-id="4d117-134">İçinde desteklenen koleksiyon türleri System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="4d117-134">Supported collection types in System.Text.Json</span></span>](system-text-json-supported-collection-types.md)
* <span data-ttu-id="4d117-135">[System.Text.Json API başvurusu](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="4d117-135">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="4d117-136">[System.Text.Json. Serileştirme API başvurusu](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="4d117-136">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
