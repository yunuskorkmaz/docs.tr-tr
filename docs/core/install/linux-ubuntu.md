---
title: Ubuntu-.NET üzerine .NET 'i yükler
description: Ubuntu 'da .NET SDK ve .NET çalışma zamanı yüklemenin çeşitli yollarını gösterir.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 14e5e9548d4aa09a586e2038f3e35a489ee65cd2
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970777"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-ubuntu"></a><span data-ttu-id="6844c-103">Ubuntu 'da .NET SDK veya .NET çalışma zamanı 'nı yükler</span><span class="sxs-lookup"><span data-stu-id="6844c-103">Install the .NET SDK or the .NET Runtime on Ubuntu</span></span>

<span data-ttu-id="6844c-104">.NET, Ubuntu 'da desteklenir.</span><span class="sxs-lookup"><span data-stu-id="6844c-104">.NET is supported on Ubuntu.</span></span> <span data-ttu-id="6844c-105">Bu makalede, Ubuntu 'da .NET yüklemesi açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6844c-105">This article describes how to install .NET on Ubuntu.</span></span> <span data-ttu-id="6844c-106">Ubuntu sürümü destek dışı kaldığında, .NET artık bu sürümde desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="6844c-106">When an Ubuntu version falls out of support, .NET is no longer supported with that version.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="6844c-107">Desteklenen dağıtımlar</span><span class="sxs-lookup"><span data-stu-id="6844c-107">Supported distributions</span></span>

<span data-ttu-id="6844c-108">Aşağıdaki tabloda, şu anda desteklenen .NET sürümlerinin ve üzerinde desteklendikleri Ubuntu sürümlerinin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6844c-108">The following table is a list of currently supported .NET releases and the versions of Ubuntu they're supported on.</span></span> <span data-ttu-id="6844c-109">Bu sürümler, [.NET sürümü destek sonuna](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya [Ubuntu sürümüne ulaşıncaya kadar yaşam süresi bitene](https://wiki.ubuntu.com/Releases)kadar desteklenmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="6844c-109">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Ubuntu reaches end-of-life](https://wiki.ubuntu.com/Releases).</span></span>

- <span data-ttu-id="6844c-110">✔️, Ubuntu veya .NET sürümünün hala desteklendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6844c-110">A ✔️ indicates that the version of Ubuntu or .NET is still supported.</span></span>
- <span data-ttu-id="6844c-111">Bir ❌ , Ubuntu veya .NET sürümünün bu Ubuntu sürümünde desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6844c-111">A ❌ indicates that the version of Ubuntu or .NET isn't supported on that Ubuntu release.</span></span>
- <span data-ttu-id="6844c-112">Ubuntu ve .NET sürümünün her ikisi de ✔️ sahip olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="6844c-112">When both a version of Ubuntu and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="6844c-113">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="6844c-113">Ubuntu</span></span>                   | <span data-ttu-id="6844c-114">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="6844c-114">.NET Core 2.1</span></span> | <span data-ttu-id="6844c-115">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="6844c-115">.NET Core 3.1</span></span> | <span data-ttu-id="6844c-116">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="6844c-116">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="6844c-117">✔️ [20,10](#2010-)</span><span class="sxs-lookup"><span data-stu-id="6844c-117">✔️ [20.10](#2010-)</span></span>       | <span data-ttu-id="6844c-118">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="6844c-118">✔️ 2.1</span></span>        | <span data-ttu-id="6844c-119">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="6844c-119">✔️ 3.1</span></span>        | <span data-ttu-id="6844c-120">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="6844c-120">✔️ 5.0</span></span> |
| <span data-ttu-id="6844c-121">✔️ [20,04 (LTS)](#2004-)</span><span class="sxs-lookup"><span data-stu-id="6844c-121">✔️ [20.04 (LTS)](#2004-)</span></span> | <span data-ttu-id="6844c-122">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="6844c-122">✔️ 2.1</span></span>        | <span data-ttu-id="6844c-123">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="6844c-123">✔️ 3.1</span></span>        | <span data-ttu-id="6844c-124">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="6844c-124">✔️ 5.0</span></span> |
| <span data-ttu-id="6844c-125">❌[19,10](#1910-)</span><span class="sxs-lookup"><span data-stu-id="6844c-125">❌ [19.10](#1910-)</span></span>       | <span data-ttu-id="6844c-126">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="6844c-126">✔️ 2.1</span></span>        | <span data-ttu-id="6844c-127">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="6844c-127">✔️ 3.1</span></span>        | <span data-ttu-id="6844c-128">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="6844c-128">✔️ 5.0</span></span> |
| <span data-ttu-id="6844c-129">❌[19,04](#1904-)</span><span class="sxs-lookup"><span data-stu-id="6844c-129">❌ [19.04](#1904-)</span></span>       | <span data-ttu-id="6844c-130">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="6844c-130">✔️ 2.1</span></span>        | <span data-ttu-id="6844c-131">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="6844c-131">✔️ 3.1</span></span>        | <span data-ttu-id="6844c-132">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="6844c-132">❌ 5.0</span></span> |
| <span data-ttu-id="6844c-133">❌[18,10](#1810-)</span><span class="sxs-lookup"><span data-stu-id="6844c-133">❌ [18.10](#1810-)</span></span>       | <span data-ttu-id="6844c-134">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="6844c-134">✔️ 2.1</span></span>        | <span data-ttu-id="6844c-135">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="6844c-135">❌ 3.1</span></span>        | <span data-ttu-id="6844c-136">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="6844c-136">❌ 5.0</span></span> |
| <span data-ttu-id="6844c-137">✔️ [18,04 (LTS)](#1804-)</span><span class="sxs-lookup"><span data-stu-id="6844c-137">✔️ [18.04 (LTS)](#1804-)</span></span> | <span data-ttu-id="6844c-138">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="6844c-138">✔️ 2.1</span></span>        | <span data-ttu-id="6844c-139">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="6844c-139">✔️ 3.1</span></span>        | <span data-ttu-id="6844c-140">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="6844c-140">✔️ 5.0</span></span> |
| <span data-ttu-id="6844c-141">❌[17,10](#1710-)</span><span class="sxs-lookup"><span data-stu-id="6844c-141">❌ [17.10](#1710-)</span></span>       | <span data-ttu-id="6844c-142">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="6844c-142">✔️ 2.1</span></span>        | <span data-ttu-id="6844c-143">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="6844c-143">❌ 3.1</span></span>        | <span data-ttu-id="6844c-144">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="6844c-144">❌ 5.0</span></span> |
| <span data-ttu-id="6844c-145">❌[17,04](#1704-)</span><span class="sxs-lookup"><span data-stu-id="6844c-145">❌ [17.04](#1704-)</span></span>       | <span data-ttu-id="6844c-146">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="6844c-146">✔️ 2.1</span></span>        | <span data-ttu-id="6844c-147">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="6844c-147">❌ 3.1</span></span>        | <span data-ttu-id="6844c-148">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="6844c-148">❌ 5.0</span></span> |
| <span data-ttu-id="6844c-149">❌[16,10](#1610-)</span><span class="sxs-lookup"><span data-stu-id="6844c-149">❌ [16.10](#1610-)</span></span>       | <span data-ttu-id="6844c-150">❌ 2,1</span><span class="sxs-lookup"><span data-stu-id="6844c-150">❌ 2.1</span></span>        | <span data-ttu-id="6844c-151">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="6844c-151">❌ 3.1</span></span>        | <span data-ttu-id="6844c-152">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="6844c-152">❌ 5.0</span></span> |
| <span data-ttu-id="6844c-153">✔️ [16,04 (LTS)](#1604-)</span><span class="sxs-lookup"><span data-stu-id="6844c-153">✔️ [16.04 (LTS)](#1604-)</span></span> | <span data-ttu-id="6844c-154">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="6844c-154">✔️ 2.1</span></span>        | <span data-ttu-id="6844c-155">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="6844c-155">✔️ 3.1</span></span>        | <span data-ttu-id="6844c-156">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="6844c-156">✔️ 5.0</span></span> |

<span data-ttu-id="6844c-157">Aşağıdaki .NET sürümleri artık desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="6844c-157">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="6844c-158">Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:</span><span class="sxs-lookup"><span data-stu-id="6844c-158">The downloads for these still remain published:</span></span>

- <span data-ttu-id="6844c-159">3,0</span><span class="sxs-lookup"><span data-stu-id="6844c-159">3.0</span></span>
- <span data-ttu-id="6844c-160">2.2</span><span class="sxs-lookup"><span data-stu-id="6844c-160">2.2</span></span>
- <span data-ttu-id="6844c-161">2.0</span><span class="sxs-lookup"><span data-stu-id="6844c-161">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="6844c-162">Önizleme sürümlerini Kaldır</span><span class="sxs-lookup"><span data-stu-id="6844c-162">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="2010-"></a><span data-ttu-id="6844c-163">20,10 ✔️</span><span class="sxs-lookup"><span data-stu-id="6844c-163">20.10 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/20.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="2004-"></a><span data-ttu-id="6844c-164">20,04 ✔️</span><span class="sxs-lookup"><span data-stu-id="6844c-164">20.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="1910-"></a><span data-ttu-id="6844c-165">19,10 ❌</span><span class="sxs-lookup"><span data-stu-id="6844c-165">19.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1904-"></a><span data-ttu-id="6844c-166">19,04 ❌</span><span class="sxs-lookup"><span data-stu-id="6844c-166">19.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1810-"></a><span data-ttu-id="6844c-167">18,10 ❌</span><span class="sxs-lookup"><span data-stu-id="6844c-167">18.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1804-"></a><span data-ttu-id="6844c-168">18,04 ✔️</span><span class="sxs-lookup"><span data-stu-id="6844c-168">18.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="1710-"></a><span data-ttu-id="6844c-169">17,10 ❌</span><span class="sxs-lookup"><span data-stu-id="6844c-169">17.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1704-"></a><span data-ttu-id="6844c-170">17,04 ❌</span><span class="sxs-lookup"><span data-stu-id="6844c-170">17.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1610-"></a><span data-ttu-id="6844c-171">16,10 ❌</span><span class="sxs-lookup"><span data-stu-id="6844c-171">16.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1604-"></a><span data-ttu-id="6844c-172">16,04 ✔️</span><span class="sxs-lookup"><span data-stu-id="6844c-172">16.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="6844c-173">Diğer sürümleri nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="6844c-173">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="use-apt-to-update-net"></a><span data-ttu-id="6844c-174">.NET 'i güncelleştirmek için APT kullanma</span><span class="sxs-lookup"><span data-stu-id="6844c-174">Use APT to update .NET</span></span>

<span data-ttu-id="6844c-175">.NET için yeni bir yama yayını varsa, aşağıdaki komutlarla APT aracılığıyla yükseltmeniz yeterlidir:</span><span class="sxs-lookup"><span data-stu-id="6844c-175">When a new patch release is available for .NET, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="6844c-176">APT sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="6844c-176">APT troubleshooting</span></span>

<span data-ttu-id="6844c-177">Bu bölümde, .NET yüklemek için APT kullanırken alabileceğiniz yaygın hatalar hakkında bilgi verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6844c-177">This section provides information on common errors you may get while using APT to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="6844c-178">Paket bulunamadı</span><span class="sxs-lookup"><span data-stu-id="6844c-178">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="unable-to-locate--some-packages-could-not-be-installed"></a><span data-ttu-id="6844c-179">\\Bazı paketlerin yüklenmesi bulunamıyor</span><span class="sxs-lookup"><span data-stu-id="6844c-179">Unable to locate \\ Some packages could not be installed</span></span>

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

### <a name="failed-to-fetch"></a><span data-ttu-id="6844c-180">Getirilemedi</span><span class="sxs-lookup"><span data-stu-id="6844c-180">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="dependencies"></a><span data-ttu-id="6844c-181">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="6844c-181">Dependencies</span></span>

<span data-ttu-id="6844c-182">Bir paket yöneticisi ile yüklediğinizde, bu kitaplıklar sizin için yüklenir.</span><span class="sxs-lookup"><span data-stu-id="6844c-182">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="6844c-183">Ancak, .NET 'i el ile veya bağımsız bir uygulama yayımladığınızda, bu kitaplıkların yüklü olduğundan emin olmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="6844c-183">But, if you manually install .NET or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="6844c-184">libc6</span><span class="sxs-lookup"><span data-stu-id="6844c-184">libc6</span></span>
- <span data-ttu-id="6844c-185">libgcc1</span><span class="sxs-lookup"><span data-stu-id="6844c-185">libgcc1</span></span>
- <span data-ttu-id="6844c-186">libgssapı-krb5-2</span><span class="sxs-lookup"><span data-stu-id="6844c-186">libgssapi-krb5-2</span></span>
- <span data-ttu-id="6844c-187">libicu52 (14. x için)</span><span class="sxs-lookup"><span data-stu-id="6844c-187">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="6844c-188">libicu55 (16. x için)</span><span class="sxs-lookup"><span data-stu-id="6844c-188">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="6844c-189">libicu60 (18. x için)</span><span class="sxs-lookup"><span data-stu-id="6844c-189">libicu60 (for 18.x)</span></span>
- <span data-ttu-id="6844c-190">libicu66 (20. x için)</span><span class="sxs-lookup"><span data-stu-id="6844c-190">libicu66 (for 20.x)</span></span>
- <span data-ttu-id="6844c-191">libssl 1.0.0 (14. x, 16. x için)</span><span class="sxs-lookup"><span data-stu-id="6844c-191">libssl1.0.0 (for 14.x, 16.x)</span></span>
- <span data-ttu-id="6844c-192">libssl 1.1 (18. x için 20. x için)</span><span class="sxs-lookup"><span data-stu-id="6844c-192">libssl1.1 (for 18.x, 20.x)</span></span>
- <span data-ttu-id="6844c-193">libstdc + + 6</span><span class="sxs-lookup"><span data-stu-id="6844c-193">libstdc++6</span></span>
- <span data-ttu-id="6844c-194">zlib1g</span><span class="sxs-lookup"><span data-stu-id="6844c-194">zlib1g</span></span>

<span data-ttu-id="6844c-195">*System. Drawing. Common* derlemesini kullanan .NET uygulamaları için aşağıdaki bağımlılığa de ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="6844c-195">For .NET apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="6844c-196">libgdiplus (sürüm 6.0.1 veya üzeri)</span><span class="sxs-lookup"><span data-stu-id="6844c-196">libgdiplus (version 6.0.1 or later)</span></span>

  > [!WARNING]
  > <span data-ttu-id="6844c-197">En son bir *libgdiplus* sürümünü sisteminize mono deposunu ekleyerek yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6844c-197">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="6844c-198">Daha fazla bilgi için bkz. <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="6844c-198">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="next-steps"></a><span data-ttu-id="6844c-199">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="6844c-199">Next steps</span></span>

- [<span data-ttu-id="6844c-200">.NET CLı için sekme tamamlamayı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="6844c-200">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="6844c-201">Öğretici: Visual Studio Code kullanarak .NET SDK ile bir konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="6844c-201">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
