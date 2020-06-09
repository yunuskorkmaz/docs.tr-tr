---
title: OpenSUSE-.NET Core 'a .NET Core 'u yükler
description: OpenSUSE üzerinde .NET Core SDK ve .NET Core çalışma zamanı yüklemesinin çeşitli yollarını gösterir.
author: thraka
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: a642cee9ae78f81cd671d8745d5ce241be6a3b69
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84603050"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-opensuse"></a><span data-ttu-id="15295-103">OpenSUSE 'e .NET Core SDK veya .NET Core çalışma zamanı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="15295-103">Install .NET Core SDK or .NET Core Runtime on openSUSE</span></span>

<span data-ttu-id="15295-104">.NET Core, openSUSE 'de desteklenir.</span><span class="sxs-lookup"><span data-stu-id="15295-104">.NET Core is supported on openSUSE.</span></span> <span data-ttu-id="15295-105">Bu makalede, openSUSE üzerinde .NET Core 'un nasıl yükleneceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="15295-105">This article describes how to install .NET Core on openSUSE.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="15295-106">Desteklenen dağıtımlar</span><span class="sxs-lookup"><span data-stu-id="15295-106">Supported distributions</span></span>

<span data-ttu-id="15295-107">Aşağıdaki tabloda, openSUSE 15 üzerinde şu anda desteklenen .NET Core sürümlerinin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="15295-107">The following table is a list of currently supported .NET Core releases on openSUSE 15.</span></span> <span data-ttu-id="15295-108">Bu sürümler, [.NET Core 'un sürümü destek sonuna](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya openSUSE 'un sürümü artık desteklenene kadar desteklenmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="15295-108">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of openSUSE is no longer supported.</span></span>

- <span data-ttu-id="15295-109">✔️, openSUSE veya .NET Core sürümünün hala desteklendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="15295-109">A ✔️ indicates that the version of openSUSE or .NET Core is still supported.</span></span>
- <span data-ttu-id="15295-110">Bir ❌ , openSUSE veya .NET Core sürümünün bu openSUSE sürümünde desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="15295-110">A ❌ indicates that the version of openSUSE or .NET Core isn't supported on that openSUSE release.</span></span>
- <span data-ttu-id="15295-111">Hem openSUSE hem de .NET Core sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="15295-111">When both a version of openSUSE and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="15295-112">openSUSE</span><span class="sxs-lookup"><span data-stu-id="15295-112">openSUSE</span></span>                   | <span data-ttu-id="15295-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="15295-113">.NET Core 2.1</span></span> | <span data-ttu-id="15295-114">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="15295-114">.NET Core 3.1</span></span> | <span data-ttu-id="15295-115">.NET 5 Preview (yalnızca el ile yüklenir)</span><span class="sxs-lookup"><span data-stu-id="15295-115">.NET 5 Preview (manual install only)</span></span> |
|----------------------------|---------------|---------------|----------------|
| <span data-ttu-id="15295-116">✔️ [15](#opensuse-15-)</span><span class="sxs-lookup"><span data-stu-id="15295-116">✔️ [15](#opensuse-15-)</span></span>     | <span data-ttu-id="15295-117">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="15295-117">✔️ 2.1</span></span>        | <span data-ttu-id="15295-118">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="15295-118">✔️ 3.1</span></span>        | <span data-ttu-id="15295-119">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="15295-119">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="15295-120">Aşağıdaki .NET Core sürümleri artık desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="15295-120">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="15295-121">Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:</span><span class="sxs-lookup"><span data-stu-id="15295-121">The downloads for these still remain published:</span></span>

- <span data-ttu-id="15295-122">3.0</span><span class="sxs-lookup"><span data-stu-id="15295-122">3.0</span></span>
- <span data-ttu-id="15295-123">2,2</span><span class="sxs-lookup"><span data-stu-id="15295-123">2.2</span></span>
- <span data-ttu-id="15295-124">2.0</span><span class="sxs-lookup"><span data-stu-id="15295-124">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="15295-125">Diğer sürümleri nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="15295-125">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="opensuse-15-"></a><span data-ttu-id="15295-126">openSUSE 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="15295-126">openSUSE 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="15295-127">Paket yöneticisinin sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="15295-127">Troubleshoot the package manager</span></span>

<span data-ttu-id="15295-128">Bu bölüm, .NET Core 'u yüklemek için Paket Yöneticisi 'ni kullanırken karşılaşabileceğiniz yaygın hatalarla ilgili bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="15295-128">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="15295-129">Getirilemedi</span><span class="sxs-lookup"><span data-stu-id="15295-129">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="15295-130">Bileşenlerinden</span><span class="sxs-lookup"><span data-stu-id="15295-130">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="15295-131">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="15295-131">Dependencies</span></span>

[!INCLUDE [linux-install-dependencies](includes/linux-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="15295-132">Komut dosyalı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="15295-132">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="15295-133">El ile yüklemesi</span><span class="sxs-lookup"><span data-stu-id="15295-133">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="15295-134">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="15295-134">Next steps</span></span>

- [<span data-ttu-id="15295-135">Öğretici: Visual Studio Code kullanarak .NET Core SDK bir konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="15295-135">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
