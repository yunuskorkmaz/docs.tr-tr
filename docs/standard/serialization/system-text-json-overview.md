---
title: .NET 'te JSON serileştirme
author: tdykstra
ms.author: tdykstra
ms.date: 09/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: 6cb45fded220b6123dbf4461f5f1cf1c3556ff69
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083089"
---
# <a name="json-serialization-in-net"></a><span data-ttu-id="2b4e3-102">.NET 'te JSON serileştirme</span><span class="sxs-lookup"><span data-stu-id="2b4e3-102">JSON serialization in .NET</span></span>

<span data-ttu-id="2b4e3-103">Ad `System.Text.Json` alanı, JavaScript nesne gösterimi (JSON) öğesine ve öğesinden serileştirmek için işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="2b4e3-103">The `System.Text.Json` namespace provides functionality for serializing to and from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="2b4e3-104">Kitaplık tasarımı, kapsamlı bir özellik kümesi üzerinden yüksek performans ve düşük bellek ayırmayı vurgular.</span><span class="sxs-lookup"><span data-stu-id="2b4e3-104">The library design emphasizes high performance and low memory allocation over an extensive feature set.</span></span> <span data-ttu-id="2b4e3-105">Yerleşik UTF-8 desteği, UTF-8 olarak kodlanmış JSON metnini okuma ve yazma sürecini en iyi duruma getirir. Bu, Web ve disk üzerindeki dosyalardaki veriler için en yaygın kodlama olur.</span><span class="sxs-lookup"><span data-stu-id="2b4e3-105">Built-in UTF-8 support optimizes the process of reading and writing JSON text encoded as UTF-8, which is the most prevalent encoding for data on the web and files on disk.</span></span>

<span data-ttu-id="2b4e3-106">Kitaplık Ayrıca, bellek içi belge nesne modeli (DOM) ile çalışmak için sınıflar sağlar.</span><span class="sxs-lookup"><span data-stu-id="2b4e3-106">The library also provides classes for working with an in-memory document object model (DOM).</span></span> <span data-ttu-id="2b4e3-107">Bu özellik bir JSON dosyası veya dizesindeki öğelerin rastgele salt okunurdur erişimine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="2b4e3-107">This feature enables random read-only access of the elements in a JSON file or string.</span></span> 

## <a name="how-to-get-the-library"></a><span data-ttu-id="2b4e3-108">Kitaplığı alma</span><span class="sxs-lookup"><span data-stu-id="2b4e3-108">How to get the library</span></span>

* <span data-ttu-id="2b4e3-109">Kitaplığı, [.NET Core 3,0](https://aka.ms/netcore3download) paylaşılan çerçevesinin bir parçası olarak yerleşik olarak bulunur.</span><span class="sxs-lookup"><span data-stu-id="2b4e3-109">The library is built-in as part of the [.NET Core 3.0](https://aka.ms/netcore3download) shared framework.</span></span>
* <span data-ttu-id="2b4e3-110">Diğer hedef çerçeveler için [System. Text. JSON](https://www.nuget.org/packages/System.Text.Json) NuGet paketini yükler.</span><span class="sxs-lookup"><span data-stu-id="2b4e3-110">For other target frameworks, install the [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet package.</span></span> <span data-ttu-id="2b4e3-111">Paket şunları destekler:</span><span class="sxs-lookup"><span data-stu-id="2b4e3-111">The package supports:</span></span>
  * <span data-ttu-id="2b4e3-112">.NET Standard 2,0 ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="2b4e3-112">.NET Standard 2.0 and later versions</span></span>
  * <span data-ttu-id="2b4e3-113">.NET Framework 4,61 ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="2b4e3-113">.NET Framework 4.61 and later versions</span></span>
  * <span data-ttu-id="2b4e3-114">.NET Core 2,0 ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="2b4e3-114">.NET Core 2.0 and later versions</span></span>

## <a name="additional-resources"></a><span data-ttu-id="2b4e3-115">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="2b4e3-115">Additional resources</span></span>

* [<span data-ttu-id="2b4e3-116">Kitaplığı kullanma</span><span class="sxs-lookup"><span data-stu-id="2b4e3-116">How to use the library</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="2b4e3-117">Kaynak kodu</span><span class="sxs-lookup"><span data-stu-id="2b4e3-117">Source code</span></span>](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json)
* [<span data-ttu-id="2b4e3-118">API başvurusu</span><span class="sxs-lookup"><span data-stu-id="2b4e3-118">API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="2b4e3-119">Yol Haritası</span><span class="sxs-lookup"><span data-stu-id="2b4e3-119">Roadmap</span></span>](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/roadmap/README.md)
* <span data-ttu-id="2b4e3-120">DotNet/corefx deposundaki GitHub sorunları</span><span class="sxs-lookup"><span data-stu-id="2b4e3-120">GitHub issues in the dotnet/corefx repository</span></span>
  * [<span data-ttu-id="2b4e3-121">System. Text. JSON geliştirmesi hakkında tartışma</span><span class="sxs-lookup"><span data-stu-id="2b4e3-121">Discussion about the development of System.Text.Json</span></span>](https://github.com/dotnet/corefx/issues/33115)
  * [<span data-ttu-id="2b4e3-122">Tüm System. Text. JSON sorunları</span><span class="sxs-lookup"><span data-stu-id="2b4e3-122">All System.Text.Json issues</span></span>](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json)
  * [<span data-ttu-id="2b4e3-123">JSON işlevi etiketli System. Text. JSON sorunları-doc</span><span class="sxs-lookup"><span data-stu-id="2b4e3-123">System.Text.Json issues labeled json-functionality-doc</span></span>](https://github.com/dotnet/corefx/labels/json-functionality-doc)
