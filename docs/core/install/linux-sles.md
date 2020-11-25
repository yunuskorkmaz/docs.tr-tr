---
title: SLES-.NET ' e .NET yükler
description: SLES 'e .NET SDK ve .NET çalışma zamanı yüklemenin çeşitli yollarını gösterir.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: f351a9b11ab16910963a1db88d88b6949b56ae11
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031806"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-sles"></a><span data-ttu-id="05da8-103">.NET SDK veya .NET çalışma zamanını SLES 'e yükler</span><span class="sxs-lookup"><span data-stu-id="05da8-103">Install the .NET SDK or the .NET Runtime on SLES</span></span>

<span data-ttu-id="05da8-104">.NET, SLES 'de desteklenir.</span><span class="sxs-lookup"><span data-stu-id="05da8-104">.NET is supported on SLES.</span></span> <span data-ttu-id="05da8-105">Bu makalede, SLES 'de .NET yüklemesi açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="05da8-105">This article describes how to install .NET on SLES.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="supported-distributions"></a><span data-ttu-id="05da8-106">Desteklenen dağıtımlar</span><span class="sxs-lookup"><span data-stu-id="05da8-106">Supported distributions</span></span>

<span data-ttu-id="05da8-107">Aşağıdaki tabloda, hem SLES 12 SP2 hem de SLES 15 üzerinde desteklenen .NET sürümlerinin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="05da8-107">The following table is a list of currently supported .NET releases on both SLES 12 SP2 and SLES 15.</span></span> <span data-ttu-id="05da8-108">Bu sürümler, [.NET sürümü destek sonu](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya SLES sürümü artık desteklenene kadar desteklenmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="05da8-108">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of SLES is no longer supported.</span></span>

- <span data-ttu-id="05da8-109">✔️, SLES veya .NET sürümünün hala desteklendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="05da8-109">A ✔️ indicates that the version of SLES or .NET is still supported.</span></span>
- <span data-ttu-id="05da8-110">Bir ❌ , SLES veya .NET sürümünün bu SLES sürümünde desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="05da8-110">A ❌ indicates that the version of SLES or .NET isn't supported on that SLES release.</span></span>
- <span data-ttu-id="05da8-111">Her iki SLES sürümü ve bir .NET sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="05da8-111">When both a version of SLES and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="05da8-112">SLES</span><span class="sxs-lookup"><span data-stu-id="05da8-112">SLES</span></span>                   | <span data-ttu-id="05da8-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="05da8-113">.NET Core 2.1</span></span> | <span data-ttu-id="05da8-114">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="05da8-114">.NET Core 3.1</span></span> | <span data-ttu-id="05da8-115">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="05da8-115">.NET 5.0</span></span> |
|------------------------|---------------|---------------|----------------|
| <span data-ttu-id="05da8-116">✔️ [15](#sles-15-)</span><span class="sxs-lookup"><span data-stu-id="05da8-116">✔️ [15](#sles-15-)</span></span>     | <span data-ttu-id="05da8-117">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="05da8-117">✔️ 2.1</span></span>        | <span data-ttu-id="05da8-118">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="05da8-118">✔️ 3.1</span></span>        | <span data-ttu-id="05da8-119">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="05da8-119">✔️ 5.0</span></span> |
| <span data-ttu-id="05da8-120">✔️ [12 SP2](#sles-12-)</span><span class="sxs-lookup"><span data-stu-id="05da8-120">✔️ [12 SP2](#sles-12-)</span></span> | <span data-ttu-id="05da8-121">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="05da8-121">✔️ 2.1</span></span>        | <span data-ttu-id="05da8-122">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="05da8-122">✔️ 3.1</span></span>        | <span data-ttu-id="05da8-123">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="05da8-123">✔️ 5.0</span></span> |

<span data-ttu-id="05da8-124">Aşağıdaki .NET Core sürümleri artık desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="05da8-124">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="05da8-125">Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:</span><span class="sxs-lookup"><span data-stu-id="05da8-125">The downloads for these still remain published:</span></span>

- <span data-ttu-id="05da8-126">3,0</span><span class="sxs-lookup"><span data-stu-id="05da8-126">3.0</span></span>
- <span data-ttu-id="05da8-127">2.2</span><span class="sxs-lookup"><span data-stu-id="05da8-127">2.2</span></span>
- <span data-ttu-id="05da8-128">2,0</span><span class="sxs-lookup"><span data-stu-id="05da8-128">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="05da8-129">Önizleme sürümlerini Kaldır</span><span class="sxs-lookup"><span data-stu-id="05da8-129">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="05da8-130">Diğer sürümleri nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="05da8-130">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="sles-15-"></a><span data-ttu-id="05da8-131">SLES 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="05da8-131">SLES 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

<span data-ttu-id="05da8-132">Şu anda, SLES 15 Microsoft Repository kurulum paketi *Microsoft-prod. repo* dosyasını yanlış dizine yükleyerek .net paketlerini bulmadan zypper 'yi önler.</span><span class="sxs-lookup"><span data-stu-id="05da8-132">Currently, the SLES 15 Microsoft repository setup package installs the *microsoft-prod.repo* file to the wrong directory, preventing zypper from finding the .NET packages.</span></span> <span data-ttu-id="05da8-133">Bu sorunu gidermek için doğru dizinde bir oluşturmaksızın oluşturun.</span><span class="sxs-lookup"><span data-stu-id="05da8-133">To fix this problem, create a symlink in the correct directory.</span></span>

```bash
sudo ln -s /etc/yum.repos.d/microsoft-prod.repo /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-50](includes/linux-install-50-zyp.md)]

## <a name="sles-12-"></a><span data-ttu-id="05da8-134">SLES 12 ✔️</span><span class="sxs-lookup"><span data-stu-id="05da8-134">SLES 12 ✔️</span></span>

<span data-ttu-id="05da8-135">.NET, SLES 12 ailesi için en düşük düzeyde SP2 gerektirir.</span><span class="sxs-lookup"><span data-stu-id="05da8-135">.NET requires SP2 as a minimum for the SLES 12 family.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-zyp-install-50](includes/linux-install-50-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="05da8-136">Paket yöneticisinin sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="05da8-136">Troubleshoot the package manager</span></span>

<span data-ttu-id="05da8-137">Bu bölüm, .NET yüklemek için Paket Yöneticisi 'ni kullanırken karşılaşabileceğiniz yaygın hatalarla ilgili bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="05da8-137">This section provides information on common errors you may get while using the package manager to install .NET.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="05da8-138">Getirilemedi</span><span class="sxs-lookup"><span data-stu-id="05da8-138">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="dependencies"></a><span data-ttu-id="05da8-139">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="05da8-139">Dependencies</span></span>

<span data-ttu-id="05da8-140">Bir paket yöneticisi ile yüklediğinizde, bu kitaplıklar sizin için yüklenir.</span><span class="sxs-lookup"><span data-stu-id="05da8-140">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="05da8-141">Ancak, .NET 'i el ile veya bağımsız bir uygulama yayımladığınızda, bu kitaplıkların yüklü olduğundan emin olmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="05da8-141">But, if you manually install .NET or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="05da8-142">krb5</span><span class="sxs-lookup"><span data-stu-id="05da8-142">krb5</span></span>
- <span data-ttu-id="05da8-143">libıu</span><span class="sxs-lookup"><span data-stu-id="05da8-143">libicu</span></span>
- <span data-ttu-id="05da8-144">libopenssl1_1</span><span class="sxs-lookup"><span data-stu-id="05da8-144">libopenssl1_1</span></span>

<span data-ttu-id="05da8-145">Hedef çalışma zamanı ortamının OpenSSL sürümü 1,1 veya daha yeniyse, **COMPAT-openssl10** yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="05da8-145">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="05da8-146">Bağımlılıklar hakkında daha fazla bilgi için bkz. [kendi Içindeki Linux uygulamaları](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="05da8-146">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="05da8-147">*System. Drawing. Common* derlemesini kullanan .NET uygulamaları için aşağıdaki bağımlılığa de ihtiyacınız olacaktır:</span><span class="sxs-lookup"><span data-stu-id="05da8-147">For .NET apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="05da8-148">libgdiplus (sürüm 6.0.1 veya üzeri)</span><span class="sxs-lookup"><span data-stu-id="05da8-148">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="05da8-149">En son bir *libgdiplus* sürümünü sisteminize mono deposunu ekleyerek yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05da8-149">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="05da8-150">Daha fazla bilgi için bkz. <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="05da8-150">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="05da8-151">Komut dosyalı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="05da8-151">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="05da8-152">El ile yüklemesi</span><span class="sxs-lookup"><span data-stu-id="05da8-152">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="05da8-153">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="05da8-153">Next steps</span></span>

- [<span data-ttu-id="05da8-154">Öğretici: Visual Studio Code kullanarak .NET SDK ile bir konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="05da8-154">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
