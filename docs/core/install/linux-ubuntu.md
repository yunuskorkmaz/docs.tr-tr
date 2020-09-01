---
title: Ubuntu-.NET Core 'a .NET Core 'u yükler
description: Ubuntu üzerinde .NET Core SDK ve .NET Core çalışma zamanı yüklemenin çeşitli yollarını gösterir.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 9694dac719024264edee849044f048970b63b7b7
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89132955"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-ubuntu"></a><span data-ttu-id="e22d7-103">Ubuntu üzerinde .NET Core SDK veya .NET Core çalışma zamanı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="e22d7-103">Install .NET Core SDK or .NET Core Runtime on Ubuntu</span></span>

<span data-ttu-id="e22d7-104">.NET Core, Ubuntu 'da desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e22d7-104">.NET Core is supported on Ubuntu.</span></span> <span data-ttu-id="e22d7-105">Bu makalede, Ubuntu 'da .NET Core 'un nasıl yükleneceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="e22d7-105">This article describes how to install .NET Core on Ubuntu.</span></span> <span data-ttu-id="e22d7-106">Ubuntu sürümü destek dışı kaldığında, .NET Core artık bu sürümde desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="e22d7-106">When an Ubuntu version falls out of support, .NET Core is no longer supported with that version.</span></span> <span data-ttu-id="e22d7-107">Ancak, bu yönergeler desteklenmese de, bu sürümler üzerinde çalışan .NET Core 'u almanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e22d7-107">However, these instructions may help you to get .NET Core running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="e22d7-108">Desteklenen dağıtımlar</span><span class="sxs-lookup"><span data-stu-id="e22d7-108">Supported distributions</span></span>

<span data-ttu-id="e22d7-109">Aşağıdaki tabloda, şu anda desteklenen .NET Core sürümlerinin ve üzerinde desteklendikleri Ubuntu sürümlerinin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e22d7-109">The following table is a list of currently supported .NET Core releases and the versions of Ubuntu they're supported on.</span></span> <span data-ttu-id="e22d7-110">[.NET Core 'un sürümü destek sonuna](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya [Ubuntu](https://wiki.ubuntu.com/Releases)sürümüne ulaştığı sürece bu sürümler desteklenmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="e22d7-110">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Ubuntu reaches end-of-life](https://wiki.ubuntu.com/Releases).</span></span>

- <span data-ttu-id="e22d7-111">✔️, Ubuntu veya .NET Core sürümünün hala desteklendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e22d7-111">A ✔️ indicates that the version of Ubuntu or .NET Core is still supported.</span></span>
- <span data-ttu-id="e22d7-112">Bir ❌ , Ubuntu veya .NET Core sürümünün bu Ubuntu sürümünde desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e22d7-112">A ❌ indicates that the version of Ubuntu or .NET Core isn't supported on that Ubuntu release.</span></span>
- <span data-ttu-id="e22d7-113">Ubuntu ve .NET Core sürümlerinin her ikisi de ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e22d7-113">When both a version of Ubuntu and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="e22d7-114">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="e22d7-114">Ubuntu</span></span>                   | <span data-ttu-id="e22d7-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="e22d7-115">.NET Core 2.1</span></span> | <span data-ttu-id="e22d7-116">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="e22d7-116">.NET Core 3.1</span></span> | <span data-ttu-id="e22d7-117">.NET 5 Preview (yalnızca el ile yüklenir)</span><span class="sxs-lookup"><span data-stu-id="e22d7-117">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="e22d7-118">✔️ [20,04 (LTS)](#2004-)</span><span class="sxs-lookup"><span data-stu-id="e22d7-118">✔️ [20.04 (LTS)](#2004-)</span></span> | <span data-ttu-id="e22d7-119">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="e22d7-119">✔️ 2.1</span></span>        | <span data-ttu-id="e22d7-120">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="e22d7-120">✔️ 3.1</span></span>        | <span data-ttu-id="e22d7-121">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="e22d7-121">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="e22d7-122">❌[19,10](#1910-)</span><span class="sxs-lookup"><span data-stu-id="e22d7-122">❌ [19.10](#1910-)</span></span>       | <span data-ttu-id="e22d7-123">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="e22d7-123">✔️ 2.1</span></span>        | <span data-ttu-id="e22d7-124">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="e22d7-124">✔️ 3.1</span></span>        | <span data-ttu-id="e22d7-125">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="e22d7-125">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="e22d7-126">❌[19,04](#1904-)</span><span class="sxs-lookup"><span data-stu-id="e22d7-126">❌ [19.04](#1904-)</span></span>       | <span data-ttu-id="e22d7-127">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="e22d7-127">✔️ 2.1</span></span>        | <span data-ttu-id="e22d7-128">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="e22d7-128">✔️ 3.1</span></span>        | <span data-ttu-id="e22d7-129">❌ 5,0 Önizleme</span><span class="sxs-lookup"><span data-stu-id="e22d7-129">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="e22d7-130">❌[18,10](#1810-)</span><span class="sxs-lookup"><span data-stu-id="e22d7-130">❌ [18.10](#1810-)</span></span>       | <span data-ttu-id="e22d7-131">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="e22d7-131">✔️ 2.1</span></span>        | <span data-ttu-id="e22d7-132">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="e22d7-132">❌ 3.1</span></span>        | <span data-ttu-id="e22d7-133">❌ 5,0 Önizleme</span><span class="sxs-lookup"><span data-stu-id="e22d7-133">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="e22d7-134">✔️ [18,04 (LTS)](#1804-)</span><span class="sxs-lookup"><span data-stu-id="e22d7-134">✔️ [18.04 (LTS)](#1804-)</span></span> | <span data-ttu-id="e22d7-135">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="e22d7-135">✔️ 2.1</span></span>        | <span data-ttu-id="e22d7-136">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="e22d7-136">✔️ 3.1</span></span>        | <span data-ttu-id="e22d7-137">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="e22d7-137">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="e22d7-138">❌[17,10](#1710-)</span><span class="sxs-lookup"><span data-stu-id="e22d7-138">❌ [17.10](#1710-)</span></span>       | <span data-ttu-id="e22d7-139">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="e22d7-139">✔️ 2.1</span></span>        | <span data-ttu-id="e22d7-140">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="e22d7-140">❌ 3.1</span></span>        | <span data-ttu-id="e22d7-141">❌ 5,0 Önizleme</span><span class="sxs-lookup"><span data-stu-id="e22d7-141">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="e22d7-142">❌[17,04](#1704-)</span><span class="sxs-lookup"><span data-stu-id="e22d7-142">❌ [17.04](#1704-)</span></span>       | <span data-ttu-id="e22d7-143">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="e22d7-143">✔️ 2.1</span></span>        | <span data-ttu-id="e22d7-144">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="e22d7-144">❌ 3.1</span></span>        | <span data-ttu-id="e22d7-145">❌ 5,0 Önizleme</span><span class="sxs-lookup"><span data-stu-id="e22d7-145">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="e22d7-146">❌ [16.10](#1610-)</span><span class="sxs-lookup"><span data-stu-id="e22d7-146">❌ [16.10](#1610-)</span></span>       | <span data-ttu-id="e22d7-147">❌ 2,1</span><span class="sxs-lookup"><span data-stu-id="e22d7-147">❌ 2.1</span></span>        | <span data-ttu-id="e22d7-148">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="e22d7-148">❌ 3.1</span></span>        | <span data-ttu-id="e22d7-149">❌ 5,0 Önizleme</span><span class="sxs-lookup"><span data-stu-id="e22d7-149">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="e22d7-150">✔️ [16,04 (LTS)](#1604-)</span><span class="sxs-lookup"><span data-stu-id="e22d7-150">✔️ [16.04 (LTS)](#1604-)</span></span> | <span data-ttu-id="e22d7-151">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="e22d7-151">✔️ 2.1</span></span>        | <span data-ttu-id="e22d7-152">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="e22d7-152">✔️ 3.1</span></span>        | <span data-ttu-id="e22d7-153">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="e22d7-153">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="e22d7-154">Aşağıdaki .NET Core sürümleri artık desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="e22d7-154">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="e22d7-155">Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:</span><span class="sxs-lookup"><span data-stu-id="e22d7-155">The downloads for these still remain published:</span></span>

- <span data-ttu-id="e22d7-156">3.0</span><span class="sxs-lookup"><span data-stu-id="e22d7-156">3.0</span></span>
- <span data-ttu-id="e22d7-157">2.2</span><span class="sxs-lookup"><span data-stu-id="e22d7-157">2.2</span></span>
- <span data-ttu-id="e22d7-158">2.0</span><span class="sxs-lookup"><span data-stu-id="e22d7-158">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="e22d7-159">Diğer sürümleri nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="e22d7-159">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="2004-"></a><span data-ttu-id="e22d7-160">20,04 ✔️</span><span class="sxs-lookup"><span data-stu-id="e22d7-160">20.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1910-"></a><span data-ttu-id="e22d7-161">19,10 ❌</span><span class="sxs-lookup"><span data-stu-id="e22d7-161">19.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1904-"></a><span data-ttu-id="e22d7-162">19,04 ❌</span><span class="sxs-lookup"><span data-stu-id="e22d7-162">19.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1810-"></a><span data-ttu-id="e22d7-163">18,10 ❌</span><span class="sxs-lookup"><span data-stu-id="e22d7-163">18.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1804-"></a><span data-ttu-id="e22d7-164">18,04 ✔️</span><span class="sxs-lookup"><span data-stu-id="e22d7-164">18.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1710-"></a><span data-ttu-id="e22d7-165">17,10 ❌</span><span class="sxs-lookup"><span data-stu-id="e22d7-165">17.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1704-"></a><span data-ttu-id="e22d7-166">17,04 ❌</span><span class="sxs-lookup"><span data-stu-id="e22d7-166">17.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1610-"></a><span data-ttu-id="e22d7-167">16,10 ❌</span><span class="sxs-lookup"><span data-stu-id="e22d7-167">16.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1604-"></a><span data-ttu-id="e22d7-168">16,04 ✔️</span><span class="sxs-lookup"><span data-stu-id="e22d7-168">16.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="apt-update-sdk-or-runtime"></a><span data-ttu-id="e22d7-169">APT güncelleştirme SDK 'Sı veya çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="e22d7-169">APT update SDK or runtime</span></span>

<span data-ttu-id="e22d7-170">.NET Core için yeni bir yama yayını varsa, aşağıdaki komutlarla APT aracılığıyla yükseltmeniz yeterlidir:</span><span class="sxs-lookup"><span data-stu-id="e22d7-170">When a new patch release is available for .NET Core, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="e22d7-171">APT sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="e22d7-171">APT troubleshooting</span></span>

<span data-ttu-id="e22d7-172">Bu bölümde, .NET Core 'u yüklemek için APT kullanırken karşılaşabileceğiniz yaygın hatalar hakkında bilgi verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e22d7-172">This section provides information on common errors you may get while using APT to install .NET Core.</span></span>

### <a name="unable-to-locate--some-packages-could-not-be-installed"></a><span data-ttu-id="e22d7-173">\\Bazı paketlerin yüklenmesi bulunamıyor</span><span class="sxs-lookup"><span data-stu-id="e22d7-173">Unable to locate \\ Some packages could not be installed</span></span>

[!INCLUDE [package-manager-failed-to-find-deb](includes/package-manager-failed-to-find-deb.md)]

```bash
sudo apt-get install -y gpg
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/ubuntu/{os-version}/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y {dotnet-package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="e22d7-174">Getirilemedi</span><span class="sxs-lookup"><span data-stu-id="e22d7-174">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="snap"></a><span data-ttu-id="e22d7-175">Bileşenlerinden</span><span class="sxs-lookup"><span data-stu-id="e22d7-175">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="e22d7-176">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="e22d7-176">Dependencies</span></span>

<span data-ttu-id="e22d7-177">Bir paket yöneticisi ile yüklediğinizde, bu kitaplıklar sizin için yüklenir.</span><span class="sxs-lookup"><span data-stu-id="e22d7-177">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="e22d7-178">Ancak, .NET Core 'u el ile yüklüyorsanız veya kendi kendine içerilen bir uygulama yayımlarsanız, bu kitaplıkların yüklü olduğundan emin olmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="e22d7-178">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="e22d7-179">libc6</span><span class="sxs-lookup"><span data-stu-id="e22d7-179">libc6</span></span>
- <span data-ttu-id="e22d7-180">libgcc1</span><span class="sxs-lookup"><span data-stu-id="e22d7-180">libgcc1</span></span>
- <span data-ttu-id="e22d7-181">libgssapı-krb5-2</span><span class="sxs-lookup"><span data-stu-id="e22d7-181">libgssapi-krb5-2</span></span>
- <span data-ttu-id="e22d7-182">libicu52 (14. x için)</span><span class="sxs-lookup"><span data-stu-id="e22d7-182">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="e22d7-183">libicu55 (16. x için)</span><span class="sxs-lookup"><span data-stu-id="e22d7-183">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="e22d7-184">libicu60 (18. x için)</span><span class="sxs-lookup"><span data-stu-id="e22d7-184">libicu60 (for 18.x)</span></span>
- <span data-ttu-id="e22d7-185">libicu66 (20. x için)</span><span class="sxs-lookup"><span data-stu-id="e22d7-185">libicu66 (for 20.x)</span></span>
- <span data-ttu-id="e22d7-186">libssl 1.0.0 (14. x, 16. x için)</span><span class="sxs-lookup"><span data-stu-id="e22d7-186">libssl1.0.0 (for 14.x, 16.x)</span></span>
- <span data-ttu-id="e22d7-187">libssl 1.1 (18. x için 20. x için)</span><span class="sxs-lookup"><span data-stu-id="e22d7-187">libssl1.1 (for 18.x, 20.x)</span></span>
- <span data-ttu-id="e22d7-188">libstdc + + 6</span><span class="sxs-lookup"><span data-stu-id="e22d7-188">libstdc++6</span></span>
- <span data-ttu-id="e22d7-189">zlib1g</span><span class="sxs-lookup"><span data-stu-id="e22d7-189">zlib1g</span></span>

<span data-ttu-id="e22d7-190">*System. Drawing. Common* derlemesini kullanan .NET Core uygulamaları için aşağıdaki bağımlılığa de ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="e22d7-190">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="e22d7-191">libgdiplus (sürüm 6.0.1 veya üzeri)</span><span class="sxs-lookup"><span data-stu-id="e22d7-191">libgdiplus (version 6.0.1 or later)</span></span>

  > [!WARNING]
  > <span data-ttu-id="e22d7-192">En son bir *libgdiplus* sürümünü sisteminize mono deposunu ekleyerek yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e22d7-192">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="e22d7-193">Daha fazla bilgi için bkz. <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="e22d7-193">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="e22d7-194">Komut dosyalı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="e22d7-194">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="e22d7-195">El ile yüklemesi</span><span class="sxs-lookup"><span data-stu-id="e22d7-195">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="e22d7-196">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="e22d7-196">Next steps</span></span>

- [<span data-ttu-id="e22d7-197">Öğretici: Visual Studio Code kullanarak .NET Core SDK bir konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="e22d7-197">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
