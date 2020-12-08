---
title: RHEL-.NET üzerinde .NET 'i yükler
description: RHEL üzerinde .NET SDK ve .NET çalışma zamanı yüklemek için çeşitli yollar gösterir.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 0b6138185bfd3e2f50c1b31e82779165715a5b6e
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851646"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-rhel"></a><span data-ttu-id="f7f89-103">RHEL üzerinde .NET SDK veya .NET çalışma zamanı 'nı yükler</span><span class="sxs-lookup"><span data-stu-id="f7f89-103">Install the .NET SDK or the .NET Runtime on RHEL</span></span>

<span data-ttu-id="f7f89-104">.NET, RHEL 'de desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f7f89-104">.NET is supported on RHEL.</span></span> <span data-ttu-id="f7f89-105">Bu makalede, RHEL 'de .NET 'in nasıl yükleneceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="f7f89-105">This article describes how to install .NET on RHEL.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="f7f89-106">Red Hat aboneliğinizi kaydetme</span><span class="sxs-lookup"><span data-stu-id="f7f89-106">Register your Red Hat subscription</span></span>

<span data-ttu-id="f7f89-107">RHEL 'de Red Hat 'ten .NET yüklemek için önce Red Hat abonelik Yöneticisi 'Ni kullanarak kaydolmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7f89-107">To install .NET from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="f7f89-108">Bu, sisteminizde yapmadıysanız veya emin değilseniz, [.net Için Red Hat ürün belgelerine](https://access.redhat.com/documentation/net/5.0/)bakın.</span><span class="sxs-lookup"><span data-stu-id="f7f89-108">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET](https://access.redhat.com/documentation/net/5.0/).</span></span>

## <a name="supported-distributions"></a><span data-ttu-id="f7f89-109">Desteklenen dağıtımlar</span><span class="sxs-lookup"><span data-stu-id="f7f89-109">Supported distributions</span></span>

<span data-ttu-id="f7f89-110">Aşağıdaki tabloda, hem RHEL 7 hem de RHEL 8 üzerinde şu anda desteklenen .NET sürümlerinin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f7f89-110">The following table is a list of currently supported .NET releases on both RHEL 7 and RHEL 8.</span></span> <span data-ttu-id="f7f89-111">Bu sürümler, [.NET sürümü destek sonu](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya RHEL sürümü artık desteklenene kadar desteklenmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="f7f89-111">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of RHEL is no longer supported.</span></span>

- <span data-ttu-id="f7f89-112">✔️, RHEL veya .NET sürümünün hala desteklendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f7f89-112">A ✔️ indicates that the version of RHEL or .NET is still supported.</span></span>
- <span data-ttu-id="f7f89-113">A ❌ , RHEL veya .NET sürümünün bu RHEL sürümünde desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f7f89-113">A ❌ indicates that the version of RHEL or .NET isn't supported on that RHEL release.</span></span>
- <span data-ttu-id="f7f89-114">Hem RHEL hem de .NET sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f7f89-114">When both a version of RHEL and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="f7f89-115">RHEL</span><span class="sxs-lookup"><span data-stu-id="f7f89-115">RHEL</span></span>                     | <span data-ttu-id="f7f89-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="f7f89-116">.NET Core 2.1</span></span> | <span data-ttu-id="f7f89-117">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="f7f89-117">.NET Core 3.1</span></span> | <span data-ttu-id="f7f89-118">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="f7f89-118">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="f7f89-119">✔️ [8](#rhel-8-)</span><span class="sxs-lookup"><span data-stu-id="f7f89-119">✔️ [8](#rhel-8-)</span></span>        | <span data-ttu-id="f7f89-120">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="f7f89-120">✔️ 2.1</span></span>        | <span data-ttu-id="f7f89-121">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="f7f89-121">✔️ 3.1</span></span>        | <span data-ttu-id="f7f89-122">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="f7f89-122">✔️ 5.0</span></span> |
| <span data-ttu-id="f7f89-123">✔️ [7](#rhel-7--net-50)</span><span class="sxs-lookup"><span data-stu-id="f7f89-123">✔️ [7](#rhel-7--net-50)</span></span> | <span data-ttu-id="f7f89-124">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="f7f89-124">✔️ 2.1</span></span>        | <span data-ttu-id="f7f89-125">✔️ [3,1](#rhel-7--net-core-31)</span><span class="sxs-lookup"><span data-stu-id="f7f89-125">✔️ [3.1](#rhel-7--net-core-31)</span></span>        | <span data-ttu-id="f7f89-126">✔️ [5,0](#rhel-7--net-50)</span><span class="sxs-lookup"><span data-stu-id="f7f89-126">✔️ [5.0](#rhel-7--net-50)</span></span> |

<span data-ttu-id="f7f89-127">Aşağıdaki .NET sürümleri artık desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="f7f89-127">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="f7f89-128">Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:</span><span class="sxs-lookup"><span data-stu-id="f7f89-128">The downloads for these still remain published:</span></span>

- <span data-ttu-id="f7f89-129">3,0</span><span class="sxs-lookup"><span data-stu-id="f7f89-129">3.0</span></span>
- <span data-ttu-id="f7f89-130">2.2</span><span class="sxs-lookup"><span data-stu-id="f7f89-130">2.2</span></span>
- <span data-ttu-id="f7f89-131">2,0</span><span class="sxs-lookup"><span data-stu-id="f7f89-131">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="f7f89-132">Önizleme sürümlerini Kaldır</span><span class="sxs-lookup"><span data-stu-id="f7f89-132">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="f7f89-133">Diğer sürümleri nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="f7f89-133">How to install other versions</span></span>

<span data-ttu-id="f7f89-134">.Net 'in diğer sürümlerini yüklemek için gereken adımlarda [.net Için Red Hat belgelerine](https://access.redhat.com/documentation/net/5.0/) başvurun.</span><span class="sxs-lookup"><span data-stu-id="f7f89-134">Consult the [Red Hat documentation for .NET](https://access.redhat.com/documentation/net/5.0/) on the steps required to install other releases of .NET.</span></span>

## <a name="rhel-8-"></a><span data-ttu-id="f7f89-135">RHEL 8 ✔️</span><span class="sxs-lookup"><span data-stu-id="f7f89-135">RHEL 8 ✔️</span></span>

<span data-ttu-id="f7f89-136">.NET, RHEL 8 için AppStream depolarına dahildir.</span><span class="sxs-lookup"><span data-stu-id="f7f89-136">.NET is included in the AppStream repositories for RHEL 8.</span></span>

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="rhel-7--net-50"></a><span data-ttu-id="f7f89-137">RHEL 7 ✔️ .NET 5,0</span><span class="sxs-lookup"><span data-stu-id="f7f89-137">RHEL 7 ✔️ .NET 5.0</span></span>

<span data-ttu-id="f7f89-138">Aşağıdaki komut `scl-utils` paketini yüklüyor:</span><span class="sxs-lookup"><span data-stu-id="f7f89-138">The following command installs the `scl-utils` package:</span></span>

```bash
sudo yum install scl-utils
```

### <a name="install-the-sdk"></a><span data-ttu-id="f7f89-139">SDK Yükleme</span><span class="sxs-lookup"><span data-stu-id="f7f89-139">Install the SDK</span></span>

<span data-ttu-id="f7f89-140">.NET SDK, .NET ile uygulama geliştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="f7f89-140">The .NET SDK allows you to develop apps with .NET .</span></span> <span data-ttu-id="f7f89-141">.NET SDK 'yı yüklerseniz, ilgili çalışma zamanını yüklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f7f89-141">If you install the .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="f7f89-142">.NET SDK 'yı yüklemek için aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="f7f89-142">To install .NET SDK, run the following commands:</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet50 -y
scl enable rh-dotnet50 bash
```

<span data-ttu-id="f7f89-143">Red hat, `rh-dotnet50` diğer programları etkileyebileceğinden, kalıcı olarak etkinleştirilmesini önermez.</span><span class="sxs-lookup"><span data-stu-id="f7f89-143">Red Hat does not recommend permanently enabling `rh-dotnet50` because it may affect other programs.</span></span> <span data-ttu-id="f7f89-144">`rh-dotnet`Kalıcı olarak etkinleştirmek istiyorsanız, _~/,bashrc_ dosyanıza şu satırı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f7f89-144">If you want to enable `rh-dotnet` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet50
```

### <a name="install-the-runtime"></a><span data-ttu-id="f7f89-145">Çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="f7f89-145">Install the runtime</span></span>

<span data-ttu-id="f7f89-146">.NET çalışma zamanı, .NET ile yapılan ve çalışma zamanını içermeyen uygulamaları çalıştırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f7f89-146">The .NET Runtime allows you to run apps that were made with .NET that didn't include the runtime.</span></span> <span data-ttu-id="f7f89-147">Aşağıdaki komutlar, .NET Core için en uyumlu çalışma zamanı olan ASP.NET Core çalışma zamanını yükler.</span><span class="sxs-lookup"><span data-stu-id="f7f89-147">The commands below install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="f7f89-148">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f7f89-148">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet50-aspnetcore-runtime-5.0 -y
scl enable rh-dotnet50 bash
```

<span data-ttu-id="f7f89-149">Red hat, `rh-dotnet50` diğer programları etkileyebileceğinden, kalıcı olarak etkinleştirilmesini önermez.</span><span class="sxs-lookup"><span data-stu-id="f7f89-149">Red Hat does not recommend permanently enabling `rh-dotnet50` because it may affect other programs.</span></span> <span data-ttu-id="f7f89-150">`rh-dotnet50`Kalıcı olarak etkinleştirmek istiyorsanız, _~/,bashrc_ dosyanıza şu satırı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f7f89-150">If you want to enable `rh-dotnet50` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet50
```

<span data-ttu-id="f7f89-151">ASP.NET Core çalışma zamanına alternatif olarak, ASP.NET Core desteği içermeyen .NET çalışma zamanını yükleyebilirsiniz: Yukarıdaki komutlarda ' ı değiştirin `rh-dotnet50-aspnetcore-runtime-5.0` `rh-dotnet50-dotnet-runtime-5.0` .</span><span class="sxs-lookup"><span data-stu-id="f7f89-151">As an alternative to the ASP.NET Core Runtime, you can install the .NET Runtime that doesn't include ASP.NET Core support: replace `rh-dotnet50-aspnetcore-runtime-5.0` in the commands above with `rh-dotnet50-dotnet-runtime-5.0`.</span></span>

## <a name="rhel-7--net-core-31"></a><span data-ttu-id="f7f89-152">RHEL 7 ✔️ .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="f7f89-152">RHEL 7 ✔️ .NET Core 3.1</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

<span data-ttu-id="f7f89-153">Aşağıdaki komut `scl-utils` paketini yüklüyor:</span><span class="sxs-lookup"><span data-stu-id="f7f89-153">The following command installs the `scl-utils` package:</span></span>

```bash
sudo yum install scl-utils
```

### <a name="install-the-sdk"></a><span data-ttu-id="f7f89-154">SDK Yükleme</span><span class="sxs-lookup"><span data-stu-id="f7f89-154">Install the SDK</span></span>

<span data-ttu-id="f7f89-155">.NET Core SDK .NET Core ile uygulama geliştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="f7f89-155">.NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="f7f89-156">.NET Core SDK yüklerseniz, ilgili çalışma zamanını yüklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f7f89-156">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="f7f89-157">.NET Core SDK yüklemek için aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="f7f89-157">To install .NET Core SDK, run the following commands:</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

<span data-ttu-id="f7f89-158">Red hat, `rh-dotnet31` diğer programları etkileyebileceğinden, kalıcı olarak etkinleştirilmesini önermez.</span><span class="sxs-lookup"><span data-stu-id="f7f89-158">Red Hat does not recommend permanently enabling `rh-dotnet31` because it may affect other programs.</span></span> <span data-ttu-id="f7f89-159">Örneğin, `rh-dotnet31` `libcurl` temel RHEL sürümünden farklı bir sürümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="f7f89-159">For example, `rh-dotnet31` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="f7f89-160">Bu, farklı bir sürümü beklemediği programlarda sorunlara yol açabilir `libcurl` .</span><span class="sxs-lookup"><span data-stu-id="f7f89-160">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="f7f89-161">`rh-dotnet`Kalıcı olarak etkinleştirmek istiyorsanız, _~/,bashrc_ dosyanıza şu satırı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f7f89-161">If you want to enable `rh-dotnet` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet31
```

### <a name="install-the-runtime"></a><span data-ttu-id="f7f89-162">Çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="f7f89-162">Install the runtime</span></span>

<span data-ttu-id="f7f89-163">.NET Core çalışma zamanı, .NET Core ile oluşturulmuş uygulamaları çalışma zamanını içermeyen uygulamalar çalıştırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="f7f89-163">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="f7f89-164">Aşağıdaki komutlar, .NET Core için en uyumlu çalışma zamanı olan ASP.NET Core çalışma zamanını yükler.</span><span class="sxs-lookup"><span data-stu-id="f7f89-164">The commands below install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="f7f89-165">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f7f89-165">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

<span data-ttu-id="f7f89-166">Red hat, `rh-dotnet31` diğer programları etkileyebileceğinden, kalıcı olarak etkinleştirilmesini önermez.</span><span class="sxs-lookup"><span data-stu-id="f7f89-166">Red Hat does not recommend permanently enabling `rh-dotnet31` because it may affect other programs.</span></span> <span data-ttu-id="f7f89-167">Örneğin, `rh-dotnet31` `libcurl` temel RHEL sürümünden farklı bir sürümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="f7f89-167">For example, `rh-dotnet31` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="f7f89-168">Bu, farklı bir sürümü beklemediği programlarda sorunlara yol açabilir `libcurl` .</span><span class="sxs-lookup"><span data-stu-id="f7f89-168">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="f7f89-169">`rh-dotnet31`Kalıcı olarak etkinleştirmek istiyorsanız, _~/,bashrc_ dosyanıza şu satırı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f7f89-169">If you want to enable `rh-dotnet31` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet31
```

<span data-ttu-id="f7f89-170">ASP.NET Core çalışma zamanına alternatif olarak, ASP.NET Core desteği içermeyen .NET Core çalışma zamanı 'nı yükleyebilirsiniz: Yukarıdaki komutlarda ' yi ile değiştirin `rh-dotnet31-aspnetcore-runtime-3.1` `rh-dotnet31-dotnet-runtime-3.1` .</span><span class="sxs-lookup"><span data-stu-id="f7f89-170">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `rh-dotnet31-aspnetcore-runtime-3.1` in the commands above with `rh-dotnet31-dotnet-runtime-3.1`.</span></span>

## <a name="snap"></a><span data-ttu-id="f7f89-171">Bileşenlerinden</span><span class="sxs-lookup"><span data-stu-id="f7f89-171">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="f7f89-172">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="f7f89-172">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="f7f89-173">Komut dosyalı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="f7f89-173">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="f7f89-174">El ile yüklemesi</span><span class="sxs-lookup"><span data-stu-id="f7f89-174">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="f7f89-175">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="f7f89-175">Next steps</span></span>

- [<span data-ttu-id="f7f89-176">Öğretici: Visual Studio Code kullanarak .NET SDK ile bir konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="f7f89-176">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
