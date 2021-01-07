---
title: RHEL-.NET üzerinde .NET 'i yükler
description: RHEL üzerinde .NET SDK ve .NET çalışma zamanı yüklemek için çeşitli yollar gösterir.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: d585017919507a8fdcbb24778a0ff3ab3d9049c2
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970804"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-rhel"></a><span data-ttu-id="3cebb-103">RHEL üzerinde .NET SDK veya .NET çalışma zamanı 'nı yükler</span><span class="sxs-lookup"><span data-stu-id="3cebb-103">Install the .NET SDK or the .NET Runtime on RHEL</span></span>

<span data-ttu-id="3cebb-104">.NET, RHEL 'de desteklenir.</span><span class="sxs-lookup"><span data-stu-id="3cebb-104">.NET is supported on RHEL.</span></span> <span data-ttu-id="3cebb-105">Bu makalede, RHEL 'de .NET 'in nasıl yükleneceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="3cebb-105">This article describes how to install .NET on RHEL.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="3cebb-106">Red Hat aboneliğinizi kaydetme</span><span class="sxs-lookup"><span data-stu-id="3cebb-106">Register your Red Hat subscription</span></span>

<span data-ttu-id="3cebb-107">RHEL 'de Red Hat 'ten .NET yüklemek için önce Red Hat abonelik Yöneticisi 'Ni kullanarak kaydolmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3cebb-107">To install .NET from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="3cebb-108">Bu, sisteminizde yapmadıysanız veya emin değilseniz, [.net Için Red Hat ürün belgelerine](https://access.redhat.com/documentation/net/5.0/)bakın.</span><span class="sxs-lookup"><span data-stu-id="3cebb-108">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET](https://access.redhat.com/documentation/net/5.0/).</span></span>

## <a name="supported-distributions"></a><span data-ttu-id="3cebb-109">Desteklenen dağıtımlar</span><span class="sxs-lookup"><span data-stu-id="3cebb-109">Supported distributions</span></span>

<span data-ttu-id="3cebb-110">Aşağıdaki tabloda, hem RHEL 7 hem de RHEL 8 üzerinde şu anda desteklenen .NET sürümlerinin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3cebb-110">The following table is a list of currently supported .NET releases on both RHEL 7 and RHEL 8.</span></span> <span data-ttu-id="3cebb-111">Bu sürümler, [.NET sürümü destek sonu](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya RHEL sürümü artık desteklenene kadar desteklenmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="3cebb-111">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of RHEL is no longer supported.</span></span>

- <span data-ttu-id="3cebb-112">✔️, RHEL veya .NET sürümünün hala desteklendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3cebb-112">A ✔️ indicates that the version of RHEL or .NET is still supported.</span></span>
- <span data-ttu-id="3cebb-113">A ❌ , RHEL veya .NET sürümünün bu RHEL sürümünde desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3cebb-113">A ❌ indicates that the version of RHEL or .NET isn't supported on that RHEL release.</span></span>
- <span data-ttu-id="3cebb-114">Hem RHEL hem de .NET sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="3cebb-114">When both a version of RHEL and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="3cebb-115">RHEL</span><span class="sxs-lookup"><span data-stu-id="3cebb-115">RHEL</span></span>                     | <span data-ttu-id="3cebb-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="3cebb-116">.NET Core 2.1</span></span> | <span data-ttu-id="3cebb-117">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="3cebb-117">.NET Core 3.1</span></span> | <span data-ttu-id="3cebb-118">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="3cebb-118">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="3cebb-119">✔️ [8](#rhel-8-)</span><span class="sxs-lookup"><span data-stu-id="3cebb-119">✔️ [8](#rhel-8-)</span></span>        | <span data-ttu-id="3cebb-120">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="3cebb-120">✔️ 2.1</span></span>        | <span data-ttu-id="3cebb-121">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="3cebb-121">✔️ 3.1</span></span>        | <span data-ttu-id="3cebb-122">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="3cebb-122">✔️ 5.0</span></span> |
| <span data-ttu-id="3cebb-123">✔️ [7](#rhel-7--net-50)</span><span class="sxs-lookup"><span data-stu-id="3cebb-123">✔️ [7](#rhel-7--net-50)</span></span> | <span data-ttu-id="3cebb-124">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="3cebb-124">✔️ 2.1</span></span>        | <span data-ttu-id="3cebb-125">✔️ [3,1](#rhel-7--net-core-31)</span><span class="sxs-lookup"><span data-stu-id="3cebb-125">✔️ [3.1](#rhel-7--net-core-31)</span></span>        | <span data-ttu-id="3cebb-126">✔️ [5,0](#rhel-7--net-50)</span><span class="sxs-lookup"><span data-stu-id="3cebb-126">✔️ [5.0](#rhel-7--net-50)</span></span> |

<span data-ttu-id="3cebb-127">Aşağıdaki .NET sürümleri artık desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="3cebb-127">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="3cebb-128">Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:</span><span class="sxs-lookup"><span data-stu-id="3cebb-128">The downloads for these still remain published:</span></span>

- <span data-ttu-id="3cebb-129">3,0</span><span class="sxs-lookup"><span data-stu-id="3cebb-129">3.0</span></span>
- <span data-ttu-id="3cebb-130">2.2</span><span class="sxs-lookup"><span data-stu-id="3cebb-130">2.2</span></span>
- <span data-ttu-id="3cebb-131">2.0</span><span class="sxs-lookup"><span data-stu-id="3cebb-131">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="3cebb-132">Önizleme sürümlerini Kaldır</span><span class="sxs-lookup"><span data-stu-id="3cebb-132">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="rhel-8-"></a><span data-ttu-id="3cebb-133">RHEL 8 ✔️</span><span class="sxs-lookup"><span data-stu-id="3cebb-133">RHEL 8 ✔️</span></span>

<span data-ttu-id="3cebb-134">.NET, RHEL 8 için AppStream depolarına dahildir.</span><span class="sxs-lookup"><span data-stu-id="3cebb-134">.NET is included in the AppStream repositories for RHEL 8.</span></span>

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="rhel-7--net-50"></a><span data-ttu-id="3cebb-135">RHEL 7 ✔️ .NET 5,0</span><span class="sxs-lookup"><span data-stu-id="3cebb-135">RHEL 7 ✔️ .NET 5.0</span></span>

<span data-ttu-id="3cebb-136">Aşağıdaki komut `scl-utils` paketini yüklüyor:</span><span class="sxs-lookup"><span data-stu-id="3cebb-136">The following command installs the `scl-utils` package:</span></span>

```bash
sudo yum install scl-utils
```

### <a name="install-the-sdk"></a><span data-ttu-id="3cebb-137">SDK Yükleme</span><span class="sxs-lookup"><span data-stu-id="3cebb-137">Install the SDK</span></span>

<span data-ttu-id="3cebb-138">.NET SDK, .NET ile uygulama geliştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3cebb-138">The .NET SDK allows you to develop apps with .NET .</span></span> <span data-ttu-id="3cebb-139">.NET SDK 'yı yüklerseniz, ilgili çalışma zamanını yüklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="3cebb-139">If you install the .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="3cebb-140">.NET SDK 'yı yüklemek için aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="3cebb-140">To install .NET SDK, run the following commands:</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet50 -y
scl enable rh-dotnet50 bash
```

<span data-ttu-id="3cebb-141">Red hat, `rh-dotnet50` diğer programları etkileyebileceğinden, kalıcı olarak etkinleştirilmesini önermez.</span><span class="sxs-lookup"><span data-stu-id="3cebb-141">Red Hat does not recommend permanently enabling `rh-dotnet50` because it may affect other programs.</span></span> <span data-ttu-id="3cebb-142">`rh-dotnet`Kalıcı olarak etkinleştirmek istiyorsanız, _~/,bashrc_ dosyanıza şu satırı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3cebb-142">If you want to enable `rh-dotnet` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet50
```

### <a name="install-the-runtime"></a><span data-ttu-id="3cebb-143">Çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="3cebb-143">Install the runtime</span></span>

<span data-ttu-id="3cebb-144">.NET çalışma zamanı, .NET ile yapılan ve çalışma zamanını içermeyen uygulamaları çalıştırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="3cebb-144">The .NET Runtime allows you to run apps that were made with .NET that didn't include the runtime.</span></span> <span data-ttu-id="3cebb-145">Aşağıdaki komutlar, .NET Core için en uyumlu çalışma zamanı olan ASP.NET Core çalışma zamanını yükler.</span><span class="sxs-lookup"><span data-stu-id="3cebb-145">The commands below install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="3cebb-146">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3cebb-146">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet50-aspnetcore-runtime-5.0 -y
scl enable rh-dotnet50 bash
```

<span data-ttu-id="3cebb-147">Red hat, `rh-dotnet50` diğer programları etkileyebileceğinden, kalıcı olarak etkinleştirilmesini önermez.</span><span class="sxs-lookup"><span data-stu-id="3cebb-147">Red Hat does not recommend permanently enabling `rh-dotnet50` because it may affect other programs.</span></span> <span data-ttu-id="3cebb-148">`rh-dotnet50`Kalıcı olarak etkinleştirmek istiyorsanız, _~/,bashrc_ dosyanıza şu satırı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3cebb-148">If you want to enable `rh-dotnet50` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet50
```

<span data-ttu-id="3cebb-149">ASP.NET Core çalışma zamanına alternatif olarak, ASP.NET Core desteği içermeyen .NET çalışma zamanını yükleyebilirsiniz: Yukarıdaki komutlarda ' ı değiştirin `rh-dotnet50-aspnetcore-runtime-5.0` `rh-dotnet50-dotnet-runtime-5.0` .</span><span class="sxs-lookup"><span data-stu-id="3cebb-149">As an alternative to the ASP.NET Core Runtime, you can install the .NET Runtime that doesn't include ASP.NET Core support: replace `rh-dotnet50-aspnetcore-runtime-5.0` in the commands above with `rh-dotnet50-dotnet-runtime-5.0`.</span></span>

## <a name="rhel-7--net-core-31"></a><span data-ttu-id="3cebb-150">RHEL 7 ✔️ .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="3cebb-150">RHEL 7 ✔️ .NET Core 3.1</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

<span data-ttu-id="3cebb-151">Aşağıdaki komut `scl-utils` paketini yüklüyor:</span><span class="sxs-lookup"><span data-stu-id="3cebb-151">The following command installs the `scl-utils` package:</span></span>

```bash
sudo yum install scl-utils
```

### <a name="install-the-sdk"></a><span data-ttu-id="3cebb-152">SDK Yükleme</span><span class="sxs-lookup"><span data-stu-id="3cebb-152">Install the SDK</span></span>

<span data-ttu-id="3cebb-153">.NET Core SDK .NET Core ile uygulama geliştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3cebb-153">.NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="3cebb-154">.NET Core SDK yüklerseniz, ilgili çalışma zamanını yüklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="3cebb-154">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="3cebb-155">.NET Core SDK yüklemek için aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="3cebb-155">To install .NET Core SDK, run the following commands:</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

<span data-ttu-id="3cebb-156">Red hat, `rh-dotnet31` diğer programları etkileyebileceğinden, kalıcı olarak etkinleştirilmesini önermez.</span><span class="sxs-lookup"><span data-stu-id="3cebb-156">Red Hat does not recommend permanently enabling `rh-dotnet31` because it may affect other programs.</span></span> <span data-ttu-id="3cebb-157">Örneğin, `rh-dotnet31` `libcurl` temel RHEL sürümünden farklı bir sürümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="3cebb-157">For example, `rh-dotnet31` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="3cebb-158">Bu, farklı bir sürümü beklemediği programlarda sorunlara yol açabilir `libcurl` .</span><span class="sxs-lookup"><span data-stu-id="3cebb-158">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="3cebb-159">`rh-dotnet`Kalıcı olarak etkinleştirmek istiyorsanız, _~/,bashrc_ dosyanıza şu satırı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3cebb-159">If you want to enable `rh-dotnet` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet31
```

### <a name="install-the-runtime"></a><span data-ttu-id="3cebb-160">Çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="3cebb-160">Install the runtime</span></span>

<span data-ttu-id="3cebb-161">.NET Core çalışma zamanı, .NET Core ile oluşturulmuş uygulamaları çalışma zamanını içermeyen uygulamalar çalıştırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3cebb-161">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="3cebb-162">Aşağıdaki komutlar, .NET Core için en uyumlu çalışma zamanı olan ASP.NET Core çalışma zamanını yükler.</span><span class="sxs-lookup"><span data-stu-id="3cebb-162">The commands below install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="3cebb-163">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3cebb-163">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

<span data-ttu-id="3cebb-164">Red hat, `rh-dotnet31` diğer programları etkileyebileceğinden, kalıcı olarak etkinleştirilmesini önermez.</span><span class="sxs-lookup"><span data-stu-id="3cebb-164">Red Hat does not recommend permanently enabling `rh-dotnet31` because it may affect other programs.</span></span> <span data-ttu-id="3cebb-165">Örneğin, `rh-dotnet31` `libcurl` temel RHEL sürümünden farklı bir sürümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="3cebb-165">For example, `rh-dotnet31` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="3cebb-166">Bu, farklı bir sürümü beklemediği programlarda sorunlara yol açabilir `libcurl` .</span><span class="sxs-lookup"><span data-stu-id="3cebb-166">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="3cebb-167">`rh-dotnet31`Kalıcı olarak etkinleştirmek istiyorsanız, _~/,bashrc_ dosyanıza şu satırı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3cebb-167">If you want to enable `rh-dotnet31` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet31
```

<span data-ttu-id="3cebb-168">ASP.NET Core çalışma zamanına alternatif olarak, ASP.NET Core desteği içermeyen .NET Core çalışma zamanı 'nı yükleyebilirsiniz: Yukarıdaki komutlarda ' yi ile değiştirin `rh-dotnet31-aspnetcore-runtime-3.1` `rh-dotnet31-dotnet-runtime-3.1` .</span><span class="sxs-lookup"><span data-stu-id="3cebb-168">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `rh-dotnet31-aspnetcore-runtime-3.1` in the commands above with `rh-dotnet31-dotnet-runtime-3.1`.</span></span>

## <a name="dependencies"></a><span data-ttu-id="3cebb-169">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="3cebb-169">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="3cebb-170">Diğer sürümleri nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="3cebb-170">How to install other versions</span></span>

<span data-ttu-id="3cebb-171">.Net 'in diğer sürümlerini yüklemek için gereken adımlarda [.net Için Red Hat belgelerine](https://access.redhat.com/documentation/net/5.0/) başvurun.</span><span class="sxs-lookup"><span data-stu-id="3cebb-171">Consult the [Red Hat documentation for .NET](https://access.redhat.com/documentation/net/5.0/) on the steps required to install other releases of .NET.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3cebb-172">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="3cebb-172">Next steps</span></span>

- [<span data-ttu-id="3cebb-173">.NET CLı için sekme tamamlamayı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="3cebb-173">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="3cebb-174">Öğretici: Visual Studio Code kullanarak .NET SDK ile bir konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="3cebb-174">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
