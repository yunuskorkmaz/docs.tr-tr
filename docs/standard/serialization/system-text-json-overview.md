---
title: C#-.NET kullanarak JSON serisini serileştirme ve serisini kaldırma
description: "Bu genel bakışta, :::no-loc(System.Text.Json)::: .net 'TEKI JSON 'a serileştirmek ve seri durumdan çıkarmak için ad alanı işlevselliği açıklanmaktadır."
ms.date: 01/10/2020
no-loc:
- ':::no-loc(System.Text.Json):::'
- ':::no-loc(Newtonsoft.Json):::'
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: d8bd5bcf78db534bd722972db01253cbd13a7a06
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282398"
---
# <a name="json-serialization-and-deserialization-marshalling-and-unmarshalling-in-net---overview"></a><span data-ttu-id="bbe4a-103">.NET 'te JSON serileştirme ve seri durumundan çıkarma (sıralama ve kaldırma)-genel bakış</span><span class="sxs-lookup"><span data-stu-id="bbe4a-103">JSON serialization and deserialization (marshalling and unmarshalling) in .NET - overview</span></span>

<span data-ttu-id="bbe4a-104">`:::no-loc(System.Text.Json):::`Ad alanı, JavaScript nesne gösterimi (JSON) öğesinden serileştirmek ve seri durumdan çıkarmak için işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="bbe4a-104">The `:::no-loc(System.Text.Json):::` namespace provides functionality for serializing to and deserializing from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="bbe4a-105">Kitaplık tasarımı, kapsamlı bir özellik kümesi üzerinden yüksek performans ve düşük bellek ayırmayı vurgular.</span><span class="sxs-lookup"><span data-stu-id="bbe4a-105">The library design emphasizes high performance and low memory allocation over an extensive feature set.</span></span> <span data-ttu-id="bbe4a-106">Yerleşik UTF-8 desteği, UTF-8 olarak kodlanmış JSON metnini okuma ve yazma sürecini en iyi duruma getirir. Bu, Web ve disk üzerindeki dosyalardaki veriler için en yaygın kodlama olur.</span><span class="sxs-lookup"><span data-stu-id="bbe4a-106">Built-in UTF-8 support optimizes the process of reading and writing JSON text encoded as UTF-8, which is the most prevalent encoding for data on the web and files on disk.</span></span>

<span data-ttu-id="bbe4a-107">Kitaplık Ayrıca, bellek içi belge nesne modeli (DOM) ile çalışmak için sınıflar sağlar.</span><span class="sxs-lookup"><span data-stu-id="bbe4a-107">The library also provides classes for working with an in-memory document object model (DOM).</span></span> <span data-ttu-id="bbe4a-108">Bu özellik bir JSON dosyası veya dizesindeki öğelerin rastgele salt okunurdur erişimine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="bbe4a-108">This feature enables random read-only access of the elements in a JSON file or string.</span></span>

## <a name="how-to-get-the-library"></a><span data-ttu-id="bbe4a-109">Kitaplığı alma</span><span class="sxs-lookup"><span data-stu-id="bbe4a-109">How to get the library</span></span>

* <span data-ttu-id="bbe4a-110">Kitaplık, .NET Core 3,0 ve üzeri sürümler için paylaşılan Framework 'ün bir parçası olarak yerleşik olarak bulunur.</span><span class="sxs-lookup"><span data-stu-id="bbe4a-110">The library is built-in as part of the shared framework for .NET Core 3.0 and later versions.</span></span>
* <span data-ttu-id="bbe4a-111">Önceki Framework sürümleri için [:::no-loc(System.Text.Json):::](https://www.nuget.org/packages/:::no-loc(System.Text.Json):::) NuGet paketini yüklersiniz.</span><span class="sxs-lookup"><span data-stu-id="bbe4a-111">For earlier framework versions, install the [:::no-loc(System.Text.Json):::](https://www.nuget.org/packages/:::no-loc(System.Text.Json):::) NuGet package.</span></span> <span data-ttu-id="bbe4a-112">Paket şunları destekler:</span><span class="sxs-lookup"><span data-stu-id="bbe4a-112">The package supports:</span></span>

  * <span data-ttu-id="bbe4a-113">.NET Standard 2,0 ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="bbe4a-113">.NET Standard 2.0 and later versions</span></span>
  * <span data-ttu-id="bbe4a-114">.NET Framework 4.7.2 ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="bbe4a-114">.NET Framework 4.7.2 and later versions</span></span>
  * <span data-ttu-id="bbe4a-115">.NET Core 2,0, 2,1 ve 2,2</span><span class="sxs-lookup"><span data-stu-id="bbe4a-115">.NET Core 2.0, 2.1, and 2.2</span></span>

## <a name="additional-resources"></a><span data-ttu-id="bbe4a-116">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="bbe4a-116">Additional resources</span></span>

* [<span data-ttu-id="bbe4a-117">Kitaplığı kullanma</span><span class="sxs-lookup"><span data-stu-id="bbe4a-117">How to use the library</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="bbe4a-118">Öğesinden geçiş :::no-loc(Newtonsoft.Json):::</span><span class="sxs-lookup"><span data-stu-id="bbe4a-118">How to migrate from :::no-loc(Newtonsoft.Json):::</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="bbe4a-119">Dönüştürücüler yazma</span><span class="sxs-lookup"><span data-stu-id="bbe4a-119">How to write converters</span></span>](system-text-json-converters-how-to.md)
* <span data-ttu-id="bbe4a-120">[:::no-loc(System.Text.Json)::: kaynak kodu](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::)</span><span class="sxs-lookup"><span data-stu-id="bbe4a-120">[:::no-loc(System.Text.Json)::: source code](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::)</span></span>
* <span data-ttu-id="bbe4a-121">[:::no-loc(System.Text.Json)::: API başvurusu](xref::::no-loc(System.Text.Json):::)</span><span class="sxs-lookup"><span data-stu-id="bbe4a-121">[:::no-loc(System.Text.Json)::: API reference](xref::::no-loc(System.Text.Json):::)</span></span>
* <span data-ttu-id="bbe4a-122">[:::no-loc(System.Text.Json):::. Serileştirme API başvurusu](xref::::no-loc(System.Text.Json):::.Serialization)</span><span class="sxs-lookup"><span data-stu-id="bbe4a-122">[:::no-loc(System.Text.Json):::.Serialization API reference](xref::::no-loc(System.Text.Json):::.Serialization)</span></span>
<!-- * [Roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/:::no-loc(System.Text.Json):::/roadmap/README.md)-->
