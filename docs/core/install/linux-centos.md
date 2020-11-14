---
title: CentOS 'a .NET yüklemesi-.NET
description: .NET SDK ve .NET çalışma zamanının CentOS 'a yüklenmesi için çeşitli yollar gösterir.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: b2ed62d024c6f0d78a4ec64693f1dafeabd8f47b
ms.sourcegitcommit: c38bf879a2611ff46aacdd529b9f2725f93e18a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/13/2020
ms.locfileid: "94594638"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-centos"></a><span data-ttu-id="415e9-103">CentOS 'a .NET SDK veya .NET çalışma zamanı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="415e9-103">Install the .NET SDK or the .NET Runtime on CentOS</span></span>

<span data-ttu-id="415e9-104">.NET, CentOS 'da desteklenir.</span><span class="sxs-lookup"><span data-stu-id="415e9-104">.NET is supported on CentOS.</span></span> <span data-ttu-id="415e9-105">Bu makalede, CentOS 'ta .NET 'in nasıl yükleneceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="415e9-105">This article describes how to install .NET on CentOS.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="415e9-106">Desteklenen dağıtımlar</span><span class="sxs-lookup"><span data-stu-id="415e9-106">Supported distributions</span></span>

<span data-ttu-id="415e9-107">Aşağıdaki tabloda, hem CentOS 7 hem de CentOS 8 ' de şu anda desteklenen .NET sürümlerinin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="415e9-107">The following table is a list of currently supported .NET releases on both CentOS 7 and CentOS 8.</span></span> <span data-ttu-id="415e9-108">Bu sürümler, [.NET sürümü destek sonu](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya CentOS sürümü artık desteklenene kadar desteklenmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="415e9-108">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of CentOS is no longer supported.</span></span>

- <span data-ttu-id="415e9-109">✔️, CentOS veya .NET sürümünün hala desteklendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="415e9-109">A ✔️ indicates that the version of CentOS or .NET is still supported.</span></span>
- <span data-ttu-id="415e9-110">Bir ❌ , CentOS veya .NET sürümünün bu CentOS sürümünde desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="415e9-110">A ❌ indicates that the version of CentOS or .NET isn't supported on that CentOS release.</span></span>
- <span data-ttu-id="415e9-111">Hem CentOS hem de .NET sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="415e9-111">When both a version of CentOS and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="415e9-112">CentOS</span><span class="sxs-lookup"><span data-stu-id="415e9-112">CentOS</span></span>                   | <span data-ttu-id="415e9-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="415e9-113">.NET Core 2.1</span></span> | <span data-ttu-id="415e9-114">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="415e9-114">.NET Core 3.1</span></span> | <span data-ttu-id="415e9-115">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="415e9-115">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="415e9-116">✔️ [8](#centos-8-)</span><span class="sxs-lookup"><span data-stu-id="415e9-116">✔️ [8](#centos-8-)</span></span> | <span data-ttu-id="415e9-117">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="415e9-117">✔️ 2.1</span></span>        | <span data-ttu-id="415e9-118">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="415e9-118">✔️ 3.1</span></span>        | <span data-ttu-id="415e9-119">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="415e9-119">✔️ 5.0</span></span> |
| <span data-ttu-id="415e9-120">✔️ [7](#centos-7-)</span><span class="sxs-lookup"><span data-stu-id="415e9-120">✔️ [7](#centos-7-)</span></span> | <span data-ttu-id="415e9-121">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="415e9-121">✔️ 2.1</span></span>        | <span data-ttu-id="415e9-122">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="415e9-122">✔️ 3.1</span></span>        | <span data-ttu-id="415e9-123">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="415e9-123">✔️ 5.0</span></span> |

<span data-ttu-id="415e9-124">Aşağıdaki .NET sürümleri artık desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="415e9-124">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="415e9-125">Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:</span><span class="sxs-lookup"><span data-stu-id="415e9-125">The downloads for these still remain published:</span></span>

- <span data-ttu-id="415e9-126">3,0</span><span class="sxs-lookup"><span data-stu-id="415e9-126">3.0</span></span>
- <span data-ttu-id="415e9-127">2.2</span><span class="sxs-lookup"><span data-stu-id="415e9-127">2.2</span></span>
- <span data-ttu-id="415e9-128">2,0</span><span class="sxs-lookup"><span data-stu-id="415e9-128">2.0</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="415e9-129">Diğer sürümleri nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="415e9-129">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="centos-8-"></a><span data-ttu-id="415e9-130">CentOS 8 ✔️</span><span class="sxs-lookup"><span data-stu-id="415e9-130">CentOS 8 ✔️</span></span>

> [!TIP]
> <span data-ttu-id="415e9-131">.NET 5,0 henüz varsayılan paket depolarında kullanılamaz, ancak .NET Core 3,1 ' dir.</span><span class="sxs-lookup"><span data-stu-id="415e9-131">.NET 5.0 isn't yet available in the default package repositories, but .NET Core 3.1 is.</span></span> <span data-ttu-id="415e9-132">.NET Core 3,1 yüklemek için, veya gibi `dnf install` uygun Paketle komutunu kullanın `aspnetcore-runtime-3.1` `dotnet-sdk-3.1` .</span><span class="sxs-lookup"><span data-stu-id="415e9-132">To install .NET Core 3.1, use the `dnf install` command with the appropriate package, such as `aspnetcore-runtime-3.1` or `dotnet-sdk-3.1`.</span></span> <span data-ttu-id="415e9-133">Aşağıdaki yönergeler .NET 5,0 içindir.</span><span class="sxs-lookup"><span data-stu-id="415e9-133">The following instructions are for .NET 5.0.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/8/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="centos-7-"></a><span data-ttu-id="415e9-134">CentOS 7 ✔️</span><span class="sxs-lookup"><span data-stu-id="415e9-134">CentOS 7 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-yum-install-50](includes/linux-install-50-yum.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="415e9-135">Paket yöneticisinin sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="415e9-135">Troubleshoot the package manager</span></span>

<span data-ttu-id="415e9-136">Bu bölüm, .NET yüklemek için Paket Yöneticisi 'ni kullanırken karşılaşabileceğiniz yaygın hatalarla ilgili bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="415e9-136">This section provides information on common errors you may get while using the package manager to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="415e9-137">Paket bulunamadı</span><span class="sxs-lookup"><span data-stu-id="415e9-137">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a><span data-ttu-id="415e9-138">Getirilemedi</span><span class="sxs-lookup"><span data-stu-id="415e9-138">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="415e9-139">Bileşenlerinden</span><span class="sxs-lookup"><span data-stu-id="415e9-139">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="415e9-140">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="415e9-140">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="415e9-141">Komut dosyalı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="415e9-141">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="415e9-142">El ile yüklemesi</span><span class="sxs-lookup"><span data-stu-id="415e9-142">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="415e9-143">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="415e9-143">Next steps</span></span>

- [<span data-ttu-id="415e9-144">Öğretici: Visual Studio Code kullanarak .NET SDK ile bir konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="415e9-144">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
