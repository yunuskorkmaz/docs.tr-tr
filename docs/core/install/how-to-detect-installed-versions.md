---
title: Windows, Linux ve macOS-.NET Core 'da yüklü .NET Core sürümlerini denetleyin
description: Bilgisayarınızda hangi .NET Core sürümlerinin yüklü olduğunu nasıl listeleyeceğinizi öğrenin. Buna .NET Core çalışma zamanı ve SDK dahildir.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 3efc54cea7e10bc21a472a7fa9d4026e305be79a
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503840"
---
# <a name="how-to-check-that-net-core-is-already-installed"></a><span data-ttu-id="41d86-104">.NET Core 'un zaten yüklü olduğunu denetleme</span><span class="sxs-lookup"><span data-stu-id="41d86-104">How to check that .NET Core is already installed</span></span>

<span data-ttu-id="41d86-105">Bu makalede, hangi .NET Core çalışma zamanı ve SDK sürümlerinin bilgisayarınızda yüklü olduğunu nasıl denetleriz öğretilir.</span><span class="sxs-lookup"><span data-stu-id="41d86-105">This article teaches you how to check which versions of the .NET Core runtime and SDK are installed on your computer.</span></span> <span data-ttu-id="41d86-106">Visual Studio veya Mac için Visual Studio gibi tümleşik bir geliştirme ortamınız varsa .NET Core zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="41d86-106">.NET core may have already been installed if you have an integrated development environment, such as Visual Studio or Visual Studio for Mac.</span></span>

<span data-ttu-id="41d86-107">SDK yükleme, ilgili çalışma zamanını yüklenir.</span><span class="sxs-lookup"><span data-stu-id="41d86-107">Installing an SDK installs the corresponding runtime.</span></span>

<span data-ttu-id="41d86-108">Bu makaledeki herhangi bir komut başarısız olursa, çalışma zamanı veya SDK yüklü değildir.</span><span class="sxs-lookup"><span data-stu-id="41d86-108">If any command in this article fails, you don't have the runtime or SDK installed.</span></span> <span data-ttu-id="41d86-109">Daha fazla bilgi için bkz. [.NET Core 'U indirme ve yükleme](index.md).</span><span class="sxs-lookup"><span data-stu-id="41d86-109">For more information, see [Download and install .NET Core](index.md).</span></span>

## <a name="check-sdk-versions"></a><span data-ttu-id="41d86-110">SDK sürümlerini denetle</span><span class="sxs-lookup"><span data-stu-id="41d86-110">Check SDK versions</span></span>

<span data-ttu-id="41d86-111">Hangi .NET Core SDK sürümlerinin bir terminalle yüklü olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41d86-111">You can see which versions of the .NET Core SDK are currently installed with a terminal.</span></span> <span data-ttu-id="41d86-112">Bir Terminal açın ve aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="41d86-112">Open a terminal and run the following command.</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="41d86-113">Aşağıdakine benzer bir çıktı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="41d86-113">You get output similar to the following.</span></span>

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

## <a name="check-runtime-versions"></a><span data-ttu-id="41d86-114">Çalışma zamanı sürümlerini denetle</span><span class="sxs-lookup"><span data-stu-id="41d86-114">Check runtime versions</span></span>

<span data-ttu-id="41d86-115">Aşağıdaki komutla .NET Core çalışma zamanının hangi sürümlerinin yüklü olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41d86-115">You can see which versions of the .NET Core runtime are currently installed with the following command.</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="41d86-116">Aşağıdakine benzer bir çıktı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="41d86-116">You get output similar to the following.</span></span>

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

## <a name="more-information"></a><span data-ttu-id="41d86-117">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="41d86-117">More information</span></span>

<span data-ttu-id="41d86-118">Komut `dotnet --info`hem SDK sürümlerini hem de çalışma zamanı sürümlerini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41d86-118">You can see both the SDK versions and runtime versions with the command `dotnet --info`.</span></span> <span data-ttu-id="41d86-119">Ayrıca, işletim sistemi sürümü ve çalışma zamanı tanımlayıcısı (RID) gibi diğer çevresel ilgili bilgileri de alacaksınız.</span><span class="sxs-lookup"><span data-stu-id="41d86-119">You'll also get other environmental related information, such as the operating system version and runtime identifier (RID).</span></span>

## <a name="next-steps"></a><span data-ttu-id="41d86-120">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="41d86-120">Next steps</span></span>

- <span data-ttu-id="41d86-121">[.NET Core çalışma zamanını yükler](runtime.md).</span><span class="sxs-lookup"><span data-stu-id="41d86-121">[Install the .NET Core Runtime](runtime.md).</span></span>
- <span data-ttu-id="41d86-122">[.NET Core SDK 'ı yükler](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="41d86-122">[Install the .NET Core SDK](sdk.md).</span></span>
