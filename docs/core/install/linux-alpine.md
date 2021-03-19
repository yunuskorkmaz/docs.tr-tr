---
title: .NET 'i alp-.NET üzerine yükler
description: .NET SDK ve .NET çalışma zamanının alp 'ye yüklenmesi için çeşitli yollar gösterir.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 19cae3c6237dc9f1a23087ec654e8f24ca13cd66
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104653445"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-alpine"></a><span data-ttu-id="92062-103">.NET SDK 'sını veya .NET çalışma zamanını alp 'ye yükler</span><span class="sxs-lookup"><span data-stu-id="92062-103">Install the .NET SDK or the .NET Runtime on Alpine</span></span>

<span data-ttu-id="92062-104">Bu makalede, alp 'de .NET yüklemesinin nasıl yapılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="92062-104">This article describes how to install .NET on Alpine.</span></span> <span data-ttu-id="92062-105">Bir alp sürümü destek dışı kaldığında, .NET artık bu sürümde desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="92062-105">When an Alpine version falls out of support, .NET is no longer supported with that version.</span></span> <span data-ttu-id="92062-106">Ancak, bu yönergeler desteklenmese de bu sürümler üzerinde çalışan .NET almanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="92062-106">However, these instructions may help you to get .NET running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="install"></a><span data-ttu-id="92062-107">Yükleme</span><span class="sxs-lookup"><span data-stu-id="92062-107">Install</span></span>

<span data-ttu-id="92062-108">Yükleyiciler alp Linux için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="92062-108">Installers aren't available for Alpine Linux.</span></span> <span data-ttu-id="92062-109">.NET 'i aşağıdaki yöntemlerle birini yüklemelisiniz:</span><span class="sxs-lookup"><span data-stu-id="92062-109">You must install .NET in one of the following ways:</span></span>

- [<span data-ttu-id="92062-110">Yaslama paketi</span><span class="sxs-lookup"><span data-stu-id="92062-110">Snap package</span></span>](linux-snap.md)
- [<span data-ttu-id="92062-111">_İnstall-DotNet.sh_ ile betikleştirilmiş install</span><span class="sxs-lookup"><span data-stu-id="92062-111">Scripted install with _install-dotnet.sh_</span></span>](linux-scripted-manual.md#scripted-install)
- [<span data-ttu-id="92062-112">El ile ikili ayıklama</span><span class="sxs-lookup"><span data-stu-id="92062-112">Manual binary extraction</span></span>](linux-scripted-manual.md#manual-install)

## <a name="supported-distributions"></a><span data-ttu-id="92062-113">Desteklenen dağıtımlar</span><span class="sxs-lookup"><span data-stu-id="92062-113">Supported distributions</span></span>

<span data-ttu-id="92062-114">Aşağıdaki tabloda, şu anda desteklenen .NET sürümlerinin ve ' de desteklendiği alp sürümlerinin bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="92062-114">The following table is a list of currently supported .NET releases and the versions of Alpine they're supported on.</span></span> <span data-ttu-id="92062-115">Bu sürümler, [.NET sürümü destek sonu](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya [alçam sürümü yaşam sonuna ulaştığında](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases)desteklenene kadar desteklenmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="92062-115">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Alpine reaches end-of-life](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).</span></span>

- <span data-ttu-id="92062-116">✔️, alp veya .NET sürümünün hala desteklendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="92062-116">A ✔️ indicates that the version of Alpine or .NET is still supported.</span></span>
- <span data-ttu-id="92062-117">A ❌ , alp veya .NET sürümünün bu alp sürümünde desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="92062-117">A ❌ indicates that the version of Alpine or .NET isn't supported on that Alpine release.</span></span>
- <span data-ttu-id="92062-118">Hem alp hem de bir .NET sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="92062-118">When both a version of Alpine and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="92062-119">Alpine</span><span class="sxs-lookup"><span data-stu-id="92062-119">Alpine</span></span>  | <span data-ttu-id="92062-120">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="92062-120">.NET Core 2.1</span></span> | <span data-ttu-id="92062-121">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="92062-121">.NET Core 3.1</span></span> | <span data-ttu-id="92062-122">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="92062-122">.NET 5.0</span></span> |
|-------- |---------------|---------------|----------------|
| <span data-ttu-id="92062-123">✔️ 3,12</span><span class="sxs-lookup"><span data-stu-id="92062-123">✔️ 3.12</span></span> | <span data-ttu-id="92062-124">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="92062-124">✔️ 2.1</span></span>        | <span data-ttu-id="92062-125">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="92062-125">✔️ 3.1</span></span>        | <span data-ttu-id="92062-126">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="92062-126">✔️ 5.0</span></span> |
| <span data-ttu-id="92062-127">✔️ 3,11</span><span class="sxs-lookup"><span data-stu-id="92062-127">✔️ 3.11</span></span> | <span data-ttu-id="92062-128">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="92062-128">✔️ 2.1</span></span>        | <span data-ttu-id="92062-129">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="92062-129">✔️ 3.1</span></span>        | <span data-ttu-id="92062-130">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="92062-130">✔️ 5.0</span></span> |
| <span data-ttu-id="92062-131">✔️ 3,10</span><span class="sxs-lookup"><span data-stu-id="92062-131">✔️ 3.10</span></span> | <span data-ttu-id="92062-132">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="92062-132">✔️ 2.1</span></span>        | <span data-ttu-id="92062-133">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="92062-133">✔️ 3.1</span></span>        | <span data-ttu-id="92062-134">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="92062-134">❌ 5.0</span></span> |
| <span data-ttu-id="92062-135">❌ 3,9</span><span class="sxs-lookup"><span data-stu-id="92062-135">❌ 3.9</span></span>  | <span data-ttu-id="92062-136">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="92062-136">✔️ 2.1</span></span>        | <span data-ttu-id="92062-137">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="92062-137">✔️ 3.1</span></span>        | <span data-ttu-id="92062-138">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="92062-138">❌ 5.0</span></span> |
| <span data-ttu-id="92062-139">❌ 3,8</span><span class="sxs-lookup"><span data-stu-id="92062-139">❌ 3.8</span></span>  | <span data-ttu-id="92062-140">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="92062-140">✔️ 2.1</span></span>        | <span data-ttu-id="92062-141">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="92062-141">✔️ 3.1</span></span>        | <span data-ttu-id="92062-142">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="92062-142">❌ 5.0</span></span> |

<span data-ttu-id="92062-143">Aşağıdaki .NET sürümleri artık desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="92062-143">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="92062-144">Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:</span><span class="sxs-lookup"><span data-stu-id="92062-144">The downloads for these still remain published:</span></span>

- <span data-ttu-id="92062-145">3.0</span><span class="sxs-lookup"><span data-stu-id="92062-145">3.0</span></span>
- <span data-ttu-id="92062-146">2,2</span><span class="sxs-lookup"><span data-stu-id="92062-146">2.2</span></span>
- <span data-ttu-id="92062-147">2.0</span><span class="sxs-lookup"><span data-stu-id="92062-147">2.0</span></span>

## <a name="dependencies"></a><span data-ttu-id="92062-148">Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="92062-148">Dependencies</span></span>

<span data-ttu-id="92062-149">.NET alp Linux 'ta aşağıdaki bağımlılıkların yüklü olmasını gerektirir:</span><span class="sxs-lookup"><span data-stu-id="92062-149">.NET on Alpine Linux requires the following dependencies installed:</span></span>

- <span data-ttu-id="92062-150">bash</span><span class="sxs-lookup"><span data-stu-id="92062-150">bash</span></span>
- <span data-ttu-id="92062-151">ICU-libs</span><span class="sxs-lookup"><span data-stu-id="92062-151">icu-libs</span></span>
- <span data-ttu-id="92062-152">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="92062-152">krb5-libs</span></span>
- <span data-ttu-id="92062-153">libgcc</span><span class="sxs-lookup"><span data-stu-id="92062-153">libgcc</span></span>
- <span data-ttu-id="92062-154">libgdiplus (.NET uygulaması *System. Drawing. Common* derlemesini gerektiriyorsa)</span><span class="sxs-lookup"><span data-stu-id="92062-154">libgdiplus (if the .NET app requires the *System.Drawing.Common* assembly)</span></span>
- <span data-ttu-id="92062-155">libintl</span><span class="sxs-lookup"><span data-stu-id="92062-155">libintl</span></span>
- <span data-ttu-id="92062-156">libssl 1.1 (alp v 3.9 veya üzeri)</span><span class="sxs-lookup"><span data-stu-id="92062-156">libssl1.1 (Alpine v3.9 or greater)</span></span>
- <span data-ttu-id="92062-157">libssl 1.0 (alp v 3.8 veya Lower)</span><span class="sxs-lookup"><span data-stu-id="92062-157">libssl1.0 (Alpine v3.8 or lower)</span></span>
- <span data-ttu-id="92062-158">libstdc + +</span><span class="sxs-lookup"><span data-stu-id="92062-158">libstdc++</span></span>
- <span data-ttu-id="92062-159">zlib</span><span class="sxs-lookup"><span data-stu-id="92062-159">zlib</span></span>

<span data-ttu-id="92062-160">Gerekli gereksinimleri yüklemek için şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="92062-160">To install the needed requirements, run the following command:</span></span>

```bash
apk add bash icu-libs krb5-libs libgcc libintl libssl1.1 libstdc++ zlib
```

<span data-ttu-id="92062-161">**Libgdiplus**'yi yüklemek için bir depo belirtmeniz gerekebilir:</span><span class="sxs-lookup"><span data-stu-id="92062-161">To install **libgdiplus**, you may need to specify a repository:</span></span>

```bash
apk add libgdiplus --repository https://dl-3.alpinelinux.org/alpine/edge/testing/
```

## <a name="next-steps"></a><span data-ttu-id="92062-162">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="92062-162">Next steps</span></span>

- [<span data-ttu-id="92062-163">.NET CLı için sekme tamamlamayı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="92062-163">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="92062-164">Öğretici: Visual Studio Code kullanarak .NET SDK ile bir konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="92062-164">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
