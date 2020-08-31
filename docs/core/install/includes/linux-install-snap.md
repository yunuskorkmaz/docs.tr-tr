---
ms.openlocfilehash: 5e77b7bd73c09e061a94a29703cf5286814d1ebb
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602917"
---

[.NET Core, Snap Store 'da bulunabilir.](https://snapcraft.io/dotnet-sdk)

Bir snap, bir uygulamanın bir paketidir ve farklı Linux dağıtımları arasında değişiklik yapılmaksızın, onun bağımlılıklarıdır. Yaslanabilirlik, ek depodan bulunabilir ve yüklenebilir. Yaslama hakkında daha fazla bilgi için bkz. [yaslama ile çalışmaya](https://snapcraft.io/docs/getting-started)başlama.

Yalnızca .NET Core 'un desteklenen sürümleri yaslama aracılığıyla kullanılabilir.

### <a name="install-the-sdk"></a>SDK Yükleme

.NET Core SDK için Yaslama paketleri aynı tanımlayıcı altında yayımlanır: `dotnet-sdk` . Belirli bir SDK sürümü kanal belirtilerek yüklenebilir. SDK, birlikte yanıt verme çalışma zamanını içerir. Aşağıdaki tabloda kanallar listelenmektedir:

| .NET Core sürümü | Yaslama paketi             |
|-------------------|--------------------------|
| 3,1 (LTS)         | `3.1` veya `latest/stable` |
| 2,1 (LTS)         | `2.1`                    |
| .NET 5,0 Preview  | `5.0/beta`               |

`snap install`.NET Core SDK bir snap paketi yüklemek için komutunu kullanın. `--channel`Hangi sürümün yükleneceğini belirtmek için parametresini kullanın. Bu parametre atlanırsa, `latest/stable` kullanılır. Bu örnekte, `3.1` belirtilir:

```bash
sudo snap install dotnet-sdk --classic --channel=3.1
```

Sonra, `dotnet` `snap alias` komutunu komutuyla sisteme kaydedin:

```bash
sudo snap alias dotnet-sdk.dotnet dotnet
```

Bu komut şöyle biçimlendirilir: `sudo snap alias {package}.{command} {alias}` . İstediğiniz `{alias}` adı seçebilirsiniz. Örneğin, komutunu Snap tarafından yüklenen belirli sürümden sonra yazabilirsiniz `sudo snap alias dotnet-sdk.dotnet dotnet31` . Komutunu kullandığınızda `dotnet31` , .net 'in bu belirli sürümünü çağıracaksınız. Ancak bu, bir komutun kullanılabilir olmasını bekledikleri için çoğu öğretici ve örneklerle uyumsuzdur `dotnet` .

### <a name="install-the-runtime"></a>Çalışma zamanını yükler

.NET Core çalışma zamanı için yapışma paketleri her biri kendi paket tanımlayıcılarıyla yayımlanır. Aşağıdaki tabloda paket tanımlayıcıları listelenmektedir:

| .NET Core sürümü | Yaslama paketi        |
|-------------------|---------------------|
| 3,1 (LTS)         | `dotnet-runtime-31` |
| 3.0               | `dotnet-runtime-30` |
| 2.2               | `dotnet-runtime-22` |
| 2,1 (LTS)         | `dotnet-runtime-21` |

`snap install`.NET Core çalışma zamanı ek paketi yüklemek için komutunu kullanın. Bu örnekte, .NET Core 3,1 yüklüdür:

```bash
sudo snap install dotnet-runtime-31 --classic
```

Sonra, `dotnet` `snap alias` komutunu komutuyla sisteme kaydedin:

```bash
sudo snap alias dotnet-runtime-31.dotnet dotnet
```

Bu komut şöyle biçimlendirilir: `sudo snap alias {package}.{command} {alias}` . İstediğiniz `{alias}` adı seçebilirsiniz. Örneğin, komutunu Snap tarafından yüklenen belirli sürümden sonra yazabilirsiniz `sudo snap alias dotnet-runtime-31.dotnet dotnet31` . Komutunu kullandığınızda `dotnet31` , .net 'in bu belirli sürümünü çağıracaksınız. Ancak bu, bir komutun kullanılabilir olmasını bekledikleri için çoğu öğretici ve örneklerle uyumsuzdur `dotnet` .

### <a name="ssl-certificate-errors"></a>SSL sertifikası hataları

.NET, Snap aracılığıyla yüklendiğinde, bazı bilgisayarlarda .NET SSL sertifikaları bulunamamış olabilir ve aşağıdakiler sırasında aşağıdakine benzer bir hata alabilirsiniz `restore` :

```bash
Processing post-creation actions...
Running 'dotnet restore' on /home/myhome/test/test.csproj...
  Restoring packages for /home/myhome/test/test.csproj...
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error : Unable to load the service index for source https://api.nuget.org/v3/index.json. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The SSL connection could not be established, see inner exception. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The remote certificate is invalid according to the validation procedure. [/home/myhome/test/test.csproj]
```

Bu sorunu çözmek için birkaç ortamınızı değişkeni ayarlayın:

```bash
export SSL_CERT_FILE=[path-to-certificate-file]
export SSL_CERT_DIR=/dev/null
```

Sertifika konumu, bir konuma göre farklılık gösterecektir. İşte bu, sorunla karşılaştiğimiz, distro 'lara için konumlar.

* Fedora `/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem`
* OpenSUSE `/etc/ssl/ca-bundle.pem`
* Solus- `/etc/ssl/certs/ca-certificates.crt`
