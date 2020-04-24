---
title: C#-.NET kullanarak JSON serisini serileştirme ve serisini kaldırma
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 660a2831aa6a807486fc47eae880bcd11347c547
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159552"
---
# <a name="json-serialization-and-deserialization-marshalling-and-unmarshalling-in-net---overview"></a><span data-ttu-id="94699-102">.NET 'te JSON serileştirme ve seri durumundan çıkarma (sıralama ve kaldırma)-genel bakış</span><span class="sxs-lookup"><span data-stu-id="94699-102">JSON serialization and deserialization (marshalling and unmarshalling) in .NET - overview</span></span>

<span data-ttu-id="94699-103">Ad `System.Text.Json` alanı, JAVASCRIPT nesne GÖSTERIMI (JSON) öğesinden serileştirmek ve seri durumdan çıkarmak için işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="94699-103">The `System.Text.Json` namespace provides functionality for serializing to and deserializing from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="94699-104">Kitaplık tasarımı, kapsamlı bir özellik kümesi üzerinden yüksek performans ve düşük bellek ayırmayı vurgular.</span><span class="sxs-lookup"><span data-stu-id="94699-104">The library design emphasizes high performance and low memory allocation over an extensive feature set.</span></span> <span data-ttu-id="94699-105">Yerleşik UTF-8 desteği, UTF-8 olarak kodlanmış JSON metnini okuma ve yazma sürecini en iyi duruma getirir. Bu, Web ve disk üzerindeki dosyalardaki veriler için en yaygın kodlama olur.</span><span class="sxs-lookup"><span data-stu-id="94699-105">Built-in UTF-8 support optimizes the process of reading and writing JSON text encoded as UTF-8, which is the most prevalent encoding for data on the web and files on disk.</span></span>

<span data-ttu-id="94699-106">Kitaplık Ayrıca, bellek içi belge nesne modeli (DOM) ile çalışmak için sınıflar sağlar.</span><span class="sxs-lookup"><span data-stu-id="94699-106">The library also provides classes for working with an in-memory document object model (DOM).</span></span> <span data-ttu-id="94699-107">Bu özellik bir JSON dosyası veya dizesindeki öğelerin rastgele salt okunurdur erişimine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="94699-107">This feature enables random read-only access of the elements in a JSON file or string.</span></span>

## <a name="how-to-get-the-library"></a><span data-ttu-id="94699-108">Kitaplığı alma</span><span class="sxs-lookup"><span data-stu-id="94699-108">How to get the library</span></span>

* <span data-ttu-id="94699-109">Kitaplığı, [.NET Core 3,0](https://aka.ms/netcore3download) paylaşılan çerçevesinin bir parçası olarak yerleşik olarak bulunur.</span><span class="sxs-lookup"><span data-stu-id="94699-109">The library is built-in as part of the [.NET Core 3.0](https://aka.ms/netcore3download) shared framework.</span></span>
* <span data-ttu-id="94699-110">Diğer hedef çerçeveler için [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet paketini yükler.</span><span class="sxs-lookup"><span data-stu-id="94699-110">For other target frameworks, install the [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet package.</span></span> <span data-ttu-id="94699-111">Paket şunları destekler:</span><span class="sxs-lookup"><span data-stu-id="94699-111">The package supports:</span></span>
  * <span data-ttu-id="94699-112">.NET Standard 2,0 ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="94699-112">.NET Standard 2.0 and later versions</span></span>
  * <span data-ttu-id="94699-113">.NET Framework 4.7.2 ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="94699-113">.NET Framework 4.7.2 and later versions</span></span>
  * <span data-ttu-id="94699-114">.NET Core 2,0, 2,1 ve 2,2</span><span class="sxs-lookup"><span data-stu-id="94699-114">.NET Core 2.0, 2.1, and 2.2</span></span>

## <a name="additional-resources"></a><span data-ttu-id="94699-115">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="94699-115">Additional resources</span></span>

* [<span data-ttu-id="94699-116">Kitaplığı kullanma</span><span class="sxs-lookup"><span data-stu-id="94699-116">How to use the library</span></span>](system-text-json-how-to.md)
* <span data-ttu-id="94699-117">[Öğesinden geçişNewtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span><span class="sxs-lookup"><span data-stu-id="94699-117">[How to migrate from Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span></span>
* [<span data-ttu-id="94699-118">Dönüştürücüler yazma</span><span class="sxs-lookup"><span data-stu-id="94699-118">How to write converters</span></span>](system-text-json-converters-how-to.md)
* <span data-ttu-id="94699-119">[System.Text.Jsonkaynak kodu](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="94699-119">[System.Text.Json source code](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json)</span></span>
* <span data-ttu-id="94699-120">[System.Text.JsonAPI başvurusu](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="94699-120">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="94699-121">[System.Text.Json. Serileştirme API başvurusu](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="94699-121">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
<!-- * [Roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
