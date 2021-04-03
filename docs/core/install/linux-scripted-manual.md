---
title: Linux 'ta .NET 'i el ile yükler-.NET
description: Linux üzerinde bir paket yöneticisi olmadan .NET SDK ve .NET çalışma zamanının nasıl yükleneceğini gösterir. Install betiğini kullanın veya ikili dosyaları el ile ayıklayın.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 9176f7477cf80c26ef0b5b7c438c47afcb423799
ms.sourcegitcommit: 44af69720863bd09bd7a4509bf1ec119466ba6e8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106231303"
---
# <a name="install-the-net-sdk-or-the-net-runtime-manually"></a>.NET SDK veya .NET çalışma zamanını el ile yükleyebilirsiniz

.NET, Linux üzerinde desteklenmektedir ve bu makalede, Install betiği kullanılarak veya ikili dosyaları ayıklanarak Linux 'ta .NET 'in nasıl yükleneceği açıklanır. Yerleşik paket yöneticisini destekleyen dağıtımların bir listesi için bkz. [Linux 'ta .net 'ı Install](linux.md).

Ayrıca, yaslama ile .NET yükleyebilirsiniz. Daha fazla bilgi için bkz. [.NET SDK 'yı veya .NET çalışma zamanını yaslama Ile yüklemeyi](linux-snap.md).

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="net-releases"></a>.NET yayınları

Aşağıdaki tabloda .NET (ve .NET Core) yayınları listelenmektedir:

| ✔️ destekleniyor | ❌ Desteklenen |
|-------------|---------------|
| 5.0         | 3.0           |
| 3,1 (LTS)   | 2,2           |
| 2,1 (LTS)   | 2.0           |
|             | 1.1           |
|             | 1.0           |

.NET sürümlerinin yaşam döngüsü hakkında daha fazla bilgi için bkz. [.NET Core ve .NET 5 destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).

## <a name="dependencies"></a>Bağımlılıklar

.NET yüklediğinizde belirli bağımlılıklar yüklenemeyebilir, örneğin [el ile yüklenirken](#manual-install). Aşağıdaki listede, Microsoft tarafından desteklenen ve yüklemeniz gerekebilecek bağımlılıklara sahip Linux dağıtımlarını ayrıntılarıyla bulabilirsiniz. Daha fazla bilgi için dağıtım sayfasına bakın:

- [Alpine](linux-alpine.md#dependencies)
- [Debian](linux-debian.md#dependencies)
- [CentOS](linux-centos.md#dependencies)
- [Fedora](linux-fedora.md#dependencies)
- [RHEL](linux-rhel.md#dependencies)
- [SLES](linux-sles.md#dependencies)
- [Ubuntu](linux-ubuntu.md#dependencies)

Bağımlılıklar hakkında genel bilgi için bkz. [kendi kendine kapsanan Linux uygulamaları](https://github.com/dotnet/core/blob/main/Documentation/self-contained-linux-apps.md).

### <a name="rpm-dependencies"></a>RPM bağımlılıkları

Dağıtım daha önce listelenmediyse ve RPM tabanlı ise, Aşağıdaki bağımlılıklara ihtiyacınız olabilir:

- krb5-libs
- libıu
- OpenSSL-libs

Hedef çalışma zamanı ortamının OpenSSL sürümü 1,1 veya daha yeniyse, **COMPAT-openssl10** yüklemeniz gerekir.

### <a name="deb-dependencies"></a>DEB bağımlılıkları

Dağıtım daha önce listelenmediyse ve temel alıyorsa, Aşağıdaki bağımlılıklara ihtiyacınız olabilir:

- libc6
- libgcc1
- libgssapı-krb5-2
- libicu67
- libssl 1.1
- libstdc + + 6
- zlib1g

### <a name="common-dependencies"></a>Ortak bağımlılıklar

*System. Drawing. Common* derlemesini kullanan .NET uygulamaları için aşağıdaki bağımlılığa de ihtiyacınız olacaktır:

- [libgdiplus (sürüm 6.0.1 veya üzeri)](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > En son bir *libgdiplus* sürümünü sisteminize mono deposunu ekleyerek yükleyebilirsiniz. Daha fazla bilgi için bkz. <https://www.mono-project.com/download/stable/>.

## <a name="scripted-install"></a>Komut dosyalı yüklemesi

[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , **SDK** ve **çalışma zamanının** Otomasyon ve yönetici olmayan yüklemeleri için kullanılır. Betiği konumundan indirebilirsiniz <https://dot.net/v1/dotnet-install.sh> .

> ! ÖNEMLI Komut dosyasını çalıştırmak için bash gereklidir.

Komut dosyası, .NET Core 3,1 olan en son SDK [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan olarak kullanılır. (LTS) sürümü olmayan geçerli sürümü yüklemek için `-c Current` parametresini kullanın.

```bash
./dotnet-install.sh -c Current
```

SDK yerine .NET Runtime yüklemek için `--runtime` parametresini kullanın.

```bash
./dotnet-install.sh -c Current --runtime aspnetcore
```

Belirli sürümü göstermek için parametresini değiştirerek belirli bir sürümü yükleyebilirsiniz `-c` . Aşağıdaki komut .NET SDK 5,0 'yi yüklüyor.

```bash
./dotnet-install.sh -c 5.0
```

Daha fazla bilgi için bkz. [DotNet-Install betikler Reference](../tools/dotnet-install-script.md).

## <a name="manual-install"></a>El ile yüklemesi

<!-- Note, this content is copied in macos.md. Any fixes should be applied there too, though content may be different -->

Paket yöneticilerine alternatif olarak SDK ve çalışma zamanını indirip el ile yükleyebilirsiniz. El ile yüklemesi, genellikle sürekli tümleştirme testinin parçası olarak veya desteklenmeyen bir Linux dağıtımında kullanılır. Bir geliştirici veya Kullanıcı için bir paket yöneticisi kullanmak daha iyidir.

.NET SDK 'yı yüklerseniz, ilgili çalışma zamanını yüklemeniz gerekmez. İlk olarak, aşağıdaki sitelerden birinden SDK veya çalışma zamanı için **ikili** bir sürüm indirin:

- ✔️ [.net 5,0 İndirmeleri](https://dotnet.microsoft.com/download/dotnet/5.0)
- ✔️ [.NET Core 3,1 İndirmeleri](https://dotnet.microsoft.com/download/dotnet/3.1)
- ✔️ [.NET Core 2,1 İndirmeleri](https://dotnet.microsoft.com/download/dotnet/2.1)
- [Tüm .NET Core İndirmeleri](https://dotnet.microsoft.com/download/dotnet)

Ardından, indirilen dosyayı ayıklayın ve `export` .NET tarafından kullanılan değişkenleri ayarlamak için komutunu kullanın ve ardından .net 'ın yol içinde olduğundan emin olun.

Çalışma zamanını ayıklamak ve .NET CLı komutlarını terminalde kullanılabilir hale getirmek için önce bir .NET ikili sürümü indirin. Ardından, bir Terminal açın ve dosyanın kaydedildiği dizinden aşağıdaki komutları çalıştırın. Arşiv dosyası adı, indirdiklerinize bağlı olarak farklı olabilir.

**İndirdiğiniz çalışma zamanını veya SDK 'Yı ayıklamak için aşağıdaki komutları kullanın.** `DOTNET_FILE`Değeri dosya adınızla değiştirmeyi unutmayın:

```bash
DOTNET_FILE=dotnet-sdk-5.0.102-linux-x64.tar.gz
export DOTNET_ROOT=$HOME/dotnet

mkdir -p "$DOTNET_ROOT" && tar zxf "$DOTNET_FILE" -C "$DOTNET_ROOT"

export PATH=$PATH:$DOTNET_ROOT
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

## <a name="next-steps"></a>Sonraki adımlar

- [.NET CLı için sekme tamamlamayı etkinleştirme](../tools/enable-tab-autocomplete.md)
- [Öğretici: Visual Studio Code kullanarak .NET SDK ile bir konsol uygulaması oluşturma](../tutorials/with-visual-studio-code.md)
