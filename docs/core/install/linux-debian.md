---
title: .NET Core 'u de, .NET Core 'a yükler
description: .NET Core SDK ve .NET Core çalışma zamanını de, yüklemenin çeşitli yollarını gösterir.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: a9ccc461362b1be3e5bc2ee7d13d5d7d383192e4
ms.sourcegitcommit: 2560a355c76b0a04cba0d34da870df9ad94ceca3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2020
ms.locfileid: "89053164"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-debian"></a><span data-ttu-id="cfc63-103">.NET Core SDK veya .NET Core çalışma zamanını Demerkezi üzerine yükler</span><span class="sxs-lookup"><span data-stu-id="cfc63-103">Install .NET Core SDK or .NET Core Runtime on Debian</span></span>

<span data-ttu-id="cfc63-104">Bu makalede, .NET Core 'un Dezimmetli üzerinde nasıl yükleneceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="cfc63-104">This article describes how to install .NET Core on Debian.</span></span> <span data-ttu-id="cfc63-105">Bir sürüm sürümü destek dışı kaldığında, .NET Core artık bu sürümle desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="cfc63-105">When a Debian version falls out of support, .NET Core is no longer supported with that version.</span></span> <span data-ttu-id="cfc63-106">Ancak, bu yönergeler desteklenmese de, bu sürümler üzerinde çalışan .NET Core 'u almanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="cfc63-106">However, these instructions may help you to get .NET Core running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="cfc63-107">Desteklenen dağıtımlar</span><span class="sxs-lookup"><span data-stu-id="cfc63-107">Supported distributions</span></span>

<span data-ttu-id="cfc63-108">Aşağıdaki tabloda, şu anda desteklenen .NET Core sürümlerinin ve üzerinde desteklendikleri kaldırıcı sürümlerinin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cfc63-108">The following table is a list of currently supported .NET Core releases and the versions of Debian they're supported on.</span></span> <span data-ttu-id="cfc63-109">Bu sürümler, [.NET Core 'un sürümü destek sonuna ulaşıncaya](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya [detem 'ın kullanım ömrü sona](https://wiki.debian.org/DebianReleases)erecek kadar desteklenmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="cfc63-109">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Debian reaches end-of-life](https://wiki.debian.org/DebianReleases).</span></span>

- <span data-ttu-id="cfc63-110">✔️, debir veya .NET Core sürümünün hala desteklendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="cfc63-110">A ✔️ indicates that the version of Debian or .NET Core is still supported.</span></span>
- <span data-ttu-id="cfc63-111">A ❌ , debir veya .NET Core sürümünün bu Dey sürümünde desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cfc63-111">A ❌ indicates that the version of Debian or .NET Core isn't supported on that Debian release.</span></span>
- <span data-ttu-id="cfc63-112">Her iki sürüm de bir .NET Core sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="cfc63-112">When both a version of Debian and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="cfc63-113">Debian</span><span class="sxs-lookup"><span data-stu-id="cfc63-113">Debian</span></span>                   | <span data-ttu-id="cfc63-114">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="cfc63-114">.NET Core 2.1</span></span> | <span data-ttu-id="cfc63-115">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="cfc63-115">.NET Core 3.1</span></span> | <span data-ttu-id="cfc63-116">.NET 5 Preview (yalnızca el ile yüklenir)</span><span class="sxs-lookup"><span data-stu-id="cfc63-116">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="cfc63-117">✔️ [10](#debian-10-)</span><span class="sxs-lookup"><span data-stu-id="cfc63-117">✔️ [10](#debian-10-)</span></span>     | <span data-ttu-id="cfc63-118">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="cfc63-118">✔️ 2.1</span></span>        | <span data-ttu-id="cfc63-119">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="cfc63-119">✔️ 3.1</span></span>        | <span data-ttu-id="cfc63-120">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="cfc63-120">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="cfc63-121">✔️ [9](#debian-9-)</span><span class="sxs-lookup"><span data-stu-id="cfc63-121">✔️ [9](#debian-9-)</span></span>       | <span data-ttu-id="cfc63-122">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="cfc63-122">✔️ 2.1</span></span>        | <span data-ttu-id="cfc63-123">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="cfc63-123">✔️ 3.1</span></span>        | <span data-ttu-id="cfc63-124">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="cfc63-124">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="cfc63-125">❌ [8](#debian-8-)</span><span class="sxs-lookup"><span data-stu-id="cfc63-125">❌ [8](#debian-8-)</span></span>       | <span data-ttu-id="cfc63-126">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="cfc63-126">✔️ 2.1</span></span>        | <span data-ttu-id="cfc63-127">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="cfc63-127">❌ 3.1</span></span>        | <span data-ttu-id="cfc63-128">❌ 5,0 Önizleme</span><span class="sxs-lookup"><span data-stu-id="cfc63-128">❌ 5.0 Preview</span></span> |

<span data-ttu-id="cfc63-129">Aşağıdaki .NET Core sürümleri artık desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="cfc63-129">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="cfc63-130">Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:</span><span class="sxs-lookup"><span data-stu-id="cfc63-130">The downloads for these still remain published:</span></span>

- <span data-ttu-id="cfc63-131">3.0</span><span class="sxs-lookup"><span data-stu-id="cfc63-131">3.0</span></span>
- <span data-ttu-id="cfc63-132">2.2</span><span class="sxs-lookup"><span data-stu-id="cfc63-132">2.2</span></span>
- <span data-ttu-id="cfc63-133">2.0</span><span class="sxs-lookup"><span data-stu-id="cfc63-133">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="cfc63-134">Diğer sürümleri nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="cfc63-134">How to install other versions</span></span>

[!INCLUDE [hack-pkgname](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="debian-10-"></a><span data-ttu-id="cfc63-135">10. ✔️</span><span class="sxs-lookup"><span data-stu-id="cfc63-135">Debian 10 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/debian/10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="debian-9-"></a><span data-ttu-id="cfc63-136">De, 9 ✔️</span><span class="sxs-lookup"><span data-stu-id="cfc63-136">Debian 9 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/9/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="debian-8-"></a><span data-ttu-id="cfc63-137">Desek8 ❌</span><span class="sxs-lookup"><span data-stu-id="cfc63-137">Debian 8 ❌</span></span>

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

## <a name="apt-update-sdk-or-runtime"></a><span data-ttu-id="cfc63-138">APT güncelleştirme SDK 'Sı veya çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="cfc63-138">APT update SDK or runtime</span></span>

<span data-ttu-id="cfc63-139">.NET Core için yeni bir yama yayını varsa, aşağıdaki komutlarla APT aracılığıyla yükseltmeniz yeterlidir:</span><span class="sxs-lookup"><span data-stu-id="cfc63-139">When a new patch release is available for .NET Core, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="cfc63-140">APT sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="cfc63-140">APT troubleshooting</span></span>

<span data-ttu-id="cfc63-141">Bu bölümde, .NET Core 'u yüklemek için APT kullanırken karşılaşabileceğiniz yaygın hatalar hakkında bilgi verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cfc63-141">This section provides information on common errors you may get while using APT to install .NET Core.</span></span>

### <a name="unable-to-locate"></a><span data-ttu-id="cfc63-142">Bulunamıyor</span><span class="sxs-lookup"><span data-stu-id="cfc63-142">Unable to locate</span></span>

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

### <a name="failed-to-fetch"></a><span data-ttu-id="cfc63-143">Getirilemedi</span><span class="sxs-lookup"><span data-stu-id="cfc63-143">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="snap"></a><span data-ttu-id="cfc63-144">Bileşenlerinden</span><span class="sxs-lookup"><span data-stu-id="cfc63-144">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="cfc63-145">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="cfc63-145">Dependencies</span></span>

<span data-ttu-id="cfc63-146">Bir paket yöneticisi ile yüklediğinizde, bu kitaplıklar sizin için yüklenir.</span><span class="sxs-lookup"><span data-stu-id="cfc63-146">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="cfc63-147">Ancak, .NET Core 'u el ile yüklüyorsanız veya kendi kendine içerilen bir uygulama yayımlarsanız, bu kitaplıkların yüklü olduğundan emin olmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="cfc63-147">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="cfc63-148">libc6</span><span class="sxs-lookup"><span data-stu-id="cfc63-148">libc6</span></span>
- <span data-ttu-id="cfc63-149">libgcc1</span><span class="sxs-lookup"><span data-stu-id="cfc63-149">libgcc1</span></span>
- <span data-ttu-id="cfc63-150">libgssapı-krb5-2</span><span class="sxs-lookup"><span data-stu-id="cfc63-150">libgssapi-krb5-2</span></span>
- <span data-ttu-id="cfc63-151">libicu52 (8. x için)</span><span class="sxs-lookup"><span data-stu-id="cfc63-151">libicu52 (for 8.x)</span></span>
- <span data-ttu-id="cfc63-152">libicu57 (9. x için)</span><span class="sxs-lookup"><span data-stu-id="cfc63-152">libicu57 (for 9.x)</span></span>
- <span data-ttu-id="cfc63-153">libicu63 (10. x için)</span><span class="sxs-lookup"><span data-stu-id="cfc63-153">libicu63 (for 10.x)</span></span>
- <span data-ttu-id="cfc63-154">libicu67 (11. x için)</span><span class="sxs-lookup"><span data-stu-id="cfc63-154">libicu67 (for 11.x)</span></span>
- <span data-ttu-id="cfc63-155">libssl 1.0.0 (8. x için)</span><span class="sxs-lookup"><span data-stu-id="cfc63-155">libssl1.0.0 (for 8.x)</span></span>
- <span data-ttu-id="cfc63-156">libssl 1.1 (9. x-11. x için)</span><span class="sxs-lookup"><span data-stu-id="cfc63-156">libssl1.1 (for 9.x-11.x)</span></span>
- <span data-ttu-id="cfc63-157">libstdc + + 6</span><span class="sxs-lookup"><span data-stu-id="cfc63-157">libstdc++6</span></span>
- <span data-ttu-id="cfc63-158">zlib1g</span><span class="sxs-lookup"><span data-stu-id="cfc63-158">zlib1g</span></span>

<span data-ttu-id="cfc63-159">*System. Drawing. Common* derlemesini kullanan .NET Core uygulamaları için aşağıdaki bağımlılığa de ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="cfc63-159">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="cfc63-160">libgdiplus (sürüm 6.0.1 veya üzeri)</span><span class="sxs-lookup"><span data-stu-id="cfc63-160">libgdiplus (version 6.0.1 or later)</span></span>

  > [!WARNING]
  > <span data-ttu-id="cfc63-161">En son bir *libgdiplus* sürümünü sisteminize mono deposunu ekleyerek yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cfc63-161">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="cfc63-162">Daha fazla bilgi için bkz. <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="cfc63-162">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="cfc63-163">Komut dosyalı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="cfc63-163">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="cfc63-164">El ile yüklemesi</span><span class="sxs-lookup"><span data-stu-id="cfc63-164">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="cfc63-165">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="cfc63-165">Next steps</span></span>

- [<span data-ttu-id="cfc63-166">Öğretici: Visual Studio Code kullanarak .NET Core SDK bir konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="cfc63-166">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
