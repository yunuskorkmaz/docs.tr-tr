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
# <a name="how-to-check-that-net-is-already-installed"></a>.NET 'in zaten yüklü olduğunu denetleme

Bu makalede, hangi .NET çalışma zamanının ve SDK sürümlerinin bilgisayarınızda yüklü olduğunu nasıl denetleriz öğretilir. Visual Studio veya Mac için Visual Studio gibi tümleşik bir geliştirme ortamınız varsa .NET zaten yüklü olabilir.

SDK yükleme, ilgili çalışma zamanını yüklenir.

Bu makaledeki herhangi bir komut başarısız olursa, çalışma zamanı veya SDK yüklü değildir. Daha fazla bilgi için bkz. [Windows](windows.md), [MacOS](macos.md)veya [Linux](linux.md)için Install makaleleri.

## <a name="check-sdk-versions"></a>SDK sürümlerini denetle

Şu anda bir terminalle hangi .NET SDK sürümünün yüklü olduğunu görebilirsiniz. Bir Terminal açın ve aşağıdaki komutu çalıştırın.

```dotnetcli
dotnet --list-sdks
```

Aşağıdakine benzer bir çıktı alırsınız.

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

## <a name="check-runtime-versions"></a>Çalışma zamanı sürümlerini denetle

Aşağıdaki komutla .NET çalışma zamanının hangi sürümlerinin yüklü olduğunu görebilirsiniz.

```dotnetcli
dotnet --list-runtimes
```

Aşağıdakine benzer bir çıktı alırsınız.

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

## <a name="check-for-install-folders"></a>Klasör yüklemeyi denetle

.NET yüklü olsa da, `PATH` işletim sisteminiz veya Kullanıcı profiliniz için değişkene eklenmemiş olabilir. Önceki bölümlerden komutlarının çalıştırılması çalışmayabilir. Alternatif olarak, .NET yüklemesi klasörlerinin mevcut olup olmadığını kontrol edebilirsiniz.

Bir yükleyiciden veya betikten .NET yüklediğinizde, bu bir standart klasöre yüklenir. .NET yüklemek için kullandığınız yükleyicinin veya betiğin çoğu zaman, farklı bir klasöre yükleme seçeneği sunar. Farklı bir klasöre yüklemeyi tercih ederseniz klasör yolunun başlangıcını ayarlayın.

::: zone pivot="os-windows"

- **DotNet çalıştırılabilir**\
_C: \\ Program Files \\ DotNet \\dotnet.exe_

- **.NET SDK**\
_C: \\ Program Files \\ DotNet \\ SDK \\ {Version}\\_

- **.NET çalışma zamanı**\
_C: \\ Program Files \\ DotNet \\ paylaşılan \\ {Runtime-Type} \\ {Version}\\_

::: zone-end

::: zone pivot="os-linux"

- **DotNet çalıştırılabilir**\
_/Home/user/Share/DotNet/DotNet_

- **.NET SDK**\
_/Home/user/Share/DotNet/SDK/{Version}/_

- **.NET çalışma zamanı**\
_/Home/user/Share/DotNet/Shared/{Runtime-Type}/{Version}/_

::: zone-end

::: zone pivot="os-macos"

- **DotNet çalıştırılabilir**\
_/usr/local/share/DotNet/DotNet_

- **.NET SDK**\
_/usr/local/share/DotNet/SDK/{Version}/_

- **.NET çalışma zamanı**\
_/usr/local/share/DotNet/Shared/{Runtime-Type}/{Version}/_

::: zone-end

## <a name="more-information"></a>Daha fazla bilgi

Komutuyla hem SDK sürümlerini hem de çalışma zamanı sürümlerini görebilirsiniz `dotnet --info` . Ayrıca, işletim sistemi sürümü ve çalışma zamanı tanımlayıcısı (RID) gibi diğer çevresel ilgili bilgileri de alacaksınız.

## <a name="next-steps"></a>Sonraki adımlar

- [Windows için .NET çalışma zamanını ve SDK 'Yı yükler](windows.md).
- [MacOS için .NET çalışma zamanını ve SDK 'Yı yükler](linux.md).
- [Linux için .NET çalışma zamanını ve SDK 'Sını yükler](macos.md).
