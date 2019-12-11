---
title: Windows, Linux ve macOS-.NET Core 'a .NET Core SDK yüklemesi
description: Windows, Linux ve macOS 'ta .NET Core 'u yüklemeyi öğrenin. .NET Core uygulamaları geliştirmek için gereken bağımlılıkları bulun.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 1f7efaedaa1a0be90f7b619f954bdf78eecafa07
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74959830"
---
# <a name="install-the-net-core-sdk"></a>.NET Core SDK 'i yükler

Bu makalede, .NET Core SDK nasıl yükleneceğini öğreneceksiniz. .NET Core SDK .NET Core Uygulamaları ve kitaplıkları oluşturmak için kullanılır. .NET Core çalışma zamanı her zaman SDK ile birlikte yüklenir.

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a>Bir yükleyici ile yükleme

Windows, .NET Core 3,1 SDK 'sını yüklemek için kullanılabilecek tek başına yükleyicilere sahiptir:

- [x64 (64-bit) CPU 'Lar](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [x86 (32 bit) CPU 'Lar](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a>Bir yükleyici ile yükleme

macOS, .NET Core 3,1 SDK 'sını yüklemek için kullanılabilecek tek başına yükleyicilere sahiptir:

- [x64 (64-bit) CPU 'Lar](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a>Paket Yöneticisi ile yüklemesi

.NET Core SDK birçok ortak Linux Paket Yöneticisi ile yükleyebilirsiniz. Daha fazla bilgi için bkz. [Linux Paket Yöneticisi-.NET Core 'U yükler](linux-package-managers.md).

## <a name="download-and-manually-install"></a>İndirme ve el ile yükleme

SDK 'Yı ayıklamak ve komutları terminalde kullanılabilir hale getirmek için önce bir .NET Core ikili sürümü [indirin](#all-net-core-downloads) . Ardından, bir Terminal açın ve aşağıdaki komutları çalıştırın.

```bash
mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-3.1.100-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> Yukarıdaki komutlar yalnızca .NET SDK komutlarını çalıştırıldığı terminal oturumu için kullanılabilir hale getirir.
>
> Komutları kalıcı olarak eklemek için kabuk profilinizi düzenleyebilirsiniz. Linux için kullanılabilen birçok farklı kabuk vardır ve her birinin farklı bir profili vardır. Örneğin:
>
> - **Bash kabuğu**: *~/. bash_profile*, *~/,bashrc*
> - **Korn kabuğu**: *~/,KSHRC* veya *. Profile*
> - **Z kabuğu**: *~/,zshrc* veya *. zprofile*
> 
> Kabuğunuz için uygun kaynak dosyayı düzenleyin ve mevcut `PATH` ifadesinin sonuna `:$HOME/dotnet` ekleyin. `PATH` bir ifade dahil yoksa, `export PATH=$PATH:$HOME/dotnet`yeni bir satır ekleyin.
>
> Ayrıca, dosyanın sonuna `export DOTNET_ROOT=$HOME/dotnet` ekleyin.

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a>Visual Studio ile Install

.NET Core uygulamaları geliştirmek için Visual Studio kullanıyorsanız, aşağıdaki tabloda, hedef .NET Core SDK sürümüne göre gerekli olan en düşük Visual Studio sürümü açıklanmaktadır.

| .NET Core SDK sürümü | Visual Studio sürüm                      |
| --------------------- | ------------------------------------------ |
| 3.1                   | Visual Studio 2019 sürüm 16,4 veya üzeri. |
| 3.0                   | Visual Studio 2019 sürüm 16,3 veya üzeri. |
| 2.2                   | Visual Studio 2017 sürüm 15,9 veya üzeri. |
| 2.1                   | Visual Studio 2017 sürüm 15,7 veya üzeri. |

Visual Studio zaten yüklüyse, aşağıdaki adımlarla sürümünüzü kontrol edebilirsiniz.

01. Visual Studio'yu açın.
01. **Microsoft Visual Studio hakkında** **Yardım** > seçin.
01. **Hakkında** iletişim kutusunda sürüm numarasını okuyun.

Visual Studio, en son .NET Core SDK ve çalışma zamanını yükleyebilir.

- [Visual Studio 'Yu indirin](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).

### <a name="select-a-workload"></a>İş yükü seçin

Visual Studio 'Yu yüklerken veya değiştirirken, oluşturmakta olduğunuz uygulamanın türüne bağlı olarak aşağıdaki iş yüklerinden birini seçin:

- **Diğer Toolsets** bölümünde yer alan **.NET Core platformlar arası geliştirme** iş yükü.
- **Web & bulut** bölümündeki **ASP.net ve Web geliştirme** iş yükü.
- **Web & bulut** bölümündeki **Azure geliştirme** iş yükü.
- **Masaüstü & mobil** bölümündeki **.net masaüstü geliştirme** iş yükü.

[.NET Core iş yüküne sahip Windows Visual Studio 2019 ![](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a>Mac için Visual Studio ile yüklensin

**.NET Core** iş yükü seçiliyken Mac için Visual Studio .NET Core SDK yüklenir. MacOS 'ta .NET Core geliştirme ile çalışmaya başlamak için bkz. [Mac Için Visual Studio 2019 'Yi yüklemek](/visualstudio/mac/installation). En son sürüm olan .NET Core 3,1 için Mac için Visual Studio 8,4 Preview ' i kullanmanız gerekir.

[.NET Core iş yükü özelliği ile Mac için macOS Visual Studio 2019 ![](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)

::: zone-end

## <a name="install-alongside-visual-studio-code"></a>Visual Studio Code birlikte yüklemeyi

Visual Studio Code, masaüstünüzde çalışan güçlü ve hafif bir kaynak kod düzenleyicisidir. Visual Studio Code Windows, macOS ve Linux için kullanılabilir.

Visual Studio Code, Visual Studio gibi otomatikleştirilmiş bir .NET Core yükleyicisi ile birlikte gelmediğinden, .NET Core desteği eklemek basittir.

01. [Visual Studio Code indirin ve yükleyin](https://code.visualstudio.com/Download).
01. [.NET Core SDK indirin ve yükleyin](https://dotnet.microsoft.com/download/dotnet-core).
01. [Uzantıyı Visual Studio Code marketi 'Nden yüklersiniz. C# ](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp)

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a>PowerShell otomasyonu ile Install

[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , SDK 'nın Otomasyon ve yönetici olmayan yüklemeleri için kullanılır. Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.

Komut dosyası, .NET Core 2,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir. Geçerli .NET Core sürümünü yüklemek için betiği aşağıdaki anahtarla çalıştırın.

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a>Bash otomasyonu ile Install

[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , SDK 'nın Otomasyon ve yönetici olmayan yüklemeleri için kullanılır. Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.

Komut dosyası, .NET Core 2,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir. Geçerli .NET Core sürümünü yüklemek için betiği aşağıdaki anahtarla çalıştırın.

```bash
./dotnet-install.sh -c Current
```

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

::: zone pivot="os-windows"

- [Öğretici: C# Merhaba Dünya öğreticisi](../tutorials/with-visual-studio.md).
- [Öğretici: Visual Basic Merhaba Dünya öğreticisi](../tutorials/vb-with-visual-studio.md).
- [Öğretici: Visual Studio Code yeni bir uygulama oluşturun](../tutorials/with-visual-studio-code.md).
- [Öğretici: bir .NET Core uygulamasını Kapsayıize](../docker/build-container.md)edin.

::: zone-end

::: zone pivot="os-macos"

- [Öğretici: macOS 'u kullanmaya](../tutorials/using-on-mac-vs.md)başlayın.
- [Öğretici: Visual Studio Code yeni bir uygulama oluşturun](../tutorials/with-visual-studio-code.md).
- [Öğretici: bir .NET Core uygulamasını Kapsayıize](../docker/build-container.md)edin.

::: zone-end

::: zone pivot="os-linux"

- [Öğretici: Visual Studio Code yeni bir uygulama oluşturun](../tutorials/with-visual-studio-code.md).
- [Öğretici: bir .NET Core uygulamasını Kapsayıize](../docker/build-container.md)edin.

::: zone-end
