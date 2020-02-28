---
title: Windows, Linux ve macOS-.NET Core 'a .NET Core çalışma zamanı 'nı yükler
description: Windows, Linux ve macOS 'ta .NET Core 'u yüklemeyi öğrenin. .NET Core uygulamalarını çalıştırmak için gereken bağımlılıkları bulur.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: a41bbdf5419585f06773583dbe82ab0d84ebaa4c
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157642"
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

## <a name="download-and-manually-install"></a>İndirme ve el ile yükleme

.NET Core için macOS yükleyicilerine alternatif olarak, çalışma zamanını indirip el ile yükleyebilirsiniz.

Çalışma zamanını yüklemek ve terminalde bulunan .NET Core CLI komutlarını etkinleştirmek için önce bir .NET Core ikili sürümü [indirin](#all-net-core-downloads) . Ardından, bir Terminal açın ve aşağıdaki komutları çalıştırın. Çalışma zamanının `~/Downloads/dotnet-runtime.pkg` dosyasına indirildiği varsayılır.

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-runtime.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a>Paket Yöneticisi ile yüklemesi

.NET Core çalışma zamanını birçok ortak Linux Paket Yöneticisi ile yükleyebilirsiniz. Daha fazla bilgi için bkz. [Linux Paket Yöneticisi-.NET Core 'U yükler](linux-package-managers.md).

Paketi bir paket yöneticisi ile yüklemek yalnızca x64 mimarisinde desteklenir. .NET Core çalışma zamanını ARM gibi farklı bir mimariye yüklüyorsanız, [indir ve el ile yükle](#download-and-manually-install) bölümündeki yönergeleri izleyin. Desteklenen mimariler hakkında daha fazla bilgi için bkz. [.NET Core Dependencies ve Requirements](dependencies.md).

## <a name="download-and-manually-install"></a>İndirme ve el ile yükleme

Çalışma zamanını ayıklamak ve .NET Core CLI komutlarının terminalde kullanılabilir hale getirmek için önce bir .NET Core ikili sürümü [indirin](#all-net-core-downloads) . Ardından, bir Terminal açın ve aşağıdaki komutları çalıştırın.

```bash
mkdir -p $HOME/dotnet && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> Yukarıdaki `export` komutları yalnızca .NET Core CLI komutlarını çalıştırıldığı terminal oturumu için kullanılabilir hale getirir.
>
> Komutları kalıcı olarak eklemek için kabuk profilinizi düzenleyebilirsiniz. Linux için kullanılabilen birçok farklı kabuk vardır ve her birinin farklı bir profili vardır. Örnek:
>
> - **Bash kabuğu**: *~/. bash_profile*, *~/,bashrc*
> - **Korn kabuğu**: *~/,KSHRC* veya *. Profile*
> - **Z kabuğu**: *~/,zshrc* veya *. zprofile*
>
> Kabuğunuz için uygun kaynak dosyayı düzenleyin ve mevcut `PATH` ifadesinin sonuna `:$HOME/dotnet` ekleyin. `PATH` bir ifade dahil yoksa, `export PATH=$PATH:$HOME/dotnet`yeni bir satır ekleyin.
>
> Ayrıca, dosyanın sonuna `export DOTNET_ROOT=$HOME/dotnet` ekleyin.

Bu yaklaşım ayrı konumlara farklı sürümler yüklemenize ve hangi uygulamayı kullanmak üzere açık bir şekilde tercih etmenize olanak tanır.

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

## <a name="download-and-manually-install"></a>İndirme ve el ile yükleme

Çalışma zamanını ayıklamak ve .NET Core CLI komutlarının terminalde kullanılabilir hale getirmek için önce bir .NET Core ikili sürümü [indirin](#all-net-core-downloads) . Ardından, yüklemek için bir dizin oluşturun, örneğin `%USERPROFILE%\dotnet`. Son olarak, indirilen ZIP dosyasını bu dizine ayıklayın.

Varsayılan olarak, .NET Core CLI komutları ve uygulamalar .NET Core 'u bu şekilde kullanmaz. Açıkça kullanmayı tercih etmeniz gerekir. Bunu yapmak için, bir uygulamanın başlatıldığı ortam değişkenlerini değiştirin:

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

Bu yaklaşım, farklı konumlara birden çok sürüm yüklemenize olanak sağlar ve ardından uygulamayı o konuma işaret eden ortam değişkenleriyle çalıştırarak uygulamanın kullanması gereken yüklemeyi açıkça seçebilirsiniz.

Bu ortam değişkenleri ayarlansa bile, .NET Core uygulamayı çalıştırmak için en iyi çerçeveyi seçerken varsayılan genel yüklemesi konumunu yine de dikkate alır. Varsayılan değer genellikle yükleyicilerin kullanacağı `C:\Program Files\dotnet`. Çalışma zamanına yalnızca bu ortam değişkenini de ayarlayarak özel bir yüklemede kullanmak üzere talimat verebilirsiniz:

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a>Bash otomasyonu ile Install

[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , çalışma zamanının Otomasyon ve yönetici olmayan yüklemeleri için kullanılır. Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.

Komut dosyası, .NET Core 3,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir. `current` anahtarını belirterek belirli bir yayını seçebilirsiniz. Çalışma zamanı yüklemek için `runtime` anahtarını ekleyin. Aksi halde, komut dosyası [SDK 'yı](sdk.md)yüklüyor.

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
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
