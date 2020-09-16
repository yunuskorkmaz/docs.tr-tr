---
title: OpenSUSE-.NET Core 'a .NET Core 'u yükler
description: OpenSUSE üzerinde .NET Core SDK ve .NET Core çalışma zamanı yüklemesinin çeşitli yollarını gösterir.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: ccdb23ca1838d2c15c9a95b45c8505efe7a6df0e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539236"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-opensuse"></a><span data-ttu-id="3626b-103">OpenSUSE 'e .NET Core SDK veya .NET Core çalışma zamanı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="3626b-103">Install .NET Core SDK or .NET Core Runtime on openSUSE</span></span>

<span data-ttu-id="3626b-104">.NET Core, openSUSE 'de desteklenir.</span><span class="sxs-lookup"><span data-stu-id="3626b-104">.NET Core is supported on openSUSE.</span></span> <span data-ttu-id="3626b-105">Bu makalede, openSUSE üzerinde .NET Core 'un nasıl yükleneceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="3626b-105">This article describes how to install .NET Core on openSUSE.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="3626b-106">Desteklenen dağıtımlar</span><span class="sxs-lookup"><span data-stu-id="3626b-106">Supported distributions</span></span>

<span data-ttu-id="3626b-107">Aşağıdaki tabloda, openSUSE 15 üzerinde şu anda desteklenen .NET Core sürümlerinin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3626b-107">The following table is a list of currently supported .NET Core releases on openSUSE 15.</span></span> <span data-ttu-id="3626b-108">Bu sürümler, [.NET Core 'un sürümü destek sonuna](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya openSUSE 'un sürümü artık desteklenene kadar desteklenmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="3626b-108">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of openSUSE is no longer supported.</span></span>

- <span data-ttu-id="3626b-109">✔️, openSUSE veya .NET Core sürümünün hala desteklendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3626b-109">A ✔️ indicates that the version of openSUSE or .NET Core is still supported.</span></span>
- <span data-ttu-id="3626b-110">Bir ❌ , openSUSE veya .NET Core sürümünün bu openSUSE sürümünde desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3626b-110">A ❌ indicates that the version of openSUSE or .NET Core isn't supported on that openSUSE release.</span></span>
- <span data-ttu-id="3626b-111">Hem openSUSE hem de .NET Core sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="3626b-111">When both a version of openSUSE and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="3626b-112">openSUSE</span><span class="sxs-lookup"><span data-stu-id="3626b-112">openSUSE</span></span>                   | <span data-ttu-id="3626b-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="3626b-113">.NET Core 2.1</span></span> | <span data-ttu-id="3626b-114">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="3626b-114">.NET Core 3.1</span></span> | <span data-ttu-id="3626b-115">.NET 5 Preview (yalnızca el ile yüklenir)</span><span class="sxs-lookup"><span data-stu-id="3626b-115">.NET 5 Preview (manual install only)</span></span> |
|----------------------------|---------------|---------------|----------------|
| <span data-ttu-id="3626b-116">✔️ [15](#opensuse-15-)</span><span class="sxs-lookup"><span data-stu-id="3626b-116">✔️ [15](#opensuse-15-)</span></span>     | <span data-ttu-id="3626b-117">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="3626b-117">✔️ 2.1</span></span>        | <span data-ttu-id="3626b-118">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="3626b-118">✔️ 3.1</span></span>        | <span data-ttu-id="3626b-119">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="3626b-119">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="3626b-120">Aşağıdaki .NET Core sürümleri artık desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="3626b-120">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="3626b-121">Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:</span><span class="sxs-lookup"><span data-stu-id="3626b-121">The downloads for these still remain published:</span></span>

- <span data-ttu-id="3626b-122">3.0</span><span class="sxs-lookup"><span data-stu-id="3626b-122">3.0</span></span>
- <span data-ttu-id="3626b-123">2.2</span><span class="sxs-lookup"><span data-stu-id="3626b-123">2.2</span></span>
- <span data-ttu-id="3626b-124">2.0</span><span class="sxs-lookup"><span data-stu-id="3626b-124">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="3626b-125">Diğer sürümleri nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="3626b-125">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="opensuse-15-"></a><span data-ttu-id="3626b-126">openSUSE 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="3626b-126">openSUSE 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="3626b-127">Paket yöneticisinin sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="3626b-127">Troubleshoot the package manager</span></span>

<span data-ttu-id="3626b-128">Bu bölüm, .NET Core 'u yüklemek için Paket Yöneticisi 'ni kullanırken karşılaşabileceğiniz yaygın hatalarla ilgili bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="3626b-128">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="3626b-129">Paket bulunamadı</span><span class="sxs-lookup"><span data-stu-id="3626b-129">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a><span data-ttu-id="3626b-130">Getirilemedi</span><span class="sxs-lookup"><span data-stu-id="3626b-130">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="3626b-131">Bileşenlerinden</span><span class="sxs-lookup"><span data-stu-id="3626b-131">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="3626b-132">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="3626b-132">Dependencies</span></span>

<span data-ttu-id="3626b-133">Bir paket yöneticisi ile yüklediğinizde, bu kitaplıklar sizin için yüklenir.</span><span class="sxs-lookup"><span data-stu-id="3626b-133">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="3626b-134">Ancak, .NET Core 'u el ile yüklüyorsanız veya kendi kendine içerilen bir uygulama yayımlarsanız, bu kitaplıkların yüklü olduğundan emin olmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="3626b-134">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="3626b-135">krb5</span><span class="sxs-lookup"><span data-stu-id="3626b-135">krb5</span></span>
- <span data-ttu-id="3626b-136">libıu</span><span class="sxs-lookup"><span data-stu-id="3626b-136">libicu</span></span>
- <span data-ttu-id="3626b-137">libopenssl1_0_0</span><span class="sxs-lookup"><span data-stu-id="3626b-137">libopenssl1_0_0</span></span>

<span data-ttu-id="3626b-138">Hedef çalışma zamanı ortamının OpenSSL sürümü 1,1 veya daha yeniyse, **COMPAT-openssl10**yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3626b-138">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="3626b-139">Bağımlılıklar hakkında daha fazla bilgi için bkz. [kendi Içindeki Linux uygulamaları](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="3626b-139">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="3626b-140">*System. Drawing. Common* derlemesini kullanan .NET Core uygulamaları için aşağıdaki bağımlılığa de ihtiyacınız olacaktır:</span><span class="sxs-lookup"><span data-stu-id="3626b-140">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="3626b-141">libgdiplus (sürüm 6.0.1 veya üzeri)</span><span class="sxs-lookup"><span data-stu-id="3626b-141">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="3626b-142">En son bir *libgdiplus* sürümünü sisteminize mono deposunu ekleyerek yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3626b-142">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="3626b-143">Daha fazla bilgi için bkz. <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="3626b-143">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="3626b-144">Komut dosyalı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="3626b-144">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="3626b-145">El ile yüklemesi</span><span class="sxs-lookup"><span data-stu-id="3626b-145">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="3626b-146">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="3626b-146">Next steps</span></span>

- [<span data-ttu-id="3626b-147">Öğretici: Visual Studio Code kullanarak .NET Core SDK bir konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="3626b-147">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
