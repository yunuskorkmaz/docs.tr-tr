---
title: Windows, Linux ve macOS-.NET Core 'a .NET Core çalışma zamanı 'nı yükler
description: Windows, Linux ve macOS 'ta .NET Core 'u yüklemeyi öğrenin. .NET Core uygulamalarını çalıştırmak için gereken bağımlılıkları bulur.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 8f4a895ad66dea3063a32f785e4c521196266978
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74835730"
---
# <a name="install-the-net-core-runtime"></a>.NET Core çalışma zamanını yükler

Bu makalede, .NET Core çalışma zamanının nasıl indirileceği ve kurulacağı hakkında bilgi edineceksiniz. .NET Core çalışma zamanı .NET Core ile oluşturulan uygulamaları çalıştırmak için kullanılır.

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a>Bir yükleyici ile yükleme

Windows, .NET Core 3,1 çalışma zamanını yüklemek için kullanılabilecek tek başına yükleyicilere sahiptir:

- [x64 (64-bit) CPU 'Lar](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [x86 (32 bit) CPU 'Lar](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a>Bir yükleyici ile yükleme

macOS, .NET Core 3,1 çalışma zamanını yüklemek için kullanılabilecek tek başına yükleyicilere sahiptir:

- [x64 (64-bit) CPU 'Lar](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a>Paket Yöneticisi ile yüklemesi

.NET Core çalışma zamanını birçok ortak Linux Paket Yöneticisi ile yükleyebilirsiniz. Daha fazla bilgi için bkz. [Linux Paket Yöneticisi-.NET Core 'U yükler](linux-package-manager-rhel7.md).

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a>PowerShell otomasyonu ile Install

[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , çalışma zamanının Otomasyon ve yönetici olmayan yüklemeleri için kullanılır. Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.

Komut dosyası, .NET Core 3,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir. `Channel` anahtarını belirterek belirli bir yayını seçebilirsiniz. Çalışma zamanı yüklemek için `Runtime` anahtarını ekleyin. Aksi halde, komut dosyası [SDK 'yı](sdk.md)yüklüyor.

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> Yukarıdaki komut, ASP.NET Core çalışma zamanını maksimum uyumluluk için yüklerse. ASP.NET Core çalışma zamanı, standart .NET Core çalışma zamanını da içerir.

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a>Bash otomasyonu ile Install

[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , çalışma zamanının Otomasyon ve yönetici olmayan yüklemeleri için kullanılır. Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.

Komut dosyası, .NET Core 3,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir. `current` anahtarını belirterek belirli bir yayını seçebilirsiniz. Çalışma zamanı yüklemek için `runtime` anahtarını ekleyin. Aksi halde, komut dosyası [SDK 'yı](sdk.md)yüklüyor.

```bash
./dotnet-install.sh --current 3.1 --runtime aspnetcore
```

> [!NOTE]
> Yukarıdaki komut, ASP.NET Core çalışma zamanını maksimum uyumluluk için yüklerse. ASP.NET Core çalışma zamanı, standart .NET Core çalışma zamanını da içerir.

::: zone-end

## <a name="all-net-core-downloads"></a>Tüm .NET Core İndirmeleri

.NET Core ' u aşağıdaki bağlantılardan biriyle doğrudan indirebilir ve yükleyebilirsiniz:

- [.NET Core 3,1 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [.NET Core 3,0 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [.NET Core 2,2 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [.NET Core 2,1 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a>Docker

Kapsayıcılar, uygulamanızı ana bilgisayar sisteminin geri kalanından yalıtmak için basit bir yol sağlar. Aynı makinedeki kapsayıcılar yalnızca çekirdeği paylaşır ve uygulamanıza verilen kaynakları kullanır.

.NET Core, Docker kapsayıcısında çalıştırılabilir. Resmi .NET Core Docker görüntüleri Microsoft Container Registry (MCR) ' de yayımlanır ve [Microsoft .NET Core Docker Hub deposunda](https://hub.docker.com/_/microsoft-dotnet-core/)bulunabilir. Her depo, .NET (SDK veya çalışma zamanı) ve kullanabileceğiniz farklı .NET birleşimlerinin görüntülerini içerir.

Microsoft, belirli senaryolar için uyarlanmış görüntüler sağlar. Örneğin, [ASP.NET Core deposu](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) üretimde ASP.NET Core uygulamaları çalıştırmak için oluşturulmuş görüntüler sağlar.

Bir Docker kapsayıcısında .NET Core kullanma hakkında daha fazla bilgi için bkz. [.net ve Docker](../docker/introduction.md) ve [örneklere](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)giriş.

## <a name="next-steps"></a>Sonraki adımlar

- [.NET Core 'un zaten yüklü olup olmadığını denetleme](how-to-detect-installed-versions.md).
