---
title: OpenSUSE-.NET üzerine .NET 'i yükler
description: OpenSUSE üzerinde .NET SDK ve .NET çalışma zamanı yüklemek için çeşitli yollar gösterir.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: eb31e3109ccd40999c22a27607d48544bf117dc2
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031871"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-opensuse"></a><span data-ttu-id="1f01b-103">OpenSUSE 'e .NET SDK veya .NET çalışma zamanı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="1f01b-103">Install the .NET SDK or the .NET Runtime on openSUSE</span></span>

<span data-ttu-id="1f01b-104">.NET, openSUSE 'de desteklenir.</span><span class="sxs-lookup"><span data-stu-id="1f01b-104">.NET is supported on openSUSE.</span></span> <span data-ttu-id="1f01b-105">Bu makalede, openSUSE 'ta .NET 'in nasıl yükleneceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="1f01b-105">This article describes how to install .NET on openSUSE.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="1f01b-106">Desteklenen dağıtımlar</span><span class="sxs-lookup"><span data-stu-id="1f01b-106">Supported distributions</span></span>

<span data-ttu-id="1f01b-107">Aşağıdaki tabloda, openSUSE 15 üzerinde şu anda desteklenen .NET sürümlerinin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1f01b-107">The following table is a list of currently supported .NET releases on openSUSE 15.</span></span> <span data-ttu-id="1f01b-108">Bu sürümler, [.NET sürümü destek sonu](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya openSUSE sürümü artık desteklenene kadar desteklenmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="1f01b-108">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of openSUSE is no longer supported.</span></span>

- <span data-ttu-id="1f01b-109">✔️, openSUSE veya .NET sürümünün hala desteklendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1f01b-109">A ✔️ indicates that the version of openSUSE or .NET is still supported.</span></span>
- <span data-ttu-id="1f01b-110">Bir ❌ , openSUSE veya .NET sürümünün bu openSUSE sürümünde desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1f01b-110">A ❌ indicates that the version of openSUSE or .NET isn't supported on that openSUSE release.</span></span>
- <span data-ttu-id="1f01b-111">Hem openSUSE hem de .NET sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="1f01b-111">When both a version of openSUSE and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="1f01b-112">openSUSE</span><span class="sxs-lookup"><span data-stu-id="1f01b-112">openSUSE</span></span>                   | <span data-ttu-id="1f01b-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="1f01b-113">.NET Core 2.1</span></span> | <span data-ttu-id="1f01b-114">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="1f01b-114">.NET Core 3.1</span></span> | <span data-ttu-id="1f01b-115">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="1f01b-115">.NET 5.0</span></span> |
|----------------------------|---------------|---------------|----------------|
| <span data-ttu-id="1f01b-116">✔️ [15](#opensuse-15-)</span><span class="sxs-lookup"><span data-stu-id="1f01b-116">✔️ [15](#opensuse-15-)</span></span>     | <span data-ttu-id="1f01b-117">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="1f01b-117">✔️ 2.1</span></span>        | <span data-ttu-id="1f01b-118">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="1f01b-118">✔️ 3.1</span></span>        | <span data-ttu-id="1f01b-119">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="1f01b-119">✔️ 5.0</span></span> |

<span data-ttu-id="1f01b-120">Aşağıdaki .NET sürümleri artık desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="1f01b-120">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="1f01b-121">Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:</span><span class="sxs-lookup"><span data-stu-id="1f01b-121">The downloads for these still remain published:</span></span>

- <span data-ttu-id="1f01b-122">3,0</span><span class="sxs-lookup"><span data-stu-id="1f01b-122">3.0</span></span>
- <span data-ttu-id="1f01b-123">2.2</span><span class="sxs-lookup"><span data-stu-id="1f01b-123">2.2</span></span>
- <span data-ttu-id="1f01b-124">2,0</span><span class="sxs-lookup"><span data-stu-id="1f01b-124">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="1f01b-125">Önizleme sürümlerini Kaldır</span><span class="sxs-lookup"><span data-stu-id="1f01b-125">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="1f01b-126">Diğer sürümleri nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="1f01b-126">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="opensuse-15-"></a><span data-ttu-id="1f01b-127">openSUSE 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="1f01b-127">openSUSE 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-50](includes/linux-install-50-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="1f01b-128">Paket yöneticisinin sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="1f01b-128">Troubleshoot the package manager</span></span>

<span data-ttu-id="1f01b-129">Bu bölüm, .NET yüklemek için Paket Yöneticisi 'ni kullanırken karşılaşabileceğiniz yaygın hatalarla ilgili bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="1f01b-129">This section provides information on common errors you may get while using the package manager to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="1f01b-130">Paket bulunamadı</span><span class="sxs-lookup"><span data-stu-id="1f01b-130">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a><span data-ttu-id="1f01b-131">Getirilemedi</span><span class="sxs-lookup"><span data-stu-id="1f01b-131">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="1f01b-132">Bileşenlerinden</span><span class="sxs-lookup"><span data-stu-id="1f01b-132">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="1f01b-133">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="1f01b-133">Dependencies</span></span>

<span data-ttu-id="1f01b-134">Bir paket yöneticisi ile yüklediğinizde, bu kitaplıklar sizin için yüklenir.</span><span class="sxs-lookup"><span data-stu-id="1f01b-134">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="1f01b-135">Ancak, .NET 'i el ile veya bağımsız bir uygulama yayımladığınızda, bu kitaplıkların yüklü olduğundan emin olmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="1f01b-135">But, if you manually install .NET or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="1f01b-136">krb5</span><span class="sxs-lookup"><span data-stu-id="1f01b-136">krb5</span></span>
- <span data-ttu-id="1f01b-137">libıu</span><span class="sxs-lookup"><span data-stu-id="1f01b-137">libicu</span></span>
- <span data-ttu-id="1f01b-138">libopenssl1_0_0</span><span class="sxs-lookup"><span data-stu-id="1f01b-138">libopenssl1_0_0</span></span>

<span data-ttu-id="1f01b-139">Hedef çalışma zamanı ortamının OpenSSL sürümü 1,1 veya daha yeniyse, **COMPAT-openssl10** yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1f01b-139">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="1f01b-140">Bağımlılıklar hakkında daha fazla bilgi için bkz. [kendi Içindeki Linux uygulamaları](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="1f01b-140">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="1f01b-141">*System. Drawing. Common* derlemesini kullanan .NET uygulamaları için aşağıdaki bağımlılığa de ihtiyacınız olacaktır:</span><span class="sxs-lookup"><span data-stu-id="1f01b-141">For .NET apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="1f01b-142">libgdiplus (sürüm 6.0.1 veya üzeri)</span><span class="sxs-lookup"><span data-stu-id="1f01b-142">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="1f01b-143">En son bir *libgdiplus* sürümünü sisteminize mono deposunu ekleyerek yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f01b-143">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="1f01b-144">Daha fazla bilgi için bkz. <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="1f01b-144">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="1f01b-145">Komut dosyalı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="1f01b-145">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="1f01b-146">El ile yüklemesi</span><span class="sxs-lookup"><span data-stu-id="1f01b-146">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="1f01b-147">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="1f01b-147">Next steps</span></span>

- [<span data-ttu-id="1f01b-148">Öğretici: Visual Studio Code kullanarak .NET SDK ile bir konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="1f01b-148">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
