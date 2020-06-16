---
title: SLES-.NET Core 'a .NET Core 'u yükler
description: SLES 'e .NET Core SDK ve .NET Core çalışma zamanı yüklemenin çeşitli yollarını gösterir.
author: thraka
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 9816e1f0253be58dc04c1302f334a7ea0b810810
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768410"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-sles"></a><span data-ttu-id="c99ea-103">SLES 'e .NET Core SDK veya .NET Core çalışma zamanı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="c99ea-103">Install .NET Core SDK or .NET Core Runtime on SLES</span></span>

<span data-ttu-id="c99ea-104">.NET Core, SLES 'de desteklenir.</span><span class="sxs-lookup"><span data-stu-id="c99ea-104">.NET Core is supported on SLES.</span></span> <span data-ttu-id="c99ea-105">Bu makalede, SLES 'de .NET Core 'un nasıl yükleneceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="c99ea-105">This article describes how to install .NET Core on SLES.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="supported-distributions"></a><span data-ttu-id="c99ea-106">Desteklenen dağıtımlar</span><span class="sxs-lookup"><span data-stu-id="c99ea-106">Supported distributions</span></span>

<span data-ttu-id="c99ea-107">Aşağıdaki tabloda, hem SLES 12 SP2 hem de SLES 15 üzerinde şu anda desteklenen .NET Core sürümlerinin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c99ea-107">The following table is a list of currently supported .NET Core releases on both SLES 12 SP2 and SLES 15.</span></span> <span data-ttu-id="c99ea-108">Bu sürümler, [.NET Core sürümü destek sonu](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya SLES sürümü artık desteklenene kadar desteklenmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="c99ea-108">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of SLES is no longer supported.</span></span>

- <span data-ttu-id="c99ea-109">✔️, SLES veya .NET Core sürümünün hala desteklendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c99ea-109">A ✔️ indicates that the version of SLES or .NET Core is still supported.</span></span>
- <span data-ttu-id="c99ea-110">Bir ❌ , SLES veya .NET Core sürümünün bu SLES sürümünde desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c99ea-110">A ❌ indicates that the version of SLES or .NET Core isn't supported on that SLES release.</span></span>
- <span data-ttu-id="c99ea-111">SLES ve .NET Core sürümlerinin her ikisi de ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="c99ea-111">When both a version of SLES and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="c99ea-112">SLES</span><span class="sxs-lookup"><span data-stu-id="c99ea-112">SLES</span></span>                   | <span data-ttu-id="c99ea-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="c99ea-113">.NET Core 2.1</span></span> | <span data-ttu-id="c99ea-114">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="c99ea-114">.NET Core 3.1</span></span> | <span data-ttu-id="c99ea-115">.NET 5 Preview (yalnızca el ile yüklenir)</span><span class="sxs-lookup"><span data-stu-id="c99ea-115">.NET 5 Preview (manual install only)</span></span> |
|------------------------|---------------|---------------|----------------|
| <span data-ttu-id="c99ea-116">✔️ [15](#sles-15-)</span><span class="sxs-lookup"><span data-stu-id="c99ea-116">✔️ [15](#sles-15-)</span></span>     | <span data-ttu-id="c99ea-117">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="c99ea-117">✔️ 2.1</span></span>        | <span data-ttu-id="c99ea-118">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="c99ea-118">✔️ 3.1</span></span>        | <span data-ttu-id="c99ea-119">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="c99ea-119">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="c99ea-120">✔️ [12 SP2](#sles-12-)</span><span class="sxs-lookup"><span data-stu-id="c99ea-120">✔️ [12 SP2](#sles-12-)</span></span> | <span data-ttu-id="c99ea-121">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="c99ea-121">✔️ 2.1</span></span>        | <span data-ttu-id="c99ea-122">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="c99ea-122">✔️ 3.1</span></span>        | <span data-ttu-id="c99ea-123">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="c99ea-123">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="c99ea-124">Aşağıdaki .NET Core sürümleri artık desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="c99ea-124">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="c99ea-125">Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:</span><span class="sxs-lookup"><span data-stu-id="c99ea-125">The downloads for these still remain published:</span></span>

- <span data-ttu-id="c99ea-126">3.0</span><span class="sxs-lookup"><span data-stu-id="c99ea-126">3.0</span></span>
- <span data-ttu-id="c99ea-127">2,2</span><span class="sxs-lookup"><span data-stu-id="c99ea-127">2.2</span></span>
- <span data-ttu-id="c99ea-128">2.0</span><span class="sxs-lookup"><span data-stu-id="c99ea-128">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="c99ea-129">Diğer sürümleri nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="c99ea-129">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="sles-15-"></a><span data-ttu-id="c99ea-130">SLES 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="c99ea-130">SLES 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

<span data-ttu-id="c99ea-131">Şu anda, SLES 15 Microsoft Repository kurulum paketi *Microsoft-prod. repo* dosyasını yanlış dizine yüklüyor ve .NET Core paketlerini bulmadan zypper 'yi engellemektedir.</span><span class="sxs-lookup"><span data-stu-id="c99ea-131">Currently, the SLES 15 Microsoft repository setup package installs the *microsoft-prod.repo* file to the wrong directory, preventing zypper from finding the .NET Core packages.</span></span> <span data-ttu-id="c99ea-132">Bu sorunu gidermek için doğru dizinde bir oluşturmaksızın oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c99ea-132">To fix this problem, create a symlink in the correct directory.</span></span>

```bash
sudo ln -s /etc/yum.repos.d/microsoft-prod.repo /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="sles-12-"></a><span data-ttu-id="c99ea-133">SLES 12 ✔️</span><span class="sxs-lookup"><span data-stu-id="c99ea-133">SLES 12 ✔️</span></span>

<span data-ttu-id="c99ea-134">.NET Core, SLES 12 ailesi için en az SP2 gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c99ea-134">.NET Core requires SP2 as a minimum for the SLES 12 family.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="c99ea-135">Paket yöneticisinin sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="c99ea-135">Troubleshoot the package manager</span></span>

<span data-ttu-id="c99ea-136">Bu bölüm, .NET Core 'u yüklemek için Paket Yöneticisi 'ni kullanırken karşılaşabileceğiniz yaygın hatalarla ilgili bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c99ea-136">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="c99ea-137">Getirilemedi</span><span class="sxs-lookup"><span data-stu-id="c99ea-137">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="dependencies"></a><span data-ttu-id="c99ea-138">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="c99ea-138">Dependencies</span></span>

[!INCLUDE [linux-install-dependencies](includes/linux-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="c99ea-139">Komut dosyalı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="c99ea-139">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="c99ea-140">El ile yüklemesi</span><span class="sxs-lookup"><span data-stu-id="c99ea-140">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="c99ea-141">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="c99ea-141">Next steps</span></span>

- [<span data-ttu-id="c99ea-142">Öğretici: Visual Studio Code kullanarak .NET Core SDK bir konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="c99ea-142">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
