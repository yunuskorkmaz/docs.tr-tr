---
title: Project. JSON ile paket bağımlılıklarını azaltma
description: Project. JSON tabanlı kitaplıklar yazarken paket bağımlılıklarını azaltın.
author: cartermp
ms.date: 06/20/2016
ms.openlocfilehash: 48ba3ef578388fd98fe7cb830df313512d359483
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740831"
---
# <a name="reducing-package-dependencies-with-projectjson"></a><span data-ttu-id="6557d-103">Project. JSON ile paket bağımlılıklarını azaltma</span><span class="sxs-lookup"><span data-stu-id="6557d-103">Reducing Package Dependencies with project.json</span></span>

<span data-ttu-id="6557d-104">Bu makalede, `project.json` kitaplıklarını yazarken paket bağımlılıklarınızı azaltma hakkında bilmeniz gereken özellikler ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6557d-104">This article covers what you need to know about reducing your package dependencies when authoring `project.json` libraries.</span></span> <span data-ttu-id="6557d-105">Bu makalenin sonuna kadar, kitaplığınızı yalnızca ihtiyaç duyduğunuz bağımlılıkları kullanacak şekilde oluşturmayı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="6557d-105">By the end of this article, you will learn how to compose your library such that it only uses the dependencies it needs.</span></span>

## <a name="why-its-important"></a><span data-ttu-id="6557d-106">Neden önemli</span><span class="sxs-lookup"><span data-stu-id="6557d-106">Why it's Important</span></span>

<span data-ttu-id="6557d-107">.NET Core, NuGet paketlerinden oluşan bir üründür.</span><span class="sxs-lookup"><span data-stu-id="6557d-107">.NET Core is a product made up of NuGet packages.</span></span>  <span data-ttu-id="6557d-108">Temel bir paket [. ](https://www.nuget.org/packages/NETStandard.Library)Diğer paketlerden oluşan bir NuGet paketi olan Netstandart. Library meta paketi.</span><span class="sxs-lookup"><span data-stu-id="6557d-108">An essential package is the [.NETStandard.Library metapackage](https://www.nuget.org/packages/NETStandard.Library), which is a NuGet package composed of other packages.</span></span> <span data-ttu-id="6557d-109">Bu, .NET Framework, .NET Core ve Xamarin/Mono gibi birden çok .NET uygulamasında çalışmak için garanti edilen paket kümesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="6557d-109">It provides you with the set of packages that are guaranteed to work on multiple .NET implementations, such as .NET Framework, .NET Core, and Xamarin/Mono.</span></span>

<span data-ttu-id="6557d-110">Ancak, kitaplığınızın içerdiği her bir paketi kullanması iyi bir şansınız vardır.</span><span class="sxs-lookup"><span data-stu-id="6557d-110">However, there's a good chance that your library won't use every single package it contains.</span></span>  <span data-ttu-id="6557d-111">Bir kitaplığı yazarken ve NuGet üzerinden dağıtırken, bağımlılıklarınızı yalnızca gerçekten kullandığınız paketlere göre "kırpmak" en iyi uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="6557d-111">When authoring a library and distributing it over NuGet, it's a best practice to "trim" your dependencies down to only the packages you actually use.</span></span>  <span data-ttu-id="6557d-112">Bu, NuGet paketleri için daha küçük bir genel parmak izine neden olur.</span><span class="sxs-lookup"><span data-stu-id="6557d-112">This results in a smaller overall footprint for NuGet packages.</span></span>

## <a name="how-to-do-it"></a><span data-ttu-id="6557d-113">Nasıl yapılır</span><span class="sxs-lookup"><span data-stu-id="6557d-113">How to do it</span></span>

<span data-ttu-id="6557d-114">Şu anda paket başvurularını kırpan resmi bir `dotnet` komutu yoktur.</span><span class="sxs-lookup"><span data-stu-id="6557d-114">Currently, there is no official `dotnet` command that trims package references.</span></span>  <span data-ttu-id="6557d-115">Bunun yerine, el ile yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6557d-115">Instead, you'll have to do it manually.</span></span>  <span data-ttu-id="6557d-116">Genel işlem aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="6557d-116">The general process looks like the following:</span></span>

1. <span data-ttu-id="6557d-117">`project.json`bir `dependencies` bölümünde sürüm `1.6.0` başvuru `NETStandard.Library`.</span><span class="sxs-lookup"><span data-stu-id="6557d-117">Reference `NETStandard.Library` version `1.6.0` in a `dependencies` section of your `project.json`.</span></span>
2. <span data-ttu-id="6557d-118">Paketleri, komut satırından `dotnet restore` ([bkz. nota](#dotnet-restore-note)) geri yükleyin.</span><span class="sxs-lookup"><span data-stu-id="6557d-118">Restore packages with `dotnet restore` ([see note](#dotnet-restore-note)) from the command line.</span></span>
3. <span data-ttu-id="6557d-119">`project.lock.json` dosyasını inceleyin ve `NETStandard.Library` bölümünü bulun.</span><span class="sxs-lookup"><span data-stu-id="6557d-119">Inspect the `project.lock.json` file and find the `NETStandard.Library` section.</span></span>  <span data-ttu-id="6557d-120">Bu, dosyanın başlangıcına yakıntı.</span><span class="sxs-lookup"><span data-stu-id="6557d-120">It's near the beginning of the file.</span></span>
4. <span data-ttu-id="6557d-121">Listelenen tüm paketleri `dependencies`altına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="6557d-121">Copy all of the listed packages under `dependencies`.</span></span>
5. <span data-ttu-id="6557d-122">`.NETStandard.Library` başvurusunu kaldırın ve kopyalanmış paketlerle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6557d-122">Remove the `.NETStandard.Library` reference and replace it with the copied packages.</span></span>
6. <span data-ttu-id="6557d-123">İhtiyacınız olmayan paketlere yönelik başvuruları kaldırın.</span><span class="sxs-lookup"><span data-stu-id="6557d-123">Remove references to packages you don't need.</span></span>

<span data-ttu-id="6557d-124">Aşağıdaki yollarla ihtiyacınız olmayan paketleri öğrenebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6557d-124">You can find out which packages you don't need by one of the following ways:</span></span>

1. <span data-ttu-id="6557d-125">Deneme ve hata.</span><span class="sxs-lookup"><span data-stu-id="6557d-125">Trial and error.</span></span> <span data-ttu-id="6557d-126">Bu, bir paketi kaldırmayı, geri yüklemeyi, kitaplığınızın hala derlendiğini görmenizi ve bu işlemi tekrarlamayı içerir.</span><span class="sxs-lookup"><span data-stu-id="6557d-126">This involves removing a package, restoring, seeing if your library still compiles, and repeating this process.</span></span>
2. <span data-ttu-id="6557d-127">Kodunuzun gerçekten kullandığını görmek için başvurularda göz atmayı sağlamak üzere [ılspy](https://github.com/icsharpcode/ILSpy#ilspy-------) veya [.net yansıtıcısı](https://www.red-gate.com/products/dotnet-development/reflector) gibi bir araç kullanma.</span><span class="sxs-lookup"><span data-stu-id="6557d-127">Using a tool such as [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) or [.NET Reflector](https://www.red-gate.com/products/dotnet-development/reflector) to peek at references to see what your code is actually using.</span></span> <span data-ttu-id="6557d-128">Daha sonra, kullanmakta olduğunuz türlere karşılık gelen paketleri kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6557d-128">You can then remove packages that don't correspond to types you're using.</span></span>

## <a name="example"></a><span data-ttu-id="6557d-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="6557d-129">Example</span></span>

<span data-ttu-id="6557d-130">Genel koleksiyon türlerine ek işlevsellik sağlayan bir kitaplık yazdığınızı düşünelim.</span><span class="sxs-lookup"><span data-stu-id="6557d-130">Imagine that you wrote a library that provided additional functionality to generic collection types.</span></span> <span data-ttu-id="6557d-131">Bu tür bir kitaplığın `System.Collections`gibi paketlere bağlı olması gerekir, ancak tümü `System.Net.Http`gibi paketlere bağlı olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="6557d-131">Such a library would need to depend on packages such as `System.Collections`, but may not at all depend on packages such as `System.Net.Http`.</span></span> <span data-ttu-id="6557d-132">Bu nedenle, paket bağımlılıklarını yalnızca bu kitaplıkta gerekli olacak şekilde kırpmak iyi olacaktır!</span><span class="sxs-lookup"><span data-stu-id="6557d-132">As such, it would be good to trim package dependencies down to only what this library required!</span></span>

<span data-ttu-id="6557d-133">Bu kitaplığı kırpmak için `project.json` dosyası ile başlar ve `NETStandard.Library` sürümü `1.6.0`başvurusunu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6557d-133">To trim this library, you start with the `project.json` file and add a reference to `NETStandard.Library` version `1.6.0`.</span></span>

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

<span data-ttu-id="6557d-134">Ardından, paketleri `dotnet restore` ([bkz. nota](#dotnet-restore-note)) geri yükler, `project.lock.json` dosyasını inceleyin ve `NETStandard.Library`için geri yüklenen tüm paketleri bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6557d-134">Next, you restore packages with `dotnet restore` ([see note](#dotnet-restore-note)), inspect the `project.lock.json` file, and find all the packages restored for `NETStandard.Library`.</span></span>

<span data-ttu-id="6557d-135">`project.lock.json` dosyadaki ilgili bölüm, `netstandard1.0`hedefleme sırasında şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="6557d-135">Here's what the relevant section in the `project.lock.json` file looks like when targeting `netstandard1.0`:</span></span>

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

<span data-ttu-id="6557d-136">Sonra, `NETStandard.Library` başvurusunu değiştirerek kitaplığın `project.json` dosyasının `dependencies` bölümüne paket başvurularını kopyalayın:</span><span class="sxs-lookup"><span data-stu-id="6557d-136">Next, copy over the package references into the `dependencies` section of the library's `project.json` file, replacing the `NETStandard.Library` reference:</span></span>

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

<span data-ttu-id="6557d-137">Bu çok sayıda paket, büyük ölçüde koleksiyon türlerini genişletmek için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="6557d-137">That's quite a lot of packages, many of which certainly aren't necessary for extending collection types.</span></span>  <span data-ttu-id="6557d-138">Kodlarınızın gerçekten hangi paketleri kullandığını belirlemek için paketleri el ile kaldırabilir veya [ılspy](https://github.com/icsharpcode/ILSpy#ilspy-------) veya [.net yansıtıcısı](https://www.red-gate.com/products/dotnet-development/reflector/) gibi bir araç kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6557d-138">You can either remove packages manually or use a tool such as [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) or [.NET Reflector](https://www.red-gate.com/products/dotnet-development/reflector/) to identify which packages your code actually uses.</span></span>

<span data-ttu-id="6557d-139">Kırpılmış bir paket şöyle görünebilir:</span><span class="sxs-lookup"><span data-stu-id="6557d-139">Here's what a trimmed package could look like:</span></span>

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

<span data-ttu-id="6557d-140">Şimdi, `NETStandard.Library` metapackage 'e bağımlı olsa da daha küçük bir ayak izine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6557d-140">Now, it has a smaller footprint than if it had depended on the `NETStandard.Library` metapackage.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
