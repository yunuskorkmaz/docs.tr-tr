---
title: Windows, Linux ve macOS-.NET üzerinde yüklü .NET sürümlerini denetleyin
description: Bilgisayarınızda hangi .NET sürümlerinin yüklü olduğunu nasıl listeleyeceğinizi öğrenin. Buna .NET çalışma zamanı ve SDK dahildir.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: d924e5bc58052cd760f367e906666d68ab79b764
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507224"
---
# <a name="how-to-check-that-net-is-already-installed"></a><span data-ttu-id="43df1-104">.NET 'in zaten yüklü olduğunu denetleme</span><span class="sxs-lookup"><span data-stu-id="43df1-104">How to check that .NET is already installed</span></span>

<span data-ttu-id="43df1-105">Bu makalede, hangi .NET çalışma zamanının ve SDK sürümlerinin bilgisayarınızda yüklü olduğunu nasıl denetleriz öğretilir.</span><span class="sxs-lookup"><span data-stu-id="43df1-105">This article teaches you how to check which versions of the .NET runtime and SDK are installed on your computer.</span></span> <span data-ttu-id="43df1-106">Visual Studio veya Mac için Visual Studio gibi tümleşik bir geliştirme ortamınız varsa .NET zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="43df1-106">.NET may have already been installed if you have an integrated development environment, such as Visual Studio or Visual Studio for Mac.</span></span>

<span data-ttu-id="43df1-107">SDK yükleme, ilgili çalışma zamanını yüklenir.</span><span class="sxs-lookup"><span data-stu-id="43df1-107">Installing an SDK installs the corresponding runtime.</span></span>

<span data-ttu-id="43df1-108">Bu makaledeki herhangi bir komut başarısız olursa, çalışma zamanı veya SDK yüklü değildir.</span><span class="sxs-lookup"><span data-stu-id="43df1-108">If any command in this article fails, you don't have the runtime or SDK installed.</span></span> <span data-ttu-id="43df1-109">Daha fazla bilgi için bkz. [Windows](windows.md), [MacOS](macos.md)veya [Linux](linux.md)için Install makaleleri.</span><span class="sxs-lookup"><span data-stu-id="43df1-109">For more information, see the install articles for [Windows](windows.md), [macOS](macos.md), or [Linux](linux.md).</span></span>

## <a name="check-sdk-versions"></a><span data-ttu-id="43df1-110">SDK sürümlerini denetle</span><span class="sxs-lookup"><span data-stu-id="43df1-110">Check SDK versions</span></span>

<span data-ttu-id="43df1-111">Şu anda bir terminalle hangi .NET SDK sürümünün yüklü olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43df1-111">You can see which versions of the .NET SDK are currently installed with a terminal.</span></span> <span data-ttu-id="43df1-112">Bir Terminal açın ve aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="43df1-112">Open a terminal and run the following command.</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="43df1-113">Aşağıdakine benzer bir çıktı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="43df1-113">You get output similar to the following.</span></span>

::: zone pivot="os-windows"

```console
2.1.500 [C:\program files\dotnet\sdk]
2.1.502 [C:\program files\dotnet\sdk]
2.1.504 [C:\program files\dotnet\sdk]
2.1.600 [C:\program files\dotnet\sdk]
2.1.602 [C:\program files\dotnet\sdk]
3.1.100 [C:\program files\dotnet\sdk]
5.0.100 [C:\program files\dotnet\sdk]
```

::: zone-end

::: zone pivot="os-linux"

```bash
2.1.500 [/home/user/dotnet/sdk]
2.1.502 [/home/user/dotnet/sdk]
2.1.504 [/home/user/dotnet/sdk]
2.1.600 [/home/user/dotnet/sdk]
2.1.602 [/home/user/dotnet/sdk]
3.1.100 [/home/user/dotnet/sdk]
5.0.100 [/home/user/dotnet/sdk]
```

::: zone-end

::: zone pivot="os-macos"

```bash
2.1.500 [/usr/local/share/dotnet/sdk]
2.1.502 [/usr/local/share/dotnet/sdk]
2.1.504 [/usr/local/share/dotnet/sdk]
2.1.600 [/usr/local/share/dotnet/sdk]
2.1.602 [/usr/local/share/dotnet/sdk]
3.1.100 [/usr/local/share/dotnet/sdk]
5.0.100 [/usr/local/share/dotnet/sdk]
```

::: zone-end

## <a name="check-runtime-versions"></a><span data-ttu-id="43df1-114">Çalışma zamanı sürümlerini denetle</span><span class="sxs-lookup"><span data-stu-id="43df1-114">Check runtime versions</span></span>

<span data-ttu-id="43df1-115">Aşağıdaki komutla .NET çalışma zamanının hangi sürümlerinin yüklü olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43df1-115">You can see which versions of the .NET runtime are currently installed with the following command.</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="43df1-116">Aşağıdakine benzer bir çıktı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="43df1-116">You get output similar to the following.</span></span>

::: zone pivot="os-windows"

```console
Microsoft.AspNetCore.All 2.1.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 5.0.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 5.0.0 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.WindowsDesktop.App 3.0.0 [c:\program files\dotnet\shared\Microsoft.WindowsDesktop.App]
Microsoft.WindowsDesktop.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.WindowsDesktop.App]
Microsoft.WindowsDesktop.App 5.0.0 [c:\program files\dotnet\shared\Microsoft.WindowsDesktop.App]
```

::: zone-end

::: zone pivot="os-linux"

```bash
Microsoft.AspNetCore.All 2.1.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 5.0.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 5.0.0 [/home/user/dotnet/shared/Microsoft.NETCore.App]
```

::: zone-end

::: zone pivot="os-macos"

```bash
Microsoft.AspNetCore.All 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 5.0.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 5.0.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
```

::: zone-end

## <a name="check-for-install-folders"></a><span data-ttu-id="43df1-117">Klasör yüklemeyi denetle</span><span class="sxs-lookup"><span data-stu-id="43df1-117">Check for install folders</span></span>

<span data-ttu-id="43df1-118">.NET yüklü olsa da, `PATH` işletim sisteminiz veya Kullanıcı profiliniz için değişkene eklenmemiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="43df1-118">It's possible that .NET is installed but not added to the `PATH` variable for your operating system or user profile.</span></span> <span data-ttu-id="43df1-119">Önceki bölümlerden komutlarının çalıştırılması çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="43df1-119">Running the commands from the previous sections may not work.</span></span> <span data-ttu-id="43df1-120">Alternatif olarak, .NET yüklemesi klasörlerinin mevcut olup olmadığını kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43df1-120">As an alternative, you can check that the .NET install folders exist.</span></span>

<span data-ttu-id="43df1-121">Bir yükleyiciden veya betikten .NET yüklediğinizde, bu bir standart klasöre yüklenir.</span><span class="sxs-lookup"><span data-stu-id="43df1-121">When you install .NET from an installer or script, it's installed to a standard folder.</span></span> <span data-ttu-id="43df1-122">.NET yüklemek için kullandığınız yükleyicinin veya betiğin çoğu zaman, farklı bir klasöre yükleme seçeneği sunar.</span><span class="sxs-lookup"><span data-stu-id="43df1-122">Much of the time the installer or script you're using to install .NET gives you an option to install to a different folder.</span></span> <span data-ttu-id="43df1-123">Farklı bir klasöre yüklemeyi tercih ederseniz klasör yolunun başlangıcını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="43df1-123">If you choose to install to a different folder, adjust the start of the folder path.</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="43df1-124">**DotNet çalıştırılabilir**</span><span class="sxs-lookup"><span data-stu-id="43df1-124">**dotnet executable**</span></span>\
<span data-ttu-id="43df1-125">_C: \\ Program Files \\ DotNet \\dotnet.exe_</span><span class="sxs-lookup"><span data-stu-id="43df1-125">_C:\\program files\\dotnet\\dotnet.exe_</span></span>

- <span data-ttu-id="43df1-126">**.NET SDK**</span><span class="sxs-lookup"><span data-stu-id="43df1-126">**.NET SDK**</span></span>\
<span data-ttu-id="43df1-127">_C: \\ Program Files \\ DotNet \\ SDK \\ {Version}\\_</span><span class="sxs-lookup"><span data-stu-id="43df1-127">_C:\\program files\\dotnet\\sdk\\{version}\\_</span></span>

- <span data-ttu-id="43df1-128">**.NET çalışma zamanı**</span><span class="sxs-lookup"><span data-stu-id="43df1-128">**.NET Runtime**</span></span>\
<span data-ttu-id="43df1-129">_C: \\ Program Files \\ DotNet \\ paylaşılan \\ {Runtime-Type} \\ {Version}\\_</span><span class="sxs-lookup"><span data-stu-id="43df1-129">_C:\\program files\\dotnet\\shared\\{runtime-type}\\{version}\\_</span></span>

::: zone-end

::: zone pivot="os-linux"

- <span data-ttu-id="43df1-130">**DotNet çalıştırılabilir**</span><span class="sxs-lookup"><span data-stu-id="43df1-130">**dotnet executable**</span></span>\
<span data-ttu-id="43df1-131">_/Home/user/Share/DotNet/DotNet_</span><span class="sxs-lookup"><span data-stu-id="43df1-131">_/home/user/share/dotnet/dotnet_</span></span>

- <span data-ttu-id="43df1-132">**.NET SDK**</span><span class="sxs-lookup"><span data-stu-id="43df1-132">**.NET SDK**</span></span>\
<span data-ttu-id="43df1-133">_/Home/user/Share/DotNet/SDK/{Version}/_</span><span class="sxs-lookup"><span data-stu-id="43df1-133">_/home/user/share/dotnet/sdk/{version}/_</span></span>

- <span data-ttu-id="43df1-134">**.NET çalışma zamanı**</span><span class="sxs-lookup"><span data-stu-id="43df1-134">**.NET Runtime**</span></span>\
<span data-ttu-id="43df1-135">_/Home/user/Share/DotNet/Shared/{Runtime-Type}/{Version}/_</span><span class="sxs-lookup"><span data-stu-id="43df1-135">_/home/user/share/dotnet/shared/{runtime-type}/{version}/_</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="43df1-136">**DotNet çalıştırılabilir**</span><span class="sxs-lookup"><span data-stu-id="43df1-136">**dotnet executable**</span></span>\
<span data-ttu-id="43df1-137">_/usr/local/share/DotNet/DotNet_</span><span class="sxs-lookup"><span data-stu-id="43df1-137">_/usr/local/share/dotnet/dotnet_</span></span>

- <span data-ttu-id="43df1-138">**.NET SDK**</span><span class="sxs-lookup"><span data-stu-id="43df1-138">**.NET SDK**</span></span>\
<span data-ttu-id="43df1-139">_/usr/local/share/DotNet/SDK/{Version}/_</span><span class="sxs-lookup"><span data-stu-id="43df1-139">_/usr/local/share/dotnet/sdk/{version}/_</span></span>

- <span data-ttu-id="43df1-140">**.NET çalışma zamanı**</span><span class="sxs-lookup"><span data-stu-id="43df1-140">**.NET Runtime**</span></span>\
<span data-ttu-id="43df1-141">_/usr/local/share/DotNet/Shared/{Runtime-Type}/{Version}/_</span><span class="sxs-lookup"><span data-stu-id="43df1-141">_/usr/local/share/dotnet/shared/{runtime-type}/{version}/_</span></span>

::: zone-end

## <a name="more-information"></a><span data-ttu-id="43df1-142">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="43df1-142">More information</span></span>

<span data-ttu-id="43df1-143">Komutuyla hem SDK sürümlerini hem de çalışma zamanı sürümlerini görebilirsiniz `dotnet --info` .</span><span class="sxs-lookup"><span data-stu-id="43df1-143">You can see both the SDK versions and runtime versions with the command `dotnet --info`.</span></span> <span data-ttu-id="43df1-144">Ayrıca, işletim sistemi sürümü ve çalışma zamanı tanımlayıcısı (RID) gibi diğer çevresel ilgili bilgileri de alacaksınız.</span><span class="sxs-lookup"><span data-stu-id="43df1-144">You'll also get other environmental related information, such as the operating system version and runtime identifier (RID).</span></span>

## <a name="next-steps"></a><span data-ttu-id="43df1-145">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="43df1-145">Next steps</span></span>

- <span data-ttu-id="43df1-146">[Windows için .NET çalışma zamanını ve SDK 'Yı yükler](windows.md).</span><span class="sxs-lookup"><span data-stu-id="43df1-146">[Install the .NET Runtime and SDK for Windows](windows.md).</span></span>
- <span data-ttu-id="43df1-147">[MacOS için .NET çalışma zamanını ve SDK 'Yı yükler](linux.md).</span><span class="sxs-lookup"><span data-stu-id="43df1-147">[Install the .NET Runtime and SDK for MacOS](linux.md).</span></span>
- <span data-ttu-id="43df1-148">[Linux için .NET çalışma zamanını ve SDK 'Sını yükler](macos.md).</span><span class="sxs-lookup"><span data-stu-id="43df1-148">[Install the .NET Runtime and SDK for Linux](macos.md).</span></span>
