---
title: OpenSUSE-.NET üzerine .NET 'i yükler
description: OpenSUSE üzerinde .NET SDK ve .NET çalışma zamanı yüklemek için çeşitli yollar gösterir.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: d238054a217a7295594db856d5497982572af377
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873958"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-opensuse"></a><span data-ttu-id="3616e-103">OpenSUSE 'e .NET SDK veya .NET çalışma zamanı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="3616e-103">Install the .NET SDK or the .NET Runtime on openSUSE</span></span>

<span data-ttu-id="3616e-104">.NET, openSUSE 'de desteklenir.</span><span class="sxs-lookup"><span data-stu-id="3616e-104">.NET is supported on openSUSE.</span></span> <span data-ttu-id="3616e-105">Bu makalede, openSUSE 'ta .NET 'in nasıl yükleneceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="3616e-105">This article describes how to install .NET on openSUSE.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="3616e-106">Desteklenen dağıtımlar</span><span class="sxs-lookup"><span data-stu-id="3616e-106">Supported distributions</span></span>

<span data-ttu-id="3616e-107">Aşağıdaki tabloda, openSUSE 15 üzerinde şu anda desteklenen .NET sürümlerinin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3616e-107">The following table is a list of currently supported .NET releases on openSUSE 15.</span></span> <span data-ttu-id="3616e-108">Bu sürümler, [.NET sürümü destek sonu](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya openSUSE sürümü artık desteklenene kadar desteklenmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="3616e-108">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of openSUSE is no longer supported.</span></span>

- <span data-ttu-id="3616e-109">✔️, openSUSE veya .NET sürümünün hala desteklendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3616e-109">A ✔️ indicates that the version of openSUSE or .NET is still supported.</span></span>
- <span data-ttu-id="3616e-110">Bir ❌ , openSUSE veya .NET sürümünün bu openSUSE sürümünde desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3616e-110">A ❌ indicates that the version of openSUSE or .NET isn't supported on that openSUSE release.</span></span>
- <span data-ttu-id="3616e-111">Hem openSUSE hem de .NET sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="3616e-111">When both a version of openSUSE and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="3616e-112">openSUSE</span><span class="sxs-lookup"><span data-stu-id="3616e-112">openSUSE</span></span>                   | <span data-ttu-id="3616e-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="3616e-113">.NET Core 2.1</span></span> | <span data-ttu-id="3616e-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="3616e-114">.NET Core 3.1</span></span> | <span data-ttu-id="3616e-115">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="3616e-115">.NET 5.0</span></span> |
|----------------------------|---------------|---------------|----------------|
| <span data-ttu-id="3616e-116">✔️ [15](#opensuse-15-)</span><span class="sxs-lookup"><span data-stu-id="3616e-116">✔️ [15](#opensuse-15-)</span></span>     | <span data-ttu-id="3616e-117">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="3616e-117">✔️ 2.1</span></span>        | <span data-ttu-id="3616e-118">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="3616e-118">✔️ 3.1</span></span>        | <span data-ttu-id="3616e-119">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="3616e-119">✔️ 5.0</span></span> |

<span data-ttu-id="3616e-120">Aşağıdaki .NET sürümleri artık desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="3616e-120">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="3616e-121">Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:</span><span class="sxs-lookup"><span data-stu-id="3616e-121">The downloads for these still remain published:</span></span>

- <span data-ttu-id="3616e-122">3.0</span><span class="sxs-lookup"><span data-stu-id="3616e-122">3.0</span></span>
- <span data-ttu-id="3616e-123">2,2</span><span class="sxs-lookup"><span data-stu-id="3616e-123">2.2</span></span>
- <span data-ttu-id="3616e-124">2.0</span><span class="sxs-lookup"><span data-stu-id="3616e-124">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="3616e-125">Önizleme sürümlerini Kaldır</span><span class="sxs-lookup"><span data-stu-id="3616e-125">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="opensuse-15-"></a><span data-ttu-id="3616e-126">openSUSE 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="3616e-126">openSUSE 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-50](includes/linux-install-50-zyp.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="3616e-127">Diğer sürümleri nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="3616e-127">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="3616e-128">Paket yöneticisinin sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="3616e-128">Troubleshoot the package manager</span></span>

<span data-ttu-id="3616e-129">Bu bölüm, .NET yüklemek için Paket Yöneticisi 'ni kullanırken karşılaşabileceğiniz yaygın hatalarla ilgili bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="3616e-129">This section provides information on common errors you may get while using the package manager to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="3616e-130">Paket bulunamadı</span><span class="sxs-lookup"><span data-stu-id="3616e-130">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a><span data-ttu-id="3616e-131">Getirilemedi</span><span class="sxs-lookup"><span data-stu-id="3616e-131">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="dependencies"></a><span data-ttu-id="3616e-132">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="3616e-132">Dependencies</span></span>

<span data-ttu-id="3616e-133">Bir paket yöneticisi ile yüklediğinizde, bu kitaplıklar sizin için yüklenir.</span><span class="sxs-lookup"><span data-stu-id="3616e-133">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="3616e-134">Ancak, .NET 'i el ile veya bağımsız bir uygulama yayımladığınızda, bu kitaplıkların yüklü olduğundan emin olmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="3616e-134">But, if you manually install .NET or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="3616e-135">krb5</span><span class="sxs-lookup"><span data-stu-id="3616e-135">krb5</span></span>
- <span data-ttu-id="3616e-136">libıu</span><span class="sxs-lookup"><span data-stu-id="3616e-136">libicu</span></span>
- <span data-ttu-id="3616e-137">libopenssl1_0_0</span><span class="sxs-lookup"><span data-stu-id="3616e-137">libopenssl1_0_0</span></span>

<span data-ttu-id="3616e-138">Hedef çalışma zamanı ortamının OpenSSL sürümü 1,1 veya daha yeniyse, **COMPAT-openssl10** yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3616e-138">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="3616e-139">Bağımlılıklar hakkında daha fazla bilgi için bkz. [kendi Içindeki Linux uygulamaları](https://github.com/dotnet/core/blob/main/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="3616e-139">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/main/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="3616e-140">*System. Drawing. Common* derlemesini kullanan .NET uygulamaları için aşağıdaki bağımlılığa de ihtiyacınız olacaktır:</span><span class="sxs-lookup"><span data-stu-id="3616e-140">For .NET apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="3616e-141">libgdiplus (sürüm 6.0.1 veya üzeri)</span><span class="sxs-lookup"><span data-stu-id="3616e-141">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="3616e-142">En son bir *libgdiplus* sürümünü sisteminize mono deposunu ekleyerek yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3616e-142">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="3616e-143">Daha fazla bilgi için bkz. <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="3616e-143">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3616e-144">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="3616e-144">Next steps</span></span>

- [<span data-ttu-id="3616e-145">.NET CLı için sekme tamamlamayı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="3616e-145">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="3616e-146">Öğretici: Visual Studio Code kullanarak .NET SDK ile bir konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="3616e-146">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
