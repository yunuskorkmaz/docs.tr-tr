---
title: Linux 'ta .NET 'i Snap-.NET ile yükler
description: Linux 'ta .NET SDK veya .NET çalışma zamanının yaslama ile nasıl yükleneceğini gösterir.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 0d91f5049c92df240e2c3e26bc67952abe17fedc
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190105"
---
# <a name="install-the-net-sdk-or-the-net-runtime-with-snap"></a>.NET SDK veya .NET çalışma zamanını yaslama ile birlikte yükler

.NET SDK veya .NET çalışma zamanı yüklemek için bir snap paketi kullanın. Yapışır, Linux dağıtımına yerleşik olarak bulunan paket yöneticisinin harika bir alternatifidir. Bu makalede, [.net aracılığıyla .net](https://snapcraft.io/dotnet-sdk)'in nasıl yükleneceği açıklanır.

Bir snap, bir uygulamanın bir paketidir ve farklı Linux dağıtımları arasında değişiklik yapılmaksızın, onun bağımlılıklarıdır. Yaslanabilirlik, ek depodan bulunabilir ve yüklenebilir. Yaslama hakkında daha fazla bilgi için bkz. [yaslama ile çalışmaya](https://snapcraft.io/docs/getting-started)başlama.

> [!CAUTION]
> Windows 10 ' da WSL2 'de yaslama paketleri desteklenmez. Alternatif olarak, belirli bir WSL2 dağıtımı için [ `dotnet-install` betiği](linux-scripted-manual.md#scripted-install) veya paket yöneticisini kullanın. Bu önerilmez, ancak anlık görüntü [forumlarından desteklenmeyen bir geçici çözümle](https://forum.snapcraft.io/t/running-snaps-on-wsl2-insiders-only-for-now/13033)birlikte Yaslama özelliğini etkinleştirmeyi deneyebilirsiniz.

## <a name="net-releases"></a>.NET yayınları

Yalnızca desteklenen .NET SDK sürümleri, Snap aracılığıyla kullanılabilir ✔️. .NET çalışma zamanının tüm sürümleri, sürüm 2,1 ' den başlayarak ek olarak kullanılabilir. Aşağıdaki tabloda .NET (ve .NET Core) yayınları listelenmektedir:

| ✔️ destekleniyor | ❌ Desteklenen |
|-------------|---------------|
| 5.0         | 3.0           |
| 3,1 (LTS)   | 2,2           |
| 2,1 (LTS)   | 2.0           |
|             | 1.1           |
|             | 1.0           |

.NET sürümlerinin yaşam döngüsü hakkında daha fazla bilgi için bkz. [.NET Core ve .NET 5 destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).

## <a name="sdk-or-runtime"></a>SDK veya çalışma zamanı

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="install-the-sdk"></a>SDK Yükleme

.NET SDK için Yaslama paketleri aynı tanımlayıcı altında yayımlanır: `dotnet-sdk` . Belirli bir SDK sürümü kanal belirtilerek yüklenebilir. SDK ilgili çalışma zamanını içerir. Aşağıdaki tabloda kanallar listelenmektedir:

| .NET sürümü | Paket veya kanala yapışma  |
|--------------|--------------------------|
| 5.0          | `5.0` veya `latest/stable` |
| 3,1 (LTS)    | `3.1` veya `lts/stable`    |
| 2,1 (LTS)    | `2.1`                    |

`snap install`.NET SDK Snap paketini yüklemek için komutunu kullanın. `--channel`Hangi sürümün yükleneceğini belirtmek için parametresini kullanın. Bu parametre atlanırsa, `latest/stable` kullanılır. Bu örnekte, `5.0` belirtilir:

```bash
sudo snap install dotnet-sdk --classic --channel=5.0
```

Sonra, `dotnet` `snap alias` komutunu komutuyla sisteme kaydedin:

```bash
sudo snap alias dotnet-sdk.dotnet dotnet
```

Bu komut şöyle biçimlendirilir: `sudo snap alias {package}.{command} {alias}` . İstediğiniz `{alias}` adı seçebilirsiniz. Örneğin, komutunu Snap tarafından yüklenen belirli sürümden sonra yazabilirsiniz `sudo snap alias dotnet-sdk.dotnet dotnet50` . Komutunu kullandığınızda `dotnet50` , .net 'in bu belirli sürümünü çağıracaksınız. Ancak farklı bir diğer ad seçilmesi, bir komutun kullanılmasını bekledikleri için birçok öğretici ve örnek ile uyumsuzdur `dotnet` .

## <a name="install-the-runtime"></a>Çalışma zamanını yükler

.NET çalışma zamanı için Yaslama paketleri kendi paket tanımlayıcılarıyla yayımlanır. Aşağıdaki tabloda paket tanımlayıcıları listelenmektedir:

| .NET sürümü      | Yaslama paketi        |
|-------------------|---------------------|
| 5.0               | `dotnet-runtime-50` |
| 3,1 (LTS)         | `dotnet-runtime-31` |
| 3.0               | `dotnet-runtime-30` |
| 2,2               | `dotnet-runtime-22` |
| 2,1 (LTS)         | `dotnet-runtime-21` |

`snap install`.NET çalışma zamanı Snap paketini yüklemek için komutunu kullanın. Bu örnekte, .NET 5,0 yüklüdür:

```bash
sudo snap install dotnet-runtime-50 --classic
```

Sonra, `dotnet` `snap alias` komutunu komutuyla sisteme kaydedin:

```bash
sudo snap alias dotnet-runtime-50.dotnet dotnet
```

Komut şöyle biçimlendirilir: `sudo snap alias {package}.{command} {alias}` . İstediğiniz `{alias}` adı seçebilirsiniz. Örneğin, komutunu Snap tarafından yüklenen belirli sürümden sonra yazabilirsiniz `sudo snap alias dotnet-runtime-50.dotnet dotnet50` . Komutunu kullandığınızda `dotnet50` , .net 'in belirli bir sürümünü çağıracaksınız. Ancak farklı bir diğer ad seçmek bir komutun kullanılabilir olmasını bekledikleri için birçok öğretici ve örnek ile uyumsuzdur `dotnet` .

## <a name="export-the-install-location"></a>Yüklemesi konumunu dışarı aktarma

`DOTNET_ROOT`Ortam değişkeni, genellikle .net 'in nerede yükleneceğini belirlemede araçlar tarafından kullanılır. .NET, Snap aracılığıyla yüklendiğinde bu ortam değişkeni yapılandırılmaz. Profilinizde *DOTNET_ROOT* ortam değişkenini yapılandırmalısınız. Yaslama yolu şu biçimi kullanır: `/snap/{package}/current` . Örneğin, yaslama 'yı yüklediyseniz `dotnet-sdk` , ortam değişkenini .NET bulunduğu yere ayarlamak için aşağıdaki komutu kullanın:

```bash
export DOTNET_ROOT=/snap/dotnet-sdk/current
```

> [!TIP]
> Yukarıdaki `export` komut yalnızca çalıştırıldığı terminal oturumu için ortam değişkenini ayarlar.
>
> Komutları kalıcı olarak eklemek için kabuk profilinizi düzenleyebilirsiniz. Linux için kullanılabilen birçok farklı kabuk vardır ve her birinin farklı bir profili vardır. Örnek:
>
> - **Bash kabuğu**: *~/.bash_profile*, *~/,bashrc*
> - **Korn kabuğu**: *~/,KSHRC* veya *. Profile*
> - **Z kabuğu**: *~/,zshrc* veya *. zprofile*
>
> Kabuğunuz için uygun kaynak dosyayı düzenleyin ve ekleyin `export DOTNET_ROOT=/snap/dotnet-sdk/current` .

## <a name="tlsssl-certificate-errors"></a>TLS/SSL sertifikası hataları

.NET yaslama aracılığıyla yüklendiğinde, bazı bilgisayarlarda .NET TLS/SSL sertifikaları bulunamamış olabilir ve şu sırada bir hata alabilirsiniz `restore` :

```bash
Processing post-creation actions...
Running 'dotnet restore' on /home/myhome/test/test.csproj...
  Restoring packages for /home/myhome/test/test.csproj...
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error : Unable to load the service index for source https://api.nuget.org/v3/index.json. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The SSL connection could not be established, see inner exception. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The remote certificate is invalid according to the validation procedure. [/home/myhome/test/test.csproj]
```

Bu sorunu çözmek için birkaç ortam değişkeni ayarlayın:

```bash
export SSL_CERT_FILE=[path-to-certificate-file]
export SSL_CERT_DIR=/dev/null
```

Sertifika konumu, bir konuma göre farklılık gösterecektir. İşte sorun yaşanmış olan yemekler için Konumlar şunlardır.

| Dağıtım | Konum                                            |
|--------------|-----------------------------------------------------|
| **Fedora**   | `/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem` |
| **OpenSUSE** | `/etc/ssl/ca-bundle.pem`                            |
| **Solus**    | `/etc/ssl/certs/ca-certificates.crt`                |

## <a name="next-steps"></a>Sonraki adımlar

- [.NET CLı için sekme tamamlamayı etkinleştirme](../tools/enable-tab-autocomplete.md)
- [Öğretici: Visual Studio Code kullanarak .NET SDK ile bir konsol uygulaması oluşturma](../tutorials/with-visual-studio-code.md)
