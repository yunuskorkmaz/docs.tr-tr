---
title: .NET kullanarak C# JSON serisini serileştirme ve serisini kaldırma
ms.date: 01/10/2020
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: c05783963ba521109fb542f247ec9e62fdb5c2d9
ms.sourcegitcommit: dfad244ba549702b649bfef3bb057e33f24a8fb2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2020
ms.locfileid: "75904639"
---
# <a name="json-serialization-and-deserialization-marshalling-and-unmarshalling-in-net---overview"></a><span data-ttu-id="dc9bc-102">.NET 'te JSON serileştirme ve seri durumundan çıkarma (sıralama ve kaldırma)-genel bakış</span><span class="sxs-lookup"><span data-stu-id="dc9bc-102">JSON serialization and deserialization (marshalling and unmarshalling) in .NET - overview</span></span>

<span data-ttu-id="dc9bc-103">`System.Text.Json` ad alanı, JavaScript Nesne Gösterimi (JSON) ' den serileştirmek ve seri durumdan çıkarmak için işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc9bc-103">The `System.Text.Json` namespace provides functionality for serializing to and deserializing from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="dc9bc-104">Kitaplık tasarımı, kapsamlı bir özellik kümesi üzerinden yüksek performans ve düşük bellek ayırmayı vurgular.</span><span class="sxs-lookup"><span data-stu-id="dc9bc-104">The library design emphasizes high performance and low memory allocation over an extensive feature set.</span></span> <span data-ttu-id="dc9bc-105">Yerleşik UTF-8 desteği, UTF-8 olarak kodlanmış JSON metnini okuma ve yazma sürecini en iyi duruma getirir. Bu, Web ve disk üzerindeki dosyalardaki veriler için en yaygın kodlama olur.</span><span class="sxs-lookup"><span data-stu-id="dc9bc-105">Built-in UTF-8 support optimizes the process of reading and writing JSON text encoded as UTF-8, which is the most prevalent encoding for data on the web and files on disk.</span></span>

<span data-ttu-id="dc9bc-106">Kitaplık Ayrıca, bellek içi belge nesne modeli (DOM) ile çalışmak için sınıflar sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc9bc-106">The library also provides classes for working with an in-memory document object model (DOM).</span></span> <span data-ttu-id="dc9bc-107">Bu özellik bir JSON dosyası veya dizesindeki öğelerin rastgele salt okunurdur erişimine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="dc9bc-107">This feature enables random read-only access of the elements in a JSON file or string.</span></span> 

## <a name="how-to-get-the-library"></a><span data-ttu-id="dc9bc-108">Kitaplığı alma</span><span class="sxs-lookup"><span data-stu-id="dc9bc-108">How to get the library</span></span>

* <span data-ttu-id="dc9bc-109">Kitaplığı, [.NET Core 3,0](https://aka.ms/netcore3download) paylaşılan çerçevesinin bir parçası olarak yerleşik olarak bulunur.</span><span class="sxs-lookup"><span data-stu-id="dc9bc-109">The library is built-in as part of the [.NET Core 3.0](https://aka.ms/netcore3download) shared framework.</span></span>
* <span data-ttu-id="dc9bc-110">Diğer hedef çerçeveler için [System. Text. JSON](https://www.nuget.org/packages/System.Text.Json) NuGet paketini yükler.</span><span class="sxs-lookup"><span data-stu-id="dc9bc-110">For other target frameworks, install the [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet package.</span></span> <span data-ttu-id="dc9bc-111">Paket şunları destekler:</span><span class="sxs-lookup"><span data-stu-id="dc9bc-111">The package supports:</span></span>
  * <span data-ttu-id="dc9bc-112">.NET Standard 2,0 ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="dc9bc-112">.NET Standard 2.0 and later versions</span></span>
  * <span data-ttu-id="dc9bc-113">.NET Framework 4.7.2 ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="dc9bc-113">.NET Framework 4.7.2 and later versions</span></span>
  * <span data-ttu-id="dc9bc-114">.NET Core 2,0, 2,1 ve 2,2</span><span class="sxs-lookup"><span data-stu-id="dc9bc-114">.NET Core 2.0, 2.1, and 2.2</span></span>

## <a name="additional-resources"></a><span data-ttu-id="dc9bc-115">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="dc9bc-115">Additional resources</span></span>

* [<span data-ttu-id="dc9bc-116">Kitaplığı kullanma</span><span class="sxs-lookup"><span data-stu-id="dc9bc-116">How to use the library</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="dc9bc-117">Newtonsoft. JSON 'dan geçiş yapma</span><span class="sxs-lookup"><span data-stu-id="dc9bc-117">How to migrate from Newtonsoft.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="dc9bc-118">Dönüştürücüler yazma</span><span class="sxs-lookup"><span data-stu-id="dc9bc-118">How to write converters</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="dc9bc-119">System. Text. JSON kaynak kodu</span><span class="sxs-lookup"><span data-stu-id="dc9bc-119">System.Text.Json source code</span></span>](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json)
* [<span data-ttu-id="dc9bc-120">System. Text. JSON API başvurusu</span><span class="sxs-lookup"><span data-stu-id="dc9bc-120">System.Text.Json API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="dc9bc-121">System. Text. JSON. Serialization API başvurusu</span><span class="sxs-lookup"><span data-stu-id="dc9bc-121">System.Text.Json.Serialization API reference</span></span>](xref:System.Text.Json.Serialization)
<!-- * [Roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
