---
title: "Azure için paket Yönetimi F # ile kullanma"
description: "F # Azure bağımlılıkları yönetmek için paket veya Nuget kullanma"
keywords: "Visual f #, f #, işlev, .NET, .NET Core, Azure programlama"
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: dd32ef9c-5416-467e-9fa3-c9ee3bb08456
ms.openlocfilehash: 22dc94ea69e0dfb95e22da4bc64ce915398190d2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="package-management-for-f-azure-dependencies"></a><span data-ttu-id="ea649-104">F # Azure bağımlılıklar için paket Yönetimi</span><span class="sxs-lookup"><span data-stu-id="ea649-104">Package Management for F# Azure Dependencies</span></span>

<span data-ttu-id="ea649-105">Bir paket Yöneticisi'ni kullandığınızda Azure geliştirme için paketleri alma kolaydır.</span><span class="sxs-lookup"><span data-stu-id="ea649-105">Obtaining packages for Azure development is easy when you use a package manager.</span></span> <span data-ttu-id="ea649-106">İki seçenek olan [Paket](https://fsprojects.github.io/Paket/) ve [NuGet](https://www.nuget.org/).</span><span class="sxs-lookup"><span data-stu-id="ea649-106">The two options are [Paket](https://fsprojects.github.io/Paket/) and [NuGet](https://www.nuget.org/).</span></span>

## <a name="using-paket"></a><span data-ttu-id="ea649-107">Paket kullanma</span><span class="sxs-lookup"><span data-stu-id="ea649-107">Using Paket</span></span>

<span data-ttu-id="ea649-108">Kullanıyorsanız, [Paket](https://fsprojects.github.io/Paket/) bağımlılık Yöneticisi olarak, kullandığınız `paket.exe` aracı Azure bağımlılıkları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ea649-108">If you're using [Paket](https://fsprojects.github.io/Paket/) as your dependency manager, you can use the `paket.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="ea649-109">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="ea649-109">For example:</span></span>

    > paket add nuget WindowsAzure.Storage

<span data-ttu-id="ea649-110">Veya kullanıyorsanız, [Mono](http://www.mono-project.com/) platformlar arası .NET geliştirme için:</span><span class="sxs-lookup"><span data-stu-id="ea649-110">Or, if you're using [Mono](http://www.mono-project.com/) for cross-platform .NET development:</span></span>

    > mono paket.exe add nuget WindowsAzure.Storage

<span data-ttu-id="ea649-111">Bu ekler `WindowsAzure.Storage` , geçerli dizin içinde projesi için Paket bağımlılıklarını kümesine değiştirme `paket.dependencies` dosya ve paketini indirin.</span><span class="sxs-lookup"><span data-stu-id="ea649-111">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, modify the `paket.dependencies` file, and download the package.</span></span> <span data-ttu-id="ea649-112">Bağımlılıklarını daha önce ayarlamış veya bağımlılıkları başka bir geliştirici tarafından Burada ayarlanan bir proje üzerinde çalışıyorsanız, çözümlemek ve yerel olarak gibi bağımlılıkları yükler:</span><span class="sxs-lookup"><span data-stu-id="ea649-112">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

    > paket install

<span data-ttu-id="ea649-113">Veya Mono geliştirme için:</span><span class="sxs-lookup"><span data-stu-id="ea649-113">Or, for Mono development:</span></span>

    > mono paket.exe install

<span data-ttu-id="ea649-114">Bu gibi en son sürümü için tüm paket bağımlılıklarını güncelleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ea649-114">You can update all your package dependencies to the latest version like this:</span></span>

    > paket update

<span data-ttu-id="ea649-115">Veya Mono geliştirme için:</span><span class="sxs-lookup"><span data-stu-id="ea649-115">Or, for Mono development:</span></span>

    > mono paket.exe update

## <a name="using-nuget"></a><span data-ttu-id="ea649-116">Nuget kullanma</span><span class="sxs-lookup"><span data-stu-id="ea649-116">Using Nuget</span></span>

<span data-ttu-id="ea649-117">Kullanıyorsanız, [NuGet](https://www.nuget.org/) bağımlılık Yöneticisi olarak, kullandığınız `nuget.exe` aracı Azure bağımlılıkları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ea649-117">If you're using [NuGet](https://www.nuget.org/) as your dependency manager, you can use the `nuget.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="ea649-118">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="ea649-118">For example:</span></span>

    > nuget install WindowsAzure.Storage -ExcludeVersion

<span data-ttu-id="ea649-119">Veya Mono geliştirme için:</span><span class="sxs-lookup"><span data-stu-id="ea649-119">Or, for Mono development:</span></span>

    > mono nuget.exe install WindowsAzure.Storage -ExcludeVersion

<span data-ttu-id="ea649-120">Bu ekler `WindowsAzure.Storage` projesi geçerli dizinde ve indirme paketi için Paket bağımlılıklarını, dizi.</span><span class="sxs-lookup"><span data-stu-id="ea649-120">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, and download the package.</span></span> <span data-ttu-id="ea649-121">Bağımlılıklarını daha önce ayarlamış veya bağımlılıkları başka bir geliştirici tarafından Burada ayarlanan bir proje üzerinde çalışıyorsanız, çözümlemek ve yerel olarak gibi bağımlılıkları yükler:</span><span class="sxs-lookup"><span data-stu-id="ea649-121">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

    > nuget restore 

<span data-ttu-id="ea649-122">Veya Mono geliştirme için:</span><span class="sxs-lookup"><span data-stu-id="ea649-122">Or, for Mono development:</span></span>

    > mono nuget.exe restore

<span data-ttu-id="ea649-123">Bu gibi en son sürümü için tüm paket bağımlılıklarını güncelleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ea649-123">You can update all your package dependencies to the latest version like this:</span></span>

    > nuget update

<span data-ttu-id="ea649-124">Veya Mono geliştirme için:</span><span class="sxs-lookup"><span data-stu-id="ea649-124">Or, for Mono development:</span></span>

    > mono nuget.exe update

## <a name="referencing-assemblies"></a><span data-ttu-id="ea649-125">Başvurulan Derlemeler</span><span class="sxs-lookup"><span data-stu-id="ea649-125">Referencing Assemblies</span></span>

<span data-ttu-id="ea649-126">Kullanarak paketlerinde derlemeleri başvuruda bulunmanız paketlerinizi F # komut dosyanıza kullanmak için bir `#r` yönergesi.</span><span class="sxs-lookup"><span data-stu-id="ea649-126">In order to use your packages in your F# script, you need to reference the assemblies included in the packages using a `#r` directive.</span></span> <span data-ttu-id="ea649-127">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="ea649-127">For example:</span></span>

    > #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"

<span data-ttu-id="ea649-128">Gördüğünüz gibi DLL ve paket adı ile aynı tam olarak olmayabilir tam DLL adı göreli yolunu belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ea649-128">As you can see, you'll need to specify the relative path to the DLL and the full DLL name, which may not be exactly the same as the package name.</span></span> <span data-ttu-id="ea649-129">Yolun framework sürümü ve büyük olasılıkla bir paket sürüm numarasını içerir.</span><span class="sxs-lookup"><span data-stu-id="ea649-129">The path will include a framework version and possibly a package version number.</span></span> <span data-ttu-id="ea649-130">Tüm yüklü derlemelerin bulmak için aşağıdakine benzer bir Windows komut satırında kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ea649-130">To find all the installed assemblies, you can use something like this on a Windows command line:</span></span>

    > cd packages/WindowsAzure.Storage
    > dir /s/b *.dll

<span data-ttu-id="ea649-131">Veya bir UNIX Kabuğu'nda bir şey şöyle:</span><span class="sxs-lookup"><span data-stu-id="ea649-131">Or in a Unix shell, something like this:</span></span>

    > find packages/WindowsAzure.Storage -name "*.dll"

<span data-ttu-id="ea649-132">Bu yüklenmiş derlemeleri yollar sağlar.</span><span class="sxs-lookup"><span data-stu-id="ea649-132">This will give you the paths to the installed assemblies.</span></span> <span data-ttu-id="ea649-133">Buradan, framework sürümünüz için doğru yolu seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ea649-133">From there, you can select the correct path for your framework version.</span></span>
