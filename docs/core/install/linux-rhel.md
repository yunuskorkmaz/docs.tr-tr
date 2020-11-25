---
title: RHEL-.NET üzerinde .NET 'i yükler
description: RHEL üzerinde .NET SDK ve .NET çalışma zamanı yüklemek için çeşitli yollar gösterir.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 931cad51ff8e35ff16b67ff9b795feb36010a66b
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031788"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-rhel"></a><span data-ttu-id="382c5-103">RHEL üzerinde .NET SDK veya .NET çalışma zamanı 'nı yükler</span><span class="sxs-lookup"><span data-stu-id="382c5-103">Install the .NET SDK or the .NET Runtime on RHEL</span></span>

<span data-ttu-id="382c5-104">.NET, RHEL 'de desteklenir.</span><span class="sxs-lookup"><span data-stu-id="382c5-104">.NET is supported on RHEL.</span></span> <span data-ttu-id="382c5-105">Bu makalede, RHEL 'de .NET 'in nasıl yükleneceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="382c5-105">This article describes how to install .NET on RHEL.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="382c5-106">Red Hat aboneliğinizi kaydetme</span><span class="sxs-lookup"><span data-stu-id="382c5-106">Register your Red Hat subscription</span></span>

<span data-ttu-id="382c5-107">RHEL 'de Red Hat 'ten .NET yüklemek için önce Red Hat abonelik Yöneticisi 'Ni kullanarak kaydolmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="382c5-107">To install .NET from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="382c5-108">Bu, sisteminizde yapmadıysanız veya emin değilseniz, [.net Için Red Hat ürün belgelerine](https://access.redhat.com/documentation/net/5.0/)bakın.</span><span class="sxs-lookup"><span data-stu-id="382c5-108">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET](https://access.redhat.com/documentation/net/5.0/).</span></span>

## <a name="supported-distributions"></a><span data-ttu-id="382c5-109">Desteklenen dağıtımlar</span><span class="sxs-lookup"><span data-stu-id="382c5-109">Supported distributions</span></span>

<span data-ttu-id="382c5-110">Aşağıdaki tabloda, hem RHEL 7 hem de RHEL 8 üzerinde şu anda desteklenen .NET sürümlerinin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="382c5-110">The following table is a list of currently supported .NET releases on both RHEL 7 and RHEL 8.</span></span> <span data-ttu-id="382c5-111">Bu sürümler, [.NET sürümü destek sonu](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya RHEL sürümü artık desteklenene kadar desteklenmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="382c5-111">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of RHEL is no longer supported.</span></span>

- <span data-ttu-id="382c5-112">✔️, RHEL veya .NET sürümünün hala desteklendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="382c5-112">A ✔️ indicates that the version of RHEL or .NET is still supported.</span></span>
- <span data-ttu-id="382c5-113">A ❌ , RHEL veya .NET sürümünün bu RHEL sürümünde desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="382c5-113">A ❌ indicates that the version of RHEL or .NET isn't supported on that RHEL release.</span></span>
- <span data-ttu-id="382c5-114">Hem RHEL hem de .NET sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="382c5-114">When both a version of RHEL and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="382c5-115">RHEL</span><span class="sxs-lookup"><span data-stu-id="382c5-115">RHEL</span></span>                     | <span data-ttu-id="382c5-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="382c5-116">.NET Core 2.1</span></span> | <span data-ttu-id="382c5-117">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="382c5-117">.NET Core 3.1</span></span> | <span data-ttu-id="382c5-118">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="382c5-118">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="382c5-119">✔️ [8](#rhel-8-)</span><span class="sxs-lookup"><span data-stu-id="382c5-119">✔️ [8](#rhel-8-)</span></span>        | <span data-ttu-id="382c5-120">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="382c5-120">✔️ 2.1</span></span>        | <span data-ttu-id="382c5-121">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="382c5-121">✔️ 3.1</span></span>        | <span data-ttu-id="382c5-122">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="382c5-122">✔️ 5.0</span></span> |
| <span data-ttu-id="382c5-123">✔️ [7](#rhel-7--net-50)</span><span class="sxs-lookup"><span data-stu-id="382c5-123">✔️ [7](#rhel-7--net-50)</span></span> | <span data-ttu-id="382c5-124">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="382c5-124">✔️ 2.1</span></span>        | <span data-ttu-id="382c5-125">✔️ [3,1](#rhel-7--net-core-31)</span><span class="sxs-lookup"><span data-stu-id="382c5-125">✔️ [3.1](#rhel-7--net-core-31)</span></span>        | <span data-ttu-id="382c5-126">✔️ [5,0](#rhel-7--net-50)</span><span class="sxs-lookup"><span data-stu-id="382c5-126">✔️ [5.0](#rhel-7--net-50)</span></span> |

<span data-ttu-id="382c5-127">Aşağıdaki .NET sürümleri artık desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="382c5-127">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="382c5-128">Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:</span><span class="sxs-lookup"><span data-stu-id="382c5-128">The downloads for these still remain published:</span></span>

- <span data-ttu-id="382c5-129">3,0</span><span class="sxs-lookup"><span data-stu-id="382c5-129">3.0</span></span>
- <span data-ttu-id="382c5-130">2.2</span><span class="sxs-lookup"><span data-stu-id="382c5-130">2.2</span></span>
- <span data-ttu-id="382c5-131">2,0</span><span class="sxs-lookup"><span data-stu-id="382c5-131">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="382c5-132">Önizleme sürümlerini Kaldır</span><span class="sxs-lookup"><span data-stu-id="382c5-132">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="382c5-133">Diğer sürümleri nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="382c5-133">How to install other versions</span></span>

<span data-ttu-id="382c5-134">.Net 'in diğer sürümlerini yüklemek için gereken adımlarda [.net Için Red Hat belgelerine](https://access.redhat.com/documentation/net/5.0/) başvurun.</span><span class="sxs-lookup"><span data-stu-id="382c5-134">Consult the [Red Hat documentation for .NET](https://access.redhat.com/documentation/net/5.0/) on the steps required to install other releases of .NET.</span></span>

## <a name="rhel-8-"></a><span data-ttu-id="382c5-135">RHEL 8 ✔️</span><span class="sxs-lookup"><span data-stu-id="382c5-135">RHEL 8 ✔️</span></span>

> [!TIP]
> <span data-ttu-id="382c5-136">.NET 5,0 henüz AppStream depolarında kullanılamaz, ancak .NET Core 3,1 ' dir.</span><span class="sxs-lookup"><span data-stu-id="382c5-136">.NET 5.0 isn't yet available in the AppStream repositories, but .NET Core 3.1 is.</span></span> <span data-ttu-id="382c5-137">.NET Core 3,1 yüklemek için, veya gibi `dnf install` uygun Paketle komutunu kullanın `aspnetcore-runtime-3.1` `dotnet-sdk-3.1` .</span><span class="sxs-lookup"><span data-stu-id="382c5-137">To install .NET Core 3.1, use the `dnf install` command with the appropriate package, such as `aspnetcore-runtime-3.1` or `dotnet-sdk-3.1`.</span></span> <span data-ttu-id="382c5-138">Aşağıdaki yönergeler .NET 5,0 içindir.</span><span class="sxs-lookup"><span data-stu-id="382c5-138">The following instructions are for .NET 5.0.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/rhel/8/prod.repo
```

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="rhel-7--net-50"></a><span data-ttu-id="382c5-139">RHEL 7 ✔️ .NET 5,0</span><span class="sxs-lookup"><span data-stu-id="382c5-139">RHEL 7 ✔️ .NET 5.0</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/rhel/7/prod.repo
```

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-yum.md)]

## <a name="rhel-7--net-core-31"></a><span data-ttu-id="382c5-140">RHEL 7 ✔️ .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="382c5-140">RHEL 7 ✔️ .NET Core 3.1</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

<span data-ttu-id="382c5-141">Aşağıdaki komut `scl-utils` paketini yüklüyor:</span><span class="sxs-lookup"><span data-stu-id="382c5-141">The following command installs the `scl-utils` package:</span></span>

```bash
sudo yum install scl-utils
```

### <a name="install-the-sdk"></a><span data-ttu-id="382c5-142">SDK Yükleme</span><span class="sxs-lookup"><span data-stu-id="382c5-142">Install the SDK</span></span>

<span data-ttu-id="382c5-143">.NET Core SDK .NET Core ile uygulama geliştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="382c5-143">.NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="382c5-144">.NET Core SDK yüklerseniz, ilgili çalışma zamanını yüklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="382c5-144">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="382c5-145">.NET Core SDK yüklemek için aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="382c5-145">To install .NET Core SDK, run the following commands:</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

<span data-ttu-id="382c5-146">Red hat, `rh-dotnet31` diğer programları etkileyebileceğinden, kalıcı olarak etkinleştirilmesini önermez.</span><span class="sxs-lookup"><span data-stu-id="382c5-146">Red Hat does not recommend permanently enabling `rh-dotnet31` because it may affect other programs.</span></span> <span data-ttu-id="382c5-147">Örneğin, `rh-dotnet31` `libcurl` temel RHEL sürümünden farklı bir sürümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="382c5-147">For example, `rh-dotnet31` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="382c5-148">Bu, farklı bir sürümü beklemediği programlarda sorunlara yol açabilir `libcurl` .</span><span class="sxs-lookup"><span data-stu-id="382c5-148">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="382c5-149">`rh-dotnet`Kalıcı olarak etkinleştirmek istiyorsanız, _~/,bashrc_ dosyanıza şu satırı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="382c5-149">If you want to enable `rh-dotnet` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet31
```

### <a name="install-the-runtime"></a><span data-ttu-id="382c5-150">Çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="382c5-150">Install the runtime</span></span>

<span data-ttu-id="382c5-151">.NET Core çalışma zamanı, .NET Core ile oluşturulmuş uygulamaları çalışma zamanını içermeyen uygulamalar çalıştırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="382c5-151">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="382c5-152">Aşağıdaki komutlar, .NET Core için en uyumlu çalışma zamanı olan ASP.NET Core çalışma zamanını yükler.</span><span class="sxs-lookup"><span data-stu-id="382c5-152">The commands below install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="382c5-153">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="382c5-153">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31-aspnetcore-runtime-3.1 bash
```

<span data-ttu-id="382c5-154">Red hat, `rh-dotnet31-aspnetcore-runtime-3.1` diğer programları etkileyebileceğinden, kalıcı olarak etkinleştirilmesini önermez.</span><span class="sxs-lookup"><span data-stu-id="382c5-154">Red Hat does not recommend permanently enabling `rh-dotnet31-aspnetcore-runtime-3.1` because it may affect other programs.</span></span> <span data-ttu-id="382c5-155">Örneğin, `rh-dotnet31-aspnetcore-runtime-3.1` `libcurl` temel RHEL sürümünden farklı bir sürümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="382c5-155">For example, `rh-dotnet31-aspnetcore-runtime-3.1` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="382c5-156">Bu, farklı bir sürümü beklemediği programlarda sorunlara yol açabilir `libcurl` .</span><span class="sxs-lookup"><span data-stu-id="382c5-156">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="382c5-157">`rh-dotnet31-aspnetcore-runtime-3.1`Kalıcı olarak etkinleştirmek istiyorsanız, _~/,bashrc_ dosyanıza şu satırı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="382c5-157">If you want to enable `rh-dotnet31-aspnetcore-runtime-3.1` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet31-aspnetcore-runtime-3.1
```

<span data-ttu-id="382c5-158">ASP.NET Core çalışma zamanına alternatif olarak, ASP.NET Core desteği içermeyen .NET Core çalışma zamanı 'nı yükleyebilirsiniz: Yukarıdaki komutlarda ' yi ile değiştirin `rh-dotnet31-aspnetcore-runtime-3.1` `rh-dotnet31-dotnet-runtime-3.1` .</span><span class="sxs-lookup"><span data-stu-id="382c5-158">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `rh-dotnet31-aspnetcore-runtime-3.1` in the commands above with `rh-dotnet31-dotnet-runtime-3.1`.</span></span>

## <a name="snap"></a><span data-ttu-id="382c5-159">Bileşenlerinden</span><span class="sxs-lookup"><span data-stu-id="382c5-159">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="382c5-160">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="382c5-160">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="382c5-161">Komut dosyalı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="382c5-161">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="382c5-162">El ile yüklemesi</span><span class="sxs-lookup"><span data-stu-id="382c5-162">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="382c5-163">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="382c5-163">Next steps</span></span>

- [<span data-ttu-id="382c5-164">Öğretici: Visual Studio Code kullanarak .NET SDK ile bir konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="382c5-164">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
