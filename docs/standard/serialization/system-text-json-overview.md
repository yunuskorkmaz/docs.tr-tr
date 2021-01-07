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
ms.openlocfilehash: b4432e7a137720216e7c0941b3384ce7ad7049e9
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970921"
---
# <a name="json-serialization-and-deserialization-marshalling-and-unmarshalling-in-net---overview"></a><span data-ttu-id="cecbf-103">.NET 'te JSON serileştirme ve seri durumundan çıkarma (sıralama ve kaldırma)-genel bakış</span><span class="sxs-lookup"><span data-stu-id="cecbf-103">JSON serialization and deserialization (marshalling and unmarshalling) in .NET - overview</span></span>

<span data-ttu-id="cecbf-104">`System.Text.Json`Ad alanı, JavaScript nesne gösterimi (JSON) öğesinden serileştirmek ve seri durumdan çıkarmak için işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="cecbf-104">The `System.Text.Json` namespace provides functionality for serializing to and deserializing from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="cecbf-105">Kitaplık tasarımı, kapsamlı bir özellik kümesi üzerinden yüksek performans ve düşük bellek ayırmayı vurgular.</span><span class="sxs-lookup"><span data-stu-id="cecbf-105">The library design emphasizes high performance and low memory allocation over an extensive feature set.</span></span> <span data-ttu-id="cecbf-106">Yerleşik UTF-8 desteği, UTF-8 olarak kodlanmış JSON metnini okuma ve yazma sürecini en iyi duruma getirir. Bu, Web ve disk üzerindeki dosyalardaki veriler için en yaygın kodlama olur.</span><span class="sxs-lookup"><span data-stu-id="cecbf-106">Built-in UTF-8 support optimizes the process of reading and writing JSON text encoded as UTF-8, which is the most prevalent encoding for data on the web and files on disk.</span></span>

<span data-ttu-id="cecbf-107">Kitaplık Ayrıca, bellek içi belge nesne modeli (DOM) ile çalışmak için sınıflar sağlar.</span><span class="sxs-lookup"><span data-stu-id="cecbf-107">The library also provides classes for working with an in-memory document object model (DOM).</span></span> <span data-ttu-id="cecbf-108">Bu özellik bir JSON dosyası veya dizesindeki öğelerin rastgele salt okunurdur erişimine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="cecbf-108">This feature enables random read-only access of the elements in a JSON file or string.</span></span>

## <a name="how-to-get-the-library"></a><span data-ttu-id="cecbf-109">Kitaplığı alma</span><span class="sxs-lookup"><span data-stu-id="cecbf-109">How to get the library</span></span>

* <span data-ttu-id="cecbf-110">Kitaplık, .NET Core 3,0 ve üzeri sürümler için paylaşılan Framework 'ün bir parçası olarak yerleşik olarak bulunur.</span><span class="sxs-lookup"><span data-stu-id="cecbf-110">The library is built-in as part of the shared framework for .NET Core 3.0 and later versions.</span></span>
* <span data-ttu-id="cecbf-111">Önceki Framework sürümleri için [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet paketini yüklersiniz.</span><span class="sxs-lookup"><span data-stu-id="cecbf-111">For earlier framework versions, install the [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet package.</span></span> <span data-ttu-id="cecbf-112">Paket şunları destekler:</span><span class="sxs-lookup"><span data-stu-id="cecbf-112">The package supports:</span></span>

  * <span data-ttu-id="cecbf-113">.NET Standard 2,0 ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="cecbf-113">.NET Standard 2.0 and later versions</span></span>
  * <span data-ttu-id="cecbf-114">.NET Framework 4.7.2 ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="cecbf-114">.NET Framework 4.7.2 and later versions</span></span>
  * <span data-ttu-id="cecbf-115">.NET Core 2,0, 2,1 ve 2,2</span><span class="sxs-lookup"><span data-stu-id="cecbf-115">.NET Core 2.0, 2.1, and 2.2</span></span>

## <a name="additional-resources"></a><span data-ttu-id="cecbf-116">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="cecbf-116">Additional resources</span></span>

* [<span data-ttu-id="cecbf-117">Kitaplığı kullanma</span><span class="sxs-lookup"><span data-stu-id="cecbf-117">How to use the library</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="cecbf-118">JsonSerializerOptions örneklerinin örneğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="cecbf-118">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="cecbf-119">Büyük/küçük harf duyarlı eşlemeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="cecbf-119">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="cecbf-120">Özellik adlarını ve değerlerini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="cecbf-120">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="cecbf-121">Özellikleri yoksayma</span><span class="sxs-lookup"><span data-stu-id="cecbf-121">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="cecbf-122">Geçersiz JSON’a izin verme</span><span class="sxs-lookup"><span data-stu-id="cecbf-122">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="cecbf-123">Sap taşması JSON’ı</span><span class="sxs-lookup"><span data-stu-id="cecbf-123">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="cecbf-124">Başvuruları koruma</span><span class="sxs-lookup"><span data-stu-id="cecbf-124">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="cecbf-125">Sabit türler ve genel olmayan erişimciler</span><span class="sxs-lookup"><span data-stu-id="cecbf-125">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="cecbf-126">Polimorfik serileştirme</span><span class="sxs-lookup"><span data-stu-id="cecbf-126">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="cecbf-127">' Den ' a geçiş Newtonsoft.JsonSystem.Text.Json</span><span class="sxs-lookup"><span data-stu-id="cecbf-127">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="cecbf-128">Karakter kodlamasını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="cecbf-128">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="cecbf-129">Özel serileştiriciler ve seri hale getiriciler yazma</span><span class="sxs-lookup"><span data-stu-id="cecbf-129">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="cecbf-130">JSON serileştirme için özel dönüştürücüler yazma</span><span class="sxs-lookup"><span data-stu-id="cecbf-130">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="cecbf-131">DateTime ve DateTimeOffset desteği</span><span class="sxs-lookup"><span data-stu-id="cecbf-131">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* [<span data-ttu-id="cecbf-132">İçinde desteklenen koleksiyon türleri System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="cecbf-132">Supported collection types in System.Text.Json</span></span>](system-text-json-supported-collection-types.md)
* <span data-ttu-id="cecbf-133">[System.Text.Json API başvurusu](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="cecbf-133">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="cecbf-134">[System.Text.Json. Serileştirme API başvurusu](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="cecbf-134">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
