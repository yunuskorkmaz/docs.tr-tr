---
title: Windows, Linux ve macOS-.NET Core 'a .NET Core çalışma zamanı 'nı yükler
description: Windows, Linux ve macOS 'ta .NET Core 'u yüklemeyi öğrenin. .NET Core uygulamalarını çalıştırmak için gereken bağımlılıkları bulur.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: d39e5912cf2ae73631c2f1192adb516e84dfed32
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552194"
---
# <a name="install-the-net-core-runtime"></a>.NET Core çalışma zamanını yükler

Bu makalede, .NET Core çalışma zamanının nasıl indirileceği ve kurulacağı hakkında bilgi edineceksiniz. .NET Core çalışma zamanı .NET Core ile oluşturulan uygulamaları çalıştırmak için kullanılır.

.NET Core ' u aşağıdaki bağlantılardan biriyle doğrudan indirebilir ve yükleyebilirsiniz:

- [.NET Core 3,1 Preview 3 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [.NET Core 3,0 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [.NET Core 2,2 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [.NET Core 2,1 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/2.1)

::: zone pivot="os-windows,os-macos"

## <a name="install-with-an-installer"></a>Bir yükleyici ile yükleme

Hem Windows hem de macOS .NET Core 3,0 çalışma zamanını yüklemek için kullanılabilecek tek başına yükleyiciler vardır.

- Windows [x64 cpu](https://dotnet.microsoft.com/download/thank-you/dotnet-runtime-3.0.0-windows-x64-installer) | [x32 CPU](https://dotnet.microsoft.com/download/thank-you/dotnet-runtime-3.0.0-windows-x86-installer)
- macOS [x64 CPU 'ları](https://dotnet.microsoft.com/download/thank-you/dotnet-runtime-3.0.0-macos-x64-installer)

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a>Paket Yöneticisi ile yüklemesi

.NET Core çalışma zamanını birçok ortak Linux Paket Yöneticisi ile yükleyebilirsiniz. Daha fazla bilgi için bkz. [Linux Paket Yöneticisi-.NET Core 'U yükler](linux-package-manager-rhel7.md).

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a>PowerShell otomasyonu ile Install

[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , çalışma zamanının Otomasyon ve yönetici olmayan yüklemeleri için kullanılır. Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.

Komut dosyası, .NET Core 2,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir. Geçerli .NET Core sürümünü (3,0) yüklemek için betiği aşağıdaki anahtarla çalıştırın:

```powershell
dotnet-install.ps1 -Channel 3.0
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a>Bash otomasyonu ile Install

[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , çalışma zamanının Otomasyon ve yönetici olmayan yüklemeleri için kullanılır. Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.

Komut dosyası, .NET Core 2,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir. Geçerli .NET Core sürümünü (3,0) yüklemek için betiği aşağıdaki anahtarla çalıştırın:

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="docker"></a>Docker

Kapsayıcılar, uygulamanızı ana bilgisayar sisteminin geri kalanından yalıtmak için basit bir yol sağlar. Aynı makinedeki kapsayıcılar yalnızca çekirdeği paylaşır ve uygulamanıza verilen kaynakları kullanır.

.NET Core, Docker kapsayıcısında çalıştırılabilir. Resmi .NET Core Docker görüntüleri Microsoft Container Registry (MCR) ' de yayımlanır ve [Microsoft .NET Core Docker Hub deposunda](https://hub.docker.com/_/microsoft-dotnet-core/)bulunabilir. Her depo, .NET (SDK veya çalışma zamanı) ve kullanabileceğiniz farklı .NET birleşimlerinin görüntülerini içerir.

Microsoft, belirli senaryolar için uyarlanmış görüntüler sağlar. Örneğin, [ASP.NET Core deposu](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) üretimde ASP.NET Core uygulamaları çalıştırmak için oluşturulmuş görüntüler sağlar.

Bir Docker kapsayıcısında .NET Core kullanma hakkında daha fazla bilgi için bkz. [.net ve Docker](../docker/introduction.md) ve [örneklere](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)giriş.

## <a name="next-steps"></a>Sonraki adımlar

- [.NET Core 'un zaten yüklü olup olmadığını denetleme](how-to-detect-installed-versions.md).
