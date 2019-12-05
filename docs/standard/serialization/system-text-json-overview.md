---
title: .NET kullanarak C# JSON serisini serileştirme ve serisini kaldırma
author: tdykstra
ms.author: tdykstra
ms.date: 09/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: b43c3f6fd8ca56aaa99fffd40317920ee7600a2c
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802719"
---
# <a name="json-serialization-in-net---overview"></a><span data-ttu-id="8b219-102">.NET 'te JSON serileştirme-genel bakış</span><span class="sxs-lookup"><span data-stu-id="8b219-102">JSON serialization in .NET - overview</span></span>

<span data-ttu-id="8b219-103">`System.Text.Json` ad alanı, JavaScript Nesne Gösterimi (JSON) ' den serileştirmek ve seri durumdan çıkarmak için işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b219-103">The `System.Text.Json` namespace provides functionality for serializing to and deserializing from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="8b219-104">Kitaplık tasarımı, kapsamlı bir özellik kümesi üzerinden yüksek performans ve düşük bellek ayırmayı vurgular.</span><span class="sxs-lookup"><span data-stu-id="8b219-104">The library design emphasizes high performance and low memory allocation over an extensive feature set.</span></span> <span data-ttu-id="8b219-105">Yerleşik UTF-8 desteği, UTF-8 olarak kodlanmış JSON metnini okuma ve yazma sürecini en iyi duruma getirir. Bu, Web ve disk üzerindeki dosyalardaki veriler için en yaygın kodlama olur.</span><span class="sxs-lookup"><span data-stu-id="8b219-105">Built-in UTF-8 support optimizes the process of reading and writing JSON text encoded as UTF-8, which is the most prevalent encoding for data on the web and files on disk.</span></span>

<span data-ttu-id="8b219-106">Kitaplık Ayrıca, bellek içi belge nesne modeli (DOM) ile çalışmak için sınıflar sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b219-106">The library also provides classes for working with an in-memory document object model (DOM).</span></span> <span data-ttu-id="8b219-107">Bu özellik bir JSON dosyası veya dizesindeki öğelerin rastgele salt okunurdur erişimine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="8b219-107">This feature enables random read-only access of the elements in a JSON file or string.</span></span> 

## <a name="how-to-get-the-library"></a><span data-ttu-id="8b219-108">Kitaplığı alma</span><span class="sxs-lookup"><span data-stu-id="8b219-108">How to get the library</span></span>

* <span data-ttu-id="8b219-109">Kitaplığı, [.NET Core 3,0](https://aka.ms/netcore3download) paylaşılan çerçevesinin bir parçası olarak yerleşik olarak bulunur.</span><span class="sxs-lookup"><span data-stu-id="8b219-109">The library is built-in as part of the [.NET Core 3.0](https://aka.ms/netcore3download) shared framework.</span></span>
* <span data-ttu-id="8b219-110">Diğer hedef çerçeveler için [System. Text. JSON](https://www.nuget.org/packages/System.Text.Json) NuGet paketini yükler.</span><span class="sxs-lookup"><span data-stu-id="8b219-110">For other target frameworks, install the [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet package.</span></span> <span data-ttu-id="8b219-111">Paket şunları destekler:</span><span class="sxs-lookup"><span data-stu-id="8b219-111">The package supports:</span></span>
  * <span data-ttu-id="8b219-112">.NET Standard 2,0 ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="8b219-112">.NET Standard 2.0 and later versions</span></span>
  * <span data-ttu-id="8b219-113">.NET Framework 4.6.1 ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="8b219-113">.NET Framework 4.6.1 and later versions</span></span>
  * <span data-ttu-id="8b219-114">.NET Core 2,0, 2,1 ve 2,2</span><span class="sxs-lookup"><span data-stu-id="8b219-114">.NET Core 2.0, 2.1, and 2.2</span></span>

## <a name="additional-resources"></a><span data-ttu-id="8b219-115">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="8b219-115">Additional resources</span></span>

* [<span data-ttu-id="8b219-116">Kitaplığı kullanma</span><span class="sxs-lookup"><span data-stu-id="8b219-116">How to use the library</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="8b219-117">Kaynak kod</span><span class="sxs-lookup"><span data-stu-id="8b219-117">Source code</span></span>](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Text.Json)
* [<span data-ttu-id="8b219-118">API başvurusu</span><span class="sxs-lookup"><span data-stu-id="8b219-118">API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="8b219-119">Yol Haritası</span><span class="sxs-lookup"><span data-stu-id="8b219-119">Roadmap</span></span>](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Text.Json/roadmap/README.md)
* <span data-ttu-id="8b219-120">DotNet/corefx deposundaki GitHub sorunları</span><span class="sxs-lookup"><span data-stu-id="8b219-120">GitHub issues in the dotnet/corefx repository</span></span>
  * [<span data-ttu-id="8b219-121">System. Text. JSON geliştirmesi hakkında tartışma</span><span class="sxs-lookup"><span data-stu-id="8b219-121">Discussion about the development of System.Text.Json</span></span>](https://github.com/dotnet/corefx/issues/33115) <!-- TODO: Issues are still not moved to the new repo-->
  * [<span data-ttu-id="8b219-122">Tüm System. Text. JSON sorunları</span><span class="sxs-lookup"><span data-stu-id="8b219-122">All System.Text.Json issues</span></span>](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json)
  * [<span data-ttu-id="8b219-123">JSON işlevi etiketli System. Text. JSON sorunları-doc</span><span class="sxs-lookup"><span data-stu-id="8b219-123">System.Text.Json issues labeled json-functionality-doc</span></span>](https://github.com/dotnet/runtime/labels/json-functionality-doc)
