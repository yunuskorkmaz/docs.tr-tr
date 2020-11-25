---
title: Ubuntu-.NET üzerine .NET 'i yükler
description: Ubuntu 'da .NET SDK ve .NET çalışma zamanı yüklemenin çeşitli yollarını gösterir.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 22ce3379e028f065528e1f507a2d8c1ae598f0e8
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031858"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-ubuntu"></a><span data-ttu-id="2b5ab-103">Ubuntu 'da .NET SDK veya .NET çalışma zamanı 'nı yükler</span><span class="sxs-lookup"><span data-stu-id="2b5ab-103">Install the .NET SDK or the .NET Runtime on Ubuntu</span></span>

<span data-ttu-id="2b5ab-104">.NET, Ubuntu 'da desteklenir.</span><span class="sxs-lookup"><span data-stu-id="2b5ab-104">.NET is supported on Ubuntu.</span></span> <span data-ttu-id="2b5ab-105">Bu makalede, Ubuntu 'da .NET yüklemesi açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2b5ab-105">This article describes how to install .NET on Ubuntu.</span></span> <span data-ttu-id="2b5ab-106">Ubuntu sürümü destek dışı kaldığında, .NET artık bu sürümde desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="2b5ab-106">When an Ubuntu version falls out of support, .NET is no longer supported with that version.</span></span> <span data-ttu-id="2b5ab-107">Ancak, bu yönergeler desteklenmese de bu sürümler üzerinde çalışan .NET almanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="2b5ab-107">However, these instructions may help you to get .NET running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="2b5ab-108">Desteklenen dağıtımlar</span><span class="sxs-lookup"><span data-stu-id="2b5ab-108">Supported distributions</span></span>

<span data-ttu-id="2b5ab-109">Aşağıdaki tabloda, şu anda desteklenen .NET sürümlerinin ve üzerinde desteklendikleri Ubuntu sürümlerinin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2b5ab-109">The following table is a list of currently supported .NET releases and the versions of Ubuntu they're supported on.</span></span> <span data-ttu-id="2b5ab-110">Bu sürümler, [.NET sürümü destek sonuna](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya [Ubuntu sürümüne ulaşıncaya kadar yaşam süresi bitene](https://wiki.ubuntu.com/Releases)kadar desteklenmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="2b5ab-110">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Ubuntu reaches end-of-life](https://wiki.ubuntu.com/Releases).</span></span>

- <span data-ttu-id="2b5ab-111">✔️, Ubuntu veya .NET sürümünün hala desteklendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="2b5ab-111">A ✔️ indicates that the version of Ubuntu or .NET is still supported.</span></span>
- <span data-ttu-id="2b5ab-112">Bir ❌ , Ubuntu veya .NET sürümünün bu Ubuntu sürümünde desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2b5ab-112">A ❌ indicates that the version of Ubuntu or .NET isn't supported on that Ubuntu release.</span></span>
- <span data-ttu-id="2b5ab-113">Ubuntu ve .NET sürümünün her ikisi de ✔️ sahip olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="2b5ab-113">When both a version of Ubuntu and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="2b5ab-114">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="2b5ab-114">Ubuntu</span></span>                   | <span data-ttu-id="2b5ab-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="2b5ab-115">.NET Core 2.1</span></span> | <span data-ttu-id="2b5ab-116">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="2b5ab-116">.NET Core 3.1</span></span> | <span data-ttu-id="2b5ab-117">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="2b5ab-117">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="2b5ab-118">✔️ [20,10](#2010-)</span><span class="sxs-lookup"><span data-stu-id="2b5ab-118">✔️ [20.10](#2010-)</span></span>       | <span data-ttu-id="2b5ab-119">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="2b5ab-119">✔️ 2.1</span></span>        | <span data-ttu-id="2b5ab-120">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="2b5ab-120">✔️ 3.1</span></span>        | <span data-ttu-id="2b5ab-121">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="2b5ab-121">✔️ 5.0</span></span> |
| <span data-ttu-id="2b5ab-122">✔️ [20,04 (LTS)](#2004-)</span><span class="sxs-lookup"><span data-stu-id="2b5ab-122">✔️ [20.04 (LTS)](#2004-)</span></span> | <span data-ttu-id="2b5ab-123">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="2b5ab-123">✔️ 2.1</span></span>        | <span data-ttu-id="2b5ab-124">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="2b5ab-124">✔️ 3.1</span></span>        | <span data-ttu-id="2b5ab-125">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="2b5ab-125">✔️ 5.0</span></span> |
| <span data-ttu-id="2b5ab-126">❌[19,10](#1910-)</span><span class="sxs-lookup"><span data-stu-id="2b5ab-126">❌ [19.10](#1910-)</span></span>       | <span data-ttu-id="2b5ab-127">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="2b5ab-127">✔️ 2.1</span></span>        | <span data-ttu-id="2b5ab-128">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="2b5ab-128">✔️ 3.1</span></span>        | <span data-ttu-id="2b5ab-129">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="2b5ab-129">✔️ 5.0</span></span> |
| <span data-ttu-id="2b5ab-130">❌[19,04](#1904-)</span><span class="sxs-lookup"><span data-stu-id="2b5ab-130">❌ [19.04](#1904-)</span></span>       | <span data-ttu-id="2b5ab-131">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="2b5ab-131">✔️ 2.1</span></span>        | <span data-ttu-id="2b5ab-132">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="2b5ab-132">✔️ 3.1</span></span>        | <span data-ttu-id="2b5ab-133">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="2b5ab-133">❌ 5.0</span></span> |
| <span data-ttu-id="2b5ab-134">❌[18,10](#1810-)</span><span class="sxs-lookup"><span data-stu-id="2b5ab-134">❌ [18.10](#1810-)</span></span>       | <span data-ttu-id="2b5ab-135">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="2b5ab-135">✔️ 2.1</span></span>        | <span data-ttu-id="2b5ab-136">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="2b5ab-136">❌ 3.1</span></span>        | <span data-ttu-id="2b5ab-137">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="2b5ab-137">❌ 5.0</span></span> |
| <span data-ttu-id="2b5ab-138">✔️ [18,04 (LTS)](#1804-)</span><span class="sxs-lookup"><span data-stu-id="2b5ab-138">✔️ [18.04 (LTS)](#1804-)</span></span> | <span data-ttu-id="2b5ab-139">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="2b5ab-139">✔️ 2.1</span></span>        | <span data-ttu-id="2b5ab-140">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="2b5ab-140">✔️ 3.1</span></span>        | <span data-ttu-id="2b5ab-141">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="2b5ab-141">✔️ 5.0</span></span> |
| <span data-ttu-id="2b5ab-142">❌[17,10](#1710-)</span><span class="sxs-lookup"><span data-stu-id="2b5ab-142">❌ [17.10](#1710-)</span></span>       | <span data-ttu-id="2b5ab-143">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="2b5ab-143">✔️ 2.1</span></span>        | <span data-ttu-id="2b5ab-144">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="2b5ab-144">❌ 3.1</span></span>        | <span data-ttu-id="2b5ab-145">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="2b5ab-145">❌ 5.0</span></span> |
| <span data-ttu-id="2b5ab-146">❌[17,04](#1704-)</span><span class="sxs-lookup"><span data-stu-id="2b5ab-146">❌ [17.04](#1704-)</span></span>       | <span data-ttu-id="2b5ab-147">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="2b5ab-147">✔️ 2.1</span></span>        | <span data-ttu-id="2b5ab-148">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="2b5ab-148">❌ 3.1</span></span>        | <span data-ttu-id="2b5ab-149">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="2b5ab-149">❌ 5.0</span></span> |
| <span data-ttu-id="2b5ab-150">❌[16,10](#1610-)</span><span class="sxs-lookup"><span data-stu-id="2b5ab-150">❌ [16.10](#1610-)</span></span>       | <span data-ttu-id="2b5ab-151">❌ 2,1</span><span class="sxs-lookup"><span data-stu-id="2b5ab-151">❌ 2.1</span></span>        | <span data-ttu-id="2b5ab-152">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="2b5ab-152">❌ 3.1</span></span>        | <span data-ttu-id="2b5ab-153">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="2b5ab-153">❌ 5.0</span></span> |
| <span data-ttu-id="2b5ab-154">✔️ [16,04 (LTS)](#1604-)</span><span class="sxs-lookup"><span data-stu-id="2b5ab-154">✔️ [16.04 (LTS)](#1604-)</span></span> | <span data-ttu-id="2b5ab-155">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="2b5ab-155">✔️ 2.1</span></span>        | <span data-ttu-id="2b5ab-156">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="2b5ab-156">✔️ 3.1</span></span>        | <span data-ttu-id="2b5ab-157">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="2b5ab-157">✔️ 5.0</span></span> |

<span data-ttu-id="2b5ab-158">Aşağıdaki .NET sürümleri artık desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="2b5ab-158">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="2b5ab-159">Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:</span><span class="sxs-lookup"><span data-stu-id="2b5ab-159">The downloads for these still remain published:</span></span>

- <span data-ttu-id="2b5ab-160">3,0</span><span class="sxs-lookup"><span data-stu-id="2b5ab-160">3.0</span></span>
- <span data-ttu-id="2b5ab-161">2.2</span><span class="sxs-lookup"><span data-stu-id="2b5ab-161">2.2</span></span>
- <span data-ttu-id="2b5ab-162">2,0</span><span class="sxs-lookup"><span data-stu-id="2b5ab-162">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="2b5ab-163">Önizleme sürümlerini Kaldır</span><span class="sxs-lookup"><span data-stu-id="2b5ab-163">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="2b5ab-164">Diğer sürümleri nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="2b5ab-164">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="2010-"></a><span data-ttu-id="2b5ab-165">20,10 ✔️</span><span class="sxs-lookup"><span data-stu-id="2b5ab-165">20.10 ✔️</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2b5ab-166">.NET Core 2,1, paket akışında henüz kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="2b5ab-166">.NET Core 2.1 isn't yet available in the package feed.</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/20.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="2004-"></a><span data-ttu-id="2b5ab-167">20,04 ✔️</span><span class="sxs-lookup"><span data-stu-id="2b5ab-167">20.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="1910-"></a><span data-ttu-id="2b5ab-168">19,10 ❌</span><span class="sxs-lookup"><span data-stu-id="2b5ab-168">19.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1904-"></a><span data-ttu-id="2b5ab-169">19,04 ❌</span><span class="sxs-lookup"><span data-stu-id="2b5ab-169">19.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1810-"></a><span data-ttu-id="2b5ab-170">18,10 ❌</span><span class="sxs-lookup"><span data-stu-id="2b5ab-170">18.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1804-"></a><span data-ttu-id="2b5ab-171">18,04 ✔️</span><span class="sxs-lookup"><span data-stu-id="2b5ab-171">18.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="1710-"></a><span data-ttu-id="2b5ab-172">17,10 ❌</span><span class="sxs-lookup"><span data-stu-id="2b5ab-172">17.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1704-"></a><span data-ttu-id="2b5ab-173">17,04 ❌</span><span class="sxs-lookup"><span data-stu-id="2b5ab-173">17.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1610-"></a><span data-ttu-id="2b5ab-174">16,10 ❌</span><span class="sxs-lookup"><span data-stu-id="2b5ab-174">16.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1604-"></a><span data-ttu-id="2b5ab-175">16,04 ✔️</span><span class="sxs-lookup"><span data-stu-id="2b5ab-175">16.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="apt-update-sdk-or-runtime"></a><span data-ttu-id="2b5ab-176">APT güncelleştirme SDK 'Sı veya çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="2b5ab-176">APT update SDK or runtime</span></span>

<span data-ttu-id="2b5ab-177">.NET için yeni bir yama yayını varsa, aşağıdaki komutlarla APT aracılığıyla yükseltmeniz yeterlidir:</span><span class="sxs-lookup"><span data-stu-id="2b5ab-177">When a new patch release is available for .NET, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="2b5ab-178">APT sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="2b5ab-178">APT troubleshooting</span></span>

<span data-ttu-id="2b5ab-179">Bu bölümde, .NET yüklemek için APT kullanırken alabileceğiniz yaygın hatalar hakkında bilgi verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2b5ab-179">This section provides information on common errors you may get while using APT to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="2b5ab-180">Paket bulunamadı</span><span class="sxs-lookup"><span data-stu-id="2b5ab-180">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="unable-to-locate--some-packages-could-not-be-installed"></a><span data-ttu-id="2b5ab-181">\\Bazı paketlerin yüklenmesi bulunamıyor</span><span class="sxs-lookup"><span data-stu-id="2b5ab-181">Unable to locate \\ Some packages could not be installed</span></span>

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

### <a name="failed-to-fetch"></a><span data-ttu-id="2b5ab-182">Getirilemedi</span><span class="sxs-lookup"><span data-stu-id="2b5ab-182">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="snap"></a><span data-ttu-id="2b5ab-183">Bileşenlerinden</span><span class="sxs-lookup"><span data-stu-id="2b5ab-183">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="2b5ab-184">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="2b5ab-184">Dependencies</span></span>

<span data-ttu-id="2b5ab-185">Bir paket yöneticisi ile yüklediğinizde, bu kitaplıklar sizin için yüklenir.</span><span class="sxs-lookup"><span data-stu-id="2b5ab-185">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="2b5ab-186">Ancak, .NET 'i el ile veya bağımsız bir uygulama yayımladığınızda, bu kitaplıkların yüklü olduğundan emin olmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="2b5ab-186">But, if you manually install .NET or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="2b5ab-187">libc6</span><span class="sxs-lookup"><span data-stu-id="2b5ab-187">libc6</span></span>
- <span data-ttu-id="2b5ab-188">libgcc1</span><span class="sxs-lookup"><span data-stu-id="2b5ab-188">libgcc1</span></span>
- <span data-ttu-id="2b5ab-189">libgssapı-krb5-2</span><span class="sxs-lookup"><span data-stu-id="2b5ab-189">libgssapi-krb5-2</span></span>
- <span data-ttu-id="2b5ab-190">libicu52 (14. x için)</span><span class="sxs-lookup"><span data-stu-id="2b5ab-190">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="2b5ab-191">libicu55 (16. x için)</span><span class="sxs-lookup"><span data-stu-id="2b5ab-191">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="2b5ab-192">libicu60 (18. x için)</span><span class="sxs-lookup"><span data-stu-id="2b5ab-192">libicu60 (for 18.x)</span></span>
- <span data-ttu-id="2b5ab-193">libicu66 (20. x için)</span><span class="sxs-lookup"><span data-stu-id="2b5ab-193">libicu66 (for 20.x)</span></span>
- <span data-ttu-id="2b5ab-194">libssl 1.0.0 (14. x, 16. x için)</span><span class="sxs-lookup"><span data-stu-id="2b5ab-194">libssl1.0.0 (for 14.x, 16.x)</span></span>
- <span data-ttu-id="2b5ab-195">libssl 1.1 (18. x için 20. x için)</span><span class="sxs-lookup"><span data-stu-id="2b5ab-195">libssl1.1 (for 18.x, 20.x)</span></span>
- <span data-ttu-id="2b5ab-196">libstdc + + 6</span><span class="sxs-lookup"><span data-stu-id="2b5ab-196">libstdc++6</span></span>
- <span data-ttu-id="2b5ab-197">zlib1g</span><span class="sxs-lookup"><span data-stu-id="2b5ab-197">zlib1g</span></span>

<span data-ttu-id="2b5ab-198">*System. Drawing. Common* derlemesini kullanan .NET uygulamaları için aşağıdaki bağımlılığa de ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="2b5ab-198">For .NET apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="2b5ab-199">libgdiplus (sürüm 6.0.1 veya üzeri)</span><span class="sxs-lookup"><span data-stu-id="2b5ab-199">libgdiplus (version 6.0.1 or later)</span></span>

  > [!WARNING]
  > <span data-ttu-id="2b5ab-200">En son bir *libgdiplus* sürümünü sisteminize mono deposunu ekleyerek yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b5ab-200">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="2b5ab-201">Daha fazla bilgi için bkz. <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="2b5ab-201">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="2b5ab-202">Komut dosyalı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="2b5ab-202">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="2b5ab-203">El ile yüklemesi</span><span class="sxs-lookup"><span data-stu-id="2b5ab-203">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="2b5ab-204">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="2b5ab-204">Next steps</span></span>

- [<span data-ttu-id="2b5ab-205">Öğretici: Visual Studio Code kullanarak .NET SDK ile bir konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="2b5ab-205">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
