---
title: .NET 'i Fedora-.NET üzerine yükler
description: Fedora üzerinde .NET SDK ve .NET çalışma zamanı yüklemenin çeşitli yollarını gösterir.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 9dd8c6264831e2a9382960be505639f1eba95151
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970830"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-fedora"></a><span data-ttu-id="19cab-103">.NET SDK veya .NET çalışma zamanını Fedora 'ya yükler</span><span class="sxs-lookup"><span data-stu-id="19cab-103">Install the .NET SDK or the .NET Runtime on Fedora</span></span>

<span data-ttu-id="19cab-104">.NET, Fedora 'da desteklenir ve bu makalede, Fedora 'da .NET yüklemesi açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="19cab-104">.NET is supported on Fedora and this article describes how to install .NET on Fedora.</span></span> <span data-ttu-id="19cab-105">Bir Fedora sürümü destek dışı kaldığında, .NET artık bu sürümde desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="19cab-105">When a Fedora version falls out of support, .NET is no longer supported with that version.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="install-net-50"></a><span data-ttu-id="19cab-106">.NET 5,0 'yi yükler</span><span class="sxs-lookup"><span data-stu-id="19cab-106">Install .NET 5.0</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

<span data-ttu-id="19cab-107">**Fedora 32**</span><span class="sxs-lookup"><span data-stu-id="19cab-107">**Fedora 32**</span></span>

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/32/prod.repo
```

<span data-ttu-id="19cab-108">**Fedora 33**</span><span class="sxs-lookup"><span data-stu-id="19cab-108">**Fedora 33**</span></span>

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/33/prod.repo
```

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="install-net-core-31"></a><span data-ttu-id="19cab-109">.NET Core 3,1 'yi yükler</span><span class="sxs-lookup"><span data-stu-id="19cab-109">Install .NET Core 3.1</span></span>

<span data-ttu-id="19cab-110">Fedora için varsayılan paket depolarında sunulan en son .NET sürümü .NET Core 3,1 ' dir.</span><span class="sxs-lookup"><span data-stu-id="19cab-110">The latest version of .NET available in the default package repositories for Fedora is .NET Core 3.1.</span></span>

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="supported-distributions"></a><span data-ttu-id="19cab-111">Desteklenen dağıtımlar</span><span class="sxs-lookup"><span data-stu-id="19cab-111">Supported distributions</span></span>

<span data-ttu-id="19cab-112">Aşağıdaki tabloda, şu anda desteklenen .NET sürümlerinin ve desteklenen Fedora sürümlerinin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="19cab-112">The following table is a list of currently supported .NET releases and the versions of Fedora they're supported on.</span></span> <span data-ttu-id="19cab-113">Bu sürümler, [.NET sürümü destek sonuna](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ya da [Fedora sürümü yaşam sonuna](https://fedoraproject.org/wiki/End_of_life)ulaşana kadar desteklenmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="19cab-113">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Fedora reaches end-of-life](https://fedoraproject.org/wiki/End_of_life).</span></span>

- <span data-ttu-id="19cab-114">✔️, Fedora veya .NET sürümünün hala desteklendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="19cab-114">A ✔️ indicates that the version of Fedora or .NET is still supported.</span></span>
- <span data-ttu-id="19cab-115">Bir ❌ , Fedora veya .NET sürümünün bu Fedora sürümünde desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="19cab-115">A ❌ indicates that the version of Fedora or .NET isn't supported on that Fedora release.</span></span>
- <span data-ttu-id="19cab-116">Hem Fedora hem de .NET sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="19cab-116">When both a version of Fedora and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="19cab-117">.NET sürümü</span><span class="sxs-lookup"><span data-stu-id="19cab-117">.NET Version</span></span>  | <span data-ttu-id="19cab-118">Fedora 33 ✔️</span><span class="sxs-lookup"><span data-stu-id="19cab-118">Fedora 33 ✔️</span></span> | <span data-ttu-id="19cab-119">32 ✔️</span><span class="sxs-lookup"><span data-stu-id="19cab-119">32 ✔️</span></span> | <span data-ttu-id="19cab-120">31 ❌</span><span class="sxs-lookup"><span data-stu-id="19cab-120">31 ❌</span></span> | <span data-ttu-id="19cab-121">ila ❌</span><span class="sxs-lookup"><span data-stu-id="19cab-121">30 ❌</span></span> | <span data-ttu-id="19cab-122">, ❌</span><span class="sxs-lookup"><span data-stu-id="19cab-122">29 ❌</span></span> | <span data-ttu-id="19cab-123">28.672 ❌</span><span class="sxs-lookup"><span data-stu-id="19cab-123">28 ❌</span></span> | <span data-ttu-id="19cab-124">döndürdü ❌</span><span class="sxs-lookup"><span data-stu-id="19cab-124">27 ❌</span></span> |
| ------------  | ---------: | --: | --: | --: | --: | --: | --: |
| <span data-ttu-id="19cab-125">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="19cab-125">.NET 5.0</span></span>      | <span data-ttu-id="19cab-126">✔️</span><span class="sxs-lookup"><span data-stu-id="19cab-126">✔️</span></span>        | <span data-ttu-id="19cab-127">✔️</span><span class="sxs-lookup"><span data-stu-id="19cab-127">✔️</span></span> | ❌|❌ |❌ |❌  |❌ |
| <span data-ttu-id="19cab-128">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="19cab-128">.NET Core 3.1</span></span> | <span data-ttu-id="19cab-129">✔️</span><span class="sxs-lookup"><span data-stu-id="19cab-129">✔️</span></span>        | <span data-ttu-id="19cab-130">✔️</span><span class="sxs-lookup"><span data-stu-id="19cab-130">✔️</span></span> | <span data-ttu-id="19cab-131">✔️</span><span class="sxs-lookup"><span data-stu-id="19cab-131">✔️</span></span>|<span data-ttu-id="19cab-132">✔️</span><span class="sxs-lookup"><span data-stu-id="19cab-132">✔️</span></span> |<span data-ttu-id="19cab-133">✔️</span><span class="sxs-lookup"><span data-stu-id="19cab-133">✔️</span></span> |❌  |❌ |
| <span data-ttu-id="19cab-134">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="19cab-134">.NET Core 2.1</span></span> | <span data-ttu-id="19cab-135">✔️</span><span class="sxs-lookup"><span data-stu-id="19cab-135">✔️</span></span>        | <span data-ttu-id="19cab-136">✔️</span><span class="sxs-lookup"><span data-stu-id="19cab-136">✔️</span></span> | <span data-ttu-id="19cab-137">✔️</span><span class="sxs-lookup"><span data-stu-id="19cab-137">✔️</span></span>|<span data-ttu-id="19cab-138">✔️</span><span class="sxs-lookup"><span data-stu-id="19cab-138">✔️</span></span> |<span data-ttu-id="19cab-139">✔️</span><span class="sxs-lookup"><span data-stu-id="19cab-139">✔️</span></span> |<span data-ttu-id="19cab-140">✔️</span><span class="sxs-lookup"><span data-stu-id="19cab-140">✔️</span></span>  |<span data-ttu-id="19cab-141">✔️</span><span class="sxs-lookup"><span data-stu-id="19cab-141">✔️</span></span> |

<span data-ttu-id="19cab-142">Aşağıdaki .NET sürümleri artık desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="19cab-142">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="19cab-143">Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:</span><span class="sxs-lookup"><span data-stu-id="19cab-143">The downloads for these still remain published:</span></span>

- <span data-ttu-id="19cab-144">3,0</span><span class="sxs-lookup"><span data-stu-id="19cab-144">3.0</span></span>
- <span data-ttu-id="19cab-145">2.2</span><span class="sxs-lookup"><span data-stu-id="19cab-145">2.2</span></span>
- <span data-ttu-id="19cab-146">2.0</span><span class="sxs-lookup"><span data-stu-id="19cab-146">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="19cab-147">Önizleme sürümlerini Kaldır</span><span class="sxs-lookup"><span data-stu-id="19cab-147">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="dependencies"></a><span data-ttu-id="19cab-148">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="19cab-148">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="install-on-older-distributions"></a><span data-ttu-id="19cab-149">Daha eski dağıtımlarla yüklensin</span><span class="sxs-lookup"><span data-stu-id="19cab-149">Install on older distributions</span></span>

<span data-ttu-id="19cab-150">Eski Fedora sürümleri, varsayılan paket depolarında .NET Core içermez.</span><span class="sxs-lookup"><span data-stu-id="19cab-150">Older versions of Fedora don't contain .NET Core in the default package repositories.</span></span> <span data-ttu-id="19cab-151">[ _DotNet-install.sh_ betiği](linux-scripted-manual.md#scripted-install)aracılığıyla .net 'i [Snap](linux-snap.md)Ile yükleyebilir veya .net yüklemek için Microsoft 'un deposunu kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="19cab-151">You can install .NET with [snap](linux-snap.md), through the [_dotnet-install.sh_ script](linux-scripted-manual.md#scripted-install), or use Microsoft's repository to install .NET:</span></span>

01. <span data-ttu-id="19cab-152">Öncelikle, güvenilen anahtarlar listenize Microsoft imzalama anahtarını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="19cab-152">First, add the Microsoft signing key to your list of trusted keys.</span></span>

    ```bash
    sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
    ```

02. <span data-ttu-id="19cab-153">Ardından, Microsoft paket deposunu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="19cab-153">Next, add the Microsoft package repository.</span></span> <span data-ttu-id="19cab-154">Deponun kaynağı Fedora sürümünüzü temel alır.</span><span class="sxs-lookup"><span data-stu-id="19cab-154">The source of the repository is based on your version of Fedora.</span></span>

    | <span data-ttu-id="19cab-155">Fedora sürümü</span><span class="sxs-lookup"><span data-stu-id="19cab-155">Fedora Version</span></span> | <span data-ttu-id="19cab-156">Paket deposu</span><span class="sxs-lookup"><span data-stu-id="19cab-156">Package repository</span></span> |
    | -------------- | ------- |
    | <span data-ttu-id="19cab-157">31</span><span class="sxs-lookup"><span data-stu-id="19cab-157">31</span></span>             | `https://packages.microsoft.com/config/fedora/31/prod.repo` |
    | <span data-ttu-id="19cab-158">30</span><span class="sxs-lookup"><span data-stu-id="19cab-158">30</span></span>             | `https://packages.microsoft.com/config/fedora/30/prod.repo` |
    | <span data-ttu-id="19cab-159">29</span><span class="sxs-lookup"><span data-stu-id="19cab-159">29</span></span>             | `https://packages.microsoft.com/config/fedora/29/prod.repo` |
    | <span data-ttu-id="19cab-160">28</span><span class="sxs-lookup"><span data-stu-id="19cab-160">28</span></span>             | `https://packages.microsoft.com/config/fedora/28/prod.repo` |
    | <span data-ttu-id="19cab-161">27</span><span class="sxs-lookup"><span data-stu-id="19cab-161">27</span></span>             | `https://packages.microsoft.com/config/fedora/27/prod.repo` |

    ```bash
    sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
    ```

[!INCLUDE [linux-dnf-install-31](./includes/linux-install-31-dnf.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="19cab-162">Diğer sürümleri nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="19cab-162">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="19cab-163">Paket yöneticisinin sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="19cab-163">Troubleshoot the package manager</span></span>

<span data-ttu-id="19cab-164">Bu bölüm, .NET veya .NET Core 'u yüklemek için Paket Yöneticisi 'ni kullanırken karşılaşabileceğiniz yaygın hatalarla ilgili bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="19cab-164">This section provides information on common errors you may get while using the package manager to install .NET or .NET Core.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="19cab-165">Paket bulunamadı</span><span class="sxs-lookup"><span data-stu-id="19cab-165">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a><span data-ttu-id="19cab-166">Getirilemedi</span><span class="sxs-lookup"><span data-stu-id="19cab-166">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="next-steps"></a><span data-ttu-id="19cab-167">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="19cab-167">Next steps</span></span>

- [<span data-ttu-id="19cab-168">.NET CLı için sekme tamamlamayı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="19cab-168">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="19cab-169">Öğretici: Visual Studio Code kullanarak .NET SDK ile bir konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="19cab-169">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
