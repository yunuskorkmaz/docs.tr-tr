---
title: RHEL-.NET üzerinde .NET 'i yükler
description: RHEL üzerinde .NET SDK ve .NET çalışma zamanı yüklemek için çeşitli yollar gösterir.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: a742497bba3459a4d8772f5c9e3d915b5b18e62e
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506933"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-rhel"></a><span data-ttu-id="fde3a-103">RHEL üzerinde .NET SDK veya .NET çalışma zamanı 'nı yükler</span><span class="sxs-lookup"><span data-stu-id="fde3a-103">Install the .NET SDK or the .NET Runtime on RHEL</span></span>

<span data-ttu-id="fde3a-104">.NET, RHEL 'de desteklenir.</span><span class="sxs-lookup"><span data-stu-id="fde3a-104">.NET is supported on RHEL.</span></span> <span data-ttu-id="fde3a-105">Bu makalede, RHEL 'de .NET 'in nasıl yükleneceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="fde3a-105">This article describes how to install .NET on RHEL.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="fde3a-106">Red Hat aboneliğinizi kaydetme</span><span class="sxs-lookup"><span data-stu-id="fde3a-106">Register your Red Hat subscription</span></span>

<span data-ttu-id="fde3a-107">RHEL 'de Red Hat 'ten .NET yüklemek için önce Red Hat abonelik Yöneticisi 'Ni kullanarak kaydolmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fde3a-107">To install .NET from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="fde3a-108">Bu, sisteminizde yapmadıysanız veya emin değilseniz, [.net Için Red Hat ürün belgelerine](https://access.redhat.com/documentation/net/5.0/)bakın.</span><span class="sxs-lookup"><span data-stu-id="fde3a-108">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET](https://access.redhat.com/documentation/net/5.0/).</span></span>

## <a name="supported-distributions"></a><span data-ttu-id="fde3a-109">Desteklenen dağıtımlar</span><span class="sxs-lookup"><span data-stu-id="fde3a-109">Supported distributions</span></span>

<span data-ttu-id="fde3a-110">Aşağıdaki tabloda, hem RHEL 7 hem de RHEL 8 üzerinde şu anda desteklenen .NET sürümlerinin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fde3a-110">The following table is a list of currently supported .NET releases on both RHEL 7 and RHEL 8.</span></span> <span data-ttu-id="fde3a-111">Bu sürümler, [.NET sürümü destek sonu](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya RHEL sürümü artık desteklenene kadar desteklenmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="fde3a-111">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of RHEL is no longer supported.</span></span>

- <span data-ttu-id="fde3a-112">✔️, RHEL veya .NET sürümünün hala desteklendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fde3a-112">A ✔️ indicates that the version of RHEL or .NET is still supported.</span></span>
- <span data-ttu-id="fde3a-113">A ❌ , RHEL veya .NET sürümünün bu RHEL sürümünde desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fde3a-113">A ❌ indicates that the version of RHEL or .NET isn't supported on that RHEL release.</span></span>
- <span data-ttu-id="fde3a-114">Hem RHEL hem de .NET sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="fde3a-114">When both a version of RHEL and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="fde3a-115">RHEL</span><span class="sxs-lookup"><span data-stu-id="fde3a-115">RHEL</span></span>                   | <span data-ttu-id="fde3a-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="fde3a-116">.NET Core 2.1</span></span> | <span data-ttu-id="fde3a-117">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="fde3a-117">.NET Core 3.1</span></span> | <span data-ttu-id="fde3a-118">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="fde3a-118">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="fde3a-119">✔️ [8](#rhel-8-)</span><span class="sxs-lookup"><span data-stu-id="fde3a-119">✔️ [8](#rhel-8-)</span></span> | <span data-ttu-id="fde3a-120">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="fde3a-120">✔️ 2.1</span></span>        | <span data-ttu-id="fde3a-121">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="fde3a-121">✔️ 3.1</span></span>        | <span data-ttu-id="fde3a-122">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="fde3a-122">✔️ 5.0</span></span> |
| <span data-ttu-id="fde3a-123">✔️ [7](#rhel-7-)</span><span class="sxs-lookup"><span data-stu-id="fde3a-123">✔️ [7](#rhel-7-)</span></span> | <span data-ttu-id="fde3a-124">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="fde3a-124">✔️ 2.1</span></span>        | <span data-ttu-id="fde3a-125">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="fde3a-125">✔️ 3.1</span></span>        | <span data-ttu-id="fde3a-126">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="fde3a-126">✔️ 5.0</span></span> |

<span data-ttu-id="fde3a-127">Aşağıdaki .NET sürümleri artık desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="fde3a-127">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="fde3a-128">Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:</span><span class="sxs-lookup"><span data-stu-id="fde3a-128">The downloads for these still remain published:</span></span>

- <span data-ttu-id="fde3a-129">3,0</span><span class="sxs-lookup"><span data-stu-id="fde3a-129">3.0</span></span>
- <span data-ttu-id="fde3a-130">2.2</span><span class="sxs-lookup"><span data-stu-id="fde3a-130">2.2</span></span>
- <span data-ttu-id="fde3a-131">2,0</span><span class="sxs-lookup"><span data-stu-id="fde3a-131">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="fde3a-132">Diğer sürümleri nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="fde3a-132">How to install other versions</span></span>

<span data-ttu-id="fde3a-133">.Net 'in diğer sürümlerini yüklemek için gereken adımlarda [.net Için Red Hat belgelerine](https://access.redhat.com/documentation/net/5.0/) başvurun.</span><span class="sxs-lookup"><span data-stu-id="fde3a-133">Consult the [Red Hat documentation for .NET](https://access.redhat.com/documentation/net/5.0/) on the steps required to install other releases of .NET.</span></span>

## <a name="rhel-8-"></a><span data-ttu-id="fde3a-134">RHEL 8 ✔️</span><span class="sxs-lookup"><span data-stu-id="fde3a-134">RHEL 8 ✔️</span></span>

<span data-ttu-id="fde3a-135">.NET, RHEL 8 için AppStream depolarına dahildir.</span><span class="sxs-lookup"><span data-stu-id="fde3a-135">.NET is included in the AppStream repositories for RHEL 8.</span></span>

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="rhel-7-"></a><span data-ttu-id="fde3a-136">RHEL 7 ✔️</span><span class="sxs-lookup"><span data-stu-id="fde3a-136">RHEL 7 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

<span data-ttu-id="fde3a-137">Aşağıdaki komut `scl-utils` paketini yüklüyor:</span><span class="sxs-lookup"><span data-stu-id="fde3a-137">The following command installs the `scl-utils` package:</span></span>

```bash
sudo yum install scl-utils
```

### <a name="install-the-sdk"></a><span data-ttu-id="fde3a-138">SDK Yükleme</span><span class="sxs-lookup"><span data-stu-id="fde3a-138">Install the SDK</span></span>

<span data-ttu-id="fde3a-139">.NET SDK, .NET ile uygulama geliştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="fde3a-139">The .NET SDK allows you to develop apps with .NET.</span></span> <span data-ttu-id="fde3a-140">.NET SDK 'yı yüklerseniz, ilgili çalışma zamanını yüklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="fde3a-140">If you install the .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="fde3a-141">.NET SDK 'yı yüklemek için aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="fde3a-141">To install the .NET SDK, run the following commands:</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet50 -y
scl enable rh-dotnet50 bash
```

<span data-ttu-id="fde3a-142">Red hat, `rh-dotnet50` diğer programları etkileyebileceğinden, kalıcı olarak etkinleştirilmesini önermez.</span><span class="sxs-lookup"><span data-stu-id="fde3a-142">Red Hat does not recommend permanently enabling `rh-dotnet50` because it may affect other programs.</span></span> <span data-ttu-id="fde3a-143">Örneğin, `rh-dotnet50` `libcurl` temel RHEL sürümünden farklı bir sürümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="fde3a-143">For example, `rh-dotnet50` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="fde3a-144">Bu, farklı bir sürümü beklemediği programlarda sorunlara yol açabilir `libcurl` .</span><span class="sxs-lookup"><span data-stu-id="fde3a-144">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="fde3a-145">`rh-dotnet`Kalıcı olarak etkinleştirmek istiyorsanız, _~/,bashrc_ dosyanıza şu satırı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fde3a-145">If you want to enable `rh-dotnet` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet50
```

### <a name="install-the-runtime"></a><span data-ttu-id="fde3a-146">Çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="fde3a-146">Install the runtime</span></span>

<span data-ttu-id="fde3a-147">ASP.NET Core çalışma zamanı, .NET ile yapılan ve çalışma zamanı sağlamayan uygulamaları çalıştırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="fde3a-147">The ASP.NET Core Runtime allows you to run apps that were made with .NET that didn't provide the runtime.</span></span> <span data-ttu-id="fde3a-148">Aşağıdaki komutlar, .NET için en uyumlu çalışma zamanı olan ASP.NET Core çalışma zamanını yükler.</span><span class="sxs-lookup"><span data-stu-id="fde3a-148">The following commands install the ASP.NET Core Runtime, which is the most compatible runtime for .NET.</span></span> <span data-ttu-id="fde3a-149">Terminalinizde aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="fde3a-149">In your terminal, run the following commands:</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet50-aspnetcore-runtime-5.0 -y
scl enable rh-dotnet50-aspnetcore-runtime-5.0 bash
```

<span data-ttu-id="fde3a-150">Red hat `rh-dotnet50-aspnetcore-runtime-5.0` , diğer programları etkileyebilecek şekilde kalıcı olarak etkinleştirilmesini önermez.</span><span class="sxs-lookup"><span data-stu-id="fde3a-150">Red Hat doesn't recommend permanently enabling `rh-dotnet50-aspnetcore-runtime-5.0` because it may affect other programs.</span></span> <span data-ttu-id="fde3a-151">Örneğin, `rh-dotnet50-aspnetcore-runtime-5.0` `libcurl` temel RHEL sürümünden farklı bir sürümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="fde3a-151">For example, `rh-dotnet50-aspnetcore-runtime-5.0` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="fde3a-152">Bu, farklı bir sürümü beklemediği programlarda sorunlara yol açabilir `libcurl` .</span><span class="sxs-lookup"><span data-stu-id="fde3a-152">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="fde3a-153">`rh-dotnet50-aspnetcore-runtime-5.0`Kalıcı olarak etkinleştirmek istiyorsanız, _~/,bashrc_ dosyanıza şu satırı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fde3a-153">If you want to enable `rh-dotnet50-aspnetcore-runtime-5.0` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet50-aspnetcore-runtime-5.0
```

<span data-ttu-id="fde3a-154">ASP.NET Core çalışma zamanına alternatif olarak, ASP.NET Core desteği içermeyen .NET çalışma zamanını yükleyebilirsiniz: `rh-dotnet50-aspnetcore-runtime-5.0` ile önceki komutlarda değiştirin `rh-dotnet50-dotnet-runtime-5.0` .</span><span class="sxs-lookup"><span data-stu-id="fde3a-154">As an alternative to the ASP.NET Core Runtime, you can install the .NET Runtime, which doesn't include ASP.NET Core support: replace `rh-dotnet50-aspnetcore-runtime-5.0` in the previous commands with `rh-dotnet50-dotnet-runtime-5.0`.</span></span>

## <a name="snap"></a><span data-ttu-id="fde3a-155">Bileşenlerinden</span><span class="sxs-lookup"><span data-stu-id="fde3a-155">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="fde3a-156">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="fde3a-156">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="fde3a-157">Komut dosyalı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="fde3a-157">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="fde3a-158">El ile yüklemesi</span><span class="sxs-lookup"><span data-stu-id="fde3a-158">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="fde3a-159">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="fde3a-159">Next steps</span></span>

- [<span data-ttu-id="fde3a-160">Öğretici: Visual Studio Code kullanarak .NET SDK ile bir konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="fde3a-160">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
