---
title: .NET Core 'u de, .NET Core 'a yükler
description: .NET Core SDK ve .NET Core çalışma zamanını de, yüklemenin çeşitli yollarını gösterir.
author: thraka
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: c66d8e1daad4e59a766781b7117600352879b724
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84603057"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-debian"></a><span data-ttu-id="e1989-103">.NET Core SDK veya .NET Core çalışma zamanını Demerkezi üzerine yükler</span><span class="sxs-lookup"><span data-stu-id="e1989-103">Install .NET Core SDK or .NET Core Runtime on Debian</span></span>

<span data-ttu-id="e1989-104">Bu makalede, .NET Core 'un Dezimmetli üzerinde nasıl yükleneceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="e1989-104">This article describes how to install .NET Core on Debian.</span></span> <span data-ttu-id="e1989-105">Bir sürüm sürümü destek dışı kaldığında, .NET Core artık bu sürümle desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="e1989-105">When a Debian version falls out of support, .NET Core is no longer supported with that version.</span></span> <span data-ttu-id="e1989-106">Ancak, bu yönergeler desteklenmese de, bu sürümler üzerinde çalışan .NET Core 'u almanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e1989-106">However, these instructions may help you to get .NET Core running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="e1989-107">Desteklenen dağıtımlar</span><span class="sxs-lookup"><span data-stu-id="e1989-107">Supported distributions</span></span>

<span data-ttu-id="e1989-108">Aşağıdaki tabloda, şu anda desteklenen .NET Core sürümlerinin ve üzerinde desteklendikleri kaldırıcı sürümlerinin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e1989-108">The following table is a list of currently supported .NET Core releases and the versions of Debian they're supported on.</span></span> <span data-ttu-id="e1989-109">Bu sürümler, [.NET Core 'un sürümü destek sonuna ulaşıncaya](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya [detem 'ın kullanım ömrü sona](https://wiki.debian.org/DebianReleases)erecek kadar desteklenmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="e1989-109">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Debian reaches end-of-life](https://wiki.debian.org/DebianReleases).</span></span>

- <span data-ttu-id="e1989-110">✔️, debir veya .NET Core sürümünün hala desteklendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e1989-110">A ✔️ indicates that the version of Debian or .NET Core is still supported.</span></span>
- <span data-ttu-id="e1989-111">A ❌ , debir veya .NET Core sürümünün bu Dey sürümünde desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e1989-111">A ❌ indicates that the version of Debian or .NET Core isn't supported on that Debian release.</span></span>
- <span data-ttu-id="e1989-112">Her iki sürüm de bir .NET Core sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e1989-112">When both a version of Debian and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="e1989-113">Debian</span><span class="sxs-lookup"><span data-stu-id="e1989-113">Debian</span></span>                   | <span data-ttu-id="e1989-114">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="e1989-114">.NET Core 2.1</span></span> | <span data-ttu-id="e1989-115">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="e1989-115">.NET Core 3.1</span></span> | <span data-ttu-id="e1989-116">.NET 5 Preview (yalnızca el ile yüklenir)</span><span class="sxs-lookup"><span data-stu-id="e1989-116">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="e1989-117">✔️ [10](#debian-10-)</span><span class="sxs-lookup"><span data-stu-id="e1989-117">✔️ [10](#debian-10-)</span></span>     | <span data-ttu-id="e1989-118">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="e1989-118">✔️ 2.1</span></span>        | <span data-ttu-id="e1989-119">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="e1989-119">✔️ 3.1</span></span>        | <span data-ttu-id="e1989-120">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="e1989-120">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="e1989-121">✔️ [9](#debian-9-)</span><span class="sxs-lookup"><span data-stu-id="e1989-121">✔️ [9](#debian-9-)</span></span>       | <span data-ttu-id="e1989-122">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="e1989-122">✔️ 2.1</span></span>        | <span data-ttu-id="e1989-123">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="e1989-123">✔️ 3.1</span></span>        | <span data-ttu-id="e1989-124">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="e1989-124">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="e1989-125">❌[8](#debian-8-)</span><span class="sxs-lookup"><span data-stu-id="e1989-125">❌ [8](#debian-8-)</span></span>       | <span data-ttu-id="e1989-126">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="e1989-126">✔️ 2.1</span></span>        | <span data-ttu-id="e1989-127">❌3,1</span><span class="sxs-lookup"><span data-stu-id="e1989-127">❌ 3.1</span></span>        | <span data-ttu-id="e1989-128">❌5,0 Önizleme</span><span class="sxs-lookup"><span data-stu-id="e1989-128">❌ 5.0 Preview</span></span> |

<span data-ttu-id="e1989-129">Aşağıdaki .NET Core sürümleri artık desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="e1989-129">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="e1989-130">Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:</span><span class="sxs-lookup"><span data-stu-id="e1989-130">The downloads for these still remain published:</span></span>

- <span data-ttu-id="e1989-131">3.0</span><span class="sxs-lookup"><span data-stu-id="e1989-131">3.0</span></span>
- <span data-ttu-id="e1989-132">2,2</span><span class="sxs-lookup"><span data-stu-id="e1989-132">2.2</span></span>
- <span data-ttu-id="e1989-133">2.0</span><span class="sxs-lookup"><span data-stu-id="e1989-133">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="e1989-134">Diğer sürümleri nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="e1989-134">How to install other versions</span></span>

[!INCLUDE [hack-pkgname](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="debian-10-"></a><span data-ttu-id="e1989-135">10. ✔️</span><span class="sxs-lookup"><span data-stu-id="e1989-135">Debian 10 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/debian/10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="debian-9-"></a><span data-ttu-id="e1989-136">De, 9 ✔️</span><span class="sxs-lookup"><span data-stu-id="e1989-136">Debian 9 ✔️</span></span>

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

## <a name="debian-8-"></a><span data-ttu-id="e1989-137">Desek8❌</span><span class="sxs-lookup"><span data-stu-id="e1989-137">Debian 8 ❌</span></span>

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

## <a name="apt-update-sdk-or-runtime"></a><span data-ttu-id="e1989-138">APT güncelleştirme SDK 'Sı veya çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="e1989-138">APT update SDK or runtime</span></span>

<span data-ttu-id="e1989-139">.NET Core için yeni bir yama yayını varsa, aşağıdaki komutlarla APT aracılığıyla yükseltmeniz yeterlidir:</span><span class="sxs-lookup"><span data-stu-id="e1989-139">When a new patch release is available for .NET Core, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="e1989-140">APT sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="e1989-140">APT troubleshooting</span></span>

<span data-ttu-id="e1989-141">Bu bölümde, .NET Core 'u yüklemek için APT kullanırken karşılaşabileceğiniz yaygın hatalar hakkında bilgi verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e1989-141">This section provides information on common errors you may get while using APT to install .NET Core.</span></span>

### <a name="unable-to-locate"></a><span data-ttu-id="e1989-142">Bulunamıyor</span><span class="sxs-lookup"><span data-stu-id="e1989-142">Unable to locate</span></span>

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

### <a name="failed-to-fetch"></a><span data-ttu-id="e1989-143">Getirilemedi</span><span class="sxs-lookup"><span data-stu-id="e1989-143">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="snap"></a><span data-ttu-id="e1989-144">Bileşenlerinden</span><span class="sxs-lookup"><span data-stu-id="e1989-144">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="e1989-145">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="e1989-145">Dependencies</span></span>

[!INCLUDE [linux-install-dependencies](includes/linux-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="e1989-146">Komut dosyalı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="e1989-146">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="e1989-147">El ile yüklemesi</span><span class="sxs-lookup"><span data-stu-id="e1989-147">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="e1989-148">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="e1989-148">Next steps</span></span>

- [<span data-ttu-id="e1989-149">Öğretici: Visual Studio Code kullanarak .NET Core SDK bir konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="e1989-149">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
