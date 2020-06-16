---
title: Alp-.NET Core 'a .NET Core 'u yükler
description: .NET Core SDK ve .NET Core çalışma zamanını alp 'ye yüklemenin çeşitli yollarını gösterir.
author: thraka
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: bbaf4ee9020dcd33c894b5376bf04ad65db8d378
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84771505"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-alpine"></a><span data-ttu-id="54233-103">Alp 'de .NET Core SDK veya .NET Core çalışma zamanı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="54233-103">Install .NET Core SDK or .NET Core Runtime on Alpine</span></span>

<span data-ttu-id="54233-104">Bu makalede, alp 'de .NET Core 'un nasıl yükleneceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="54233-104">This article describes how to install .NET Core on Alpine.</span></span> <span data-ttu-id="54233-105">Bir alp sürümü destek dışı kaldığında, .NET Core artık bu sürümle desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="54233-105">When a Alpine version falls out of support, .NET Core is no longer supported with that version.</span></span> <span data-ttu-id="54233-106">Ancak, bu yönergeler desteklenmese de, bu sürümler üzerinde çalışan .NET Core 'u almanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="54233-106">However, these instructions may help you to get .NET Core running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

<span data-ttu-id="54233-107">Alp için yükleyiciler yok.</span><span class="sxs-lookup"><span data-stu-id="54233-107">There are no installers for Alpine.</span></span> <span data-ttu-id="54233-108">[Install betiğini](#scripted-install) kullanmanız veya [el ile Install](#manual-install) yönergelerini izlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="54233-108">You must either use the [install script](#scripted-install) or follow the [manual install](#manual-install) instructions.</span></span>

## <a name="supported-distributions"></a><span data-ttu-id="54233-109">Desteklenen dağıtımlar</span><span class="sxs-lookup"><span data-stu-id="54233-109">Supported distributions</span></span>

<span data-ttu-id="54233-110">Aşağıdaki tabloda, şu anda desteklenen .NET Core sürümlerinin ve ' de desteklendiği alp sürümlerinin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="54233-110">The following table is a list of currently supported .NET Core releases and the versions of Alpine they're supported on.</span></span> <span data-ttu-id="54233-111">Bu sürümler, [.NET Core 'un sürümü destek sonuna ulaşana](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya [alçam sürümü yaşam sonuna ulaştığında](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases)desteklenene kadar desteklenmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="54233-111">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Alpine reaches end-of-life](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).</span></span>

- <span data-ttu-id="54233-112">✔️, alp veya .NET Core sürümünün hala desteklendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="54233-112">A ✔️ indicates that the version of Alpine or .NET Core is still supported.</span></span>
- <span data-ttu-id="54233-113">A ❌ , alp veya .NET Core sürümünün bu Alu sürümünde desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="54233-113">A ❌ indicates that the version of Alpine or .NET Core isn't supported on that Alpine release.</span></span>
- <span data-ttu-id="54233-114">Hem alp hem de bir .NET Core sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="54233-114">When both a version of Alpine and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="54233-115">Alpine</span><span class="sxs-lookup"><span data-stu-id="54233-115">Alpine</span></span>                   | <span data-ttu-id="54233-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="54233-116">.NET Core 2.1</span></span> | <span data-ttu-id="54233-117">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="54233-117">.NET Core 3.1</span></span> | <span data-ttu-id="54233-118">.NET 5 Preview</span><span class="sxs-lookup"><span data-stu-id="54233-118">.NET 5 Preview</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="54233-119">✔️ 3,12</span><span class="sxs-lookup"><span data-stu-id="54233-119">✔️ 3.12</span></span>  | <span data-ttu-id="54233-120">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="54233-120">✔️ 2.1</span></span>        | <span data-ttu-id="54233-121">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="54233-121">✔️ 3.1</span></span>        | <span data-ttu-id="54233-122">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="54233-122">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="54233-123">✔️ 3,11</span><span class="sxs-lookup"><span data-stu-id="54233-123">✔️ 3.11</span></span>  | <span data-ttu-id="54233-124">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="54233-124">✔️ 2.1</span></span>        | <span data-ttu-id="54233-125">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="54233-125">✔️ 3.1</span></span>        | <span data-ttu-id="54233-126">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="54233-126">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="54233-127">✔️ 3,10</span><span class="sxs-lookup"><span data-stu-id="54233-127">✔️ 3.10</span></span>  | <span data-ttu-id="54233-128">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="54233-128">✔️ 2.1</span></span>        | <span data-ttu-id="54233-129">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="54233-129">✔️ 3.1</span></span>        | <span data-ttu-id="54233-130">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="54233-130">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="54233-131">✔️ 3,9</span><span class="sxs-lookup"><span data-stu-id="54233-131">✔️ 3.9</span></span>   | <span data-ttu-id="54233-132">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="54233-132">✔️ 2.1</span></span>        | <span data-ttu-id="54233-133">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="54233-133">✔️ 3.1</span></span>        | <span data-ttu-id="54233-134">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="54233-134">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="54233-135">❌3,8</span><span class="sxs-lookup"><span data-stu-id="54233-135">❌ 3.8</span></span>   | <span data-ttu-id="54233-136">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="54233-136">✔️ 2.1</span></span>        | <span data-ttu-id="54233-137">❌3,1</span><span class="sxs-lookup"><span data-stu-id="54233-137">❌ 3.1</span></span>        | <span data-ttu-id="54233-138">❌5,0 Önizleme</span><span class="sxs-lookup"><span data-stu-id="54233-138">❌ 5.0 Preview</span></span> |

<span data-ttu-id="54233-139">Aşağıdaki .NET Core sürümleri artık desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="54233-139">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="54233-140">Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:</span><span class="sxs-lookup"><span data-stu-id="54233-140">The downloads for these still remain published:</span></span>

- <span data-ttu-id="54233-141">3.0</span><span class="sxs-lookup"><span data-stu-id="54233-141">3.0</span></span>
- <span data-ttu-id="54233-142">2,2</span><span class="sxs-lookup"><span data-stu-id="54233-142">2.2</span></span>
- <span data-ttu-id="54233-143">2.0</span><span class="sxs-lookup"><span data-stu-id="54233-143">2.0</span></span>

## <a name="dependencies"></a><span data-ttu-id="54233-144">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="54233-144">Dependencies</span></span>

<span data-ttu-id="54233-145">Alp Linux üzerinde .NET Core aşağıdaki bağımlılıkların yüklü olmasını gerektirir:</span><span class="sxs-lookup"><span data-stu-id="54233-145">.NET Core on Alpine Linux requires the following dependencies installed:</span></span>

- <span data-ttu-id="54233-146">ICU-libs</span><span class="sxs-lookup"><span data-stu-id="54233-146">icu-libs</span></span>
- <span data-ttu-id="54233-147">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="54233-147">krb5-libs</span></span>
- <span data-ttu-id="54233-148">libintl</span><span class="sxs-lookup"><span data-stu-id="54233-148">libintl</span></span>
- <span data-ttu-id="54233-149">libssl 1.1 (alp v 3.9 veya üzeri)</span><span class="sxs-lookup"><span data-stu-id="54233-149">libssl1.1 (Alpine v3.9 or greater)</span></span>
- <span data-ttu-id="54233-150">libssl 1.0 (alp v 3.8)</span><span class="sxs-lookup"><span data-stu-id="54233-150">libssl1.0 (Alpine v3.8)</span></span>
- <span data-ttu-id="54233-151">libstdc + +</span><span class="sxs-lookup"><span data-stu-id="54233-151">libstdc++</span></span>
- <span data-ttu-id="54233-152">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="54233-152">lttng-ust</span></span>
- <span data-ttu-id="54233-153">numactl (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="54233-153">numactl (optional)</span></span>
- <span data-ttu-id="54233-154">zlib</span><span class="sxs-lookup"><span data-stu-id="54233-154">zlib</span></span>

## <a name="scripted-install"></a><span data-ttu-id="54233-155">Komut dosyalı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="54233-155">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="54233-156">El ile yüklemesi</span><span class="sxs-lookup"><span data-stu-id="54233-156">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="54233-157">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="54233-157">Next steps</span></span>

- [<span data-ttu-id="54233-158">Öğretici: Visual Studio Code kullanarak .NET Core SDK bir konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="54233-158">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
