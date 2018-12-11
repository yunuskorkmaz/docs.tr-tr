---
title: Project.json ile Paket bağımlılıklarını azaltma
description: Project.json tabanlı kitaplıkları yazma Paket bağımlılıklarını azaltın.
author: cartermp
ms.date: 06/20/2016
ms.custom: seodec18
ms.openlocfilehash: 932344ff40dd32793727fbce7bc0d6cd02592f8b
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53168289"
---
# <a name="reducing-package-dependencies-with-projectjson"></a><span data-ttu-id="1f95f-103">Project.json ile Paket bağımlılıklarını azaltma</span><span class="sxs-lookup"><span data-stu-id="1f95f-103">Reducing Package Dependencies with project.json</span></span>

<span data-ttu-id="1f95f-104">Bu makale yazarken paket bağımlılıklarınızı azaltma hakkında bilmeniz gerekenler kapsar `project.json` kitaplıkları.</span><span class="sxs-lookup"><span data-stu-id="1f95f-104">This article covers what you need to know about reducing your package dependencies when authoring `project.json` libraries.</span></span> <span data-ttu-id="1f95f-105">Bu makalenin sonunda, yalnızca gerekli bağımlılıkları kullanır, kitaplığınıza compose öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="1f95f-105">By the end of this article, you will learn how to compose your library such that it only uses the dependencies it needs.</span></span> 

## <a name="why-its-important"></a><span data-ttu-id="1f95f-106">Neden önemli olduğu</span><span class="sxs-lookup"><span data-stu-id="1f95f-106">Why it's Important</span></span>

<span data-ttu-id="1f95f-107">.NET core NuGet paketlerini oluşan bir üründür.</span><span class="sxs-lookup"><span data-stu-id="1f95f-107">.NET Core is a product made up of NuGet packages.</span></span>  <span data-ttu-id="1f95f-108">Temel bir pakettir [. NETStandard.Library metapackage](https://www.nuget.org/packages/NETStandard.Library), bir NuGet paketi diğer paketleri oluşur.</span><span class="sxs-lookup"><span data-stu-id="1f95f-108">An essential package is the [.NETStandard.Library metapackage](https://www.nuget.org/packages/NETStandard.Library), which is a NuGet package composed of other packages.</span></span>  <span data-ttu-id="1f95f-109">.NET Framework, .NET Core ve Xamarin/Mono gibi birden çok .NET uygulamaları üzerinde çalışacağı garanti paketleri kümesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="1f95f-109">It provides you with the set of packages that are guaranteed to work on multiple .NET implementations, such as .NET Framework, .NET Core and Xamarin/Mono.</span></span>

<span data-ttu-id="1f95f-110">Ancak, içerdiği her tek bir paket kitaplığınızı kullanmayacaksa şansı yoktur.</span><span class="sxs-lookup"><span data-stu-id="1f95f-110">However, there's a good chance that your library won't use every single package it contains.</span></span>  <span data-ttu-id="1f95f-111">Bir kitaplığı yazma ve NuGet dağıtma, "yalnızca paketler aşağı bağımlılıklarınızı kırpmak için" en iyi yöntem olduğunda, gerçekten kullanın.</span><span class="sxs-lookup"><span data-stu-id="1f95f-111">When authoring a library and distributing it over NuGet, it's a best practice to "trim" your dependencies down to only the packages you actually use.</span></span>  <span data-ttu-id="1f95f-112">NuGet paketleri için daha küçük bütün kapladığı alanı sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="1f95f-112">This results in a smaller overall footprint for NuGet packages.</span></span>

## <a name="how-to-do-it"></a><span data-ttu-id="1f95f-113">Nasıl yapılır</span><span class="sxs-lookup"><span data-stu-id="1f95f-113">How to do it</span></span>

<span data-ttu-id="1f95f-114">Şu anda, resmi yoktur `dotnet` paket başvuruları kırpar komutu.</span><span class="sxs-lookup"><span data-stu-id="1f95f-114">Currently, there is no official `dotnet` command which trims package references.</span></span>  <span data-ttu-id="1f95f-115">Bunun yerine, el ile yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1f95f-115">Instead, you'll have to do it manually.</span></span>  <span data-ttu-id="1f95f-116">Genel süreç aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="1f95f-116">The general process looks like the following:</span></span>

1. <span data-ttu-id="1f95f-117">Başvuru `NETStandard.Library` sürüm `1.6.0` içinde bir `dependencies` bölümünü, `project.json`.</span><span class="sxs-lookup"><span data-stu-id="1f95f-117">Reference `NETStandard.Library` version `1.6.0` in a `dependencies` section of your `project.json`.</span></span>
2. <span data-ttu-id="1f95f-118">Paketleri geri `dotnet restore` ([bkz. Not](#dotnet-restore-note)) komut satırı.</span><span class="sxs-lookup"><span data-stu-id="1f95f-118">Restore packages with `dotnet restore` ([see note](#dotnet-restore-note)) from the command line.</span></span>
3. <span data-ttu-id="1f95f-119">İnceleme `project.lock.json` dosya ve bulma `NETSTandard.Library` bölümü.</span><span class="sxs-lookup"><span data-stu-id="1f95f-119">Inspect the `project.lock.json` file and find the `NETSTandard.Library` section.</span></span>  <span data-ttu-id="1f95f-120">Bu, dosyanın başına yakın olur.</span><span class="sxs-lookup"><span data-stu-id="1f95f-120">It's near the beginning of the file.</span></span>
4. <span data-ttu-id="1f95f-121">Tüm altında listelenen paketlerin bir bölümünü kopyalayın `dependencies`.</span><span class="sxs-lookup"><span data-stu-id="1f95f-121">Copy all of the listed packages under `dependencies`.</span></span>
5. <span data-ttu-id="1f95f-122">Kaldırma `.NETStandard.Library` başvuru ve kopyalanan paketleri ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1f95f-122">Remove the `.NETStandard.Library` reference and replace it with the copied packages.</span></span>
6. <span data-ttu-id="1f95f-123">İhtiyacınız olmayan paketleri başvuruları kaldırın.</span><span class="sxs-lookup"><span data-stu-id="1f95f-123">Remove references to packages you don't need.</span></span>


<span data-ttu-id="1f95f-124">Aşağıdaki yöntemlerden birini kullanarak ihtiyacınız olmayan paketler bulabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1f95f-124">You can find out which packages you don't need by one of the following ways:</span></span>

1. <span data-ttu-id="1f95f-125">Deneme yanılma.</span><span class="sxs-lookup"><span data-stu-id="1f95f-125">Trial and error.</span></span>  <span data-ttu-id="1f95f-126">Bu paketi kaldırma, geri yükleme, kitaplığınıza derlenmeye devam eder, görme ve bu süreci tekrarlayarak içerir.</span><span class="sxs-lookup"><span data-stu-id="1f95f-126">This involves removing a package, restoring, seeing if your library still compiles, and repeating this process.</span></span>
2. <span data-ttu-id="1f95f-127">Gibi bir araç kullanarak [yetenek](https://github.com/icsharpcode/ILSpy#ilspy-------) veya [.NET Reflector](https://www.red-gate.com/products/dotnet-development/reflector) ne kodunuzun gerçekte kullanmakta olduğunu görmenizi sağlayan başvurular göz atmak için.</span><span class="sxs-lookup"><span data-stu-id="1f95f-127">Using a tool such as [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) or [.NET Reflector](https://www.red-gate.com/products/dotnet-development/reflector) to peek at references to see what your code is actually using.</span></span>  <span data-ttu-id="1f95f-128">Ardından, kullanmakta olduğunuz türlerine karşılık gelen paketler kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f95f-128">You can then remove packages which don't correspond to types you're using.</span></span>

## <a name="example"></a><span data-ttu-id="1f95f-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="1f95f-129">Example</span></span> 

<span data-ttu-id="1f95f-130">Genel koleksiyon türleri için ek işlevler sağlanan kitaplık yazdığınız varsayalım.</span><span class="sxs-lookup"><span data-stu-id="1f95f-130">Imagine that you wrote a library which provided additional functionality to generic collection types.</span></span>  <span data-ttu-id="1f95f-131">Bir tür kitaplığı paketleri gibi bağımlı gerek `System.Collections`, ancak hiç paketleri gibi değişebilir `System.Net.Http`.</span><span class="sxs-lookup"><span data-stu-id="1f95f-131">Such a library would need to depend on packages such as `System.Collections`, but may not at all depend on packages such as `System.Net.Http`.</span></span>  <span data-ttu-id="1f95f-132">Bu nedenle, yalnızca ne bu kitaplığı gerekli aşağı Paket bağımlılıklarını trim yararlı olabilir!</span><span class="sxs-lookup"><span data-stu-id="1f95f-132">As such, it would be good to trim package dependencies down to only what this library required!</span></span>

<span data-ttu-id="1f95f-133">Bu kitaplık kırpmak için ile başlamanız `project.json` bir başvuru ekleyin ve dosya `NETStandard.Library` sürüm `1.6.0`.</span><span class="sxs-lookup"><span data-stu-id="1f95f-133">To trim this library, you start with the `project.json` file and add a reference to `NETStandard.Library` version `1.6.0`.</span></span>

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

<span data-ttu-id="1f95f-134">Ardından, paketleri geri `dotnet restore` ([bkz. Not](#dotnet-restore-note)), inceleme `project.lock.json` dosyasını ve tüm paketleri için geri `NETSTandard.Library`.</span><span class="sxs-lookup"><span data-stu-id="1f95f-134">Next, you restore packages with `dotnet restore` ([see note](#dotnet-restore-note)), inspect the `project.lock.json` file, and find all the packages restored for `NETSTandard.Library`.</span></span>

<span data-ttu-id="1f95f-135">İlgili bölüme işte `project.lock.json` dosya göründüğüne hedeflenirken `netstandard1.0`:</span><span class="sxs-lookup"><span data-stu-id="1f95f-135">Here's what the relevant section in the `project.lock.json` file looks like when targeting `netstandard1.0`:</span></span>

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

<span data-ttu-id="1f95f-136">Ardından, paket başvuruları kopyalayabilirsiniz `dependencies` kitaplığın bölümünü `project.json` değiştirerek, dosya `NETStandard.Library` başvurusu:</span><span class="sxs-lookup"><span data-stu-id="1f95f-136">Next, copy over the package references into the `dependencies` section of the library's `project.json` file, replacing the `NETStandard.Library` reference:</span></span>

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

<span data-ttu-id="1f95f-137">Birçok paketleri, çoğu kesinlikle koleksiyon türlerini genişletmek için gerekli olmayan olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="1f95f-137">That's quite a lot of packages, many of which certainly aren't necessary for extending collection types.</span></span>  <span data-ttu-id="1f95f-138">Paketleri el ile kaldırmanız veya gibi bir araç kullanın [yetenek](https://github.com/icsharpcode/ILSpy#ilspy-------) veya [.NET Reflector](https://www.red-gate.com/products/dotnet-development/reflector/) , kodunuzun gerçekte paketleri tanımlamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="1f95f-138">You can either remove packages manually or use a tool such as [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) or [.NET Reflector](https://www.red-gate.com/products/dotnet-development/reflector/) to identify which packages your code actually uses.</span></span>

<span data-ttu-id="1f95f-139">İşte kırpılmış paket aşağıdaki gibi görünebilir:</span><span class="sxs-lookup"><span data-stu-id="1f95f-139">Here's what a trimmed package could look like:</span></span>

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

<span data-ttu-id="1f95f-140">Şimdi, bağımlı, daha küçük ayak izine sahip üzerinde `NETStandard.Library` metapackage.</span><span class="sxs-lookup"><span data-stu-id="1f95f-140">Now, it has a smaller footprint than if it had depended on the `NETStandard.Library` metapackage.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]