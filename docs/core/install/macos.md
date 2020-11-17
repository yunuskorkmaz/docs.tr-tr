---
title: MacOS 'ta .NET 'i yükler
description: .NET yükleyebileceğiniz macOS sürümleri hakkında bilgi edinin.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 983c5d2c04b87759b898f449bc092161b03c8ace
ms.sourcegitcommit: c38bf879a2611ff46aacdd529b9f2725f93e18a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/13/2020
ms.locfileid: "94594462"
---
# <a name="install-net-on-macos"></a>MacOS 'ta .NET 'i yükler

> [!div class="op_single_selector"]
>
> - [Windows’ta yükleme](windows.md)
> - [macOS’ta yükleme](macos.md)
> - [Linux'ta yükleme](linux.md)

Bu makalede, macOS 'ta .NET yüklemeyi öğreneceksiniz. .NET çalışma zamanı ve SDK 'dan oluşur. Çalışma zamanı, .NET uygulamasını çalıştırmak için kullanılır ve uygulama ile birlikte bulunmayabilir veya bulunmayabilir. SDK, .NET uygulamaları ve kitaplıkları oluşturmak için kullanılır. .NET çalışma zamanı her zaman SDK ile birlikte yüklenir.

En son .NET sürümü 5,0 ' dir.

> [!div class="button"]
> [.NET Core indirin](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a>Desteklenen yayınlar

Aşağıdaki tabloda, şu anda desteklenen .NET sürümlerinin ve desteklenen macOS sürümlerinin bir listesi verilmiştir. Bu sürümler, [.NET sürümünün destek sonuna ulaşmasını](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)ve bu sürümlerin desteklenmemesini destekler.

- ✔️, .NET Core sürümünün hala desteklendiğini gösterir.
- Bir ❌ , .NET Core sürümünün desteklenmediğini belirtir.

| İşletim Sistemi          | .NET Core 2.1 | .NET Core 3,1 | .NET 5,0 |
|---------------------------|---------------|---------------|----------------|
| macOS 10,15 "Catalina"    | ✔️ 2,1 ([sürüm notları][release-notes-21]) | ✔️ 3,1 ([sürüm notları][release-notes-31]) | ✔️ 5,0 ([sürüm notları][release-notes-50]) |
| macOS 10,14 "Mojave"      | ✔️ 2,1 ([sürüm notları][release-notes-21]) | ✔️ 3,1 ([sürüm notları][release-notes-31]) | ✔️ 5,0 ([sürüm notları][release-notes-50]) |
| macOS 10,13 "High Sierra" | ✔️ 2,1 ([sürüm notları][release-notes-21]) | ✔️ 3,1 ([sürüm notları][release-notes-31]) | ✔️ 5,0 ([sürüm notları][release-notes-50]) |
| macOS 10,12 "Sierra"      | ✔️ 2,1 ([sürüm notları][release-notes-21]) | ❌ 3,1 ([sürüm notları][release-notes-31]) | ❌ 5,0 ([sürüm notları][release-notes-50]) |

## <a name="unsupported-releases"></a>Desteklenmeyen yayınlar

Aşağıdaki .NET sürümleri ❌ artık desteklenmemektedir. Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:

- 3,0 ([sürüm notları][release-notes-30])
- 2,2 ([sürüm notları][release-notes-22])
- 2,0 ([sürüm notları][release-notes-20])

## <a name="runtime-information"></a>Çalışma zamanı bilgileri

Çalışma zamanı .NET ile oluşturulan uygulamaları çalıştırmak için kullanılır. Uygulama yazarı bir uygulama yayımladığında, çalışma zamanını uygulamayla birlikte dahil edebilirler. Çalışma zamanını içermiyorsa, bu kullanıcı çalışma zamanını yüklemek için kullanıcıya ait olur.

MacOS 'ta yükleyebileceğiniz üç farklı çalışma zamanı vardır:

*ASP.NET Core çalışma zamanı*\
ASP.NET Core uygulamalar çalıştırır. .NET çalışma zamanı içerir.

*.NET çalışma zamanı*\
Bu çalışma zamanı, en basit çalışma zamanı ve başka bir çalışma zamanı içermez. .NET uygulamalarıyla en iyi uyumluluk için *ASP.NET Core çalışma zamanı* yüklemenizi kesinlikle öneririz.

> [!div class="button"]
> [.NET çalışma zamanını indirin](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a>SDK bilgileri

SDK, .NET uygulamaları ve kitaplıkları derlemek ve yayımlamak için kullanılır. SDK 'nın [yüklenmesi her iki](#runtime-information)çalışma zamanını da içerir: ASP.NET Core ve .net.

## <a name="dependencies"></a>Bağımlılıklar

.NET aşağıdaki macOS sürümleriyle desteklenir:

> [!NOTE]
> Bir `+` sembol en düşük sürümü temsil eder.

| .NET Core sürümü | macOS                 | Mimariler | Daha fazla bilgi    |
| ----------------- | --------------------- | --------------| --- |
| 5.0               | High Sierra (10.13 +)  | x64 | [Daha fazla bilgi](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md) |
| 3,1               | High Sierra (10.13 +)  | x64 | [Daha fazla bilgi](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| 3,0               | High Sierra (10.13 +)  | x64 | [Daha fazla bilgi](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| 2.2               | Sierra (10.12 +)       | x64 | [Daha fazla bilgi](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| 2.1               | Sierra (10.12 +)       | x64 | [Daha fazla bilgi](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

MacOS Catalina (sürüm 10,15) ile başlayarak, geliştirici KIMLIĞIYLE dağıtılan 1 Haziran 2019 ' den sonra oluşturulan tüm yazılımlar, dikkat edilmiş olmalıdır. Bu gereksinim .NET çalışma zamanı, .NET SDK ve .NET ile oluşturulan yazılımlar için geçerlidir.

.NET 5,0 ve .NET Core 3,1, 3,0 ve 2,1 için çalışma zamanı ve SDK yükleyicileri, 18 Şubat 2020 ' den itibaren giderilmiş. Önceki yayınlanmış sürümler yok. Desteklenmeyen bir uygulama çalıştırırsanız aşağıdaki görüntüye benzer bir hata görürsünüz:

![macOS Catalina notarleştirme uyarısı](media/dependencies/macos-notarized-pkg-warning.png)

Zorlanan uygulamanın .NET 'i (ve .NET uygulamalarınızı) nasıl etkilediği hakkında daha fazla bilgi için bkz. [macOS Catalina Ile çalışma](macos-notarization-issues.md).

## <a name="libgdiplus"></a>libgdiplus

*System. Drawing. Common* derlemesini kullanan .NET uygulamaları, libgdiplus 'in yüklenmesini gerektirir.

Libgdiplus almanın kolay bir yolu, macOS için [homebrew ("Brew")](https://brew.sh/) paket yöneticisini kullanmaktır. *Brew* yükledikten sonra, bir Terminal (komut) isteminde aşağıdaki komutları yürüterek libgdiplus yükleme yapın:

```console
brew update
brew install mono-libgdiplus
```

## <a name="install-with-an-installer"></a>Bir yükleyici ile yükleme

macOS, .NET 5,0 SDK 'Yı yüklemek için kullanılabilecek tek başına yükleyicilere sahiptir:

- [x64 (64-bit) CPU 'Lar](https://dotnet.microsoft.com/download/dotnet-core/5.0)

## <a name="download-and-manually-install"></a>İndirme ve el ile yükleme

<!-- Note, this content is taken from includes/linux-install-manual.md but changed for macOS. Any fixes should be applied there too, though content may be different -->

.NET için macOS yükleyicilerine alternatif olarak SDK ve çalışma zamanını indirip el ile yükleyebilirsiniz. El ile yüklemeyi, genellikle sürekli tümleştirme testinin bir parçası olarak gerçekleştirilir. Bir geliştirici veya Kullanıcı için genellikle bir [Yükleyici](https://dotnet.microsoft.com/download/dotnet-core)kullanmak daha iyidir.

.NET SDK 'yı yüklerseniz, ilgili çalışma zamanını yüklemeniz gerekmez. İlk olarak, aşağıdaki sitelerden birinden SDK veya çalışma zamanı için **ikili** bir sürüm indirin:

- ✔️ [.net 5,0 İndirmeleri](https://dotnet.microsoft.com/download/dotnet/5.0)
- ✔️ [.NET Core 3,1 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- ✔️ [.NET Core 2,1 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/2.1)
- [Tüm .NET Core İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core)

Ardından, indirilen dosyayı ayıklayın ve `export` .NET tarafından kullanılan değişkenleri ayarlamak için komutunu kullanın ve ardından .net 'ın yol içinde olduğundan emin olun.

Çalışma zamanını ayıklamak ve .NET CLı komutlarını terminalde kullanılabilir hale getirmek için önce bir .NET ikili sürümü indirin. Ardından, bir Terminal açın ve dosyanın kaydedildiği dizinden aşağıdaki komutları çalıştırın. Arşiv dosyası adı, indirdiklerinize bağlı olarak farklı olabilir.

**Çalışma zamanını ayıklamak için aşağıdaki komutu kullanın**:

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-5.0.0-osx-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

**SDK 'yı ayıklamak için aşağıdaki komutu kullanın**:

```bash
mkdir -p "$HOME/dotnet" && tar zxf dotnet-sdk-5.0.100-osx-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> Yukarıdaki `export` Komutlar yalnızca .net CLI komutlarını çalıştırıldığı terminal oturumu için kullanılabilir hale getirir.
>
> Komutları kalıcı olarak eklemek için kabuk profilinizi düzenleyebilirsiniz. Linux için kullanılabilen birçok farklı kabuk vardır ve her birinin farklı bir profili vardır. Örnek:
>
> - **Bash kabuğu**: *~/.bash_profile*, *~/,bashrc*
> - **Korn kabuğu**: *~/,KSHRC* veya *. Profile*
> - **Z kabuğu**: *~/,zshrc* veya *. zprofile*
>
> Kabuğunuz için uygun kaynak dosyayı düzenleyin ve `:$HOME/dotnet` var olan deyimin sonuna ekleyin `PATH` . Hiçbir `PATH` ifade dahil yoksa, ile yeni bir satır ekleyin `export PATH=$PATH:$HOME/dotnet` .
>
> Ayrıca, `export DOTNET_ROOT=$HOME/dotnet` dosyanın sonuna ekleyin.

Bu yaklaşım ayrı konumlara farklı sürümler yüklemenize ve hangi uygulamayı kullanmak üzere açık bir şekilde tercih etmenize olanak tanır.

## <a name="install-with-visual-studio-for-mac"></a>Mac için Visual Studio ile yüklensin

**.Net** iş yükü seçiliyken Mac için Visual Studio .NET SDK 'sını yüklüyor. MacOS 'ta .NET geliştirme ile çalışmaya başlamak için bkz. [Mac Için Visual Studio 2019 'Yi yüklemek](/visualstudio/mac/installation).

| .NET SDK sürümü      | Visual Studio sürüm                      |
| --------------------- | ------------------------------------------ |
| 5.0                   | Mac için Visual Studio 2019 sürüm 8,8 veya üzeri. |
| 3,1                   | Mac için Visual Studio 2019 sürüm 8,4 veya üzeri. |
| 2.1                   | Mac için Visual Studio 2019 sürüm 8,0 veya üzeri. |

[![.NET iş yükü özelliği ile Mac için macOS Visual Studio 2019](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)

## <a name="install-alongside-visual-studio-code"></a>Visual Studio Code birlikte yüklemeyi

Visual Studio Code, masaüstünüzde çalışan güçlü ve hafif bir kaynak kod düzenleyicisidir. Visual Studio Code Windows, macOS ve Linux için kullanılabilir.

Visual Studio Code, Visual Studio gibi otomatikleştirilmiş bir .NET yükleyicisi ile birlikte gelmediğinden, .NET desteği ekleme basittir.

01. [Visual Studio Code indirin ve yükleyin](https://code.visualstudio.com/Download).
01. [.NET SDK 'Sını indirip yükleyin](https://dotnet.microsoft.com/download/dotnet-core).
01. [Visual Studio Code marketi 'Nden C# uzantısını yükler](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).

## <a name="install-with-bash-automation"></a>Bash otomasyonu ile Install

[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , çalışma zamanının Otomasyon ve yönetici olmayan yüklemeleri için kullanılır. Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.

Komut dosyası, .NET 3,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir. Anahtarı belirterek belirli bir sürümü seçebilirsiniz `current` . `runtime`Çalışma zamanı yüklemek için anahtarı ekleyin. Aksi halde, komut dosyası [SDK 'yı](./windows.md)yüklüyor.

```bash
./dotnet-install.sh --channel 5.0 --runtime aspnetcore
```

> [!NOTE]
> Önceki komut, ASP.NET Core çalışma zamanını maksimum uyumluluk için yüklerse. ASP.NET Core çalışma zamanı standart .NET çalışma zamanını da içerir.

## <a name="docker"></a>Docker

Kapsayıcılar, uygulamanızı ana bilgisayar sisteminin geri kalanından yalıtmak için basit bir yol sağlar. Aynı makinedeki kapsayıcılar yalnızca çekirdeği paylaşır ve uygulamanıza verilen kaynakları kullanır.

.NET, bir Docker kapsayıcısında çalıştırılabilir. Resmi .NET Docker görüntüleri Microsoft Container Registry (MCR) ' de yayımlanır ve [Microsoft .NET Core Docker Hub deposunda](https://hub.docker.com/_/microsoft-dotnet/)bulunabilir. Her depo, .NET (SDK veya çalışma zamanı) ve kullanabileceğiniz farklı .NET birleşimlerinin görüntülerini içerir.

Microsoft, belirli senaryolar için uyarlanmış görüntüler sağlar. Örneğin, [ASP.NET Core deposu](https://hub.docker.com/_/microsoft-dotnet-aspnet) üretimde ASP.NET Core uygulamaları çalıştırmak için oluşturulmuş görüntüler sağlar.

Bir Docker kapsayıcısında .NET Core kullanma hakkında daha fazla bilgi için bkz. [.net ve Docker](../docker/introduction.md) ve [örneklere](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)giriş.

## <a name="next-steps"></a>Sonraki adımlar

- [.NET Core 'un zaten yüklü olup olmadığını denetleme](how-to-detect-installed-versions.md?pivots=os-macos).
- [MacOS Catalina Ile çalışma](macos-notarization-issues.md).
- [Öğretici: macOS 'u kullanmaya](../tutorials/with-visual-studio-mac.md)başlayın.
- [Öğretici: Visual Studio Code yeni bir uygulama oluşturun](../tutorials/with-visual-studio-code.md).
- [Öğretici: bir .NET Core uygulamasını Kapsayıize](../docker/build-container.md)edin.

[release-notes-21]: https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md
[release-notes-31]: https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md
[release-notes-50]: https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md
[release-notes-20]: https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md
[release-notes-22]: https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md
[release-notes-30]: https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md
