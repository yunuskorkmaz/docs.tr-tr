---
title: Windows, Linux ve macOS'a .NET Core SDK'yı yükleyin - .NET Core
description: .NET Core'u Windows, Linux ve macOS'a nasıl yükleyin öğrenin. .NET Core uygulamalarını geliştirmek için gereken bağımlılıkları keşfedin.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 13600ea01e18ad47e6295653ba3b79ce53ff3257
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399009"
---
# <a name="install-the-net-core-sdk"></a>.NET Core SDK’sını yükleme

Bu makalede, .NET Core SDK'yı nasıl yükleyeceğinizi öğreneceksiniz. .NET Core SDK ,NET Core uygulamaları ve kitaplıkları oluşturmak için kullanılır. .NET Core çalışma süresi her zaman SDK ile yüklenir.

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a>Yükleyiciyle yükleme

Windows'da .NET Core 3.1 SDK'yı yüklemek için kullanılabilecek bağımsız yükleyiciler vardır:

- [x64 (64-bit) CPU'lar](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [x86 (32-bit) CPU'lar](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a>Yükleyiciyle yükleme

macOS,.NET Core 3.1 SDK'yı yüklemek için kullanılabilecek bağımsız yükleyicilere sahiptir:

- [x64 (64-bit) CPU'lar](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a>İndirin ve el ile yükleyin

.NET Core için macOS yükleyicilere alternatif olarak SDK'yı indirebilir ve el ile yükleyebilirsiniz.

SDK'yı ayıklamak ve .NET Core CLI komutlarını terminalde kullanılabilir hale getirmek için önce bir .NET Core ikili sürüm [indirin.](#all-net-core-downloads) Ardından, bir terminal açın ve aşağıdaki komutları çalıştırın. Çalışma zamanının `~/Downloads/dotnet-sdk.pkg` dosyaya indirilmiş olduğu varsayılır.

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-sdk.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a>Paket yöneticisiyle yükleme

.NET Core SDK'yı birçok ortak Linux paket yöneticisiyle birlikte yükleyebilirsiniz. Daha fazla bilgi için [Linux Package Manager - Install .NET Core](linux-package-managers.md)'a bakın.

Paket yöneticisiyle yükleme yalnızca x64 mimarisinde desteklenir. .NET Core SDK'yı ARM gibi farklı bir mimariyle yüklüyorsanız, [İndirme'yi](#download-and-manually-install) izleyin ve aşağıdaki talimatları el ile yükleyin. Hangi mimarilerin desteklendirilip desteklendirildigini daha fazla bilgi için [.NET Core bağımlılıkları ve gereksinimleri](dependencies.md)bölümüne bakın.

## <a name="download-and-manually-install"></a>İndirin ve el ile yükleyin

SDK'yı ayıklamak ve .NET Core CLI komutlarını terminalde kullanılabilir hale getirmek için önce bir .NET Core ikili sürüm [indirin.](#all-net-core-downloads) Ardından, bir terminal açın ve aşağıdaki komutları çalıştırın.

```bash
mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-3.1.100-linux-x64.tar.gz -C $HOME/dotnet
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

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a>Visual Studio ile yükleyin

.NET Core uygulamaları geliştirmek için Visual Studio kullanıyorsanız, aşağıdaki tabloda Visual Studio'nun hedef .NET Core SDK sürümüne göre en az gerekli sürümünü açıklanır.

| .NET Core SDK sürümü | Visual Studio sürüm                      |
| --------------------- | ------------------------------------------ |
| 3.1                   | Visual Studio 2019 sürüm 16.4 veya üzeri. |
| 3,0                   | Visual Studio 2019 sürüm 16.3 veya üzeri. |
| 2,2                   | Visual Studio 2017 sürümü 15.9 veya üzeri. |
| 2.1                   | Visual Studio 2017 sürüm 15.7 veya üzeri. |

Visual Studio zaten yüklüyse, sürümünüzü aşağıdaki adımlarla kontrol edebilirsiniz.

01. Visual Studio'yu açın.
01. **Microsoft Visual Studio Hakkında** **Yardım'ı** > seçin.
01. **Hakkında** iletişim kutusundan sürüm numarasını okuyun.

Visual Studio en son .NET Core SDK'yı ve çalışma süresini yükleyebilir.

- [Karşıdan yükleme Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).

### <a name="select-a-workload"></a>İş yükü seçin

Visual Studio'yu yüklerken veya değiştirirken, oluşturmakta olduğunuz uygulama türüne bağlı olarak aşağıdaki iş yüklerinden birini veya birkaçını seçin:

- **Diğer Araç Kümeleri** **bölümündeki .NET Core çapraz platform geliştirme** iş yükü.
- **Web & Bulut** bölümündeki ASP.NET ve web **geliştirme** iş yükü.
- **Web & Bulut** **bölümündeki Azure geliştirme** iş yükü.
- **Masaüstü & Mobil** bölümündeki **.NET masaüstü geliştirme** iş yükü.

[![.NET Core iş yükü ile Windows Visual Studio 2019](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)

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

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a>Mac için Visual Studio ile yükleyin

Mac için Visual **Studio,.NET Core** iş yükü seçildiğinde .NET Core SDK'yı yükler. macOS'ta .NET Core geliştirmeye başlamak [için Mac için Visual Studio 2019'u yükle'ye](/visualstudio/mac/installation)bakın. Son sürüm olan .NET Core 3.1 için Mac 8.4 Önizleme için Visual Studio'yu kullanmanız gerekir.

[![macOS Visual Studio 2019 mac için .NET Core iş yükü özelliği ile Mac](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)

::: zone-end

## <a name="install-alongside-visual-studio-code"></a>Visual Studio Code'un yanına yükleyin

Visual Studio Code, masaüstünüzde çalışan güçlü ve hafif bir kaynak kod düzenleyicisidir. Visual Studio Code, Windows, macOS ve Linux için kullanılabilir.

Visual Studio Code Visual Studio gibi otomatik bir .NET Core yükleyici ile gelmiyor olsa da, .NET Core desteği eklemek basittir.

01. [Visual Studio Code'u indirin ve kurun.](https://code.visualstudio.com/Download)
01. [.NET Core SDK'yı indirin ve kurun.](https://dotnet.microsoft.com/download/dotnet-core)
01. [Visual Studio Code pazar yerinden C# uzantısını yükleyin.](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a>PowerShell otomasyonu ile yükleme

[Dotnet yükleme komut dosyaları](../tools/dotnet-install-script.md) Otomasyon ve SDK'nın yönetici olmayan yüklemeleri için kullanılır. Komut dosyasını [dotnet yükleme komut dosyası başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.

Komut dosyası, .NET Core 3.1 olan en son [uzun vadeli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılandır. .NET Core'un geçerli sürümüne yüklemek için komut dosyasını aşağıdaki anahtarla çalıştırın.

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a>Bash otomasyonu ile yükleyin

[Dotnet yükleme komut dosyaları](../tools/dotnet-install-script.md) Otomasyon ve SDK'nın yönetici olmayan yüklemeleri için kullanılır. Komut dosyasını [dotnet yükleme komut dosyası başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.

Komut dosyası, .NET Core 3.1 olan en son [uzun vadeli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılandır. .NET Core'un geçerli sürümüne yüklemek için komut dosyasını aşağıdaki anahtarla çalıştırın.

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a>Tüm .NET Core indirmeleri

.NET Core'u aşağıdaki bağlantılardan biriyle doğrudan indirip yükleyebilirsiniz:

- [.NET Core 3.1 indirme](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [.NET Core 3.0 indirme](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [.NET Core 2.2 indirme](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [.NET Core 2.1 indirme](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a>Docker

Kapsayıcılar, uygulamanızı ana bilgisayar sisteminin geri kalanından yalıtmak için hafif bir yol sağlar. Aynı makinedeki kaplar sadece çekirdeği paylaşır ve uygulamanıza verilen kaynakları kullanır.

.NET Core bir Docker konteynerinde çalıştırılabilir. Resmi .NET Core Docker görüntüleri Microsoft Konteyner Kayıt Defteri'nde (MCR) yayınlanır ve [Microsoft .NET Core Docker Hub deposunda](https://hub.docker.com/_/microsoft-dotnet-core/)keşfedilebilir. Her depo, kullanabilirsiniz .NET (SDK veya Runtime) ve işletim sistemi farklı kombinasyonları için görüntüler içerir.

Microsoft, belirli senaryolar için özel leştirilmiş görüntüler sağlar. Örneğin, [ASP.NET Core deposu,](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) üretimde Core uygulamaları ASP.NET çalıştırmak için oluşturulmuş görüntüler sağlar.

Docker konteynerinde .NET Core kullanma hakkında daha fazla bilgi için [.NET ve Docker ve Örneklere Giriş'e](../docker/introduction.md) bakın. [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)

## <a name="next-steps"></a>Sonraki adımlar

::: zone pivot="os-windows"

- [Öğretici: Merhaba Dünya öğretici](../tutorials/with-visual-studio.md).
- [Öğretici: Visual Studio Code ile yeni bir uygulama oluşturun.](../tutorials/with-visual-studio-code.md)
- [Öğretici: Containerize bir .NET Core uygulaması](../docker/build-container.md).

::: zone-end

::: zone pivot="os-macos"

- [macOS Catalina noterizasyonu ile çalışma.](macos-notarization-issues.md)
- [Öğretici: macOS'a başlayın.](../tutorials/using-on-mac-vs.md)
- [Öğretici: Visual Studio Code ile yeni bir uygulama oluşturun.](../tutorials/with-visual-studio-code.md)
- [Öğretici: Containerize bir .NET Core uygulaması](../docker/build-container.md).

::: zone-end

::: zone pivot="os-linux"

- [Öğretici: Visual Studio Code ile yeni bir uygulama oluşturun.](../tutorials/with-visual-studio-code.md)
- [Öğretici: Containerize bir .NET Core uygulaması](../docker/build-container.md).

::: zone-end
