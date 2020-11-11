---
title: .NET 'i alp-.NET üzerine yükler
description: .NET SDK ve .NET çalışma zamanının alp 'ye yüklenmesi için çeşitli yollar gösterir.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 29901cc24ddd4bbe8200a36765ddd29f501394c0
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506833"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-alpine"></a><span data-ttu-id="f8e70-103">.NET SDK 'sını veya .NET çalışma zamanını alp 'ye yükler</span><span class="sxs-lookup"><span data-stu-id="f8e70-103">Install the .NET SDK or the .NET Runtime on Alpine</span></span>

<span data-ttu-id="f8e70-104">Bu makalede, alp 'de .NET yüklemesinin nasıl yapılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="f8e70-104">This article describes how to install .NET on Alpine.</span></span> <span data-ttu-id="f8e70-105">Bir alp sürümü destek dışı kaldığında, .NET artık bu sürümde desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="f8e70-105">When an Alpine version falls out of support, .NET is no longer supported with that version.</span></span> <span data-ttu-id="f8e70-106">Ancak, bu yönergeler desteklenmese de bu sürümler üzerinde çalışan .NET almanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="f8e70-106">However, these instructions may help you to get .NET running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

<span data-ttu-id="f8e70-107">Alp için yükleyiciler yok.</span><span class="sxs-lookup"><span data-stu-id="f8e70-107">There are no installers for Alpine.</span></span> <span data-ttu-id="f8e70-108">[Install betiğini](#scripted-install) kullanmanız veya [el ile Install](#manual-install) yönergelerini izlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f8e70-108">You must either use the [install script](#scripted-install) or follow the [manual install](#manual-install) instructions.</span></span>

## <a name="supported-distributions"></a><span data-ttu-id="f8e70-109">Desteklenen dağıtımlar</span><span class="sxs-lookup"><span data-stu-id="f8e70-109">Supported distributions</span></span>

<span data-ttu-id="f8e70-110">Aşağıdaki tabloda, şu anda desteklenen .NET sürümlerinin ve ' de desteklendiği alp sürümlerinin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f8e70-110">The following table is a list of currently supported .NET releases and the versions of Alpine they're supported on.</span></span> <span data-ttu-id="f8e70-111">Bu sürümler, [.NET sürümü destek sonu](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya [alçam sürümü yaşam sonuna ulaştığında](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases)desteklenene kadar desteklenmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="f8e70-111">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Alpine reaches end-of-life](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).</span></span>

- <span data-ttu-id="f8e70-112">✔️, alp veya .NET sürümünün hala desteklendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f8e70-112">A ✔️ indicates that the version of Alpine or .NET is still supported.</span></span>
- <span data-ttu-id="f8e70-113">A ❌ , alp veya .NET sürümünün bu alp sürümünde desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f8e70-113">A ❌ indicates that the version of Alpine or .NET isn't supported on that Alpine release.</span></span>
- <span data-ttu-id="f8e70-114">Hem alp hem de bir .NET sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f8e70-114">When both a version of Alpine and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="f8e70-115">Alpine</span><span class="sxs-lookup"><span data-stu-id="f8e70-115">Alpine</span></span>  | <span data-ttu-id="f8e70-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="f8e70-116">.NET Core 2.1</span></span> | <span data-ttu-id="f8e70-117">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="f8e70-117">.NET Core 3.1</span></span> | <span data-ttu-id="f8e70-118">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="f8e70-118">.NET 5.0</span></span> |
|-------- |---------------|---------------|----------------|
| <span data-ttu-id="f8e70-119">✔️ 3,12</span><span class="sxs-lookup"><span data-stu-id="f8e70-119">✔️ 3.12</span></span> | <span data-ttu-id="f8e70-120">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="f8e70-120">✔️ 2.1</span></span>        | <span data-ttu-id="f8e70-121">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="f8e70-121">✔️ 3.1</span></span>        | <span data-ttu-id="f8e70-122">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="f8e70-122">✔️ 5.0</span></span> |
| <span data-ttu-id="f8e70-123">✔️ 3,11</span><span class="sxs-lookup"><span data-stu-id="f8e70-123">✔️ 3.11</span></span> | <span data-ttu-id="f8e70-124">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="f8e70-124">✔️ 2.1</span></span>        | <span data-ttu-id="f8e70-125">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="f8e70-125">✔️ 3.1</span></span>        | <span data-ttu-id="f8e70-126">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="f8e70-126">✔️ 5.0</span></span> |
| <span data-ttu-id="f8e70-127">✔️ 3,10</span><span class="sxs-lookup"><span data-stu-id="f8e70-127">✔️ 3.10</span></span> | <span data-ttu-id="f8e70-128">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="f8e70-128">✔️ 2.1</span></span>        | <span data-ttu-id="f8e70-129">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="f8e70-129">✔️ 3.1</span></span>        | <span data-ttu-id="f8e70-130">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="f8e70-130">❌ 5.0</span></span> |
| <span data-ttu-id="f8e70-131">❌ 3,9</span><span class="sxs-lookup"><span data-stu-id="f8e70-131">❌ 3.9</span></span>  | <span data-ttu-id="f8e70-132">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="f8e70-132">✔️ 2.1</span></span>        | <span data-ttu-id="f8e70-133">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="f8e70-133">✔️ 3.1</span></span>        | <span data-ttu-id="f8e70-134">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="f8e70-134">❌ 5.0</span></span> |
| <span data-ttu-id="f8e70-135">❌ 3,8</span><span class="sxs-lookup"><span data-stu-id="f8e70-135">❌ 3.8</span></span>  | <span data-ttu-id="f8e70-136">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="f8e70-136">✔️ 2.1</span></span>        | <span data-ttu-id="f8e70-137">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="f8e70-137">✔️ 3.1</span></span>        | <span data-ttu-id="f8e70-138">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="f8e70-138">❌ 5.0</span></span> |

<span data-ttu-id="f8e70-139">Aşağıdaki .NET sürümleri artık desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="f8e70-139">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="f8e70-140">Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:</span><span class="sxs-lookup"><span data-stu-id="f8e70-140">The downloads for these still remain published:</span></span>

- <span data-ttu-id="f8e70-141">3,0</span><span class="sxs-lookup"><span data-stu-id="f8e70-141">3.0</span></span>
- <span data-ttu-id="f8e70-142">2.2</span><span class="sxs-lookup"><span data-stu-id="f8e70-142">2.2</span></span>
- <span data-ttu-id="f8e70-143">2,0</span><span class="sxs-lookup"><span data-stu-id="f8e70-143">2.0</span></span>

## <a name="dependencies"></a><span data-ttu-id="f8e70-144">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="f8e70-144">Dependencies</span></span>

<span data-ttu-id="f8e70-145">.NET alp Linux 'ta aşağıdaki bağımlılıkların yüklü olmasını gerektirir:</span><span class="sxs-lookup"><span data-stu-id="f8e70-145">.NET on Alpine Linux requires the following dependencies installed:</span></span>

- <span data-ttu-id="f8e70-146">ICU-libs</span><span class="sxs-lookup"><span data-stu-id="f8e70-146">icu-libs</span></span>
- <span data-ttu-id="f8e70-147">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="f8e70-147">krb5-libs</span></span>
- <span data-ttu-id="f8e70-148">libgcc</span><span class="sxs-lookup"><span data-stu-id="f8e70-148">libgcc</span></span>
- <span data-ttu-id="f8e70-149">libintl</span><span class="sxs-lookup"><span data-stu-id="f8e70-149">libintl</span></span>
- <span data-ttu-id="f8e70-150">libssl 1.1 (alp v 3.9 veya üzeri)</span><span class="sxs-lookup"><span data-stu-id="f8e70-150">libssl1.1 (Alpine v3.9 or greater)</span></span>
- <span data-ttu-id="f8e70-151">libssl 1.0 (alp v 3.8 veya Lower)</span><span class="sxs-lookup"><span data-stu-id="f8e70-151">libssl1.0 (Alpine v3.8 or lower)</span></span>
- <span data-ttu-id="f8e70-152">libstdc + +</span><span class="sxs-lookup"><span data-stu-id="f8e70-152">libstdc++</span></span>
- <span data-ttu-id="f8e70-153">zlib</span><span class="sxs-lookup"><span data-stu-id="f8e70-153">zlib</span></span>

## <a name="scripted-install"></a><span data-ttu-id="f8e70-154">Komut dosyalı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="f8e70-154">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="f8e70-155">El ile yüklemesi</span><span class="sxs-lookup"><span data-stu-id="f8e70-155">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="f8e70-156">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="f8e70-156">Next steps</span></span>

- [<span data-ttu-id="f8e70-157">Öğretici: Visual Studio Code kullanarak .NET SDK ile bir konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="f8e70-157">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
