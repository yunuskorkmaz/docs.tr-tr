---
title: CentOS 'a .NET yüklemesi-.NET
description: .NET SDK ve .NET çalışma zamanının CentOS 'a yüklenmesi için çeşitli yollar gösterir.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 7e73f90a1f1f7e11e592b1b074f243c9f5b32ced
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970869"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-centos"></a><span data-ttu-id="c6305-103">CentOS 'a .NET SDK veya .NET çalışma zamanı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="c6305-103">Install the .NET SDK or the .NET Runtime on CentOS</span></span>

<span data-ttu-id="c6305-104">.NET, CentOS 'da desteklenir.</span><span class="sxs-lookup"><span data-stu-id="c6305-104">.NET is supported on CentOS.</span></span> <span data-ttu-id="c6305-105">Bu makalede, CentOS 'ta .NET 'in nasıl yükleneceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="c6305-105">This article describes how to install .NET on CentOS.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="c6305-106">Desteklenen dağıtımlar</span><span class="sxs-lookup"><span data-stu-id="c6305-106">Supported distributions</span></span>

<span data-ttu-id="c6305-107">Aşağıdaki tabloda, hem CentOS 7 hem de CentOS 8 ' de şu anda desteklenen .NET sürümlerinin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c6305-107">The following table is a list of currently supported .NET releases on both CentOS 7 and CentOS 8.</span></span> <span data-ttu-id="c6305-108">Bu sürümler, [.NET sürümü destek sonu](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya CentOS sürümü artık desteklenene kadar desteklenmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="c6305-108">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of CentOS is no longer supported.</span></span>

- <span data-ttu-id="c6305-109">✔️, CentOS veya .NET sürümünün hala desteklendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c6305-109">A ✔️ indicates that the version of CentOS or .NET is still supported.</span></span>
- <span data-ttu-id="c6305-110">Bir ❌ , CentOS veya .NET sürümünün bu CentOS sürümünde desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6305-110">A ❌ indicates that the version of CentOS or .NET isn't supported on that CentOS release.</span></span>
- <span data-ttu-id="c6305-111">Hem CentOS hem de .NET sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="c6305-111">When both a version of CentOS and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="c6305-112">CentOS</span><span class="sxs-lookup"><span data-stu-id="c6305-112">CentOS</span></span>                   | <span data-ttu-id="c6305-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="c6305-113">.NET Core 2.1</span></span> | <span data-ttu-id="c6305-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="c6305-114">.NET Core 3.1</span></span> | <span data-ttu-id="c6305-115">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="c6305-115">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="c6305-116">✔️ [8](#centos-8-)</span><span class="sxs-lookup"><span data-stu-id="c6305-116">✔️ [8](#centos-8-)</span></span> | <span data-ttu-id="c6305-117">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="c6305-117">✔️ 2.1</span></span>        | <span data-ttu-id="c6305-118">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="c6305-118">✔️ 3.1</span></span>        | <span data-ttu-id="c6305-119">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="c6305-119">✔️ 5.0</span></span> |
| <span data-ttu-id="c6305-120">✔️ [7](#centos-7-)</span><span class="sxs-lookup"><span data-stu-id="c6305-120">✔️ [7](#centos-7-)</span></span> | <span data-ttu-id="c6305-121">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="c6305-121">✔️ 2.1</span></span>        | <span data-ttu-id="c6305-122">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="c6305-122">✔️ 3.1</span></span>        | <span data-ttu-id="c6305-123">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="c6305-123">✔️ 5.0</span></span> |

<span data-ttu-id="c6305-124">Aşağıdaki .NET sürümleri artık desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="c6305-124">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="c6305-125">Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:</span><span class="sxs-lookup"><span data-stu-id="c6305-125">The downloads for these still remain published:</span></span>

- <span data-ttu-id="c6305-126">3,0</span><span class="sxs-lookup"><span data-stu-id="c6305-126">3.0</span></span>
- <span data-ttu-id="c6305-127">2.2</span><span class="sxs-lookup"><span data-stu-id="c6305-127">2.2</span></span>
- <span data-ttu-id="c6305-128">2.0</span><span class="sxs-lookup"><span data-stu-id="c6305-128">2.0</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="remove-preview-versions"></a><span data-ttu-id="c6305-129">Önizleme sürümlerini Kaldır</span><span class="sxs-lookup"><span data-stu-id="c6305-129">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="centos-8-"></a><span data-ttu-id="c6305-130">CentOS 8 ✔️</span><span class="sxs-lookup"><span data-stu-id="c6305-130">CentOS 8 ✔️</span></span>

<span data-ttu-id="c6305-131">.NET 5,0, CentOS 8 için varsayılan paket depolarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c6305-131">.NET 5.0 is available in the default package repositories for CentOS 8.</span></span>

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="centos-7-"></a><span data-ttu-id="c6305-132">CentOS 7 ✔️</span><span class="sxs-lookup"><span data-stu-id="c6305-132">CentOS 7 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-yum-install-50](includes/linux-install-50-yum.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="c6305-133">Diğer sürümleri nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="c6305-133">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="c6305-134">Paket yöneticisinin sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="c6305-134">Troubleshoot the package manager</span></span>

<span data-ttu-id="c6305-135">Bu bölüm, .NET yüklemek için Paket Yöneticisi 'ni kullanırken karşılaşabileceğiniz yaygın hatalarla ilgili bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c6305-135">This section provides information on common errors you may get while using the package manager to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="c6305-136">Paket bulunamadı</span><span class="sxs-lookup"><span data-stu-id="c6305-136">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a><span data-ttu-id="c6305-137">Getirilemedi</span><span class="sxs-lookup"><span data-stu-id="c6305-137">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="dependencies"></a><span data-ttu-id="c6305-138">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="c6305-138">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="next-steps"></a><span data-ttu-id="c6305-139">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="c6305-139">Next steps</span></span>

- [<span data-ttu-id="c6305-140">.NET CLı için sekme tamamlamayı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="c6305-140">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="c6305-141">Öğretici: Visual Studio Code kullanarak .NET SDK ile bir konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="c6305-141">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
