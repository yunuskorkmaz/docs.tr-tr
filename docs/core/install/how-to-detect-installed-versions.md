---
title: Windows, Linux ve macOS'ta yüklü .NET Core sürümlerini kontrol edin - .NET Core
description: .NET Core'un bilgisayarınıza hangi sürümlerinin yüklendiği listelenmeyi öğrenin. Buna .NET Core çalışma zamanı ve SDK dahildir.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 3a78acee6cf427085e98f14353fc2c0ac65d3d80
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645341"
---
# <a name="how-to-check-that-net-core-is-already-installed"></a><span data-ttu-id="70486-104">.NET Core'un zaten yüklü olduğunu kontrol etme</span><span class="sxs-lookup"><span data-stu-id="70486-104">How to check that .NET Core is already installed</span></span>

<span data-ttu-id="70486-105">Bu makalede, .NET Core çalışma zamanı ve SDK'nın hangi sürümlerinin bilgisayarınıza yüklendiği kontrol edilir.</span><span class="sxs-lookup"><span data-stu-id="70486-105">This article teaches you how to check which versions of the .NET Core runtime and SDK are installed on your computer.</span></span> <span data-ttu-id="70486-106">.NET core, Mac için Visual Studio veya Visual Studio gibi tümleşik bir geliştirme ortamınız varsa zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="70486-106">.NET core may have already been installed if you have an integrated development environment, such as Visual Studio or Visual Studio for Mac.</span></span>

<span data-ttu-id="70486-107">Bir SDK yükleme ilgili çalışma süresini yükler.</span><span class="sxs-lookup"><span data-stu-id="70486-107">Installing an SDK installs the corresponding runtime.</span></span>

<span data-ttu-id="70486-108">Bu makaledeki herhangi bir komut başarısız olursa, çalışma saatini veya SDK yüklü değil.</span><span class="sxs-lookup"><span data-stu-id="70486-108">If any command in this article fails, you don't have the runtime or SDK installed.</span></span> <span data-ttu-id="70486-109">Daha fazla bilgi için [.NET Core'u İndirve yükleyin.](index.md)</span><span class="sxs-lookup"><span data-stu-id="70486-109">For more information, see [Download and install .NET Core](index.md).</span></span>

## <a name="check-sdk-versions"></a><span data-ttu-id="70486-110">SDK sürümlerini kontrol edin</span><span class="sxs-lookup"><span data-stu-id="70486-110">Check SDK versions</span></span>

<span data-ttu-id="70486-111">.NET Core SDK'nın hangi sürümlerinin şu anda bir terminalle yüklü olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70486-111">You can see which versions of the .NET Core SDK are currently installed with a terminal.</span></span> <span data-ttu-id="70486-112">Bir terminal açın ve aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="70486-112">Open a terminal and run the following command.</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="70486-113">Aşağıdakine benzer çıktı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="70486-113">You get output similar to the following.</span></span>

::: zone pivot="os-windows"

```console
2.1.500 [C:\program files\dotnet\sdk]
2.1.502 [C:\program files\dotnet\sdk]
2.1.504 [C:\program files\dotnet\sdk]
2.1.600 [C:\program files\dotnet\sdk]
2.1.602 [C:\program files\dotnet\sdk]
2.2.101 [C:\program files\dotnet\sdk]
3.0.100 [C:\program files\dotnet\sdk]
3.1.100 [C:\program files\dotnet\sdk]
```

::: zone-end

::: zone pivot="os-linux"

```bash
2.1.500 [/home/user/dotnet/sdk]
2.1.502 [/home/user/dotnet/sdk]
2.1.504 [/home/user/dotnet/sdk]
2.1.600 [/home/user/dotnet/sdk]
2.1.602 [/home/user/dotnet/sdk]
2.2.101 [/home/user/dotnet/sdk]
3.0.100 [/home/user/dotnet/sdk]
3.1.100 [/home/user/dotnet/sdk]
```

::: zone-end

::: zone pivot="os-macos"

```bash
2.1.500 [/usr/local/share/dotnet/sdk]
2.1.502 [/usr/local/share/dotnet/sdk]
2.1.504 [/usr/local/share/dotnet/sdk]
2.1.600 [/usr/local/share/dotnet/sdk]
2.1.602 [/usr/local/share/dotnet/sdk]
2.2.101 [/usr/local/share/dotnet/sdk]
3.0.100 [/usr/local/share/dotnet/sdk]
3.1.100 [/usr/local/share/dotnet/sdk]
```

::: zone-end

## <a name="check-runtime-versions"></a><span data-ttu-id="70486-114">Çalışma zamanı sürümlerini denetleyin</span><span class="sxs-lookup"><span data-stu-id="70486-114">Check runtime versions</span></span>

<span data-ttu-id="70486-115">.NET Core çalışma zamanının hangi sürümlerinin şu anda aşağıdaki komutla yüklenmiş olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70486-115">You can see which versions of the .NET Core runtime are currently installed with the following command.</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="70486-116">Aşağıdakine benzer çıktı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="70486-116">You get output similar to the following.</span></span>

::: zone pivot="os-windows"

```console
Microsoft.AspNetCore.All 2.1.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.3 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.6 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.0.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.0 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.3 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.7 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 3.0.0 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.WindowsDesktop.App 3.0.0 [c:\program files\dotnet\shared\Microsoft.WindowsDesktop.App]
Microsoft.WindowsDesktop.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.WindowsDesktop.App]
```

::: zone-end

::: zone pivot="os-linux"

```bash
Microsoft.AspNetCore.All 2.1.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.3 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.6 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.0.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.0 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.3 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.7 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.0.0 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [/home/user/dotnet/shared/Microsoft.NETCore.App]
```

::: zone-end

::: zone pivot="os-macos"

```bash
Microsoft.AspNetCore.All 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.3 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.6 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.0.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.3 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.7 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.0.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
```

::: zone-end

## <a name="check-for-install-folders"></a><span data-ttu-id="70486-117">Klasörleri yükle denetimini denetleme</span><span class="sxs-lookup"><span data-stu-id="70486-117">Check for install folders</span></span>

<span data-ttu-id="70486-118">.NET Core'un yüklü olması ancak işletim sisteminiz `PATH` veya kullanıcı profiliniz için değişkene eklenmemiş olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="70486-118">It's possible that .NET Core is installed but not added to the `PATH` variable for your operating system or user profile.</span></span> <span data-ttu-id="70486-119">Önceki bölümlerdeki komutları çalıştırmak çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="70486-119">Running the commands from the previous sections may not work.</span></span> <span data-ttu-id="70486-120">Alternatif olarak, .NET Core yükleme klasörlerinin var olup olmadığını denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70486-120">As an alternative, you can check that the .NET Core install folders exist.</span></span>

<span data-ttu-id="70486-121">.NET Core'u yükleyiciden veya komut dosyasından yüklediğinizde, standart bir klasöre yüklenir.</span><span class="sxs-lookup"><span data-stu-id="70486-121">When you install .NET Core from an installer or script, it's installed to a standard folder.</span></span> <span data-ttu-id="70486-122">.NET Core'u yüklemek için kullandığınız yükleyici veya komut dosyası çoğu zaman farklı bir klasöre yükleme seçeneği sunar.</span><span class="sxs-lookup"><span data-stu-id="70486-122">Much of the time the installer or script you're using to install .NET Core gives you an option to install to a different folder.</span></span> <span data-ttu-id="70486-123">Farklı bir klasöre yüklemeyi seçerseniz, klasör yolunun başlangıcını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="70486-123">If you choose to install to a different folder, adjust the start of the folder path.</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="70486-124">**dotnet çalıştırılabilir**</span><span class="sxs-lookup"><span data-stu-id="70486-124">**dotnet executable**</span></span>\
<span data-ttu-id="70486-125">_C:\\program\\dosyaları\\dotnet dotnet.exe_</span><span class="sxs-lookup"><span data-stu-id="70486-125">_C:\\program files\\dotnet\\dotnet.exe_</span></span>

- <span data-ttu-id="70486-126">**.NET SDK**</span><span class="sxs-lookup"><span data-stu-id="70486-126">**.NET SDK**</span></span>\
<span data-ttu-id="70486-127">_C:\\program\\dosyaları\\dotnet sdk\\{sürüm}\\_</span><span class="sxs-lookup"><span data-stu-id="70486-127">_C:\\program files\\dotnet\\sdk\\{version}\\_</span></span>

- <span data-ttu-id="70486-128">**.NET Çalışma Süresi**</span><span class="sxs-lookup"><span data-stu-id="70486-128">**.NET Runtime**</span></span>\
<span data-ttu-id="70486-129">_C:\\program\\dosyaları\\dotnet paylaşılan\\{runtime-type}\\{version}\\_</span><span class="sxs-lookup"><span data-stu-id="70486-129">_C:\\program files\\dotnet\\shared\\{runtime-type}\\{version}\\_</span></span>

::: zone-end

::: zone pivot="os-linux"

- <span data-ttu-id="70486-130">**dotnet çalıştırılabilir**</span><span class="sxs-lookup"><span data-stu-id="70486-130">**dotnet executable**</span></span>\
<span data-ttu-id="70486-131">_/home/user/share/dotnet/dotnet_</span><span class="sxs-lookup"><span data-stu-id="70486-131">_/home/user/share/dotnet/dotnet_</span></span>

- <span data-ttu-id="70486-132">**.NET SDK**</span><span class="sxs-lookup"><span data-stu-id="70486-132">**.NET SDK**</span></span>\
<span data-ttu-id="70486-133">_/home/user/share/dotnet/sdk/{version}/_</span><span class="sxs-lookup"><span data-stu-id="70486-133">_/home/user/share/dotnet/sdk/{version}/_</span></span>

- <span data-ttu-id="70486-134">**.NET Çalışma Süresi**</span><span class="sxs-lookup"><span data-stu-id="70486-134">**.NET Runtime**</span></span>\
<span data-ttu-id="70486-135">_/home/user/share/dotnet/shared/{runtime-type}/{version}/_</span><span class="sxs-lookup"><span data-stu-id="70486-135">_/home/user/share/dotnet/shared/{runtime-type}/{version}/_</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="70486-136">**dotnet çalıştırılabilir**</span><span class="sxs-lookup"><span data-stu-id="70486-136">**dotnet executable**</span></span>\
<span data-ttu-id="70486-137">_/usr/local/share/dotnet/dotnet_</span><span class="sxs-lookup"><span data-stu-id="70486-137">_/usr/local/share/dotnet/dotnet_</span></span>

- <span data-ttu-id="70486-138">**.NET SDK**</span><span class="sxs-lookup"><span data-stu-id="70486-138">**.NET SDK**</span></span>\
<span data-ttu-id="70486-139">_/usr/local/share/dotnet/sdk/{version}/_</span><span class="sxs-lookup"><span data-stu-id="70486-139">_/usr/local/share/dotnet/sdk/{version}/_</span></span>

- <span data-ttu-id="70486-140">**.NET Çalışma Süresi**</span><span class="sxs-lookup"><span data-stu-id="70486-140">**.NET Runtime**</span></span>\
<span data-ttu-id="70486-141">_/usr/local/share/dotnet/shared/{runtime-type}/{version}/_</span><span class="sxs-lookup"><span data-stu-id="70486-141">_/usr/local/share/dotnet/shared/{runtime-type}/{version}/_</span></span>

::: zone-end

## <a name="more-information"></a><span data-ttu-id="70486-142">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="70486-142">More information</span></span>

<span data-ttu-id="70486-143">Hem SDK sürümlerini hem de çalışma zamanı `dotnet --info`sürümlerini komutla görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70486-143">You can see both the SDK versions and runtime versions with the command `dotnet --info`.</span></span> <span data-ttu-id="70486-144">Ayrıca, işletim sistemi sürümü ve çalışma zamanı tanımlayıcısı (RID) gibi çevreyle ilgili diğer bilgileri de alırsınız.</span><span class="sxs-lookup"><span data-stu-id="70486-144">You'll also get other environmental related information, such as the operating system version and runtime identifier (RID).</span></span>

## <a name="next-steps"></a><span data-ttu-id="70486-145">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="70486-145">Next steps</span></span>

- <span data-ttu-id="70486-146">[.NET Çekirdek Çalışma Süresini yükleyin.](runtime.md)</span><span class="sxs-lookup"><span data-stu-id="70486-146">[Install the .NET Core Runtime](runtime.md).</span></span>
- <span data-ttu-id="70486-147">[.NET Çekirdek SDK'yı yükleyin.](sdk.md)</span><span class="sxs-lookup"><span data-stu-id="70486-147">[Install the .NET Core SDK](sdk.md).</span></span>
