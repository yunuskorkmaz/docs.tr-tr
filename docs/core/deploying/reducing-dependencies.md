---
title: Paket bağımlılıkları project.json ile azaltma
description: Paket bağımlılıklarını project.json tabanlı kitaplıkları yazarken azaltın.
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.openlocfilehash: ae314800f789cee363728def8347b5e6990acb0b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33211790"
---
# <a name="reducing-package-dependencies-with-projectjson"></a><span data-ttu-id="a7ec6-103">Paket bağımlılıkları project.json ile azaltma</span><span class="sxs-lookup"><span data-stu-id="a7ec6-103">Reducing Package Dependencies with project.json</span></span>

<span data-ttu-id="a7ec6-104">Bu makale, Paket bağımlılıklarını yazarken azaltma hakkında bilmeniz gerekenler kapsamaktadır `project.json` kitaplıkları.</span><span class="sxs-lookup"><span data-stu-id="a7ec6-104">This article covers what you need to know about reducing your package dependencies when authoring `project.json` libraries.</span></span> <span data-ttu-id="a7ec6-105">Bu makalenin sonundaki tarafından yalnızca gerekli bağımlılıkları kullanır, kitaplığınızı oluşturmak öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="a7ec6-105">By the end of this article, you will learn how to compose your library such that it only uses the dependencies it needs.</span></span> 

## <a name="why-its-important"></a><span data-ttu-id="a7ec6-106">Neden önemli olduğunu</span><span class="sxs-lookup"><span data-stu-id="a7ec6-106">Why it's Important</span></span>

<span data-ttu-id="a7ec6-107">.NET core NuGet paketlerini oluşan bir üründür.</span><span class="sxs-lookup"><span data-stu-id="a7ec6-107">.NET Core is a product made up of NuGet packages.</span></span>  <span data-ttu-id="a7ec6-108">Temel bir pakettir [. NETStandard.Library metapackage](https://www.nuget.org/packages/NETStandard.Library), hangi bir NuGet paketi diğer paketler halinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="a7ec6-108">An essential package is the [.NETStandard.Library metapackage](https://www.nuget.org/packages/NETStandard.Library), which is a NuGet package composed of other packages.</span></span>  <span data-ttu-id="a7ec6-109">.NET Framework, .NET Core ve Xamarin/Mono gibi birden çok .NET uygulamaları üzerinde çalışmak için garanti paket kümesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a7ec6-109">It provides you with the set of packages that are guaranteed to work on multiple .NET implementations, such as .NET Framework, .NET Core and Xamarin/Mono.</span></span>

<span data-ttu-id="a7ec6-110">Ancak, kitaplık içerdiği her tek bir paket kullanmayacaksa şansı yoktur.</span><span class="sxs-lookup"><span data-stu-id="a7ec6-110">However, there's a good chance that your library won't use every single package it contains.</span></span>  <span data-ttu-id="a7ec6-111">Bir kitaplık yazma ve NuGet dağıtma, "yalnızca paketler aşağı kaydırın, bağımlılıkları kırpma için" en iyi yöntem olduğunda, aslında kullanın.</span><span class="sxs-lookup"><span data-stu-id="a7ec6-111">When authoring a library and distributing it over NuGet, it's a best practice to "trim" your dependencies down to only the packages you actually use.</span></span>  <span data-ttu-id="a7ec6-112">Bu, NuGet paketleri için daha küçük genel ayak izini sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="a7ec6-112">This results in a smaller overall footprint for NuGet packages.</span></span>

## <a name="how-to-do-it"></a><span data-ttu-id="a7ec6-113">Bunu nasıl</span><span class="sxs-lookup"><span data-stu-id="a7ec6-113">How to do it</span></span>

<span data-ttu-id="a7ec6-114">Şu anda hiçbir resmi yoktur `dotnet` paket referanslarını kırpar komutu.</span><span class="sxs-lookup"><span data-stu-id="a7ec6-114">Currently, there is no official `dotnet` command which trims package references.</span></span>  <span data-ttu-id="a7ec6-115">Bunun yerine, el ile yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a7ec6-115">Instead, you'll have to do it manually.</span></span>  <span data-ttu-id="a7ec6-116">Genel işlem aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="a7ec6-116">The general process looks like the following:</span></span>

1. <span data-ttu-id="a7ec6-117">Başvuru `NETStandard.Library` sürüm `1.6.0` içinde bir `dependencies` bölümü, `project.json`.</span><span class="sxs-lookup"><span data-stu-id="a7ec6-117">Reference `NETStandard.Library` version `1.6.0` in a `dependencies` section of your `project.json`.</span></span>
2. <span data-ttu-id="a7ec6-118">Paketlerle geri `dotnet restore` ([bkz. Not](#dotnet-restore-note)) komut satırından.</span><span class="sxs-lookup"><span data-stu-id="a7ec6-118">Restore packages with `dotnet restore` ([see note](#dotnet-restore-note)) from the command line.</span></span>
3. <span data-ttu-id="a7ec6-119">İnceleme `project.lock.json` dosya ve Bul `NETSTandard.Library` bölümü.</span><span class="sxs-lookup"><span data-stu-id="a7ec6-119">Inspect the `project.lock.json` file and find the `NETSTandard.Library` section.</span></span>  <span data-ttu-id="a7ec6-120">Dosya başına yakın olur.</span><span class="sxs-lookup"><span data-stu-id="a7ec6-120">It's near the beginning of the file.</span></span>
4. <span data-ttu-id="a7ec6-121">Tüm altında listelenen paketler kopyalama `dependencies`.</span><span class="sxs-lookup"><span data-stu-id="a7ec6-121">Copy all of the listed packages under `dependencies`.</span></span>
5. <span data-ttu-id="a7ec6-122">Kaldırma `.NETStandard.Library` başvuru ve kopyalanan paketlerle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="a7ec6-122">Remove the `.NETStandard.Library` reference and replace it with the copied packages.</span></span>
6. <span data-ttu-id="a7ec6-123">Gerekmeyen Paketlerine yönelik başvuruları kaldırın.</span><span class="sxs-lookup"><span data-stu-id="a7ec6-123">Remove references to packages you don't need.</span></span>


<span data-ttu-id="a7ec6-124">Aşağıdaki yollardan birini kullanarak gerekmeyen hangi paketlerin bulabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a7ec6-124">You can find out which packages you don't need by one of the following ways:</span></span>

1. <span data-ttu-id="a7ec6-125">Deneme yanılma.</span><span class="sxs-lookup"><span data-stu-id="a7ec6-125">Trial and error.</span></span>  <span data-ttu-id="a7ec6-126">Bu, bir paketi kaldırma, geri yükleme, kitaplığınızı hala derler, görme ve bu işlem yinelenen içerir.</span><span class="sxs-lookup"><span data-stu-id="a7ec6-126">This involves removing a package, restoring, seeing if your library still compiles, and repeating this process.</span></span>
2. <span data-ttu-id="a7ec6-127">Bir aracı gibi kullanarak [ILSpy](http://ilspy.net) veya [.NET Reflector](http://www.red-gate.com/products/dotnet-development/reflector) ne kodunuzu gerçekte kullandığını görmek için başvurular atmaya.</span><span class="sxs-lookup"><span data-stu-id="a7ec6-127">Using a tool such as [ILSpy](http://ilspy.net) or [.NET Reflector](http://www.red-gate.com/products/dotnet-development/reflector) to peek at references to see what your code is actually using.</span></span>  <span data-ttu-id="a7ec6-128">Sonra kullanmakta olduğunuz türlerine karşılık gelen paketler kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7ec6-128">You can then remove packages which don't correspond to types you're using.</span></span>

## <a name="example"></a><span data-ttu-id="a7ec6-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="a7ec6-129">Example</span></span> 

<span data-ttu-id="a7ec6-130">Genel koleksiyon türleri için ek işlevler sağlanan bir kitaplık yazdı düşünün.</span><span class="sxs-lookup"><span data-stu-id="a7ec6-130">Imagine that you wrote a library which provided additional functionality to generic collection types.</span></span>  <span data-ttu-id="a7ec6-131">Bu tür bir kitaplığı gibi paketlere bağımlı gerek `System.Collections`, ancak hiç paketleri gibi değişebilir `System.Net.Http`.</span><span class="sxs-lookup"><span data-stu-id="a7ec6-131">Such a library would need to depend on packages such as `System.Collections`, but may not at all depend on packages such as `System.Net.Http`.</span></span>  <span data-ttu-id="a7ec6-132">Bu nedenle, yalnızca ne bu kitaplığı gerekli aşağıya doğru Paket bağımlılıklarını kırpma iyi olur!</span><span class="sxs-lookup"><span data-stu-id="a7ec6-132">As such, it would be good to trim package dependencies down to only what this library required!</span></span>

<span data-ttu-id="a7ec6-133">Bu kitaplık kırpma için ile başlamanız `project.json` dosyası ve bir başvuru ekleyin `NETStandard.Library` sürüm `1.6.0`.</span><span class="sxs-lookup"><span data-stu-id="a7ec6-133">To trim this library, you start with the `project.json` file and add a reference to `NETStandard.Library` version `1.6.0`.</span></span>

```json
{
    "version":"1.0.0",
    "dependencies":{
        "NETStandard.Library":"1.6.0"
    },
    "frameworks": {
        "netstandard1.0": {}
     }
}
```

<span data-ttu-id="a7ec6-134">Ardından, paketlerle geri `dotnet restore` ([nota bakın](#dotnet-restore-note)), incelemek `project.lock.json` dosya ve bulmak için geri tüm paketler `NETSTandard.Library`.</span><span class="sxs-lookup"><span data-stu-id="a7ec6-134">Next, you restore packages with `dotnet restore` ([see note](#dotnet-restore-note)), inspect the `project.lock.json` file, and find all the packages restored for `NETSTandard.Library`.</span></span>

<span data-ttu-id="a7ec6-135">İlgili bölümü işte `project.lock.json` dosya görülüyor hedeflerken `netstandard1.0`:</span><span class="sxs-lookup"><span data-stu-id="a7ec6-135">Here's what the relevant section in the `project.lock.json` file looks like when targeting `netstandard1.0`:</span></span>

```json
"NETStandard.Library/1.6.0":{
    "type": "package",
    "dependencies": {
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Diagnostics.Debug": "4.0.11",
        "System.Diagnostics.Tools": "4.0.1",
        "System.Globalization": "4.0.11",
        "System.IO": "4.1.0",
        "System.Linq": "4.1.0",
        "System.Net.Primitives": "4.0.11",
        "System.ObjectModel": "4.0.12",
        "System.Reflection": "4.1.0",
        "System.Reflection.Extensions": "4.0.1",
        "System.Reflection.Primitives": "4.0.1",
        "System.Resources.ResourceManager": "4.0.1",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Text.Encoding": "4.0.11",
        "System.Text.Encoding.Extensions": "4.0.11",
        "System.Text.RegularExpressions": "4.1.0",
        "System.Threading": "4.0.11",
        "System.Threading.Tasks": "4.0.11",
        "System.Xml.ReaderWriter": "4.0.11",
        "System.Xml.XDocument": "4.0.11"
    }
}
```

<span data-ttu-id="a7ec6-136">Ardından, paket referanslarını üzerinden kopyalama `dependencies` kitaplığın bölümünü `project.json` dosya, değiştirme `NETStandard.Library` başvurusu:</span><span class="sxs-lookup"><span data-stu-id="a7ec6-136">Next, copy over the package references into the `dependencies` section of the library's `project.json` file, replacing the `NETStandard.Library` reference:</span></span>

```json
{
    "version":"1.0.0",
    "dependencies":{
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Diagnostics.Debug": "4.0.11",
        "System.Diagnostics.Tools": "4.0.1",
        "System.Globalization": "4.0.11",
        "System.IO": "4.1.0",
        "System.Linq": "4.1.0",
        "System.Net.Primitives": "4.0.11",
        "System.ObjectModel": "4.0.12",
        "System.Reflection": "4.1.0",
        "System.Reflection.Extensions": "4.0.1",
        "System.Reflection.Primitives": "4.0.1",
        "System.Resources.ResourceManager": "4.0.1",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Text.Encoding": "4.0.11",
        "System.Text.Encoding.Extensions": "4.0.11",
        "System.Text.RegularExpressions": "4.1.0",
        "System.Threading": "4.0.11",
        "System.Threading.Tasks": "4.0.11",
        "System.Xml.ReaderWriter": "4.0.11",
        "System.Xml.XDocument": "4.0.11"
    },
    "frameworks":{
        "netstandard1.0": {}
    }
}
```

<span data-ttu-id="a7ec6-137">Paketler, oldukça çok miktarda olan hangi hangi kesinlikle koleksiyon türleri genişletmek için gerekli olmayan birçoğu.</span><span class="sxs-lookup"><span data-stu-id="a7ec6-137">That's quite a lot of packages, many of which which certainly aren't necessary for extending collection types.</span></span>  <span data-ttu-id="a7ec6-138">Paketlerini el ile kaldırın veya gibi bir araç kullanın [ILSpy](http://ilspy.net) veya [.NET Reflector](http://www.red-gate.com/products/dotnet-development/reflector) , kodunuzu gerçekte paketleri tanımlamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="a7ec6-138">You can either remove packages manually or use a tool such as [ILSpy](http://ilspy.net) or [.NET Reflector](http://www.red-gate.com/products/dotnet-development/reflector) to identify which packages your code actually uses.</span></span>

<span data-ttu-id="a7ec6-139">İşte bölünen paketi gibi görünebilir:</span><span class="sxs-lookup"><span data-stu-id="a7ec6-139">Here's what a trimmed package could look like:</span></span>

```json
{
    "dependencies":{
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Linq": "4.1.0",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Runtime.Handles": "4.0.1",
        "System.Runtime.InteropServices": "4.1.0",
        "System.Runtime.InteropServices.RuntimeInformation": "4.0.0",
        "System.Threading.Tasks": "4.0.11"
    },
    "frameworks":{
        "netstandard1.0": {}
     }
}
```

<span data-ttu-id="a7ec6-140">Şimdi, bağlı, daha küçük bir yer olan üzerinde `NETStandard.Library` metapackage.</span><span class="sxs-lookup"><span data-stu-id="a7ec6-140">Now, it has a smaller footprint than if it had depended on the `NETStandard.Library` metapackage.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]