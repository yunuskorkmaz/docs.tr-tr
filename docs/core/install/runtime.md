---
title: Windows, Linux ve macOS'a .NET Core çalışma süresini yükleme - .NET Core
description: .NET Core'u Windows, Linux ve macOS'a nasıl yükleyin öğrenin. .NET Core uygulamalarını çalıştırmak için gereken bağımlılıkları keşfedin.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: ca55b8fab4aa9ca9f7e308cce57181e2c7e89f4b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399016"
---
# <a name="install-the-net-core-runtime"></a>.NET Çekirdek Çalışma Süresini Yükleyin

Bu makalede, .NET Core çalışma saatini nasıl indireceğinizi ve yükleyeceğinizi öğreneceksiniz. .NET Core çalışma süresi , .NET Core ile oluşturulan uygulamaları çalıştırmak için kullanılır.

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a>Yükleyiciyle yükleme

Windows'da .NET Core 3.1 çalışma süresini yüklemek için kullanılabilecek bağımsız yükleyiciler vardır:

- [x64 (64-bit) CPU'lar](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [x86 (32-bit) CPU'lar](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a>Yükleyiciyle yükleme

macOS,.NET Core 3.1 çalışma süresini yüklemek için kullanılabilecek bağımsız yükleyicilere sahiptir:

- [x64 (64-bit) CPU'lar](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a>İndirin ve el ile yükleyin

.NET Core için macOS yükleyicilere alternatif olarak çalışma süresini indirebilir ve el ile yükleyebilirsiniz.

Çalışma süresini yüklemek ve terminalde bulunan .NET Core CLI komutlarını etkinleştirmek için önce bir .NET Core ikili sürümü [indirin.](#all-net-core-downloads) Ardından, bir terminal açın ve aşağıdaki komutları çalıştırın. Çalışma zamanının `~/Downloads/dotnet-runtime.pkg` dosyaya indirilmiş olduğu varsayılır.

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-runtime.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a>Paket yöneticisiyle yükleme

.NET Core Runtime'ı birçok ortak Linux paket yöneticisiyle birlikte yükleyebilirsiniz. Daha fazla bilgi için [Linux Package Manager - Install .NET Core](linux-package-managers.md)'a bakın.

Bir paket yöneticisi ile yükleme yalnızca x64 mimarisinde desteklenir. .NET Core Runtime'ı ARM gibi farklı bir mimariyle yüklüyorsanız, İndir meyhanedeki yönergeleri izleyin [ve el ile yükleyin.](#download-and-manually-install) Hangi mimarilerin desteklendirilip desteklendirildigini daha fazla bilgi için [.NET Core bağımlılıkları ve gereksinimleri](dependencies.md)bölümüne bakın.

## <a name="download-and-manually-install"></a>İndirin ve el ile yükleyin

Çalışma süresini ayıklamak ve .NET Core CLI komutlarını terminalde kullanılabilir hale getirmek için önce bir .NET Core ikili sürüm [indirin.](#all-net-core-downloads) Ardından, bir terminal açın ve aşağıdaki komutları çalıştırın.

```bash
mkdir -p $HOME/dotnet && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> Önceki `export` komutlar yalnızca çalıştırıldığı terminal oturumu için .NET Core CLI komutlarını kullanılabilir hale getirin.
>
> Komutları kalıcı olarak eklemek için kabuk profilinizi edebilirsiniz. Linux için farklı kabukları bir dizi vardır ve her biri farklı bir profile sahiptir. Örnek:
>
> - **Bash Kabuk**: *~/.bash_profile*, *~/.bashrc*
> - **Korn Kabuk**: *~/.kshrc* veya *.profile*
> - **Z Kabuk**: *~/.zshrc* veya *.zprofile*
>
> Kabuğunuz için uygun kaynak dosyayı `:$HOME/dotnet` edin ve `PATH` varolan ifadenin sonuna ekleyin. Hiçbir `PATH` deyim dahil değilse, `export PATH=$PATH:$HOME/dotnet`yeni bir satır ekleyin.
>
> Ayrıca, `export DOTNET_ROOT=$HOME/dotnet` dosyanın sonuna ekleyin.

Bu yaklaşım, farklı sürümleri ayrı konumlara yüklemenize ve hangi uygulamatarafından kullanılacağını açıkça seçmenize olanak tanır.

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a>PowerShell otomasyonu ile yükleme

[Dotnet yükleme komut dosyaları,](../tools/dotnet-install-script.md) çalışma zamanının otomasyonu ve yönetici olmayan yüklemeleri için kullanılır. Komut dosyasını [dotnet yükleme komut dosyası başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.

Komut dosyası, .NET Core 3.1 olan en son [uzun vadeli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılandır. `Channel` Anahtarı belirterek belirli bir sürüm seçebilirsiniz. Çalışma `Runtime` süresini yüklemek için anahtarı ekleyin. Aksi takdirde, komut dosyası [SDK](sdk.md)yükler.

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> Yukarıdaki komut, maksimum uyumluluk için ASP.NET Core çalışma süresini yükler. core ASP.NET çalışma süresi standart .NET Core çalışma süresini de içerir.

## <a name="download-and-manually-install"></a>İndirin ve el ile yükleyin

Çalışma süresini ayıklamak ve .NET Core CLI komutlarını terminalde kullanılabilir hale getirmek için önce bir .NET Core ikili sürüm [indirin.](#all-net-core-downloads) Ardından, yüklemek için bir dizin `%USERPROFILE%\dotnet`oluşturun, örneğin. Son olarak, indirilen zip dosyasını bu dizine ayıklayın.

Varsayılan olarak, .NET Core CLI komutları ve uygulamaları bu şekilde yüklenen .NET Core'u kullanmaz. Açıkça kullanmayı seçmelisiniz. Bunu yapmak için, bir uygulamanın başlatıldıği ortam değişkenlerini değiştirin:

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

Bu yaklaşım, birden çok sürümü ayrı konumlara yüklemenize olanak tanır, ardından uygulamayı o konumu işaret eden ortam değişkenleri ile çalıştırarak uygulamanın hangi yükleme konumunu kullanması gerektiğini açıkça seçebilirsiniz.

Bu ortam değişkenleri ayarlandığında bile,.NET Core, uygulamayı çalıştırmak için en iyi çerçeveyi seçerken varsayılan genel yükleme konumunu dikkate alır. Varsayılan genellikle `C:\Program Files\dotnet`, yükleyiciler kullanır. Çalışma zamanını yalnızca bu ortam değişkenini ayarlayarak özel yükleme konumunu kullanması için talimat verebilirsiniz:

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a>Bash otomasyonu ile yükleyin

[Dotnet yükleme komut dosyaları,](../tools/dotnet-install-script.md) çalışma zamanının otomasyonu ve yönetici olmayan yüklemeleri için kullanılır. Komut dosyasını [dotnet yükleme komut dosyası başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.

Komut dosyası, .NET Core 3.1 olan en son [uzun vadeli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılandır. `current` Anahtarı belirterek belirli bir sürüm seçebilirsiniz. Çalışma `runtime` süresini yüklemek için anahtarı ekleyin. Aksi takdirde, komut dosyası [SDK](sdk.md)yükler.

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> Yukarıdaki komut, maksimum uyumluluk için ASP.NET Core çalışma süresini yükler. core ASP.NET çalışma süresi standart .NET Core çalışma süresini de içerir.

::: zone-end

## <a name="all-net-core-downloads"></a>Tüm .NET Core indirmeleri

.NET Core'u aşağıdaki bağlantılardan biriyle doğrudan indirip yükleyebilirsiniz:

- [.NET Core 3.1 indirme](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [.NET Core 2.1 indirme](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a>Docker

Kapsayıcılar, uygulamanızı ana bilgisayar sisteminin geri kalanından yalıtmak için hafif bir yol sağlar. Aynı makinedeki kaplar sadece çekirdeği paylaşır ve uygulamanıza verilen kaynakları kullanır.

.NET Core bir Docker konteynerinde çalıştırılabilir. Resmi .NET Core Docker görüntüleri Microsoft Konteyner Kayıt Defteri'nde (MCR) yayınlanır ve [Microsoft .NET Core Docker Hub deposunda](https://hub.docker.com/_/microsoft-dotnet-core/)keşfedilebilir. Her depo, kullanabilirsiniz .NET (SDK veya Runtime) ve işletim sistemi farklı kombinasyonları için görüntüler içerir.

Microsoft, belirli senaryolar için özel leştirilmiş görüntüler sağlar. Örneğin, [ASP.NET Core deposu,](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) üretimde Core uygulamaları ASP.NET çalıştırmak için oluşturulmuş görüntüler sağlar.

Docker konteynerinde .NET Core kullanma hakkında daha fazla bilgi için [.NET ve Docker ve Örneklere Giriş'e](../docker/introduction.md) bakın. [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)

## <a name="next-steps"></a>Sonraki adımlar

- [.NET Core'un zaten yüklü olup olmadığını nasıl kontrol edilir?](how-to-detect-installed-versions.md)
