---
title: 'Azure için F # ile Paket Yönetimi kullanma'
description: 'F # Azure bağımlılıklarını yönetmek için paket veya NuGet kullanma'
author: sylvanc
ms.date: 09/20/2016
ms.custom: devx-track-fsharp
ms.openlocfilehash: 7816c82e87db113a35fef967886c8c3e27959332
ms.sourcegitcommit: a8a205034eeffc7c3e1bdd6f506a75b0f7099ebf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91756240"
---
# <a name="package-management-for-f-azure-dependencies"></a><span data-ttu-id="55751-103">F# Azure Bağımlılıkları için Paket Yönetimi</span><span class="sxs-lookup"><span data-stu-id="55751-103">Package Management for F# Azure Dependencies</span></span>

<span data-ttu-id="55751-104">Paket Yöneticisi kullandığınızda Azure geliştirme için paketleri almak kolaydır.</span><span class="sxs-lookup"><span data-stu-id="55751-104">Obtaining packages for Azure development is easy when you use a package manager.</span></span> <span data-ttu-id="55751-105">İki seçenek, [paket](https://fsprojects.github.io/Paket/) ve [NuGet](https://www.nuget.org/)' dir.</span><span class="sxs-lookup"><span data-stu-id="55751-105">The two options are [Paket](https://fsprojects.github.io/Paket/) and [NuGet](https://www.nuget.org/).</span></span>

## <a name="using-paket"></a><span data-ttu-id="55751-106">Paket kullanımı</span><span class="sxs-lookup"><span data-stu-id="55751-106">Using Paket</span></span>

<span data-ttu-id="55751-107">Bağımlılık yöneticiniz olarak [paket](https://fsprojects.github.io/Paket/) kullanıyorsanız, `paket.exe` Azure bağımlılıklarını eklemek için aracını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55751-107">If you're using [Paket](https://fsprojects.github.io/Paket/) as your dependency manager, you can use the `paket.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="55751-108">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="55751-108">For example:</span></span>

```console
> paket add nuget WindowsAzure.Storage
```

<span data-ttu-id="55751-109">Veya, platformlar arası .NET geliştirme için [mono](https://www.mono-project.com/) kullanıyorsanız:</span><span class="sxs-lookup"><span data-stu-id="55751-109">Or, if you're using [Mono](https://www.mono-project.com/) for cross-platform .NET development:</span></span>

```console
> mono paket.exe add nuget WindowsAzure.Storage
```

<span data-ttu-id="55751-110">Bu, `WindowsAzure.Storage` geçerli dizindeki proje için paket bağımlılıkları kümesine eklenir, `paket.dependencies` dosyayı değiştirebilir ve paketi indirebilir.</span><span class="sxs-lookup"><span data-stu-id="55751-110">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, modify the `paket.dependencies` file, and download the package.</span></span> <span data-ttu-id="55751-111">Daha önce bağımlılıkları ayarladıysanız veya başka bir geliştirici tarafından bağımlılıkların ayarlandığı bir proje ile çalışıyorsanız, bağımlılıkları yerel olarak aşağıdaki gibi çözümleyebilir ve yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="55751-111">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

```console
> paket install
```

<span data-ttu-id="55751-112">Ya da, mono geliştirme için:</span><span class="sxs-lookup"><span data-stu-id="55751-112">Or, for Mono development:</span></span>

```console
> mono paket.exe install
```

<span data-ttu-id="55751-113">Tüm paket bağımlılıklarınızı şu şekilde en son sürüme güncelleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="55751-113">You can update all your package dependencies to the latest version like this:</span></span>

```console
> paket update
```

<span data-ttu-id="55751-114">Ya da, mono geliştirme için:</span><span class="sxs-lookup"><span data-stu-id="55751-114">Or, for Mono development:</span></span>

```console
> mono paket.exe update
```

## <a name="using-nuget"></a><span data-ttu-id="55751-115">NuGet kullanma</span><span class="sxs-lookup"><span data-stu-id="55751-115">Using NuGet</span></span>

<span data-ttu-id="55751-116">Bağımlılık yöneticiniz olarak [NuGet](https://www.nuget.org/) kullanıyorsanız, `nuget.exe` aracı kullanarak Azure bağımlılıklarını ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55751-116">If you're using [NuGet](https://www.nuget.org/) as your dependency manager, you can use the `nuget.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="55751-117">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="55751-117">For example:</span></span>

```console
> nuget install WindowsAzure.Storage -ExcludeVersion
```

<span data-ttu-id="55751-118">Ya da, mono geliştirme için:</span><span class="sxs-lookup"><span data-stu-id="55751-118">Or, for Mono development:</span></span>

```console
> mono nuget.exe install WindowsAzure.Storage -ExcludeVersion
```

<span data-ttu-id="55751-119">Bu, `WindowsAzure.Storage` geçerli dizindeki proje için paket bağımlılıkları kümesine ekler ve paketi indirir.</span><span class="sxs-lookup"><span data-stu-id="55751-119">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, and download the package.</span></span> <span data-ttu-id="55751-120">Daha önce bağımlılıkları ayarladıysanız veya başka bir geliştirici tarafından bağımlılıkların ayarlandığı bir proje ile çalışıyorsanız, bağımlılıkları yerel olarak aşağıdaki gibi çözümleyebilir ve yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="55751-120">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

```console
> nuget restore
```

<span data-ttu-id="55751-121">Ya da, mono geliştirme için:</span><span class="sxs-lookup"><span data-stu-id="55751-121">Or, for Mono development:</span></span>

```console
> mono nuget.exe restore
```

<span data-ttu-id="55751-122">Tüm paket bağımlılıklarınızı şu şekilde en son sürüme güncelleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="55751-122">You can update all your package dependencies to the latest version like this:</span></span>

```console
> nuget update
```

<span data-ttu-id="55751-123">Ya da, mono geliştirme için:</span><span class="sxs-lookup"><span data-stu-id="55751-123">Or, for Mono development:</span></span>

```console
> mono nuget.exe update
```

## <a name="referencing-assemblies"></a><span data-ttu-id="55751-124">Başvurulan Derlemeler</span><span class="sxs-lookup"><span data-stu-id="55751-124">Referencing Assemblies</span></span>

<span data-ttu-id="55751-125">Paketlerinizi F # betiğinizdeki kullanabilmeniz için, bir yönergesi kullanarak paketlere dahil olan derlemelere başvurmanız gerekir `#r` .</span><span class="sxs-lookup"><span data-stu-id="55751-125">In order to use your packages in your F# script, you need to reference the assemblies included in the packages using a `#r` directive.</span></span> <span data-ttu-id="55751-126">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="55751-126">For example:</span></span>

```fsharp
> #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"
```

<span data-ttu-id="55751-127">Gördüğünüz gibi, DLL için göreli yolu ve tam DLL adını belirtmeniz gerekir. Bu, paket adıyla tam olarak aynı olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="55751-127">As you can see, you'll need to specify the relative path to the DLL and the full DLL name, which may not be exactly the same as the package name.</span></span> <span data-ttu-id="55751-128">Yol, çerçeve sürümü ve muhtemelen paket sürüm numarası içerecektir.</span><span class="sxs-lookup"><span data-stu-id="55751-128">The path will include a framework version and possibly a package version number.</span></span> <span data-ttu-id="55751-129">Yüklü tüm derlemeleri bulmak için bir Windows komut satırında şuna benzer bir şey kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="55751-129">To find all the installed assemblies, you can use something like this on a Windows command line:</span></span>

```console
> cd packages/WindowsAzure.Storage
> dir /s/b *.dll
```

<span data-ttu-id="55751-130">Ya da bir UNIX kabuğunda şuna benzer:</span><span class="sxs-lookup"><span data-stu-id="55751-130">Or in a Unix shell, something like this:</span></span>

```console
> find packages/WindowsAzure.Storage -name "*.dll"
```

<span data-ttu-id="55751-131">Bu, size yüklü derlemelerin yollarını verecektir.</span><span class="sxs-lookup"><span data-stu-id="55751-131">This will give you the paths to the installed assemblies.</span></span> <span data-ttu-id="55751-132">Buradan, çerçeve sürümünüz için doğru yolu seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55751-132">From there, you can select the correct path for your framework version.</span></span>
