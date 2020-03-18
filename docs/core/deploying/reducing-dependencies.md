---
title: project.json ile Paket Bağımlılıklarını Azaltma
description: project.json tabanlı kitaplıkları yazarken paket bağımlılıklarını azaltın.
author: cartermp
ms.date: 06/20/2016
ms.openlocfilehash: 48ba3ef578388fd98fe7cb830df313512d359483
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75740831"
---
# <a name="reducing-package-dependencies-with-projectjson"></a><span data-ttu-id="85875-103">project.json ile Paket Bağımlılıklarını Azaltma</span><span class="sxs-lookup"><span data-stu-id="85875-103">Reducing Package Dependencies with project.json</span></span>

<span data-ttu-id="85875-104">Bu makalede, `project.json` kitaplıklar yazarken paket bağımlılıklarınızı azaltma hakkında bilmeniz gerekenler yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="85875-104">This article covers what you need to know about reducing your package dependencies when authoring `project.json` libraries.</span></span> <span data-ttu-id="85875-105">Bu makalenin sonunda, kitaplığınızı yalnızca gereksinimleri olan bağımlılıkları kullanacak şekilde nasıl oluşturacağınızı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="85875-105">By the end of this article, you will learn how to compose your library such that it only uses the dependencies it needs.</span></span>

## <a name="why-its-important"></a><span data-ttu-id="85875-106">Neden Önemli</span><span class="sxs-lookup"><span data-stu-id="85875-106">Why it's Important</span></span>

<span data-ttu-id="85875-107">.NET Core, NuGet paketlerinden oluşan bir üründür.</span><span class="sxs-lookup"><span data-stu-id="85875-107">.NET Core is a product made up of NuGet packages.</span></span>  <span data-ttu-id="85875-108">Önemli bir paket [. NETStandard.Library metapackage](https://www.nuget.org/packages/NETStandard.Library), diğer paketlerden oluşan bir NuGet paketidir.</span><span class="sxs-lookup"><span data-stu-id="85875-108">An essential package is the [.NETStandard.Library metapackage](https://www.nuget.org/packages/NETStandard.Library), which is a NuGet package composed of other packages.</span></span> <span data-ttu-id="85875-109">.NET Framework, .NET Core ve Xamarin/Mono gibi birden çok .NET uygulaması üzerinde çalışması garanti edilen paket kümesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="85875-109">It provides you with the set of packages that are guaranteed to work on multiple .NET implementations, such as .NET Framework, .NET Core, and Xamarin/Mono.</span></span>

<span data-ttu-id="85875-110">Ancak, kitaplığınuzun içerdiği her paketi kullanmama olasılığı yüksektir.</span><span class="sxs-lookup"><span data-stu-id="85875-110">However, there's a good chance that your library won't use every single package it contains.</span></span>  <span data-ttu-id="85875-111">Bir kitaplık yazarken ve NuGet üzerinden dağıtırken, bağımlılıklarınızı yalnızca kullandığınız paketlere "kırpmak" en iyi yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="85875-111">When authoring a library and distributing it over NuGet, it's a best practice to "trim" your dependencies down to only the packages you actually use.</span></span>  <span data-ttu-id="85875-112">Bu, NuGet paketleri için daha küçük bir genel ayak izi sağlar.</span><span class="sxs-lookup"><span data-stu-id="85875-112">This results in a smaller overall footprint for NuGet packages.</span></span>

## <a name="how-to-do-it"></a><span data-ttu-id="85875-113">Nasıl yapılacağını</span><span class="sxs-lookup"><span data-stu-id="85875-113">How to do it</span></span>

<span data-ttu-id="85875-114">Şu anda, `dotnet` paket başvurularını kesen resmi bir komut yoktur.</span><span class="sxs-lookup"><span data-stu-id="85875-114">Currently, there is no official `dotnet` command that trims package references.</span></span>  <span data-ttu-id="85875-115">Bunun yerine, el ile yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="85875-115">Instead, you'll have to do it manually.</span></span>  <span data-ttu-id="85875-116">Genel süreç aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="85875-116">The general process looks like the following:</span></span>

1. <span data-ttu-id="85875-117">Bir `NETStandard.Library` `1.6.0` `dependencies` bölümünde referans sürümü `project.json`.</span><span class="sxs-lookup"><span data-stu-id="85875-117">Reference `NETStandard.Library` version `1.6.0` in a `dependencies` section of your `project.json`.</span></span>
2. <span data-ttu-id="85875-118">Paketleri komut `dotnet restore` satırından[(nota bakınız)](#dotnet-restore-note)geri yükleyin.</span><span class="sxs-lookup"><span data-stu-id="85875-118">Restore packages with `dotnet restore` ([see note](#dotnet-restore-note)) from the command line.</span></span>
3. <span data-ttu-id="85875-119">Dosyayı `project.lock.json` inceleyin `NETStandard.Library` ve bölümü bulun.</span><span class="sxs-lookup"><span data-stu-id="85875-119">Inspect the `project.lock.json` file and find the `NETStandard.Library` section.</span></span>  <span data-ttu-id="85875-120">Dosyanın başına yakın.</span><span class="sxs-lookup"><span data-stu-id="85875-120">It's near the beginning of the file.</span></span>
4. <span data-ttu-id="85875-121">Listelenen tüm paketleri aşağıdaki `dependencies`gibi kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="85875-121">Copy all of the listed packages under `dependencies`.</span></span>
5. <span data-ttu-id="85875-122">Başvuruyu `.NETStandard.Library` kaldırın ve kopyalanan paketlerle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="85875-122">Remove the `.NETStandard.Library` reference and replace it with the copied packages.</span></span>
6. <span data-ttu-id="85875-123">İhtiyacınız olmayan paketlere yapılan başvuruları kaldırın.</span><span class="sxs-lookup"><span data-stu-id="85875-123">Remove references to packages you don't need.</span></span>

<span data-ttu-id="85875-124">Hangi paketlere ihtiyacınız olmadığını aşağıdaki yollardan biriyle öğrenebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="85875-124">You can find out which packages you don't need by one of the following ways:</span></span>

1. <span data-ttu-id="85875-125">Deneme yanılma.</span><span class="sxs-lookup"><span data-stu-id="85875-125">Trial and error.</span></span> <span data-ttu-id="85875-126">Bu, bir paketi kaldırmayı, geri toplamayı, kitaplığınızın hala derleyip derlemediğini görmeyi ve bu işlemi yinelemeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="85875-126">This involves removing a package, restoring, seeing if your library still compiles, and repeating this process.</span></span>
2. <span data-ttu-id="85875-127">KODUnuzun gerçekte ne kullandığını görmek için referanslara göz atmak için [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) veya [.NET Reflektör](https://www.red-gate.com/products/dotnet-development/reflector) gibi bir araç kullanmak.</span><span class="sxs-lookup"><span data-stu-id="85875-127">Using a tool such as [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) or [.NET Reflector](https://www.red-gate.com/products/dotnet-development/reflector) to peek at references to see what your code is actually using.</span></span> <span data-ttu-id="85875-128">Ardından, kullandığınız türe uymayan paketleri kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="85875-128">You can then remove packages that don't correspond to types you're using.</span></span>

## <a name="example"></a><span data-ttu-id="85875-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="85875-129">Example</span></span>

<span data-ttu-id="85875-130">Genel koleksiyon türlerine ek işlevsellik sağlayan bir kitaplık yazdığınızı düşünün.</span><span class="sxs-lookup"><span data-stu-id="85875-130">Imagine that you wrote a library that provided additional functionality to generic collection types.</span></span> <span data-ttu-id="85875-131">Böyle bir kitaplığın `System.Collections`, , ancak hiç de. `System.Net.Http`</span><span class="sxs-lookup"><span data-stu-id="85875-131">Such a library would need to depend on packages such as `System.Collections`, but may not at all depend on packages such as `System.Net.Http`.</span></span> <span data-ttu-id="85875-132">Bu nedenle, paket bağımlılıklarını yalnızca bu kütüphanenin gerektirdiği şekilde kırpmak iyi olurdu!</span><span class="sxs-lookup"><span data-stu-id="85875-132">As such, it would be good to trim package dependencies down to only what this library required!</span></span>

<span data-ttu-id="85875-133">Bu kitaplığı kırpmak `project.json` için, dosyayla başlar `NETStandard.Library` `1.6.0`ve sürüme bir başvuru eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="85875-133">To trim this library, you start with the `project.json` file and add a reference to `NETStandard.Library` version `1.6.0`.</span></span>

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

<span data-ttu-id="85875-134">`dotnet restore` Daha sonra, paketleri geri yükleyin ([nota bakınız),](#dotnet-restore-note)dosyayı `project.lock.json` inceler ve tüm paketleri geri `NETStandard.Library`yükleyin.</span><span class="sxs-lookup"><span data-stu-id="85875-134">Next, you restore packages with `dotnet restore` ([see note](#dotnet-restore-note)), inspect the `project.lock.json` file, and find all the packages restored for `NETStandard.Library`.</span></span>

<span data-ttu-id="85875-135">Dosyadaki `project.lock.json` ilgili bölümün hedefleme yaparken nasıl göründüğü `netstandard1.0`aşağıda veda edin:</span><span class="sxs-lookup"><span data-stu-id="85875-135">Here's what the relevant section in the `project.lock.json` file looks like when targeting `netstandard1.0`:</span></span>

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

<span data-ttu-id="85875-136">Ardından, paket başvurularının üzerine `dependencies` kitaplığın `project.json` dosyasının bölümüne kopyalayarak başvuruyu değiştirin: `NETStandard.Library`</span><span class="sxs-lookup"><span data-stu-id="85875-136">Next, copy over the package references into the `dependencies` section of the library's `project.json` file, replacing the `NETStandard.Library` reference:</span></span>

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

<span data-ttu-id="85875-137">Bu paketler, birçoğu kesinlikle toplama türleri genişletmek için gerekli değildir oldukça çok şey var.</span><span class="sxs-lookup"><span data-stu-id="85875-137">That's quite a lot of packages, many of which certainly aren't necessary for extending collection types.</span></span>  <span data-ttu-id="85875-138">Kodunuzu gerçekte hangi paketleri kullandığını belirlemek için paketleri el ile kaldırabilir veya [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) veya [.NET Reflektör](https://www.red-gate.com/products/dotnet-development/reflector/) gibi bir araç kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="85875-138">You can either remove packages manually or use a tool such as [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) or [.NET Reflector](https://www.red-gate.com/products/dotnet-development/reflector/) to identify which packages your code actually uses.</span></span>

<span data-ttu-id="85875-139">Kesilmiş bir paketin nasıl görünebileceği aşağıda açıklanabilir:</span><span class="sxs-lookup"><span data-stu-id="85875-139">Here's what a trimmed package could look like:</span></span>

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

<span data-ttu-id="85875-140">Metapakete bağlı `NETStandard.Library` olduğundan daha küçük bir ayak izi var.</span><span class="sxs-lookup"><span data-stu-id="85875-140">Now, it has a smaller footprint than if it had depended on the `NETStandard.Library` metapackage.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
