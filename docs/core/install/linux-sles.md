---
title: SLES-.NET Core 'a .NET Core 'u yükler
description: SLES 'e .NET Core SDK ve .NET Core çalışma zamanı yüklemenin çeşitli yollarını gösterir.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 8f64efcc8206b47855871104e5b6914570c06da0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619422"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-sles"></a><span data-ttu-id="ca008-103">SLES 'e .NET Core SDK veya .NET Core çalışma zamanı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="ca008-103">Install .NET Core SDK or .NET Core Runtime on SLES</span></span>

<span data-ttu-id="ca008-104">.NET Core, SLES 'de desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ca008-104">.NET Core is supported on SLES.</span></span> <span data-ttu-id="ca008-105">Bu makalede, SLES 'de .NET Core 'un nasıl yükleneceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="ca008-105">This article describes how to install .NET Core on SLES.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="supported-distributions"></a><span data-ttu-id="ca008-106">Desteklenen dağıtımlar</span><span class="sxs-lookup"><span data-stu-id="ca008-106">Supported distributions</span></span>

<span data-ttu-id="ca008-107">Aşağıdaki tabloda, hem SLES 12 SP2 hem de SLES 15 üzerinde şu anda desteklenen .NET Core sürümlerinin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ca008-107">The following table is a list of currently supported .NET Core releases on both SLES 12 SP2 and SLES 15.</span></span> <span data-ttu-id="ca008-108">Bu sürümler, [.NET Core sürümü destek sonu](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya SLES sürümü artık desteklenene kadar desteklenmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="ca008-108">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of SLES is no longer supported.</span></span>

- <span data-ttu-id="ca008-109">✔️, SLES veya .NET Core sürümünün hala desteklendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ca008-109">A ✔️ indicates that the version of SLES or .NET Core is still supported.</span></span>
- <span data-ttu-id="ca008-110">Bir ❌ , SLES veya .NET Core sürümünün bu SLES sürümünde desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ca008-110">A ❌ indicates that the version of SLES or .NET Core isn't supported on that SLES release.</span></span>
- <span data-ttu-id="ca008-111">SLES ve .NET Core sürümlerinin her ikisi de ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ca008-111">When both a version of SLES and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="ca008-112">SLES</span><span class="sxs-lookup"><span data-stu-id="ca008-112">SLES</span></span>                   | <span data-ttu-id="ca008-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="ca008-113">.NET Core 2.1</span></span> | <span data-ttu-id="ca008-114">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="ca008-114">.NET Core 3.1</span></span> | <span data-ttu-id="ca008-115">.NET 5 Preview (yalnızca el ile yüklenir)</span><span class="sxs-lookup"><span data-stu-id="ca008-115">.NET 5 Preview (manual install only)</span></span> |
|------------------------|---------------|---------------|----------------|
| <span data-ttu-id="ca008-116">✔️ [15](#sles-15-)</span><span class="sxs-lookup"><span data-stu-id="ca008-116">✔️ [15](#sles-15-)</span></span>     | <span data-ttu-id="ca008-117">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="ca008-117">✔️ 2.1</span></span>        | <span data-ttu-id="ca008-118">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="ca008-118">✔️ 3.1</span></span>        | <span data-ttu-id="ca008-119">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="ca008-119">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="ca008-120">✔️ [12 SP2](#sles-12-)</span><span class="sxs-lookup"><span data-stu-id="ca008-120">✔️ [12 SP2](#sles-12-)</span></span> | <span data-ttu-id="ca008-121">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="ca008-121">✔️ 2.1</span></span>        | <span data-ttu-id="ca008-122">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="ca008-122">✔️ 3.1</span></span>        | <span data-ttu-id="ca008-123">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="ca008-123">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="ca008-124">Aşağıdaki .NET Core sürümleri artık desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="ca008-124">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="ca008-125">Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:</span><span class="sxs-lookup"><span data-stu-id="ca008-125">The downloads for these still remain published:</span></span>

- <span data-ttu-id="ca008-126">3.0</span><span class="sxs-lookup"><span data-stu-id="ca008-126">3.0</span></span>
- <span data-ttu-id="ca008-127">2,2</span><span class="sxs-lookup"><span data-stu-id="ca008-127">2.2</span></span>
- <span data-ttu-id="ca008-128">2.0</span><span class="sxs-lookup"><span data-stu-id="ca008-128">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="ca008-129">Diğer sürümleri nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="ca008-129">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="sles-15-"></a><span data-ttu-id="ca008-130">SLES 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="ca008-130">SLES 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

<span data-ttu-id="ca008-131">Şu anda, SLES 15 Microsoft Repository kurulum paketi *Microsoft-prod. repo* dosyasını yanlış dizine yüklüyor ve .NET Core paketlerini bulmadan zypper 'yi engellemektedir.</span><span class="sxs-lookup"><span data-stu-id="ca008-131">Currently, the SLES 15 Microsoft repository setup package installs the *microsoft-prod.repo* file to the wrong directory, preventing zypper from finding the .NET Core packages.</span></span> <span data-ttu-id="ca008-132">Bu sorunu gidermek için doğru dizinde bir oluşturmaksızın oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ca008-132">To fix this problem, create a symlink in the correct directory.</span></span>

```bash
sudo ln -s /etc/yum.repos.d/microsoft-prod.repo /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="sles-12-"></a><span data-ttu-id="ca008-133">SLES 12 ✔️</span><span class="sxs-lookup"><span data-stu-id="ca008-133">SLES 12 ✔️</span></span>

<span data-ttu-id="ca008-134">.NET Core, SLES 12 ailesi için en az SP2 gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ca008-134">.NET Core requires SP2 as a minimum for the SLES 12 family.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="ca008-135">Paket yöneticisinin sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="ca008-135">Troubleshoot the package manager</span></span>

<span data-ttu-id="ca008-136">Bu bölüm, .NET Core 'u yüklemek için Paket Yöneticisi 'ni kullanırken karşılaşabileceğiniz yaygın hatalarla ilgili bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ca008-136">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="ca008-137">Getirilemedi</span><span class="sxs-lookup"><span data-stu-id="ca008-137">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="dependencies"></a><span data-ttu-id="ca008-138">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="ca008-138">Dependencies</span></span>

<span data-ttu-id="ca008-139">Bir paket yöneticisi ile yüklediğinizde, bu kitaplıklar sizin için yüklenir.</span><span class="sxs-lookup"><span data-stu-id="ca008-139">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="ca008-140">Ancak, .NET Core 'u el ile yüklüyorsanız veya kendi kendine içerilen bir uygulama yayımlarsanız, bu kitaplıkların yüklü olduğundan emin olmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="ca008-140">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="ca008-141">krb5</span><span class="sxs-lookup"><span data-stu-id="ca008-141">krb5</span></span>
- <span data-ttu-id="ca008-142">libıu</span><span class="sxs-lookup"><span data-stu-id="ca008-142">libicu</span></span>
- <span data-ttu-id="ca008-143">libopenssl1_1</span><span class="sxs-lookup"><span data-stu-id="ca008-143">libopenssl1_1</span></span>

<span data-ttu-id="ca008-144">Hedef çalışma zamanı ortamının OpenSSL sürümü 1,1 veya daha yeniyse, **COMPAT-openssl10**yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ca008-144">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="ca008-145">Bağımlılıklar hakkında daha fazla bilgi için bkz. [kendi Içindeki Linux uygulamaları](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="ca008-145">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="ca008-146">*System. Drawing. Common* derlemesini kullanan .NET Core uygulamaları için aşağıdaki bağımlılığa de ihtiyacınız olacaktır:</span><span class="sxs-lookup"><span data-stu-id="ca008-146">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="ca008-147">libgdiplus (sürüm 6.0.1 veya üzeri)</span><span class="sxs-lookup"><span data-stu-id="ca008-147">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="ca008-148">En son bir *libgdiplus* sürümünü sisteminize mono deposunu ekleyerek yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca008-148">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="ca008-149">Daha fazla bilgi için bkz. <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="ca008-149">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="ca008-150">Komut dosyalı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="ca008-150">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="ca008-151">El ile yüklemesi</span><span class="sxs-lookup"><span data-stu-id="ca008-151">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="ca008-152">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="ca008-152">Next steps</span></span>

- [<span data-ttu-id="ca008-153">Öğretici: Visual Studio Code kullanarak .NET Core SDK bir konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="ca008-153">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
