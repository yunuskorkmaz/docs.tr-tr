---
title: Mac üzerinde .NET Core önkoşulları
description: MacOS makinelerinde .NET Core uygulamaları geliştirmek, dağıtmak ve çalıştırmak için desteklenen macOS sürümleri ve .NET Core bağımlılıkları.
author: thraka
ms.author: adegeo
ms.custom: updateeachvsrelease
ms.date: 10/11/2019
ms.openlocfilehash: 2d4fc0b37be08988440325db8b507124c36bf053
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318322"
---
# <a name="prerequisites-for-net-core-on-macos"></a><span data-ttu-id="fe7b0-103">MacOS 'ta .NET Core önkoşulları</span><span class="sxs-lookup"><span data-stu-id="fe7b0-103">Prerequisites for .NET Core on macOS</span></span>

<span data-ttu-id="fe7b0-104">Bu makalede, macOS makinelerinde .NET Core uygulamaları geliştirmek, dağıtmak ve çalıştırmak için ihtiyacınız olan desteklenen macOS sürümleri ve .NET Core bağımlılıkları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fe7b0-104">This article shows you the supported macOS versions and .NET Core dependencies that you need to develop, deploy, and run .NET Core applications on macOS machines.</span></span> <span data-ttu-id="fe7b0-105">Desteklenen işletim sistemi sürümleri ve bağımlılıklar, bir Mac üzerinde .NET Core uygulamaları geliştirmenin üç yolu için geçerlidir: en sevdiğiniz düzenleyici, [Visual Studio Code](https://code.visualstudio.com/)ve [Mac için Visual Studio](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) [ile komut satırı](tutorials/using-with-xplat-cli.md)aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="fe7b0-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on a Mac: via the [command-line with your favorite editor](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/), and [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span>

## <a name="downloads-and-dependencies"></a><span data-ttu-id="fe7b0-106">İndirmeler ve bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="fe7b0-106">Downloads and dependencies</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="fe7b0-107">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="fe7b0-107">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="fe7b0-108">.NET Core 3,0, **MacOS High Sierra (sürüm 10,13)** ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="fe7b0-108">.NET Core 3.0 is supported on **macOS High Sierra (version 10.13)** and later versions.</span></span> <span data-ttu-id="fe7b0-109">**X64** CPU mimarisi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fe7b0-109">A **x64** CPU architecture is required.</span></span>

<span data-ttu-id="fe7b0-110">.NET Core SDK [.NET Core 3,0 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/3.0) sayfasından indirin ve yükleyin.</span><span class="sxs-lookup"><span data-stu-id="fe7b0-110">Download and install the .NET Core SDK from the [.NET Core 3.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.0) page.</span></span> <span data-ttu-id="fe7b0-111">.NET Core 3,0 desteklenen işletim sistemlerinin, dağıtımların ve sürümlerin tamamı, destek SISTEMI sürümlerinden ve yaşam döngüsü ilkesi bağlantılarından 3,0 oluşan tüm liste için [.net core tarafından desteklenen IŞLETIM sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) .</span><span class="sxs-lookup"><span data-stu-id="fe7b0-111">[.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) for the complete list of .NET Core 3.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="fe7b0-112">Bilinen sorunların listesi için bkz. [.NET Core bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-known-issues.md).</span><span class="sxs-lookup"><span data-stu-id="fe7b0-112">For a list of known issues, see [.NET Core known issues](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-known-issues.md).</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="fe7b0-113">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="fe7b0-113">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="fe7b0-114">.NET Core 2,2 **macOS Sierra (sürüm 10,12)** ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="fe7b0-114">.NET Core 2.2 is supported on **macOS Sierra (version 10.12)** and later versions.</span></span> <span data-ttu-id="fe7b0-115">**X64** CPU mimarisi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fe7b0-115">A **x64** CPU architecture is required.</span></span>

<span data-ttu-id="fe7b0-116">.NET Core SDK [.NET Core 2,2 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/2.2) sayfasından indirin ve yükleyin.</span><span class="sxs-lookup"><span data-stu-id="fe7b0-116">Download and install the .NET Core SDK from the [.NET Core 2.2 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.2) page.</span></span> <span data-ttu-id="fe7b0-117">.NET Core 2,2 desteklenen işletim sistemlerinin, dağıtımların ve sürümlerin tamamı, destek SISTEMI sürümlerinden ve yaşam döngüsü ilkesi bağlantılarından 2,2 oluşan tüm liste için [.net core tarafından desteklenen IŞLETIM sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) .</span><span class="sxs-lookup"><span data-stu-id="fe7b0-117">[.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) for the complete list of .NET Core 2.2 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="fe7b0-118">Bilinen sorunların listesi için bkz. [.NET Core bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-known-issues.md).</span><span class="sxs-lookup"><span data-stu-id="fe7b0-118">For a list of known issues, see [.NET Core known issues](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-known-issues.md).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="fe7b0-119">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="fe7b0-119">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="fe7b0-120">.NET Core 2,1 **macOS Sierra (sürüm 10,12)** ve sonraki sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="fe7b0-120">.NET Core 2.1 is supported on **macOS Sierra (version 10.12)** and later versions.</span></span> <span data-ttu-id="fe7b0-121">**X64** CPU mimarisi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fe7b0-121">A **x64** CPU architecture is required.</span></span>

<span data-ttu-id="fe7b0-122">.NET Core SDK [.NET Core 2,1 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/2.1) sayfasından indirin ve yükleyin.</span><span class="sxs-lookup"><span data-stu-id="fe7b0-122">Download and install the .NET Core SDK from the [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1) page.</span></span> <span data-ttu-id="fe7b0-123">.NET Core 2,1 desteklenen işletim sistemlerinin, dağıtımların ve sürümlerin tamamı, destek SISTEMI sürümlerinden ve yaşam döngüsü ilkesi bağlantılarından 2,1 oluşan tüm liste için [.net core tarafından desteklenen IŞLETIM sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) .</span><span class="sxs-lookup"><span data-stu-id="fe7b0-123">[.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) for the complete list of .NET Core 2.1 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="fe7b0-124">Bilinen sorunların listesi için bkz. [.NET Core bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-known-issues.md).</span><span class="sxs-lookup"><span data-stu-id="fe7b0-124">For a list of known issues, see [.NET Core known issues](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-known-issues.md).</span></span>

---

## <a name="libgdiplus"></a><span data-ttu-id="fe7b0-125">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="fe7b0-125">libgdiplus</span></span>

<span data-ttu-id="fe7b0-126">*System. Drawing. Common* derlemesini kullanan .NET Core Uygulamaları, libgdiplus 'in yüklenmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="fe7b0-126">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="fe7b0-127">Libgdiplus almanın kolay bir yolu, macOS için [homebrew ("Brew")](https://brew.sh/) paket yöneticisini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="fe7b0-127">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="fe7b0-128">*Brew*yükledikten sonra, bir Terminal (komut) isteminde aşağıdaki komutları yürüterek libgdiplus yükleme yapın:</span><span class="sxs-lookup"><span data-stu-id="fe7b0-128">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install libgdiplus
```

## <a name="visual-studio-for-mac"></a><span data-ttu-id="fe7b0-129">Mac için Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fe7b0-129">Visual Studio for Mac</span></span>

<span data-ttu-id="fe7b0-130">.NET Core SDK kullanarak .NET Core uygulamaları geliştirmek için herhangi bir düzenleyici kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe7b0-130">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="fe7b0-131">Ancak, tümleşik bir geliştirme ortamında Mac 'te .NET Core uygulamaları geliştirmek istiyorsanız [Mac için Visual Studio](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe7b0-131">However, if you want to develop .NET Core applications on a Mac in an integrated development environment, you can use [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span>
