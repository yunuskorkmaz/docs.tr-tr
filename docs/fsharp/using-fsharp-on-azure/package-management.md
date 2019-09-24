---
title: Azure için ile F# paket yönetimi kullanma
description: Azure bağımlılıklarını yönetmek F# için paket veya NuGet kullanma
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 4aa32ace91f30d0e43b9c40067f5f0f456cc4069
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214219"
---
# <a name="package-management-for-f-azure-dependencies"></a><span data-ttu-id="93b2f-103">F# Azure Bağımlılıkları için Paket Yönetimi</span><span class="sxs-lookup"><span data-stu-id="93b2f-103">Package Management for F# Azure Dependencies</span></span>

<span data-ttu-id="93b2f-104">Paket Yöneticisi kullandığınızda Azure geliştirme için paketleri almak kolaydır.</span><span class="sxs-lookup"><span data-stu-id="93b2f-104">Obtaining packages for Azure development is easy when you use a package manager.</span></span> <span data-ttu-id="93b2f-105">İki seçenek, [paket](https://fsprojects.github.io/Paket/) ve [NuGet](https://www.nuget.org/)' dir.</span><span class="sxs-lookup"><span data-stu-id="93b2f-105">The two options are [Paket](https://fsprojects.github.io/Paket/) and [NuGet](https://www.nuget.org/).</span></span>

## <a name="using-paket"></a><span data-ttu-id="93b2f-106">Paket kullanımı</span><span class="sxs-lookup"><span data-stu-id="93b2f-106">Using Paket</span></span>

<span data-ttu-id="93b2f-107">Bağımlılık yöneticiniz olarak [paket](https://fsprojects.github.io/Paket/) kullanıyorsanız, Azure bağımlılıklarını eklemek için `paket.exe` aracını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="93b2f-107">If you're using [Paket](https://fsprojects.github.io/Paket/) as your dependency manager, you can use the `paket.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="93b2f-108">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="93b2f-108">For example:</span></span>

```console
> paket add nuget WindowsAzure.Storage
```

<span data-ttu-id="93b2f-109">Veya, platformlar arası .NET geliştirme için [mono](https://www.mono-project.com/) kullanıyorsanız:</span><span class="sxs-lookup"><span data-stu-id="93b2f-109">Or, if you're using [Mono](https://www.mono-project.com/) for cross-platform .NET development:</span></span>

```console
> mono paket.exe add nuget WindowsAzure.Storage
```

<span data-ttu-id="93b2f-110">Bu, geçerli `WindowsAzure.Storage` dizindeki proje için paket bağımlılıkları kümesine eklenir, `paket.dependencies` dosyayı değiştirebilir ve paketi indirebilir.</span><span class="sxs-lookup"><span data-stu-id="93b2f-110">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, modify the `paket.dependencies` file, and download the package.</span></span> <span data-ttu-id="93b2f-111">Daha önce bağımlılıkları ayarladıysanız veya başka bir geliştirici tarafından bağımlılıkların ayarlandığı bir proje ile çalışıyorsanız, bağımlılıkları yerel olarak aşağıdaki gibi çözümleyebilir ve yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="93b2f-111">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

```console
> paket install
```

<span data-ttu-id="93b2f-112">Ya da, mono geliştirme için:</span><span class="sxs-lookup"><span data-stu-id="93b2f-112">Or, for Mono development:</span></span>

```console
> mono paket.exe install
```

<span data-ttu-id="93b2f-113">Tüm paket bağımlılıklarınızı şu şekilde en son sürüme güncelleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="93b2f-113">You can update all your package dependencies to the latest version like this:</span></span>

```console
> paket update
```

<span data-ttu-id="93b2f-114">Ya da, mono geliştirme için:</span><span class="sxs-lookup"><span data-stu-id="93b2f-114">Or, for Mono development:</span></span>

```console
> mono paket.exe update
```

## <a name="using-nuget"></a><span data-ttu-id="93b2f-115">NuGet kullanma</span><span class="sxs-lookup"><span data-stu-id="93b2f-115">Using Nuget</span></span>

<span data-ttu-id="93b2f-116">Bağımlılık yöneticiniz olarak [NuGet](https://www.nuget.org/) kullanıyorsanız, `nuget.exe` aracı kullanarak Azure bağımlılıklarını ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="93b2f-116">If you're using [NuGet](https://www.nuget.org/) as your dependency manager, you can use the `nuget.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="93b2f-117">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="93b2f-117">For example:</span></span>

```console
> nuget install WindowsAzure.Storage -ExcludeVersion
```

<span data-ttu-id="93b2f-118">Ya da, mono geliştirme için:</span><span class="sxs-lookup"><span data-stu-id="93b2f-118">Or, for Mono development:</span></span>

```console
> mono nuget.exe install WindowsAzure.Storage -ExcludeVersion
```

<span data-ttu-id="93b2f-119">Bu, geçerli `WindowsAzure.Storage` dizindeki proje için paket bağımlılıkları kümesine ekler ve paketi indirir.</span><span class="sxs-lookup"><span data-stu-id="93b2f-119">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, and download the package.</span></span> <span data-ttu-id="93b2f-120">Daha önce bağımlılıkları ayarladıysanız veya başka bir geliştirici tarafından bağımlılıkların ayarlandığı bir proje ile çalışıyorsanız, bağımlılıkları yerel olarak aşağıdaki gibi çözümleyebilir ve yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="93b2f-120">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

```console
> nuget restore
```

<span data-ttu-id="93b2f-121">Ya da, mono geliştirme için:</span><span class="sxs-lookup"><span data-stu-id="93b2f-121">Or, for Mono development:</span></span>

```console
> mono nuget.exe restore
```

<span data-ttu-id="93b2f-122">Tüm paket bağımlılıklarınızı şu şekilde en son sürüme güncelleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="93b2f-122">You can update all your package dependencies to the latest version like this:</span></span>

```console
> nuget update
```

<span data-ttu-id="93b2f-123">Ya da, mono geliştirme için:</span><span class="sxs-lookup"><span data-stu-id="93b2f-123">Or, for Mono development:</span></span>

```console
> mono nuget.exe update
```

## <a name="referencing-assemblies"></a><span data-ttu-id="93b2f-124">Başvurulan Derlemeler</span><span class="sxs-lookup"><span data-stu-id="93b2f-124">Referencing Assemblies</span></span>

<span data-ttu-id="93b2f-125">F# Komut betiğinizdeki paketleri kullanabilmeniz için, bir `#r` yönergesi kullanarak paketlere dahil olan derlemelere başvurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="93b2f-125">In order to use your packages in your F# script, you need to reference the assemblies included in the packages using a `#r` directive.</span></span> <span data-ttu-id="93b2f-126">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="93b2f-126">For example:</span></span>

```fsharp
> #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"
```

<span data-ttu-id="93b2f-127">Gördüğünüz gibi, DLL için göreli yolu ve tam DLL adını belirtmeniz gerekir. Bu, paket adıyla tam olarak aynı olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="93b2f-127">As you can see, you'll need to specify the relative path to the DLL and the full DLL name, which may not be exactly the same as the package name.</span></span> <span data-ttu-id="93b2f-128">Yol, çerçeve sürümü ve muhtemelen paket sürüm numarası içerecektir.</span><span class="sxs-lookup"><span data-stu-id="93b2f-128">The path will include a framework version and possibly a package version number.</span></span> <span data-ttu-id="93b2f-129">Yüklü tüm derlemeleri bulmak için bir Windows komut satırında şuna benzer bir şey kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="93b2f-129">To find all the installed assemblies, you can use something like this on a Windows command line:</span></span>

```console
> cd packages/WindowsAzure.Storage
> dir /s/b *.dll
```

<span data-ttu-id="93b2f-130">Ya da bir UNIX kabuğunda şuna benzer:</span><span class="sxs-lookup"><span data-stu-id="93b2f-130">Or in a Unix shell, something like this:</span></span>

```console
> find packages/WindowsAzure.Storage -name "*.dll"
```

<span data-ttu-id="93b2f-131">Bu, size yüklü derlemelerin yollarını verecektir.</span><span class="sxs-lookup"><span data-stu-id="93b2f-131">This will give you the paths to the installed assemblies.</span></span> <span data-ttu-id="93b2f-132">Buradan, çerçeve sürümünüz için doğru yolu seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="93b2f-132">From there, you can select the correct path for your framework version.</span></span>
