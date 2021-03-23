---
title: .NET 'i alp-.NET üzerine yükler
description: .NET SDK ve .NET çalışma zamanının alp 'ye yüklenmesi için çeşitli yollar gösterir.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: ece9a253cc11195c67e79c89747efe462a71632d
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873763"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-alpine"></a><span data-ttu-id="0e1f8-103">.NET SDK 'sını veya .NET çalışma zamanını alp 'ye yükler</span><span class="sxs-lookup"><span data-stu-id="0e1f8-103">Install the .NET SDK or the .NET Runtime on Alpine</span></span>

<span data-ttu-id="0e1f8-104">Bu makalede, alp 'de .NET yüklemesinin nasıl yapılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="0e1f8-104">This article describes how to install .NET on Alpine.</span></span> <span data-ttu-id="0e1f8-105">Bir alp sürümü destek dışı kaldığında, .NET artık bu sürümde desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="0e1f8-105">When an Alpine version falls out of support, .NET is no longer supported with that version.</span></span> <span data-ttu-id="0e1f8-106">Ancak, bu yönergeler desteklenmese de bu sürümler üzerinde çalışan .NET almanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="0e1f8-106">However, these instructions may help you to get .NET running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="install"></a><span data-ttu-id="0e1f8-107">Yükleme</span><span class="sxs-lookup"><span data-stu-id="0e1f8-107">Install</span></span>

<span data-ttu-id="0e1f8-108">Yükleyiciler alp Linux için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0e1f8-108">Installers aren't available for Alpine Linux.</span></span> <span data-ttu-id="0e1f8-109">.NET 'i aşağıdaki yöntemlerle birini yüklemelisiniz:</span><span class="sxs-lookup"><span data-stu-id="0e1f8-109">You must install .NET in one of the following ways:</span></span>

- [<span data-ttu-id="0e1f8-110">Yaslama paketi</span><span class="sxs-lookup"><span data-stu-id="0e1f8-110">Snap package</span></span>](linux-snap.md)
- [<span data-ttu-id="0e1f8-111">_İnstall-DotNet.sh_ ile betikleştirilmiş install</span><span class="sxs-lookup"><span data-stu-id="0e1f8-111">Scripted install with _install-dotnet.sh_</span></span>](linux-scripted-manual.md#scripted-install)
- [<span data-ttu-id="0e1f8-112">El ile ikili ayıklama</span><span class="sxs-lookup"><span data-stu-id="0e1f8-112">Manual binary extraction</span></span>](linux-scripted-manual.md#manual-install)

## <a name="supported-distributions"></a><span data-ttu-id="0e1f8-113">Desteklenen dağıtımlar</span><span class="sxs-lookup"><span data-stu-id="0e1f8-113">Supported distributions</span></span>

<span data-ttu-id="0e1f8-114">Aşağıdaki tabloda, şu anda desteklenen .NET sürümlerinin ve ' de desteklendiği alp sürümlerinin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0e1f8-114">The following table is a list of currently supported .NET releases and the versions of Alpine they're supported on.</span></span> <span data-ttu-id="0e1f8-115">Bu sürümler, [.NET sürümü destek sonu](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya [alçam sürümü yaşam sonuna ulaştığında](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases)desteklenene kadar desteklenmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="0e1f8-115">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Alpine reaches end-of-life](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).</span></span>

- <span data-ttu-id="0e1f8-116">✔️, alp veya .NET sürümünün hala desteklendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0e1f8-116">A ✔️ indicates that the version of Alpine or .NET is still supported.</span></span>
- <span data-ttu-id="0e1f8-117">A ❌ , alp veya .NET sürümünün bu alp sürümünde desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0e1f8-117">A ❌ indicates that the version of Alpine or .NET isn't supported on that Alpine release.</span></span>
- <span data-ttu-id="0e1f8-118">Hem alp hem de bir .NET sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="0e1f8-118">When both a version of Alpine and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="0e1f8-119">Alpine</span><span class="sxs-lookup"><span data-stu-id="0e1f8-119">Alpine</span></span>  | <span data-ttu-id="0e1f8-120">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="0e1f8-120">.NET Core 2.1</span></span> | <span data-ttu-id="0e1f8-121">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="0e1f8-121">.NET Core 3.1</span></span> | <span data-ttu-id="0e1f8-122">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="0e1f8-122">.NET 5.0</span></span> |
|-------- |---------------|---------------|----------------|
| <span data-ttu-id="0e1f8-123">✔️ 3,13</span><span class="sxs-lookup"><span data-stu-id="0e1f8-123">✔️ 3.13</span></span> | <span data-ttu-id="0e1f8-124">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="0e1f8-124">✔️ 2.1</span></span>        | <span data-ttu-id="0e1f8-125">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="0e1f8-125">✔️ 3.1</span></span>        | <span data-ttu-id="0e1f8-126">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="0e1f8-126">✔️ 5.0</span></span> |
| <span data-ttu-id="0e1f8-127">✔️ 3,12</span><span class="sxs-lookup"><span data-stu-id="0e1f8-127">✔️ 3.12</span></span> | <span data-ttu-id="0e1f8-128">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="0e1f8-128">✔️ 2.1</span></span>        | <span data-ttu-id="0e1f8-129">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="0e1f8-129">✔️ 3.1</span></span>        | <span data-ttu-id="0e1f8-130">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="0e1f8-130">✔️ 5.0</span></span> |
| <span data-ttu-id="0e1f8-131">✔️ 3,11</span><span class="sxs-lookup"><span data-stu-id="0e1f8-131">✔️ 3.11</span></span> | <span data-ttu-id="0e1f8-132">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="0e1f8-132">✔️ 2.1</span></span>        | <span data-ttu-id="0e1f8-133">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="0e1f8-133">✔️ 3.1</span></span>        | <span data-ttu-id="0e1f8-134">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="0e1f8-134">✔️ 5.0</span></span> |
| <span data-ttu-id="0e1f8-135">✔️ 3,10</span><span class="sxs-lookup"><span data-stu-id="0e1f8-135">✔️ 3.10</span></span> | <span data-ttu-id="0e1f8-136">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="0e1f8-136">✔️ 2.1</span></span>        | <span data-ttu-id="0e1f8-137">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="0e1f8-137">✔️ 3.1</span></span>        | <span data-ttu-id="0e1f8-138">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="0e1f8-138">❌ 5.0</span></span> |
| <span data-ttu-id="0e1f8-139">❌ 3,9</span><span class="sxs-lookup"><span data-stu-id="0e1f8-139">❌ 3.9</span></span>  | <span data-ttu-id="0e1f8-140">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="0e1f8-140">✔️ 2.1</span></span>        | <span data-ttu-id="0e1f8-141">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="0e1f8-141">✔️ 3.1</span></span>        | <span data-ttu-id="0e1f8-142">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="0e1f8-142">❌ 5.0</span></span> |
| <span data-ttu-id="0e1f8-143">❌ 3,8</span><span class="sxs-lookup"><span data-stu-id="0e1f8-143">❌ 3.8</span></span>  | <span data-ttu-id="0e1f8-144">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="0e1f8-144">✔️ 2.1</span></span>        | <span data-ttu-id="0e1f8-145">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="0e1f8-145">✔️ 3.1</span></span>        | <span data-ttu-id="0e1f8-146">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="0e1f8-146">❌ 5.0</span></span> |

<span data-ttu-id="0e1f8-147">Aşağıdaki .NET sürümleri artık desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="0e1f8-147">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="0e1f8-148">Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:</span><span class="sxs-lookup"><span data-stu-id="0e1f8-148">The downloads for these still remain published:</span></span>

- <span data-ttu-id="0e1f8-149">3.0</span><span class="sxs-lookup"><span data-stu-id="0e1f8-149">3.0</span></span>
- <span data-ttu-id="0e1f8-150">2,2</span><span class="sxs-lookup"><span data-stu-id="0e1f8-150">2.2</span></span>
- <span data-ttu-id="0e1f8-151">2.0</span><span class="sxs-lookup"><span data-stu-id="0e1f8-151">2.0</span></span>

## <a name="dependencies"></a><span data-ttu-id="0e1f8-152">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="0e1f8-152">Dependencies</span></span>

<span data-ttu-id="0e1f8-153">.NET alp Linux 'ta aşağıdaki bağımlılıkların yüklü olmasını gerektirir:</span><span class="sxs-lookup"><span data-stu-id="0e1f8-153">.NET on Alpine Linux requires the following dependencies installed:</span></span>

- <span data-ttu-id="0e1f8-154">bash</span><span class="sxs-lookup"><span data-stu-id="0e1f8-154">bash</span></span>
- <span data-ttu-id="0e1f8-155">ICU-libs</span><span class="sxs-lookup"><span data-stu-id="0e1f8-155">icu-libs</span></span>
- <span data-ttu-id="0e1f8-156">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="0e1f8-156">krb5-libs</span></span>
- <span data-ttu-id="0e1f8-157">libgcc</span><span class="sxs-lookup"><span data-stu-id="0e1f8-157">libgcc</span></span>
- <span data-ttu-id="0e1f8-158">libgdiplus (.NET uygulaması *System. Drawing. Common* derlemesini gerektiriyorsa)</span><span class="sxs-lookup"><span data-stu-id="0e1f8-158">libgdiplus (if the .NET app requires the *System.Drawing.Common* assembly)</span></span>
- <span data-ttu-id="0e1f8-159">libintl</span><span class="sxs-lookup"><span data-stu-id="0e1f8-159">libintl</span></span>
- <span data-ttu-id="0e1f8-160">libssl 1.1 (alp v 3.9 veya üzeri)</span><span class="sxs-lookup"><span data-stu-id="0e1f8-160">libssl1.1 (Alpine v3.9 or greater)</span></span>
- <span data-ttu-id="0e1f8-161">libssl 1.0 (alp v 3.8 veya Lower)</span><span class="sxs-lookup"><span data-stu-id="0e1f8-161">libssl1.0 (Alpine v3.8 or lower)</span></span>
- <span data-ttu-id="0e1f8-162">libstdc + +</span><span class="sxs-lookup"><span data-stu-id="0e1f8-162">libstdc++</span></span>
- <span data-ttu-id="0e1f8-163">zlib</span><span class="sxs-lookup"><span data-stu-id="0e1f8-163">zlib</span></span>

<span data-ttu-id="0e1f8-164">Gerekli gereksinimleri yüklemek için şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="0e1f8-164">To install the needed requirements, run the following command:</span></span>

```bash
apk add bash icu-libs krb5-libs libgcc libintl libssl1.1 libstdc++ zlib
```

<span data-ttu-id="0e1f8-165">**Libgdiplus**'yi yüklemek için bir depo belirtmeniz gerekebilir:</span><span class="sxs-lookup"><span data-stu-id="0e1f8-165">To install **libgdiplus**, you may need to specify a repository:</span></span>

```bash
apk add libgdiplus --repository https://dl-3.alpinelinux.org/alpine/edge/testing/
```

## <a name="next-steps"></a><span data-ttu-id="0e1f8-166">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="0e1f8-166">Next steps</span></span>

- [<span data-ttu-id="0e1f8-167">.NET CLı için sekme tamamlamayı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="0e1f8-167">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="0e1f8-168">Öğretici: Visual Studio Code kullanarak .NET SDK ile bir konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="0e1f8-168">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
