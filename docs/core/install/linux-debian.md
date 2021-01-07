---
title: .NET ' i dekas 'e yükler-.NET
description: .NET SDK ve .NET çalışma zamanı 'nı de, yüklemenin çeşitli yollarını gösterir.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 913d8bffdd6c0b5e88a70dae0ec4c8d732e80cc0
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970843"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-debian"></a><span data-ttu-id="b4ba7-103">.NET SDK 'sını veya .NET çalışma zamanını depon 'a yükler</span><span class="sxs-lookup"><span data-stu-id="b4ba7-103">Install the .NET SDK or the .NET Runtime on Debian</span></span>

<span data-ttu-id="b4ba7-104">Bu makalede, .NET 'in de, 'da nasıl yükleneceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="b4ba7-104">This article describes how to install .NET on Debian.</span></span> <span data-ttu-id="b4ba7-105">Bir sürüm sürümü destek dışı kaldığında, .NET artık bu sürümde desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="b4ba7-105">When a Debian version falls out of support, .NET is no longer supported with that version.</span></span> <span data-ttu-id="b4ba7-106">Ancak, bu yönergeler desteklenmese de bu sürümler üzerinde çalışan .NET almanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="b4ba7-106">However, these instructions may help you to get .NET running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="b4ba7-107">Desteklenen dağıtımlar</span><span class="sxs-lookup"><span data-stu-id="b4ba7-107">Supported distributions</span></span>

<span data-ttu-id="b4ba7-108">Aşağıdaki tabloda, şu anda desteklenen .NET sürümlerinin ve üzerinde desteklendikleri kaldırıcı sürümlerinin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b4ba7-108">The following table is a list of currently supported .NET releases and the versions of Debian they're supported on.</span></span> <span data-ttu-id="b4ba7-109">Bu sürümler, [.NET sürümü destek sonuna](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya [detem 'un yaşam sonuna](https://wiki.debian.org/DebianReleases)ulaştığı sürece desteklenene kadar desteklenmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="b4ba7-109">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Debian reaches end-of-life](https://wiki.debian.org/DebianReleases).</span></span>

- <span data-ttu-id="b4ba7-110">✔️, deni veya .NET sürümünün hala desteklendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b4ba7-110">A ✔️ indicates that the version of Debian or .NET is still supported.</span></span>
- <span data-ttu-id="b4ba7-111">A ❌ , debir veya .NET sürümünün bu Dey sürümünde desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b4ba7-111">A ❌ indicates that the version of Debian or .NET isn't supported on that Debian release.</span></span>
- <span data-ttu-id="b4ba7-112">Her iki sürümü de ve bir .NET sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="b4ba7-112">When both a version of Debian and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="b4ba7-113">Debian</span><span class="sxs-lookup"><span data-stu-id="b4ba7-113">Debian</span></span>                   | <span data-ttu-id="b4ba7-114">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="b4ba7-114">.NET Core 2.1</span></span> | <span data-ttu-id="b4ba7-115">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="b4ba7-115">.NET Core 3.1</span></span> | <span data-ttu-id="b4ba7-116">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="b4ba7-116">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="b4ba7-117">✔️ [10](#debian-10-)</span><span class="sxs-lookup"><span data-stu-id="b4ba7-117">✔️ [10](#debian-10-)</span></span>     | <span data-ttu-id="b4ba7-118">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="b4ba7-118">✔️ 2.1</span></span>        | <span data-ttu-id="b4ba7-119">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="b4ba7-119">✔️ 3.1</span></span>        | <span data-ttu-id="b4ba7-120">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="b4ba7-120">✔️ 5.0</span></span> |
| <span data-ttu-id="b4ba7-121">✔️ [9](#debian-9-)</span><span class="sxs-lookup"><span data-stu-id="b4ba7-121">✔️ [9](#debian-9-)</span></span>       | <span data-ttu-id="b4ba7-122">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="b4ba7-122">✔️ 2.1</span></span>        | <span data-ttu-id="b4ba7-123">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="b4ba7-123">✔️ 3.1</span></span>        | <span data-ttu-id="b4ba7-124">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="b4ba7-124">✔️ 5.0</span></span> |
| <span data-ttu-id="b4ba7-125">❌ [8](#debian-8-)</span><span class="sxs-lookup"><span data-stu-id="b4ba7-125">❌ [8](#debian-8-)</span></span>       | <span data-ttu-id="b4ba7-126">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="b4ba7-126">✔️ 2.1</span></span>        | <span data-ttu-id="b4ba7-127">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="b4ba7-127">❌ 3.1</span></span>        | <span data-ttu-id="b4ba7-128">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="b4ba7-128">❌ 5.0</span></span> |

<span data-ttu-id="b4ba7-129">Aşağıdaki .NET sürümleri artık desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="b4ba7-129">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="b4ba7-130">Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:</span><span class="sxs-lookup"><span data-stu-id="b4ba7-130">The downloads for these still remain published:</span></span>

- <span data-ttu-id="b4ba7-131">3,0</span><span class="sxs-lookup"><span data-stu-id="b4ba7-131">3.0</span></span>
- <span data-ttu-id="b4ba7-132">2.2</span><span class="sxs-lookup"><span data-stu-id="b4ba7-132">2.2</span></span>
- <span data-ttu-id="b4ba7-133">2.0</span><span class="sxs-lookup"><span data-stu-id="b4ba7-133">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="b4ba7-134">Önizleme sürümlerini Kaldır</span><span class="sxs-lookup"><span data-stu-id="b4ba7-134">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="debian-10-"></a><span data-ttu-id="b4ba7-135">10. ✔️</span><span class="sxs-lookup"><span data-stu-id="b4ba7-135">Debian 10 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/debian/10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="debian-9-"></a><span data-ttu-id="b4ba7-136">De, 9 ✔️</span><span class="sxs-lookup"><span data-stu-id="b4ba7-136">Debian 9 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/9/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="debian-8-"></a><span data-ttu-id="b4ba7-137">Desek8 ❌</span><span class="sxs-lookup"><span data-stu-id="b4ba7-137">Debian 8 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-debian.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/8/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="b4ba7-138">Diğer sürümleri nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="b4ba7-138">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="use-apt-to-update-net"></a><span data-ttu-id="b4ba7-139">.NET 'i güncelleştirmek için APT kullanma</span><span class="sxs-lookup"><span data-stu-id="b4ba7-139">Use APT to update .NET</span></span>

<span data-ttu-id="b4ba7-140">.NET için yeni bir yama yayını varsa, aşağıdaki komutlarla APT aracılığıyla yükseltmeniz yeterlidir:</span><span class="sxs-lookup"><span data-stu-id="b4ba7-140">When a new patch release is available for .NET, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="b4ba7-141">APT sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="b4ba7-141">APT troubleshooting</span></span>

<span data-ttu-id="b4ba7-142">Bu bölümde, .NET yüklemek için APT kullanırken alabileceğiniz yaygın hatalar hakkında bilgi verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b4ba7-142">This section provides information on common errors you may get while using APT to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="b4ba7-143">Paket bulunamadı</span><span class="sxs-lookup"><span data-stu-id="b4ba7-143">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="unable-to-locate--some-packages-could-not-be-installed"></a><span data-ttu-id="b4ba7-144">\\Bazı paketlerin yüklenmesi bulunamıyor</span><span class="sxs-lookup"><span data-stu-id="b4ba7-144">Unable to locate \\ Some packages could not be installed</span></span>

[!INCLUDE [package-manager-failed-to-find-deb](includes/package-manager-failed-to-find-deb.md)]

```bash
sudo apt-get install -y gpg
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/{os-version}/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y {dotnet-package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="b4ba7-145">Getirilemedi</span><span class="sxs-lookup"><span data-stu-id="b4ba7-145">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="dependencies"></a><span data-ttu-id="b4ba7-146">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="b4ba7-146">Dependencies</span></span>

<span data-ttu-id="b4ba7-147">Bir paket yöneticisi ile yüklediğinizde, bu kitaplıklar sizin için yüklenir.</span><span class="sxs-lookup"><span data-stu-id="b4ba7-147">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="b4ba7-148">Ancak, .NET Core 'u el ile yüklüyorsanız veya kendi kendine içerilen bir uygulama yayımlarsanız, bu kitaplıkların yüklü olduğundan emin olmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="b4ba7-148">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="b4ba7-149">libc6</span><span class="sxs-lookup"><span data-stu-id="b4ba7-149">libc6</span></span>
- <span data-ttu-id="b4ba7-150">libgcc1</span><span class="sxs-lookup"><span data-stu-id="b4ba7-150">libgcc1</span></span>
- <span data-ttu-id="b4ba7-151">libgssapı-krb5-2</span><span class="sxs-lookup"><span data-stu-id="b4ba7-151">libgssapi-krb5-2</span></span>
- <span data-ttu-id="b4ba7-152">libicu52 (8. x için)</span><span class="sxs-lookup"><span data-stu-id="b4ba7-152">libicu52 (for 8.x)</span></span>
- <span data-ttu-id="b4ba7-153">libicu57 (9. x için)</span><span class="sxs-lookup"><span data-stu-id="b4ba7-153">libicu57 (for 9.x)</span></span>
- <span data-ttu-id="b4ba7-154">libicu63 (10. x için)</span><span class="sxs-lookup"><span data-stu-id="b4ba7-154">libicu63 (for 10.x)</span></span>
- <span data-ttu-id="b4ba7-155">libicu67 (11. x için)</span><span class="sxs-lookup"><span data-stu-id="b4ba7-155">libicu67 (for 11.x)</span></span>
- <span data-ttu-id="b4ba7-156">libssl 1.0.0 (8. x için)</span><span class="sxs-lookup"><span data-stu-id="b4ba7-156">libssl1.0.0 (for 8.x)</span></span>
- <span data-ttu-id="b4ba7-157">libssl 1.1 (9. x-11. x için)</span><span class="sxs-lookup"><span data-stu-id="b4ba7-157">libssl1.1 (for 9.x-11.x)</span></span>
- <span data-ttu-id="b4ba7-158">libstdc + + 6</span><span class="sxs-lookup"><span data-stu-id="b4ba7-158">libstdc++6</span></span>
- <span data-ttu-id="b4ba7-159">zlib1g</span><span class="sxs-lookup"><span data-stu-id="b4ba7-159">zlib1g</span></span>

<span data-ttu-id="b4ba7-160">*System. Drawing. Common* derlemesini kullanan .NET Core uygulamaları için aşağıdaki bağımlılığa de ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="b4ba7-160">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="b4ba7-161">libgdiplus (sürüm 6.0.1 veya üzeri)</span><span class="sxs-lookup"><span data-stu-id="b4ba7-161">libgdiplus (version 6.0.1 or later)</span></span>

  > [!WARNING]
  > <span data-ttu-id="b4ba7-162">En son bir *libgdiplus* sürümünü sisteminize mono deposunu ekleyerek yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4ba7-162">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="b4ba7-163">Daha fazla bilgi için bkz. <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="b4ba7-163">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b4ba7-164">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="b4ba7-164">Next steps</span></span>

- [<span data-ttu-id="b4ba7-165">.NET CLı için sekme tamamlamayı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="b4ba7-165">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="b4ba7-166">Öğretici: Visual Studio Code kullanarak .NET SDK ile bir konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="b4ba7-166">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
