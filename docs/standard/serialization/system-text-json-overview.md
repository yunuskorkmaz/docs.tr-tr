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
ms.openlocfilehash: cb5c15c2a5c336e2d5b4a3754fa7a02a370602f3
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009891"
---
# <a name="json-serialization-and-deserialization-marshalling-and-unmarshalling-in-net---overview"></a><span data-ttu-id="b8b63-103">.NET 'te JSON serileştirme ve seri durumundan çıkarma (sıralama ve kaldırma)-genel bakış</span><span class="sxs-lookup"><span data-stu-id="b8b63-103">JSON serialization and deserialization (marshalling and unmarshalling) in .NET - overview</span></span>

<span data-ttu-id="b8b63-104">`System.Text.Json`Ad alanı, JavaScript nesne gösterimi (JSON) öğesinden serileştirmek ve seri durumdan çıkarmak için işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8b63-104">The `System.Text.Json` namespace provides functionality for serializing to and deserializing from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="b8b63-105">Kitaplık tasarımı, kapsamlı bir özellik kümesi üzerinden yüksek performans ve düşük bellek ayırmayı vurgular.</span><span class="sxs-lookup"><span data-stu-id="b8b63-105">The library design emphasizes high performance and low memory allocation over an extensive feature set.</span></span> <span data-ttu-id="b8b63-106">Yerleşik UTF-8 desteği, UTF-8 olarak kodlanmış JSON metnini okuma ve yazma sürecini en iyi duruma getirir. Bu, Web ve disk üzerindeki dosyalardaki veriler için en yaygın kodlama olur.</span><span class="sxs-lookup"><span data-stu-id="b8b63-106">Built-in UTF-8 support optimizes the process of reading and writing JSON text encoded as UTF-8, which is the most prevalent encoding for data on the web and files on disk.</span></span>

<span data-ttu-id="b8b63-107">Kitaplık Ayrıca, bellek içi belge nesne modeli (DOM) ile çalışmak için sınıflar sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8b63-107">The library also provides classes for working with an in-memory document object model (DOM).</span></span> <span data-ttu-id="b8b63-108">Bu özellik bir JSON dosyası veya dizesindeki öğelerin rastgele salt okunurdur erişimine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="b8b63-108">This feature enables random read-only access of the elements in a JSON file or string.</span></span>

## <a name="how-to-get-the-library"></a><span data-ttu-id="b8b63-109">Kitaplığı alma</span><span class="sxs-lookup"><span data-stu-id="b8b63-109">How to get the library</span></span>

* <span data-ttu-id="b8b63-110">Kitaplık, .NET Core 3,0 ve üzeri sürümler için paylaşılan Framework 'ün bir parçası olarak yerleşik olarak bulunur.</span><span class="sxs-lookup"><span data-stu-id="b8b63-110">The library is built-in as part of the shared framework for .NET Core 3.0 and later versions.</span></span>
* <span data-ttu-id="b8b63-111">Önceki Framework sürümleri için [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet paketini yüklersiniz.</span><span class="sxs-lookup"><span data-stu-id="b8b63-111">For earlier framework versions, install the [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet package.</span></span> <span data-ttu-id="b8b63-112">Paket şunları destekler:</span><span class="sxs-lookup"><span data-stu-id="b8b63-112">The package supports:</span></span>

  * <span data-ttu-id="b8b63-113">.NET Standard 2,0 ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="b8b63-113">.NET Standard 2.0 and later versions</span></span>
  * <span data-ttu-id="b8b63-114">.NET Framework 4.7.2 ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="b8b63-114">.NET Framework 4.7.2 and later versions</span></span>
  * <span data-ttu-id="b8b63-115">.NET Core 2,0, 2,1 ve 2,2</span><span class="sxs-lookup"><span data-stu-id="b8b63-115">.NET Core 2.0, 2.1, and 2.2</span></span>

## <a name="additional-resources"></a><span data-ttu-id="b8b63-116">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="b8b63-116">Additional resources</span></span>

* [<span data-ttu-id="b8b63-117">Kitaplığı kullanma</span><span class="sxs-lookup"><span data-stu-id="b8b63-117">How to use the library</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="b8b63-118">JsonSerializerOptions örneklerinin örneğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="b8b63-118">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="b8b63-119">Büyük/küçük harf duyarlı eşlemeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="b8b63-119">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="b8b63-120">Özellik adlarını ve değerlerini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="b8b63-120">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="b8b63-121">Özellikleri yoksayma</span><span class="sxs-lookup"><span data-stu-id="b8b63-121">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="b8b63-122">Geçersiz JSON’a izin verme</span><span class="sxs-lookup"><span data-stu-id="b8b63-122">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="b8b63-123">Sap taşması JSON’ı</span><span class="sxs-lookup"><span data-stu-id="b8b63-123">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="b8b63-124">Başvuruları koruma</span><span class="sxs-lookup"><span data-stu-id="b8b63-124">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="b8b63-125">Sabit türler ve genel olmayan erişimciler</span><span class="sxs-lookup"><span data-stu-id="b8b63-125">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="b8b63-126">Polimorfik serileştirme</span><span class="sxs-lookup"><span data-stu-id="b8b63-126">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="b8b63-127">' Den ' a geçiş Newtonsoft.JsonSystem.Text.Json</span><span class="sxs-lookup"><span data-stu-id="b8b63-127">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="b8b63-128">Karakter kodlamasını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="b8b63-128">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="b8b63-129">Özel serileştiriciler ve seri hale getiriciler yazma</span><span class="sxs-lookup"><span data-stu-id="b8b63-129">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="b8b63-130">JSON serileştirme için özel dönüştürücüler yazma</span><span class="sxs-lookup"><span data-stu-id="b8b63-130">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="b8b63-131">DateTime ve DateTimeOffset desteği</span><span class="sxs-lookup"><span data-stu-id="b8b63-131">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="b8b63-132">[System.Text.Json API başvurusu](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="b8b63-132">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="b8b63-133">[System.Text.Json. Serileştirme API başvurusu](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="b8b63-133">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
