---
title: .NET 'i Fedora-.NET üzerine yükler
description: Fedora üzerinde .NET SDK ve .NET çalışma zamanı yüklemenin çeşitli yollarını gösterir.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: d5b5886f8b29e0f8e935850686cc84f78c55be02
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507080"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-fedora"></a><span data-ttu-id="0bb88-103">.NET SDK veya .NET çalışma zamanını Fedora 'ya yükler</span><span class="sxs-lookup"><span data-stu-id="0bb88-103">Install the .NET SDK or the .NET Runtime on Fedora</span></span>

<span data-ttu-id="0bb88-104">.NET, Fedora 'da desteklenir.</span><span class="sxs-lookup"><span data-stu-id="0bb88-104">.NET is supported on Fedora.</span></span> <span data-ttu-id="0bb88-105">Bu makalede, Fedora 'da .NET yüklemesi açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0bb88-105">This article describes how to install .NET on Fedora.</span></span> <span data-ttu-id="0bb88-106">Bir Fedora sürümü destek dışı kaldığında, .NET artık bu sürümde desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="0bb88-106">When a Fedora version falls out of support, .NET is no longer supported with that version.</span></span> <span data-ttu-id="0bb88-107">Ancak, bu yönergeler desteklenmese de bu sürümler üzerinde çalışan .NET almanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="0bb88-107">However, these instructions may help you to get .NET running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="0bb88-108">Desteklenen dağıtımlar</span><span class="sxs-lookup"><span data-stu-id="0bb88-108">Supported distributions</span></span>

<span data-ttu-id="0bb88-109">Aşağıdaki tabloda, şu anda desteklenen .NET sürümlerinin ve desteklenen Fedora sürümlerinin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0bb88-109">The following table is a list of currently supported .NET releases and the versions of Fedora they're supported on.</span></span> <span data-ttu-id="0bb88-110">Bu sürümler, [.NET sürümü destek sonuna](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ya da [Fedora sürümü yaşam sonuna](https://fedoraproject.org/wiki/End_of_life)ulaşana kadar desteklenmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="0bb88-110">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Fedora reaches end-of-life](https://fedoraproject.org/wiki/End_of_life).</span></span>

- <span data-ttu-id="0bb88-111">✔️, Fedora veya .NET sürümünün hala desteklendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0bb88-111">A ✔️ indicates that the version of Fedora or .NET is still supported.</span></span>
- <span data-ttu-id="0bb88-112">Bir ❌ , Fedora veya .NET sürümünün bu Fedora sürümünde desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0bb88-112">A ❌ indicates that the version of Fedora or .NET isn't supported on that Fedora release.</span></span>
- <span data-ttu-id="0bb88-113">Hem Fedora hem de .NET sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="0bb88-113">When both a version of Fedora and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="0bb88-114">Fedora</span><span class="sxs-lookup"><span data-stu-id="0bb88-114">Fedora</span></span>               | <span data-ttu-id="0bb88-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="0bb88-115">.NET Core 2.1</span></span> | <span data-ttu-id="0bb88-116">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="0bb88-116">.NET Core 3.1</span></span> | <span data-ttu-id="0bb88-117">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="0bb88-117">.NET 5.0</span></span> |
|----------------------|---------------|---------------|----------|
| <span data-ttu-id="0bb88-118">✔️ [33](#fedora-33-)</span><span class="sxs-lookup"><span data-stu-id="0bb88-118">✔️ [33](#fedora-33-)</span></span> | <span data-ttu-id="0bb88-119">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="0bb88-119">✔️ 2.1</span></span>        | <span data-ttu-id="0bb88-120">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="0bb88-120">✔️ 3.1</span></span>        | <span data-ttu-id="0bb88-121">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="0bb88-121">✔️ 5.0</span></span> |
| <span data-ttu-id="0bb88-122">✔️ [32](#fedora-32-)</span><span class="sxs-lookup"><span data-stu-id="0bb88-122">✔️ [32](#fedora-32-)</span></span> | <span data-ttu-id="0bb88-123">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="0bb88-123">✔️ 2.1</span></span>        | <span data-ttu-id="0bb88-124">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="0bb88-124">✔️ 3.1</span></span>        | <span data-ttu-id="0bb88-125">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="0bb88-125">✔️ 5.0</span></span> |
| <span data-ttu-id="0bb88-126">❌[31](#fedora-31-)</span><span class="sxs-lookup"><span data-stu-id="0bb88-126">❌ [31](#fedora-31-)</span></span> | <span data-ttu-id="0bb88-127">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="0bb88-127">✔️ 2.1</span></span>        | <span data-ttu-id="0bb88-128">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="0bb88-128">✔️ 3.1</span></span>        | <span data-ttu-id="0bb88-129">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="0bb88-129">❌ 5.0</span></span> |
| <span data-ttu-id="0bb88-130">❌[30](#fedora-30-)</span><span class="sxs-lookup"><span data-stu-id="0bb88-130">❌ [30](#fedora-30-)</span></span> | <span data-ttu-id="0bb88-131">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="0bb88-131">✔️ 2.1</span></span>        | <span data-ttu-id="0bb88-132">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="0bb88-132">✔️ 3.1</span></span>        | <span data-ttu-id="0bb88-133">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="0bb88-133">❌ 5.0</span></span> |
| <span data-ttu-id="0bb88-134">❌[29](#fedora-29-)</span><span class="sxs-lookup"><span data-stu-id="0bb88-134">❌ [29](#fedora-29-)</span></span> | <span data-ttu-id="0bb88-135">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="0bb88-135">✔️ 2.1</span></span>        | <span data-ttu-id="0bb88-136">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="0bb88-136">✔️ 3.1</span></span>        | <span data-ttu-id="0bb88-137">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="0bb88-137">❌ 5.0</span></span> |
| <span data-ttu-id="0bb88-138">❌[28](#fedora-28-)</span><span class="sxs-lookup"><span data-stu-id="0bb88-138">❌ [28](#fedora-28-)</span></span> | <span data-ttu-id="0bb88-139">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="0bb88-139">✔️ 2.1</span></span>        | <span data-ttu-id="0bb88-140">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="0bb88-140">❌ 3.1</span></span>        | <span data-ttu-id="0bb88-141">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="0bb88-141">❌ 5.0</span></span> |
| <span data-ttu-id="0bb88-142">❌[27](#fedora-27-)</span><span class="sxs-lookup"><span data-stu-id="0bb88-142">❌ [27](#fedora-27-)</span></span> | <span data-ttu-id="0bb88-143">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="0bb88-143">✔️ 2.1</span></span>        | <span data-ttu-id="0bb88-144">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="0bb88-144">❌ 3.1</span></span>        | <span data-ttu-id="0bb88-145">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="0bb88-145">❌ 5.0</span></span> |

<span data-ttu-id="0bb88-146">Aşağıdaki .NET sürümleri artık desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="0bb88-146">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="0bb88-147">Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:</span><span class="sxs-lookup"><span data-stu-id="0bb88-147">The downloads for these still remain published:</span></span>

- <span data-ttu-id="0bb88-148">3,0</span><span class="sxs-lookup"><span data-stu-id="0bb88-148">3.0</span></span>
- <span data-ttu-id="0bb88-149">2.2</span><span class="sxs-lookup"><span data-stu-id="0bb88-149">2.2</span></span>
- <span data-ttu-id="0bb88-150">2,0</span><span class="sxs-lookup"><span data-stu-id="0bb88-150">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="0bb88-151">Diğer sürümleri nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="0bb88-151">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="fedora-33-"></a><span data-ttu-id="0bb88-152">Fedora 33 ✔️</span><span class="sxs-lookup"><span data-stu-id="0bb88-152">Fedora 33 ✔️</span></span>

<span data-ttu-id="0bb88-153">.NET 5 ve .NET Core 3,1, Fedora 33 için varsayılan paket depolarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0bb88-153">.NET 5 and .NET Core 3.1 are available in the default package repositories for Fedora 33.</span></span>

[!INCLUDE [linux-dnf-install-31](includes/linux-install-50-dnf.md)]

## <a name="fedora-32-"></a><span data-ttu-id="0bb88-154">Fedora 32 ✔️</span><span class="sxs-lookup"><span data-stu-id="0bb88-154">Fedora 32 ✔️</span></span>

<span data-ttu-id="0bb88-155">.NET Core 3,1, Fedora 32 için varsayılan paket depolarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0bb88-155">.NET Core 3.1 is available in the default package repositories for Fedora 32.</span></span>

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-31-"></a><span data-ttu-id="0bb88-156">Fedora 31 ❌</span><span class="sxs-lookup"><span data-stu-id="0bb88-156">Fedora 31 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-30-"></a><span data-ttu-id="0bb88-157">Fedora 30 ❌</span><span class="sxs-lookup"><span data-stu-id="0bb88-157">Fedora 30 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/30/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-29-"></a><span data-ttu-id="0bb88-158">Fedora 29 ❌</span><span class="sxs-lookup"><span data-stu-id="0bb88-158">Fedora 29 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/29/prod.repo
```

[!INCLUDE [linux-dnf-install-30](includes/linux-install-30-dnf.md)]

## <a name="fedora-28-"></a><span data-ttu-id="0bb88-159">Fedora 28 ❌</span><span class="sxs-lookup"><span data-stu-id="0bb88-159">Fedora 28 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/28/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="fedora-27-"></a><span data-ttu-id="0bb88-160">Fedora 27 ❌</span><span class="sxs-lookup"><span data-stu-id="0bb88-160">Fedora 27 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/27/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="0bb88-161">Paket yöneticisinin sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="0bb88-161">Troubleshoot the package manager</span></span>

<span data-ttu-id="0bb88-162">Bu bölüm, .NET Core 'u yüklemek için Paket Yöneticisi 'ni kullanırken karşılaşabileceğiniz yaygın hatalarla ilgili bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0bb88-162">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="0bb88-163">Paket bulunamadı</span><span class="sxs-lookup"><span data-stu-id="0bb88-163">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a><span data-ttu-id="0bb88-164">Getirilemedi</span><span class="sxs-lookup"><span data-stu-id="0bb88-164">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="0bb88-165">Bileşenlerinden</span><span class="sxs-lookup"><span data-stu-id="0bb88-165">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="0bb88-166">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="0bb88-166">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="0bb88-167">Komut dosyalı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="0bb88-167">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="0bb88-168">El ile yüklemesi</span><span class="sxs-lookup"><span data-stu-id="0bb88-168">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="0bb88-169">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="0bb88-169">Next steps</span></span>

- [<span data-ttu-id="0bb88-170">Öğretici: Visual Studio Code kullanarak .NET SDK ile bir konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="0bb88-170">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
