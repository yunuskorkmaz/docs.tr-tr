---
title: RHEL-.NET Core 'a .NET Core 'u yükler
description: RHEL üzerinde .NET Core SDK ve .NET Core çalışma zamanı yüklemesinin çeşitli yollarını gösterir.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 4a406fe1834c16bab9a5548b69206b51270b33fa
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324718"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-rhel"></a><span data-ttu-id="1e3fe-103">RHEL üzerinde .NET Core SDK veya .NET Core çalışma zamanı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="1e3fe-103">Install .NET Core SDK or .NET Core Runtime on RHEL</span></span>

<span data-ttu-id="1e3fe-104">.NET Core, RHEL 'de desteklenir.</span><span class="sxs-lookup"><span data-stu-id="1e3fe-104">.NET Core is supported on RHEL.</span></span> <span data-ttu-id="1e3fe-105">Bu makalede, RHEL üzerinde .NET Core 'un nasıl yükleneceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="1e3fe-105">This article describes how to install .NET Core on RHEL.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="1e3fe-106">Red Hat aboneliğinizi kaydetme</span><span class="sxs-lookup"><span data-stu-id="1e3fe-106">Register your Red Hat subscription</span></span>

<span data-ttu-id="1e3fe-107">RHEL 'de Red Hat 'ten .NET Core yüklemek için, önce Red Hat abonelik Yöneticisi 'Ni kullanarak kaydolmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1e3fe-107">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="1e3fe-108">Bu, sisteminizde yapmadıysanız veya emin değilseniz, [.NET Core Için Red Hat ürün belgelerine](https://access.redhat.com/documentation/net_core/)bakın.</span><span class="sxs-lookup"><span data-stu-id="1e3fe-108">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="supported-distributions"></a><span data-ttu-id="1e3fe-109">Desteklenen dağıtımlar</span><span class="sxs-lookup"><span data-stu-id="1e3fe-109">Supported distributions</span></span>

<span data-ttu-id="1e3fe-110">Aşağıdaki tabloda, hem RHEL 7 hem de RHEL 8 üzerinde şu anda desteklenen .NET Core sürümlerinin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1e3fe-110">The following table is a list of currently supported .NET Core releases on both RHEL 7 and RHEL 8.</span></span> <span data-ttu-id="1e3fe-111">Bu sürümler, [.NET Core sürümü destek sonuna](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya RHEL sürümüne ulaşıncaya kadar desteklenmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="1e3fe-111">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of RHEL is no longer supported.</span></span>

- <span data-ttu-id="1e3fe-112">✔️, RHEL veya .NET Core sürümünün hala desteklendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1e3fe-112">A ✔️ indicates that the version of RHEL or .NET Core is still supported.</span></span>
- <span data-ttu-id="1e3fe-113">A ❌ , RHEL veya .NET Core sürümünün bu RHEL sürümünde desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1e3fe-113">A ❌ indicates that the version of RHEL or .NET Core isn't supported on that RHEL release.</span></span>
- <span data-ttu-id="1e3fe-114">Hem RHEL hem de bir .NET Core sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="1e3fe-114">When both a version of RHEL and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="1e3fe-115">RHEL</span><span class="sxs-lookup"><span data-stu-id="1e3fe-115">RHEL</span></span>                   | <span data-ttu-id="1e3fe-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="1e3fe-116">.NET Core 2.1</span></span> | <span data-ttu-id="1e3fe-117">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="1e3fe-117">.NET Core 3.1</span></span> | <span data-ttu-id="1e3fe-118">.NET 5 Preview (yalnızca el ile yüklenir)</span><span class="sxs-lookup"><span data-stu-id="1e3fe-118">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="1e3fe-119">✔️ [8](#rhel-8-)</span><span class="sxs-lookup"><span data-stu-id="1e3fe-119">✔️ [8](#rhel-8-)</span></span> | <span data-ttu-id="1e3fe-120">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="1e3fe-120">✔️ 2.1</span></span>        | <span data-ttu-id="1e3fe-121">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="1e3fe-121">✔️ 3.1</span></span>        | <span data-ttu-id="1e3fe-122">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="1e3fe-122">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="1e3fe-123">✔️ [7](#rhel-7-)</span><span class="sxs-lookup"><span data-stu-id="1e3fe-123">✔️ [7](#rhel-7-)</span></span> | <span data-ttu-id="1e3fe-124">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="1e3fe-124">✔️ 2.1</span></span>        | <span data-ttu-id="1e3fe-125">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="1e3fe-125">✔️ 3.1</span></span>        | <span data-ttu-id="1e3fe-126">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="1e3fe-126">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="1e3fe-127">Aşağıdaki .NET Core sürümleri artık desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="1e3fe-127">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="1e3fe-128">Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:</span><span class="sxs-lookup"><span data-stu-id="1e3fe-128">The downloads for these still remain published:</span></span>

- <span data-ttu-id="1e3fe-129">3.0</span><span class="sxs-lookup"><span data-stu-id="1e3fe-129">3.0</span></span>
- <span data-ttu-id="1e3fe-130">2,2</span><span class="sxs-lookup"><span data-stu-id="1e3fe-130">2.2</span></span>
- <span data-ttu-id="1e3fe-131">2.0</span><span class="sxs-lookup"><span data-stu-id="1e3fe-131">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="1e3fe-132">Diğer sürümleri nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="1e3fe-132">How to install other versions</span></span>

<span data-ttu-id="1e3fe-133">.NET Core 'un diğer sürümlerini yüklemek için gereken adımlarda [.NET Core Için Red Hat belgelerine](https://access.redhat.com/documentation/net_core/) bakın.</span><span class="sxs-lookup"><span data-stu-id="1e3fe-133">Consult the [Red Hat documentation for .NET Core](https://access.redhat.com/documentation/net_core/) on the steps required to install other releases of .NET Core.</span></span>

## <a name="rhel-8-"></a><span data-ttu-id="1e3fe-134">RHEL 8 ✔️</span><span class="sxs-lookup"><span data-stu-id="1e3fe-134">RHEL 8 ✔️</span></span>

<span data-ttu-id="1e3fe-135">.NET Core, RHEL 8 için AppStream depolarına dahildir.</span><span class="sxs-lookup"><span data-stu-id="1e3fe-135">.NET Core is included in the AppStream repositories for RHEL 8.</span></span>

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="rhel-7-"></a><span data-ttu-id="1e3fe-136">RHEL 7 ✔️</span><span class="sxs-lookup"><span data-stu-id="1e3fe-136">RHEL 7 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

<span data-ttu-id="1e3fe-137">Aşağıdaki komut `scl-utils` paketini yüklüyor:</span><span class="sxs-lookup"><span data-stu-id="1e3fe-137">The following command installs the `scl-utils` package:</span></span>

```bash
sudo yum install scl-utils
```

### <a name="install-the-sdk"></a><span data-ttu-id="1e3fe-138">SDK Yükleme</span><span class="sxs-lookup"><span data-stu-id="1e3fe-138">Install the SDK</span></span>

<span data-ttu-id="1e3fe-139">.NET Core SDK .NET Core ile uygulama geliştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="1e3fe-139">.NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="1e3fe-140">.NET Core SDK yüklerseniz, ilgili çalışma zamanını yüklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="1e3fe-140">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="1e3fe-141">.NET Core SDK yüklemek için aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="1e3fe-141">To install .NET Core SDK, run the following commands:</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

<span data-ttu-id="1e3fe-142">Red hat, `rh-dotnet31` diğer programları etkileyebileceğinden, kalıcı olarak etkinleştirilmesini önermez.</span><span class="sxs-lookup"><span data-stu-id="1e3fe-142">Red Hat does not recommend permanently enabling `rh-dotnet31` because it may affect other programs.</span></span> <span data-ttu-id="1e3fe-143">Örneğin, `rh-dotnet31` `libcurl` temel RHEL sürümünden farklı bir sürümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="1e3fe-143">For example, `rh-dotnet31` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="1e3fe-144">Bu, farklı bir sürümü beklemediği programlarda sorunlara yol açabilir `libcurl` .</span><span class="sxs-lookup"><span data-stu-id="1e3fe-144">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="1e3fe-145">`rh-dotnet`Kalıcı olarak etkinleştirmek istiyorsanız, _~/,bashrc_ dosyanıza şu satırı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1e3fe-145">If you want to enable `rh-dotnet` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet31
```

### <a name="install-the-runtime"></a><span data-ttu-id="1e3fe-146">Çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="1e3fe-146">Install the runtime</span></span>

<span data-ttu-id="1e3fe-147">.NET Core çalışma zamanı, .NET Core ile oluşturulmuş uygulamaları çalışma zamanını içermeyen uygulamalar çalıştırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="1e3fe-147">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="1e3fe-148">Aşağıdaki komutlar, .NET Core için en uyumlu çalışma zamanı olan ASP.NET Core çalışma zamanını yükler.</span><span class="sxs-lookup"><span data-stu-id="1e3fe-148">The commands below install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="1e3fe-149">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1e3fe-149">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31-aspnetcore-runtime-3.1 bash
```

<span data-ttu-id="1e3fe-150">Red hat, `rh-dotnet31-aspnetcore-runtime-3.1` diğer programları etkileyebileceğinden, kalıcı olarak etkinleştirilmesini önermez.</span><span class="sxs-lookup"><span data-stu-id="1e3fe-150">Red Hat does not recommend permanently enabling `rh-dotnet31-aspnetcore-runtime-3.1` because it may affect other programs.</span></span> <span data-ttu-id="1e3fe-151">Örneğin, `rh-dotnet31-aspnetcore-runtime-3.1` `libcurl` temel RHEL sürümünden farklı bir sürümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="1e3fe-151">For example, `rh-dotnet31-aspnetcore-runtime-3.1` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="1e3fe-152">Bu, farklı bir sürümü beklemediği programlarda sorunlara yol açabilir `libcurl` .</span><span class="sxs-lookup"><span data-stu-id="1e3fe-152">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="1e3fe-153">`rh-dotnet31-aspnetcore-runtime-3.1`Kalıcı olarak etkinleştirmek istiyorsanız, _~/,bashrc_ dosyanıza şu satırı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1e3fe-153">If you want to enable `rh-dotnet31-aspnetcore-runtime-3.1` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet31-aspnetcore-runtime-3.1
```

<span data-ttu-id="1e3fe-154">ASP.NET Core çalışma zamanına alternatif olarak, ASP.NET Core desteği içermeyen .NET Core çalışma zamanı 'nı yükleyebilirsiniz: Yukarıdaki komutlarda ' yi ile değiştirin `rh-dotnet31-aspnetcore-runtime-3.1` `rh-dotnet31-dotnet-runtime-3.1` .</span><span class="sxs-lookup"><span data-stu-id="1e3fe-154">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `rh-dotnet31-aspnetcore-runtime-3.1` in the commands above with `rh-dotnet31-dotnet-runtime-3.1`.</span></span>

## <a name="snap"></a><span data-ttu-id="1e3fe-155">Bileşenlerinden</span><span class="sxs-lookup"><span data-stu-id="1e3fe-155">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="1e3fe-156">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="1e3fe-156">Dependencies</span></span>

[!INCLUDE [linux-install-dependencies](includes/linux-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="1e3fe-157">Komut dosyalı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="1e3fe-157">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="1e3fe-158">El ile yüklemesi</span><span class="sxs-lookup"><span data-stu-id="1e3fe-158">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="1e3fe-159">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="1e3fe-159">Next steps</span></span>

- [<span data-ttu-id="1e3fe-160">Öğretici: Visual Studio Code kullanarak .NET Core SDK bir konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="1e3fe-160">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
