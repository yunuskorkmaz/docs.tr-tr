---
title: "Paket bağımlılıkları project.json ile azaltma"
description: "Paket bağımlılıklarını project.json tabanlı kitaplıkları yazarken azaltın."
keywords: .NET, .NET core
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 916251e3-87f9-4eee-81ec-94076215e6fa
ms.workload: dotnetcore
ms.openlocfilehash: 858fc77d9652bfa59ed0bb3159260f40c76156a4
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="reducing-package-dependencies-with-projectjson"></a><span data-ttu-id="c0b98-104">Paket bağımlılıkları project.json ile azaltma</span><span class="sxs-lookup"><span data-stu-id="c0b98-104">Reducing Package Dependencies with project.json</span></span>

<span data-ttu-id="c0b98-105">Bu makale, Paket bağımlılıklarını yazarken azaltma hakkında bilmeniz gerekenler kapsamaktadır `project.json` kitaplıkları.</span><span class="sxs-lookup"><span data-stu-id="c0b98-105">This article covers what you need to know about reducing your package dependencies when authoring `project.json` libraries.</span></span> <span data-ttu-id="c0b98-106">Bu makalenin sonundaki tarafından yalnızca gerekli bağımlılıkları kullanır, kitaplığınızı oluşturmak öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="c0b98-106">By the end of this article, you will learn how to compose your library such that it only uses the dependencies it needs.</span></span> 

## <a name="why-its-important"></a><span data-ttu-id="c0b98-107">Neden önemli olduğunu</span><span class="sxs-lookup"><span data-stu-id="c0b98-107">Why it's Important</span></span>

<span data-ttu-id="c0b98-108">.NET core NuGet paketlerini oluşan bir üründür.</span><span class="sxs-lookup"><span data-stu-id="c0b98-108">.NET Core is a product made up of NuGet packages.</span></span>  <span data-ttu-id="c0b98-109">Temel bir pakettir [. NETStandard.Library metapackage](https://www.nuget.org/packages/NETStandard.Library), hangi bir NuGet paketi diğer paketler halinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="c0b98-109">An essential package is the [.NETStandard.Library metapackage](https://www.nuget.org/packages/NETStandard.Library), which is a NuGet package composed of other packages.</span></span>  <span data-ttu-id="c0b98-110">.NET Framework, .NET Core ve Xamarin/Mono gibi birden çok .NET uygulamaları üzerinde çalışmak için garanti paket kümesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c0b98-110">It provides you with the set of packages that are guaranteed to work on multiple .NET implementations, such as .NET Framework, .NET Core and Xamarin/Mono.</span></span>

<span data-ttu-id="c0b98-111">Ancak, kitaplık içerdiği her tek bir paket kullanmayacaksa şansı yoktur.</span><span class="sxs-lookup"><span data-stu-id="c0b98-111">However, there's a good chance that your library won't use every single package it contains.</span></span>  <span data-ttu-id="c0b98-112">Bir kitaplık yazma ve NuGet dağıtma, "yalnızca paketler aşağı kaydırın, bağımlılıkları kırpma için" en iyi yöntem olduğunda, aslında kullanın.</span><span class="sxs-lookup"><span data-stu-id="c0b98-112">When authoring a library and distributing it over NuGet, it's a best practice to "trim" your dependencies down to only the packages you actually use.</span></span>  <span data-ttu-id="c0b98-113">Bu, NuGet paketleri için daha küçük genel ayak izini sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="c0b98-113">This results in a smaller overall footprint for NuGet packages.</span></span>

## <a name="how-to-do-it"></a><span data-ttu-id="c0b98-114">Bunu nasıl</span><span class="sxs-lookup"><span data-stu-id="c0b98-114">How to do it</span></span>

<span data-ttu-id="c0b98-115">Şu anda hiçbir resmi yoktur `dotnet` paket referanslarını kırpar komutu.</span><span class="sxs-lookup"><span data-stu-id="c0b98-115">Currently, there is no official `dotnet` command which trims package references.</span></span>  <span data-ttu-id="c0b98-116">Bunun yerine, el ile yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c0b98-116">Instead, you'll have to do it manually.</span></span>  <span data-ttu-id="c0b98-117">Genel işlem aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="c0b98-117">The general process looks like the following:</span></span>

1. <span data-ttu-id="c0b98-118">Başvuru `NETStandard.Library` sürüm `1.6.0` içinde bir `dependencies` bölümü, `project.json`.</span><span class="sxs-lookup"><span data-stu-id="c0b98-118">Reference `NETStandard.Library` version `1.6.0` in a `dependencies` section of your `project.json`.</span></span>
2. <span data-ttu-id="c0b98-119">Paketlerle geri `dotnet restore` ([bkz. Not](#dotnet-restore-note)) komut satırından.</span><span class="sxs-lookup"><span data-stu-id="c0b98-119">Restore packages with `dotnet restore` ([see note](#dotnet-restore-note)) from the command line.</span></span>
3. <span data-ttu-id="c0b98-120">İnceleme `project.lock.json` dosya ve Bul `NETSTandard.Library` bölümü.</span><span class="sxs-lookup"><span data-stu-id="c0b98-120">Inspect the `project.lock.json` file and find the `NETSTandard.Library` section.</span></span>  <span data-ttu-id="c0b98-121">Dosya başına yakın olur.</span><span class="sxs-lookup"><span data-stu-id="c0b98-121">It's near the beginning of the file.</span></span>
4. <span data-ttu-id="c0b98-122">Tüm altında listelenen paketler kopyalama `dependencies`.</span><span class="sxs-lookup"><span data-stu-id="c0b98-122">Copy all of the listed packages under `dependencies`.</span></span>
5. <span data-ttu-id="c0b98-123">Kaldırma `.NETStandard.Library` başvuru ve kopyalanan paketlerle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c0b98-123">Remove the `.NETStandard.Library` reference and replace it with the copied packages.</span></span>
6. <span data-ttu-id="c0b98-124">Gerekmeyen Paketlerine yönelik başvuruları kaldırın.</span><span class="sxs-lookup"><span data-stu-id="c0b98-124">Remove references to packages you don't need.</span></span>


<span data-ttu-id="c0b98-125">Aşağıdaki yollardan birini kullanarak gerekmeyen hangi paketlerin bulabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c0b98-125">You can find out which packages you don't need by one of the following ways:</span></span>

1. <span data-ttu-id="c0b98-126">Deneme yanılma.</span><span class="sxs-lookup"><span data-stu-id="c0b98-126">Trial and error.</span></span>  <span data-ttu-id="c0b98-127">Bu, bir paketi kaldırma, geri yükleme, kitaplığınızı hala derler, görme ve bu işlem yinelenen içerir.</span><span class="sxs-lookup"><span data-stu-id="c0b98-127">This involves removing a package, restoring, seeing if your library still compiles, and repeating this process.</span></span>
2. <span data-ttu-id="c0b98-128">Bir aracı gibi kullanarak [ILSpy](http://ilspy.net) veya [.NET Reflector](http://www.red-gate.com/products/dotnet-development/reflector) ne kodunuzu gerçekte kullandığını görmek için başvurular atmaya.</span><span class="sxs-lookup"><span data-stu-id="c0b98-128">Using a tool such as [ILSpy](http://ilspy.net) or [.NET Reflector](http://www.red-gate.com/products/dotnet-development/reflector) to peek at references to see what your code is actually using.</span></span>  <span data-ttu-id="c0b98-129">Sonra kullanmakta olduğunuz türlerine karşılık gelen paketler kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c0b98-129">You can then remove packages which don't correspond to types you're using.</span></span>

## <a name="example"></a><span data-ttu-id="c0b98-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="c0b98-130">Example</span></span> 

<span data-ttu-id="c0b98-131">Genel koleksiyon türleri için ek işlevler sağlanan bir kitaplık yazdı düşünün.</span><span class="sxs-lookup"><span data-stu-id="c0b98-131">Imagine that you wrote a library which provided additional functionality to generic collection types.</span></span>  <span data-ttu-id="c0b98-132">Bu tür bir kitaplığı gibi paketlere bağımlı gerek `System.Collections`, ancak hiç paketleri gibi değişebilir `System.Net.Http`.</span><span class="sxs-lookup"><span data-stu-id="c0b98-132">Such a library would need to depend on packages such as `System.Collections`, but may not at all depend on packages such as `System.Net.Http`.</span></span>  <span data-ttu-id="c0b98-133">Bu nedenle, yalnızca ne bu kitaplığı gerekli aşağıya doğru Paket bağımlılıklarını kırpma iyi olur!</span><span class="sxs-lookup"><span data-stu-id="c0b98-133">As such, it would be good to trim package dependencies down to only what this library required!</span></span>

<span data-ttu-id="c0b98-134">Bu kitaplık kırpma için ile başlamanız `project.json` dosyası ve bir başvuru ekleyin `NETStandard.Library` sürüm `1.6.0`.</span><span class="sxs-lookup"><span data-stu-id="c0b98-134">To trim this library, you start with the `project.json` file and add a reference to `NETStandard.Library` version `1.6.0`.</span></span>

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

<span data-ttu-id="c0b98-135">Ardından, paketlerle geri `dotnet restore` ([nota bakın](#dotnet-restore-note)), incelemek `project.lock.json` dosya ve bulmak için geri tüm paketler `NETSTandard.Library`.</span><span class="sxs-lookup"><span data-stu-id="c0b98-135">Next, you restore packages with `dotnet restore` ([see note](#dotnet-restore-note)), inspect the `project.lock.json` file, and find all the packages restored for `NETSTandard.Library`.</span></span>

<span data-ttu-id="c0b98-136">İlgili bölümü işte `project.lock.json` dosya görülüyor hedeflerken `netstandard1.0`:</span><span class="sxs-lookup"><span data-stu-id="c0b98-136">Here's what the relevant section in the `project.lock.json` file looks like when targeting `netstandard1.0`:</span></span>

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

<span data-ttu-id="c0b98-137">Ardından, paket referanslarını üzerinden kopyalama `dependencies` kitaplığın bölümünü `project.json` dosya, değiştirme `NETStandard.Library` başvurusu:</span><span class="sxs-lookup"><span data-stu-id="c0b98-137">Next, copy over the package references into the `dependencies` section of the library's `project.json` file, replacing the `NETStandard.Library` reference:</span></span>

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

<span data-ttu-id="c0b98-138">Paketler, oldukça çok miktarda olan hangi hangi kesinlikle koleksiyon türleri genişletmek için gerekli olmayan birçoğu.</span><span class="sxs-lookup"><span data-stu-id="c0b98-138">That's quite a lot of packages, many of which which certainly aren't necessary for extending collection types.</span></span>  <span data-ttu-id="c0b98-139">Paketlerini el ile kaldırın veya gibi bir araç kullanın [ILSpy](http://ilspy.net) veya [.NET Reflector](http://www.red-gate.com/products/dotnet-development/reflector) , kodunuzu gerçekte paketleri tanımlamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="c0b98-139">You can either remove packages manually or use a tool such as [ILSpy](http://ilspy.net) or [.NET Reflector](http://www.red-gate.com/products/dotnet-development/reflector) to identify which packages your code actually uses.</span></span>

<span data-ttu-id="c0b98-140">İşte bölünen paketi gibi görünebilir:</span><span class="sxs-lookup"><span data-stu-id="c0b98-140">Here's what a trimmed package could look like:</span></span>

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

<span data-ttu-id="c0b98-141">Şimdi, bağlı, daha küçük bir yer olan üzerinde `NETStandard.Library` metapackage.</span><span class="sxs-lookup"><span data-stu-id="c0b98-141">Now, it has a smaller footprint than if it had depended on the `NETStandard.Library` metapackage.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]