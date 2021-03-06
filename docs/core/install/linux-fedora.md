---
title: .NET 'i Fedora-.NET üzerine yükler
description: Fedora üzerinde .NET SDK ve .NET çalışma zamanı yüklemenin çeşitli yollarını gösterir.
author: adegeo
ms.author: adegeo
ms.date: 02/17/2021
ms.openlocfilehash: efaad4788db2200b1a47f9b4ae2414730588c6ae
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255769"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-fedora"></a><span data-ttu-id="719a8-103">.NET SDK veya .NET çalışma zamanını Fedora 'ya yükler</span><span class="sxs-lookup"><span data-stu-id="719a8-103">Install the .NET SDK or the .NET Runtime on Fedora</span></span>

<span data-ttu-id="719a8-104">.NET, Fedora 'da desteklenir ve bu makalede, Fedora 'da .NET yüklemesi açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="719a8-104">.NET is supported on Fedora and this article describes how to install .NET on Fedora.</span></span> <span data-ttu-id="719a8-105">Bir Fedora sürümü destek dışı kaldığında, .NET artık bu sürümde desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="719a8-105">When a Fedora version falls out of support, .NET is no longer supported with that version.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

<span data-ttu-id="719a8-106">Bir paket yöneticisi olmadan .NET yükleme hakkında daha fazla bilgi için aşağıdaki makalelerden birine bakın:</span><span class="sxs-lookup"><span data-stu-id="719a8-106">For more information on installing .NET without a package manager, see one of the following articles:</span></span>

- [<span data-ttu-id="719a8-107">.NET SDK veya .NET çalışma zamanını yaslama ile birlikte yükler.</span><span class="sxs-lookup"><span data-stu-id="719a8-107">Install the .NET SDK or the .NET Runtime with Snap.</span></span>](linux-snap.md)
- [<span data-ttu-id="719a8-108">.NET SDK veya .NET çalışma zamanını bir komut dosyası ile birlikte yükler.</span><span class="sxs-lookup"><span data-stu-id="719a8-108">Install the .NET SDK or the .NET Runtime with a script.</span></span>](linux-scripted-manual.md#scripted-install)
- [<span data-ttu-id="719a8-109">.NET SDK veya .NET çalışma zamanını el ile yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="719a8-109">Install the .NET SDK or the .NET Runtime manually.</span></span>](linux-scripted-manual.md#manual-install)

## <a name="install-net-50"></a><span data-ttu-id="719a8-110">.NET 5,0 'yi yükler</span><span class="sxs-lookup"><span data-stu-id="719a8-110">Install .NET 5.0</span></span>

<span data-ttu-id="719a8-111">Fedora için varsayılan paket depolarında sunulan en son .NET sürümü .NET 5,0 ' dir.</span><span class="sxs-lookup"><span data-stu-id="719a8-111">The latest version of .NET available in the default package repositories for Fedora is .NET 5.0.</span></span>

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="install-net-core-31"></a><span data-ttu-id="719a8-112">.NET Core 3,1 'yi yükler</span><span class="sxs-lookup"><span data-stu-id="719a8-112">Install .NET Core 3.1</span></span>

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="supported-distributions"></a><span data-ttu-id="719a8-113">Desteklenen dağıtımlar</span><span class="sxs-lookup"><span data-stu-id="719a8-113">Supported distributions</span></span>

<span data-ttu-id="719a8-114">Aşağıdaki tabloda, şu anda desteklenen .NET sürümlerinin ve desteklenen Fedora sürümlerinin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="719a8-114">The following table is a list of currently supported .NET releases and the versions of Fedora they're supported on.</span></span> <span data-ttu-id="719a8-115">Bu sürümler, [.NET sürümü destek sonuna](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ya da [Fedora sürümü yaşam sonuna](https://fedoraproject.org/wiki/End_of_life)ulaşana kadar desteklenmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="719a8-115">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Fedora reaches end-of-life](https://fedoraproject.org/wiki/End_of_life).</span></span>

- <span data-ttu-id="719a8-116">✔️, Fedora veya .NET sürümünün hala desteklendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="719a8-116">A ✔️ indicates that the version of Fedora or .NET is still supported.</span></span>
- <span data-ttu-id="719a8-117">Bir ❌ , Fedora veya .NET sürümünün bu Fedora sürümünde desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="719a8-117">A ❌ indicates that the version of Fedora or .NET isn't supported on that Fedora release.</span></span>
- <span data-ttu-id="719a8-118">Hem Fedora hem de .NET sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="719a8-118">When both a version of Fedora and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="719a8-119">.NET sürümü</span><span class="sxs-lookup"><span data-stu-id="719a8-119">.NET Version</span></span>  | <span data-ttu-id="719a8-120">Fedora 33 ✔️</span><span class="sxs-lookup"><span data-stu-id="719a8-120">Fedora 33 ✔️</span></span> | <span data-ttu-id="719a8-121">32 ✔️</span><span class="sxs-lookup"><span data-stu-id="719a8-121">32 ✔️</span></span> | <span data-ttu-id="719a8-122">31 ❌</span><span class="sxs-lookup"><span data-stu-id="719a8-122">31 ❌</span></span> | <span data-ttu-id="719a8-123">ila ❌</span><span class="sxs-lookup"><span data-stu-id="719a8-123">30 ❌</span></span> | <span data-ttu-id="719a8-124">, ❌</span><span class="sxs-lookup"><span data-stu-id="719a8-124">29 ❌</span></span> | <span data-ttu-id="719a8-125">28.672 ❌</span><span class="sxs-lookup"><span data-stu-id="719a8-125">28 ❌</span></span> | <span data-ttu-id="719a8-126">döndürdü ❌</span><span class="sxs-lookup"><span data-stu-id="719a8-126">27 ❌</span></span> |
| ------------  | ---------: | --: | --: | --: | --: | --: | --: |
| <span data-ttu-id="719a8-127">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="719a8-127">.NET 5.0</span></span>      | <span data-ttu-id="719a8-128">✔️</span><span class="sxs-lookup"><span data-stu-id="719a8-128">✔️</span></span>        | <span data-ttu-id="719a8-129">✔️</span><span class="sxs-lookup"><span data-stu-id="719a8-129">✔️</span></span> | ❌|❌ |❌ |❌  |❌ |
| <span data-ttu-id="719a8-130">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="719a8-130">.NET Core 3.1</span></span> | <span data-ttu-id="719a8-131">✔️</span><span class="sxs-lookup"><span data-stu-id="719a8-131">✔️</span></span>        | <span data-ttu-id="719a8-132">✔️</span><span class="sxs-lookup"><span data-stu-id="719a8-132">✔️</span></span> | <span data-ttu-id="719a8-133">✔️</span><span class="sxs-lookup"><span data-stu-id="719a8-133">✔️</span></span>|<span data-ttu-id="719a8-134">✔️</span><span class="sxs-lookup"><span data-stu-id="719a8-134">✔️</span></span> |<span data-ttu-id="719a8-135">✔️</span><span class="sxs-lookup"><span data-stu-id="719a8-135">✔️</span></span> |❌  |❌ |
| <span data-ttu-id="719a8-136">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="719a8-136">.NET Core 2.1</span></span> | <span data-ttu-id="719a8-137">✔️</span><span class="sxs-lookup"><span data-stu-id="719a8-137">✔️</span></span>        | <span data-ttu-id="719a8-138">✔️</span><span class="sxs-lookup"><span data-stu-id="719a8-138">✔️</span></span> | <span data-ttu-id="719a8-139">✔️</span><span class="sxs-lookup"><span data-stu-id="719a8-139">✔️</span></span>|<span data-ttu-id="719a8-140">✔️</span><span class="sxs-lookup"><span data-stu-id="719a8-140">✔️</span></span> |<span data-ttu-id="719a8-141">✔️</span><span class="sxs-lookup"><span data-stu-id="719a8-141">✔️</span></span> |<span data-ttu-id="719a8-142">✔️</span><span class="sxs-lookup"><span data-stu-id="719a8-142">✔️</span></span>  |<span data-ttu-id="719a8-143">✔️</span><span class="sxs-lookup"><span data-stu-id="719a8-143">✔️</span></span> |

<span data-ttu-id="719a8-144">Aşağıdaki .NET sürümleri artık desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="719a8-144">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="719a8-145">Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:</span><span class="sxs-lookup"><span data-stu-id="719a8-145">The downloads for these still remain published:</span></span>

- <span data-ttu-id="719a8-146">3.0</span><span class="sxs-lookup"><span data-stu-id="719a8-146">3.0</span></span>
- <span data-ttu-id="719a8-147">2,2</span><span class="sxs-lookup"><span data-stu-id="719a8-147">2.2</span></span>
- <span data-ttu-id="719a8-148">2.0</span><span class="sxs-lookup"><span data-stu-id="719a8-148">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="719a8-149">Önizleme sürümlerini Kaldır</span><span class="sxs-lookup"><span data-stu-id="719a8-149">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="dependencies"></a><span data-ttu-id="719a8-150">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="719a8-150">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="install-on-older-distributions"></a><span data-ttu-id="719a8-151">Daha eski dağıtımlarla yüklensin</span><span class="sxs-lookup"><span data-stu-id="719a8-151">Install on older distributions</span></span>

<span data-ttu-id="719a8-152">Eski Fedora sürümleri, varsayılan paket depolarında .NET Core içermez.</span><span class="sxs-lookup"><span data-stu-id="719a8-152">Older versions of Fedora don't contain .NET Core in the default package repositories.</span></span> <span data-ttu-id="719a8-153">[ _DotNet-install.sh_ betiği](linux-scripted-manual.md#scripted-install)aracılığıyla .net 'i [Snap](linux-snap.md)Ile yükleyebilir veya .net yüklemek için Microsoft 'un deposunu kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="719a8-153">You can install .NET with [snap](linux-snap.md), through the [_dotnet-install.sh_ script](linux-scripted-manual.md#scripted-install), or use Microsoft's repository to install .NET:</span></span>

01. <span data-ttu-id="719a8-154">Öncelikle, güvenilen anahtarlar listenize Microsoft imzalama anahtarını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="719a8-154">First, add the Microsoft signing key to your list of trusted keys.</span></span>

    ```bash
    sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
    ```

02. <span data-ttu-id="719a8-155">Ardından, Microsoft paket deposunu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="719a8-155">Next, add the Microsoft package repository.</span></span> <span data-ttu-id="719a8-156">Deponun kaynağı Fedora sürümünüzü temel alır.</span><span class="sxs-lookup"><span data-stu-id="719a8-156">The source of the repository is based on your version of Fedora.</span></span>

    | <span data-ttu-id="719a8-157">Fedora sürümü</span><span class="sxs-lookup"><span data-stu-id="719a8-157">Fedora Version</span></span> | <span data-ttu-id="719a8-158">Paket deposu</span><span class="sxs-lookup"><span data-stu-id="719a8-158">Package repository</span></span> |
    | -------------- | ------- |
    | <span data-ttu-id="719a8-159">31</span><span class="sxs-lookup"><span data-stu-id="719a8-159">31</span></span>             | `https://packages.microsoft.com/config/fedora/31/prod.repo` |
    | <span data-ttu-id="719a8-160">30</span><span class="sxs-lookup"><span data-stu-id="719a8-160">30</span></span>             | `https://packages.microsoft.com/config/fedora/30/prod.repo` |
    | <span data-ttu-id="719a8-161">29</span><span class="sxs-lookup"><span data-stu-id="719a8-161">29</span></span>             | `https://packages.microsoft.com/config/fedora/29/prod.repo` |
    | <span data-ttu-id="719a8-162">28</span><span class="sxs-lookup"><span data-stu-id="719a8-162">28</span></span>             | `https://packages.microsoft.com/config/fedora/28/prod.repo` |
    | <span data-ttu-id="719a8-163">27</span><span class="sxs-lookup"><span data-stu-id="719a8-163">27</span></span>             | `https://packages.microsoft.com/config/fedora/27/prod.repo` |

    ```bash
    sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
    ```

[!INCLUDE [linux-dnf-install-31](./includes/linux-install-31-dnf.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="719a8-164">Diğer sürümleri nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="719a8-164">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="719a8-165">Paket yöneticisinin sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="719a8-165">Troubleshoot the package manager</span></span>

<span data-ttu-id="719a8-166">Bu bölüm, .NET veya .NET Core 'u yüklemek için Paket Yöneticisi 'ni kullanırken karşılaşabileceğiniz yaygın hatalarla ilgili bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="719a8-166">This section provides information on common errors you may get while using the package manager to install .NET or .NET Core.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="719a8-167">Paket bulunamadı</span><span class="sxs-lookup"><span data-stu-id="719a8-167">Unable to find package</span></span>

<span data-ttu-id="719a8-168">Bir paket yöneticisi olmadan .NET yükleme hakkında daha fazla bilgi için aşağıdaki makalelerden birine bakın:</span><span class="sxs-lookup"><span data-stu-id="719a8-168">For more information on installing .NET without a package manager, see one of the following articles:</span></span>

- [<span data-ttu-id="719a8-169">.NET SDK veya .NET çalışma zamanını yaslama ile birlikte yükler.</span><span class="sxs-lookup"><span data-stu-id="719a8-169">Install the .NET SDK or the .NET Runtime with Snap.</span></span>](linux-snap.md)
- [<span data-ttu-id="719a8-170">.NET SDK veya .NET çalışma zamanını bir komut dosyası ile birlikte yükler.</span><span class="sxs-lookup"><span data-stu-id="719a8-170">Install the .NET SDK or the .NET Runtime with a script.</span></span>](linux-scripted-manual.md#scripted-install)
- [<span data-ttu-id="719a8-171">.NET SDK veya .NET çalışma zamanını el ile yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="719a8-171">Install the .NET SDK or the .NET Runtime manually.</span></span>](linux-scripted-manual.md#manual-install)

### <a name="failed-to-fetch"></a><span data-ttu-id="719a8-172">Getirilemedi</span><span class="sxs-lookup"><span data-stu-id="719a8-172">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="next-steps"></a><span data-ttu-id="719a8-173">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="719a8-173">Next steps</span></span>

- [<span data-ttu-id="719a8-174">.NET CLı için sekme tamamlamayı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="719a8-174">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="719a8-175">Öğretici: Visual Studio Code kullanarak .NET SDK ile bir konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="719a8-175">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
