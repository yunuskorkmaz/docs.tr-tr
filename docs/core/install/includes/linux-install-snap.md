---
ms.openlocfilehash: 83808f2f3a05333ed5d9e3809cbc2fd6e230d02c
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031787"
---

[.NET Core, Snap Store 'da bulunabilir.](https://snapcraft.io/dotnet-sdk)

Bir snap, bir uygulamanın bir paketidir ve farklı Linux dağıtımları arasında değişiklik yapılmaksızın, onun bağımlılıklarıdır. Yaslanabilirlik, ek depodan bulunabilir ve yüklenebilir. Yaslama hakkında daha fazla bilgi için bkz. [yaslama ile çalışmaya](https://snapcraft.io/docs/getting-started)başlama.

Yalnızca .NET Core 'un desteklenen sürümleri yaslama aracılığıyla kullanılabilir.

### <a name="install-the-sdk"></a>SDK Yükleme

.NET SDK için Yaslama paketleri aynı tanımlayıcı altında yayımlanır: `dotnet-sdk` . Belirli bir SDK sürümü kanal belirtilerek yüklenebilir. SDK ilgili çalışma zamanını içerir. Aşağıdaki tabloda kanallar listelenmektedir:

| .NET sürümü | Yaslama paketi             |
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

Bu komut şöyle biçimlendirilir: `sudo snap alias {package}.{command} {alias}` . İstediğiniz `{alias}` adı seçebilirsiniz. Örneğin, komutunu Snap tarafından yüklenen belirli sürümden sonra yazabilirsiniz `sudo snap alias dotnet-sdk.dotnet dotnet50` . Komutunu kullandığınızda `dotnet50` , .net 'in bu belirli sürümünü çağıracaksınız. Ancak bu, bir komutun kullanılabilir olmasını bekledikleri için çoğu öğretici ve örneklerle uyumsuzdur `dotnet` .

### <a name="install-the-runtime"></a>Çalışma zamanını yükler

.NET Core çalışma zamanı için yapışma paketleri her biri kendi paket tanımlayıcılarıyla yayımlanır. Aşağıdaki tabloda paket tanımlayıcıları listelenmektedir:

| .NET sürümü      | Yaslama paketi        |
|-------------------|---------------------|
| 5.0               | `dotnet-runtime-50` |
| 3,1 (LTS)         | `dotnet-runtime-31` |
| 3,0               | `dotnet-runtime-30` |
| 2.2               | `dotnet-runtime-22` |
| 2,1 (LTS)         | `dotnet-runtime-21` |

`snap install`.NET çalışma zamanı Snap paketini yüklemek için komutunu kullanın. Bu örnekte, .NET 5,0 yüklüdür:

```bash
sudo snap install dotnet-runtime-50 --classic
```

Sonra, `dotnet` `snap alias` komutunu komutuyla sisteme kaydedin:

```bash
sudo snap alias dotnet-runtime-50.dotnet dotnet
```

Bu komut şöyle biçimlendirilir: `sudo snap alias {package}.{command} {alias}` . İstediğiniz `{alias}` adı seçebilirsiniz. Örneğin, komutunu Snap tarafından yüklenen belirli sürümden sonra yazabilirsiniz `sudo snap alias dotnet-runtime-50.dotnet dotnet50` . Komutunu kullandığınızda `dotnet50` , .net 'in bu belirli sürümünü çağıracaksınız. Ancak bu, bir komutun kullanılabilir olmasını bekledikleri için çoğu öğretici ve örneklerle uyumsuzdur `dotnet` .

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

Bu sorunu çözmek için birkaç ortam değişkeni ayarlayın:

```bash
export SSL_CERT_FILE=[path-to-certificate-file]
export SSL_CERT_DIR=/dev/null
```

Sertifika konumu, bir konuma göre farklılık gösterecektir. İşte bu, sorunla karşılaştiğimiz, distro 'lara için konumlar.

* Fedora `/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem`
* OpenSUSE `/etc/ssl/ca-bundle.pem`
* Solus- `/etc/ssl/certs/ca-certificates.crt`
