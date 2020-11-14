---
title: .NET 'i Fedora-.NET üzerine yükler
description: Fedora üzerinde .NET SDK ve .NET çalışma zamanı yüklemenin çeşitli yollarını gösterir.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 9e96773e30fb8ee395e37dca7a4794cd42359bb2
ms.sourcegitcommit: c38bf879a2611ff46aacdd529b9f2725f93e18a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/13/2020
ms.locfileid: "94594618"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-fedora"></a><span data-ttu-id="5f4ea-103">.NET SDK veya .NET çalışma zamanını Fedora 'ya yükler</span><span class="sxs-lookup"><span data-stu-id="5f4ea-103">Install the .NET SDK or the .NET Runtime on Fedora</span></span>

<span data-ttu-id="5f4ea-104">.NET, Fedora 'da desteklenir.</span><span class="sxs-lookup"><span data-stu-id="5f4ea-104">.NET is supported on Fedora.</span></span> <span data-ttu-id="5f4ea-105">Bu makalede, Fedora 'da .NET yüklemesi açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5f4ea-105">This article describes how to install .NET on Fedora.</span></span> <span data-ttu-id="5f4ea-106">Bir Fedora sürümü destek dışı kaldığında, .NET artık bu sürümde desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="5f4ea-106">When a Fedora version falls out of support, .NET is no longer supported with that version.</span></span> <span data-ttu-id="5f4ea-107">Ancak, bu yönergeler desteklenmese de bu sürümler üzerinde çalışan .NET almanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="5f4ea-107">However, these instructions may help you to get .NET running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="5f4ea-108">Desteklenen dağıtımlar</span><span class="sxs-lookup"><span data-stu-id="5f4ea-108">Supported distributions</span></span>

<span data-ttu-id="5f4ea-109">Aşağıdaki tabloda, şu anda desteklenen .NET sürümlerinin ve desteklenen Fedora sürümlerinin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5f4ea-109">The following table is a list of currently supported .NET releases and the versions of Fedora they're supported on.</span></span> <span data-ttu-id="5f4ea-110">Bu sürümler, [.NET sürümü destek sonuna](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ya da [Fedora sürümü yaşam sonuna](https://fedoraproject.org/wiki/End_of_life)ulaşana kadar desteklenmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="5f4ea-110">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Fedora reaches end-of-life](https://fedoraproject.org/wiki/End_of_life).</span></span>

- <span data-ttu-id="5f4ea-111">✔️, Fedora veya .NET sürümünün hala desteklendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5f4ea-111">A ✔️ indicates that the version of Fedora or .NET is still supported.</span></span>
- <span data-ttu-id="5f4ea-112">Bir ❌ , Fedora veya .NET sürümünün bu Fedora sürümünde desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5f4ea-112">A ❌ indicates that the version of Fedora or .NET isn't supported on that Fedora release.</span></span>
- <span data-ttu-id="5f4ea-113">Hem Fedora hem de .NET sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="5f4ea-113">When both a version of Fedora and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="5f4ea-114">Fedora</span><span class="sxs-lookup"><span data-stu-id="5f4ea-114">Fedora</span></span>               | <span data-ttu-id="5f4ea-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="5f4ea-115">.NET Core 2.1</span></span> | <span data-ttu-id="5f4ea-116">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="5f4ea-116">.NET Core 3.1</span></span> | <span data-ttu-id="5f4ea-117">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="5f4ea-117">.NET 5.0</span></span> |
|----------------------|---------------|---------------|----------|
| <span data-ttu-id="5f4ea-118">✔️ [33](#fedora-33-)</span><span class="sxs-lookup"><span data-stu-id="5f4ea-118">✔️ [33](#fedora-33-)</span></span> | <span data-ttu-id="5f4ea-119">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="5f4ea-119">✔️ 2.1</span></span>        | <span data-ttu-id="5f4ea-120">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="5f4ea-120">✔️ 3.1</span></span>        | <span data-ttu-id="5f4ea-121">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="5f4ea-121">✔️ 5.0</span></span> |
| <span data-ttu-id="5f4ea-122">✔️ [32](#fedora-32-)</span><span class="sxs-lookup"><span data-stu-id="5f4ea-122">✔️ [32](#fedora-32-)</span></span> | <span data-ttu-id="5f4ea-123">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="5f4ea-123">✔️ 2.1</span></span>        | <span data-ttu-id="5f4ea-124">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="5f4ea-124">✔️ 3.1</span></span>        | <span data-ttu-id="5f4ea-125">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="5f4ea-125">✔️ 5.0</span></span> |
| <span data-ttu-id="5f4ea-126">❌[31](#fedora-31-)</span><span class="sxs-lookup"><span data-stu-id="5f4ea-126">❌ [31](#fedora-31-)</span></span> | <span data-ttu-id="5f4ea-127">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="5f4ea-127">✔️ 2.1</span></span>        | <span data-ttu-id="5f4ea-128">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="5f4ea-128">✔️ 3.1</span></span>        | <span data-ttu-id="5f4ea-129">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="5f4ea-129">❌ 5.0</span></span> |
| <span data-ttu-id="5f4ea-130">❌[30](#fedora-30-)</span><span class="sxs-lookup"><span data-stu-id="5f4ea-130">❌ [30](#fedora-30-)</span></span> | <span data-ttu-id="5f4ea-131">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="5f4ea-131">✔️ 2.1</span></span>        | <span data-ttu-id="5f4ea-132">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="5f4ea-132">✔️ 3.1</span></span>        | <span data-ttu-id="5f4ea-133">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="5f4ea-133">❌ 5.0</span></span> |
| <span data-ttu-id="5f4ea-134">❌[29](#fedora-29-)</span><span class="sxs-lookup"><span data-stu-id="5f4ea-134">❌ [29](#fedora-29-)</span></span> | <span data-ttu-id="5f4ea-135">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="5f4ea-135">✔️ 2.1</span></span>        | <span data-ttu-id="5f4ea-136">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="5f4ea-136">✔️ 3.1</span></span>        | <span data-ttu-id="5f4ea-137">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="5f4ea-137">❌ 5.0</span></span> |
| <span data-ttu-id="5f4ea-138">❌[28](#fedora-28-)</span><span class="sxs-lookup"><span data-stu-id="5f4ea-138">❌ [28](#fedora-28-)</span></span> | <span data-ttu-id="5f4ea-139">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="5f4ea-139">✔️ 2.1</span></span>        | <span data-ttu-id="5f4ea-140">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="5f4ea-140">❌ 3.1</span></span>        | <span data-ttu-id="5f4ea-141">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="5f4ea-141">❌ 5.0</span></span> |
| <span data-ttu-id="5f4ea-142">❌[27](#fedora-27-)</span><span class="sxs-lookup"><span data-stu-id="5f4ea-142">❌ [27](#fedora-27-)</span></span> | <span data-ttu-id="5f4ea-143">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="5f4ea-143">✔️ 2.1</span></span>        | <span data-ttu-id="5f4ea-144">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="5f4ea-144">❌ 3.1</span></span>        | <span data-ttu-id="5f4ea-145">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="5f4ea-145">❌ 5.0</span></span> |

<span data-ttu-id="5f4ea-146">Aşağıdaki .NET sürümleri artık desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="5f4ea-146">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="5f4ea-147">Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:</span><span class="sxs-lookup"><span data-stu-id="5f4ea-147">The downloads for these still remain published:</span></span>

- <span data-ttu-id="5f4ea-148">3,0</span><span class="sxs-lookup"><span data-stu-id="5f4ea-148">3.0</span></span>
- <span data-ttu-id="5f4ea-149">2.2</span><span class="sxs-lookup"><span data-stu-id="5f4ea-149">2.2</span></span>
- <span data-ttu-id="5f4ea-150">2,0</span><span class="sxs-lookup"><span data-stu-id="5f4ea-150">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="5f4ea-151">Diğer sürümleri nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="5f4ea-151">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="fedora-33-"></a><span data-ttu-id="5f4ea-152">Fedora 33 ✔️</span><span class="sxs-lookup"><span data-stu-id="5f4ea-152">Fedora 33 ✔️</span></span>

> [!TIP]
> <span data-ttu-id="5f4ea-153">.NET Core 3,1, Fedora 33 için varsayılan paket depolarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5f4ea-153">.NET Core 3.1 is available in the default package repositories for Fedora 33.</span></span> <span data-ttu-id="5f4ea-154">.NET Core 3,1 yüklemek için, veya gibi `dnf install` uygun Paketle komutunu kullanın `aspnetcore-runtime-3.1` `dotnet-sdk-3.1` .</span><span class="sxs-lookup"><span data-stu-id="5f4ea-154">To install .NET Core 3.1, use the `dnf install` command with the appropriate package, such as `aspnetcore-runtime-3.1` or `dotnet-sdk-3.1`.</span></span> <span data-ttu-id="5f4ea-155">.NET 5,0 henüz varsayılan paket depolarında kullanılabilir değildir.</span><span class="sxs-lookup"><span data-stu-id="5f4ea-155">.NET 5.0 isn't yet available in the default package repositories.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/33/prod.repo
```

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="fedora-32-"></a><span data-ttu-id="5f4ea-156">Fedora 32 ✔️</span><span class="sxs-lookup"><span data-stu-id="5f4ea-156">Fedora 32 ✔️</span></span>

> [!TIP]
> <span data-ttu-id="5f4ea-157">.NET Core 3,1, Fedora 32 için varsayılan paket depolarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5f4ea-157">.NET Core 3.1 is available in the default package repositories for Fedora 32.</span></span> <span data-ttu-id="5f4ea-158">.NET Core 3,1 yüklemek için, veya gibi `dnf install` uygun Paketle komutunu kullanın `aspnetcore-runtime-3.1` `dotnet-sdk-3.1` .</span><span class="sxs-lookup"><span data-stu-id="5f4ea-158">To install .NET Core 3.1, use the `dnf install` command with the appropriate package, such as `aspnetcore-runtime-3.1` or `dotnet-sdk-3.1`.</span></span> <span data-ttu-id="5f4ea-159">.NET 5,0 henüz varsayılan paket depolarında kullanılabilir değildir.</span><span class="sxs-lookup"><span data-stu-id="5f4ea-159">.NET 5.0 isn't yet available in the default package repositories.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/32/prod.repo
```

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="fedora-31-"></a><span data-ttu-id="5f4ea-160">Fedora 31 ❌</span><span class="sxs-lookup"><span data-stu-id="5f4ea-160">Fedora 31 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-30-"></a><span data-ttu-id="5f4ea-161">Fedora 30 ❌</span><span class="sxs-lookup"><span data-stu-id="5f4ea-161">Fedora 30 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/30/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-29-"></a><span data-ttu-id="5f4ea-162">Fedora 29 ❌</span><span class="sxs-lookup"><span data-stu-id="5f4ea-162">Fedora 29 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/29/prod.repo
```

[!INCLUDE [linux-dnf-install-30](includes/linux-install-30-dnf.md)]

## <a name="fedora-28-"></a><span data-ttu-id="5f4ea-163">Fedora 28 ❌</span><span class="sxs-lookup"><span data-stu-id="5f4ea-163">Fedora 28 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/28/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="fedora-27-"></a><span data-ttu-id="5f4ea-164">Fedora 27 ❌</span><span class="sxs-lookup"><span data-stu-id="5f4ea-164">Fedora 27 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/27/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="5f4ea-165">Paket yöneticisinin sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="5f4ea-165">Troubleshoot the package manager</span></span>

<span data-ttu-id="5f4ea-166">Bu bölüm, .NET Core 'u yüklemek için Paket Yöneticisi 'ni kullanırken karşılaşabileceğiniz yaygın hatalarla ilgili bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5f4ea-166">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="5f4ea-167">Paket bulunamadı</span><span class="sxs-lookup"><span data-stu-id="5f4ea-167">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a><span data-ttu-id="5f4ea-168">Getirilemedi</span><span class="sxs-lookup"><span data-stu-id="5f4ea-168">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="5f4ea-169">Bileşenlerinden</span><span class="sxs-lookup"><span data-stu-id="5f4ea-169">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="5f4ea-170">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="5f4ea-170">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="5f4ea-171">Komut dosyalı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="5f4ea-171">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="5f4ea-172">El ile yüklemesi</span><span class="sxs-lookup"><span data-stu-id="5f4ea-172">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="5f4ea-173">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="5f4ea-173">Next steps</span></span>

- [<span data-ttu-id="5f4ea-174">Öğretici: Visual Studio Code kullanarak .NET SDK ile bir konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="5f4ea-174">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
