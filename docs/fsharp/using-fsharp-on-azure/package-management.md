---
title: Paket yönetimi ile kullanarak F# Azure
description: Yönetmek için paket veya Nuget kullanma F# Azure bağımlılıkları
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: fd9c4a15ab0741d44d6d5cf909b7219d310affb0
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "33566983"
---
# <a name="package-management-for-f-azure-dependencies"></a><span data-ttu-id="6a5cc-103">Paket yönetimi için F# Azure bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="6a5cc-103">Package Management for F# Azure Dependencies</span></span>

<span data-ttu-id="6a5cc-104">Bir paket Yöneticisi'ni kullandığınızda, Azure geliştirme için paketler almak kolaydır.</span><span class="sxs-lookup"><span data-stu-id="6a5cc-104">Obtaining packages for Azure development is easy when you use a package manager.</span></span> <span data-ttu-id="6a5cc-105">İki seçenek olan [Paket](https://fsprojects.github.io/Paket/) ve [NuGet](https://www.nuget.org/).</span><span class="sxs-lookup"><span data-stu-id="6a5cc-105">The two options are [Paket](https://fsprojects.github.io/Paket/) and [NuGet](https://www.nuget.org/).</span></span>

## <a name="using-paket"></a><span data-ttu-id="6a5cc-106">Paket kullanma</span><span class="sxs-lookup"><span data-stu-id="6a5cc-106">Using Paket</span></span>

<span data-ttu-id="6a5cc-107">Kullanıyorsanız [Paket](https://fsprojects.github.io/Paket/) bağımlılık Yöneticisi olarak, kullandığınız `paket.exe` aracı Azure bağımlılıkları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6a5cc-107">If you're using [Paket](https://fsprojects.github.io/Paket/) as your dependency manager, you can use the `paket.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="6a5cc-108">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="6a5cc-108">For example:</span></span>

    > paket add nuget WindowsAzure.Storage

<span data-ttu-id="6a5cc-109">Veya kullanıyorsanız [Mono](https://www.mono-project.com/) platformlar arası .NET geliştirme için:</span><span class="sxs-lookup"><span data-stu-id="6a5cc-109">Or, if you're using [Mono](https://www.mono-project.com/) for cross-platform .NET development:</span></span>

    > mono paket.exe add nuget WindowsAzure.Storage

<span data-ttu-id="6a5cc-110">Bu ekler `WindowsAzure.Storage` kümenize paket bağımlılıklarının geçerli dizinde proje için değişiklik `paket.dependencies` dosya ve paketini indirin.</span><span class="sxs-lookup"><span data-stu-id="6a5cc-110">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, modify the `paket.dependencies` file, and download the package.</span></span> <span data-ttu-id="6a5cc-111">Bağımlılıkları daha önce ayarlamış ya da bir proje üzerinde bağımlılıkları başka bir geliştirici tarafından Burada ayarlanan çalışıyorsanız, çözümlemek ve yerel olarak gibi bağımlılıklarını yükleyin:</span><span class="sxs-lookup"><span data-stu-id="6a5cc-111">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

    > paket install

<span data-ttu-id="6a5cc-112">Veya, Mono geliştirme için:</span><span class="sxs-lookup"><span data-stu-id="6a5cc-112">Or, for Mono development:</span></span>

    > mono paket.exe install

<span data-ttu-id="6a5cc-113">Tüm paket bağımlılıklarını, en son sürüme şöyle güncelleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6a5cc-113">You can update all your package dependencies to the latest version like this:</span></span>

    > paket update

<span data-ttu-id="6a5cc-114">Veya, Mono geliştirme için:</span><span class="sxs-lookup"><span data-stu-id="6a5cc-114">Or, for Mono development:</span></span>

    > mono paket.exe update

## <a name="using-nuget"></a><span data-ttu-id="6a5cc-115">Nuget kullanarak</span><span class="sxs-lookup"><span data-stu-id="6a5cc-115">Using Nuget</span></span>

<span data-ttu-id="6a5cc-116">Kullanıyorsanız [NuGet](https://www.nuget.org/) bağımlılık Yöneticisi olarak, kullandığınız `nuget.exe` aracı Azure bağımlılıkları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6a5cc-116">If you're using [NuGet](https://www.nuget.org/) as your dependency manager, you can use the `nuget.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="6a5cc-117">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="6a5cc-117">For example:</span></span>

    > nuget install WindowsAzure.Storage -ExcludeVersion

<span data-ttu-id="6a5cc-118">Veya, Mono geliştirme için:</span><span class="sxs-lookup"><span data-stu-id="6a5cc-118">Or, for Mono development:</span></span>

    > mono nuget.exe install WindowsAzure.Storage -ExcludeVersion

<span data-ttu-id="6a5cc-119">Bu ekler `WindowsAzure.Storage` kümenize proje geçerli dizindeki ve indirme paketi için paket bağımlılıklarının.</span><span class="sxs-lookup"><span data-stu-id="6a5cc-119">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, and download the package.</span></span> <span data-ttu-id="6a5cc-120">Bağımlılıkları daha önce ayarlamış ya da bir proje üzerinde bağımlılıkları başka bir geliştirici tarafından Burada ayarlanan çalışıyorsanız, çözümlemek ve yerel olarak gibi bağımlılıklarını yükleyin:</span><span class="sxs-lookup"><span data-stu-id="6a5cc-120">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

    > nuget restore 

<span data-ttu-id="6a5cc-121">Veya, Mono geliştirme için:</span><span class="sxs-lookup"><span data-stu-id="6a5cc-121">Or, for Mono development:</span></span>

    > mono nuget.exe restore

<span data-ttu-id="6a5cc-122">Tüm paket bağımlılıklarını, en son sürüme şöyle güncelleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6a5cc-122">You can update all your package dependencies to the latest version like this:</span></span>

    > nuget update

<span data-ttu-id="6a5cc-123">Veya, Mono geliştirme için:</span><span class="sxs-lookup"><span data-stu-id="6a5cc-123">Or, for Mono development:</span></span>

    > mono nuget.exe update

## <a name="referencing-assemblies"></a><span data-ttu-id="6a5cc-124">Başvurulan Derlemeler</span><span class="sxs-lookup"><span data-stu-id="6a5cc-124">Referencing Assemblies</span></span>

<span data-ttu-id="6a5cc-125">Paketlerinizi kullanmak için F# komut dosyası için gereksinim duyduğunuz kullanarak paketlerinde derlemelerine bir `#r` yönergesi.</span><span class="sxs-lookup"><span data-stu-id="6a5cc-125">In order to use your packages in your F# script, you need to reference the assemblies included in the packages using a `#r` directive.</span></span> <span data-ttu-id="6a5cc-126">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="6a5cc-126">For example:</span></span>

    > #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"

<span data-ttu-id="6a5cc-127">Gördüğünüz gibi DLL ve paket adı ile aynı tam olarak olmayabilir tam DLL adı göreli yolunu belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6a5cc-127">As you can see, you'll need to specify the relative path to the DLL and the full DLL name, which may not be exactly the same as the package name.</span></span> <span data-ttu-id="6a5cc-128">Yolun bir framework sürümünü ve büyük olasılıkla bir paket sürüm numarası içerir.</span><span class="sxs-lookup"><span data-stu-id="6a5cc-128">The path will include a framework version and possibly a package version number.</span></span> <span data-ttu-id="6a5cc-129">Tüm yüklenmiş derlemeleri bulmak için aşağıdakine benzer bir Windows komut satırında kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6a5cc-129">To find all the installed assemblies, you can use something like this on a Windows command line:</span></span>

    > cd packages/WindowsAzure.Storage
    > dir /s/b *.dll

<span data-ttu-id="6a5cc-130">Bir UNIX Kabuğu'nda bir şey gibi veya bu:</span><span class="sxs-lookup"><span data-stu-id="6a5cc-130">Or in a Unix shell, something like this:</span></span>

    > find packages/WindowsAzure.Storage -name "*.dll"

<span data-ttu-id="6a5cc-131">Bu yüklenen derlemeler için yollar sağlar.</span><span class="sxs-lookup"><span data-stu-id="6a5cc-131">This will give you the paths to the installed assemblies.</span></span> <span data-ttu-id="6a5cc-132">Burada, framework sürümünüz için doğru yol seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6a5cc-132">From there, you can select the correct path for your framework version.</span></span>
