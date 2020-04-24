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
# <a name="how-to-check-that-net-core-is-already-installed"></a>.NET Core'un zaten yüklü olduğunu kontrol etme

Bu makalede, .NET Core çalışma zamanı ve SDK'nın hangi sürümlerinin bilgisayarınıza yüklendiği kontrol edilir. .NET core, Mac için Visual Studio veya Visual Studio gibi tümleşik bir geliştirme ortamınız varsa zaten yüklenmiş olabilir.

Bir SDK yükleme ilgili çalışma süresini yükler.

Bu makaledeki herhangi bir komut başarısız olursa, çalışma saatini veya SDK yüklü değil. Daha fazla bilgi için [.NET Core'u İndirve yükleyin.](index.md)

## <a name="check-sdk-versions"></a>SDK sürümlerini kontrol edin

.NET Core SDK'nın hangi sürümlerinin şu anda bir terminalle yüklü olduğunu görebilirsiniz. Bir terminal açın ve aşağıdaki komutu çalıştırın.

```dotnetcli
dotnet --list-sdks
```

Aşağıdakine benzer çıktı alırsınız.

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

## <a name="check-runtime-versions"></a>Çalışma zamanı sürümlerini denetleyin

.NET Core çalışma zamanının hangi sürümlerinin şu anda aşağıdaki komutla yüklenmiş olduğunu görebilirsiniz.

```dotnetcli
dotnet --list-runtimes
```

Aşağıdakine benzer çıktı alırsınız.

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

## <a name="check-for-install-folders"></a>Klasörleri yükle denetimini denetleme

.NET Core'un yüklü olması ancak işletim sisteminiz `PATH` veya kullanıcı profiliniz için değişkene eklenmemiş olması mümkündür. Önceki bölümlerdeki komutları çalıştırmak çalışmayabilir. Alternatif olarak, .NET Core yükleme klasörlerinin var olup olmadığını denetleyebilirsiniz.

.NET Core'u yükleyiciden veya komut dosyasından yüklediğinizde, standart bir klasöre yüklenir. .NET Core'u yüklemek için kullandığınız yükleyici veya komut dosyası çoğu zaman farklı bir klasöre yükleme seçeneği sunar. Farklı bir klasöre yüklemeyi seçerseniz, klasör yolunun başlangıcını ayarlayın.

::: zone pivot="os-windows"

- **dotnet çalıştırılabilir**\
_C:\\program\\dosyaları\\dotnet dotnet.exe_

- **.NET SDK**\
_C:\\program\\dosyaları\\dotnet sdk\\{sürüm}\\_

- **.NET Çalışma Süresi**\
_C:\\program\\dosyaları\\dotnet paylaşılan\\{runtime-type}\\{version}\\_

::: zone-end

::: zone pivot="os-linux"

- **dotnet çalıştırılabilir**\
_/home/user/share/dotnet/dotnet_

- **.NET SDK**\
_/home/user/share/dotnet/sdk/{version}/_

- **.NET Çalışma Süresi**\
_/home/user/share/dotnet/shared/{runtime-type}/{version}/_

::: zone-end

::: zone pivot="os-macos"

- **dotnet çalıştırılabilir**\
_/usr/local/share/dotnet/dotnet_

- **.NET SDK**\
_/usr/local/share/dotnet/sdk/{version}/_

- **.NET Çalışma Süresi**\
_/usr/local/share/dotnet/shared/{runtime-type}/{version}/_

::: zone-end

## <a name="more-information"></a>Daha fazla bilgi

Hem SDK sürümlerini hem de çalışma zamanı `dotnet --info`sürümlerini komutla görebilirsiniz. Ayrıca, işletim sistemi sürümü ve çalışma zamanı tanımlayıcısı (RID) gibi çevreyle ilgili diğer bilgileri de alırsınız.

## <a name="next-steps"></a>Sonraki adımlar

- [.NET Çekirdek Çalışma Süresini yükleyin.](runtime.md)
- [.NET Çekirdek SDK'yı yükleyin.](sdk.md)
