---
title: dotnet-install scripts
description: .NET Core CLI araçlarını ve paylaşılan çalışma zamanını yüklemek için DotNet-install betikleri hakkında bilgi edinin.
ms.date: 01/16/2019
ms.openlocfilehash: ed1a3341e678b405ae4aca35e3b49ada89eb069a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253906"
---
# <a name="dotnet-install-scripts-reference"></a>DotNet-betiklerin başvurusunu yüklemeyi

## <a name="name"></a>Ad

`dotnet-install.ps1` | `dotnet-install.sh`-.NET Core CLI araçları ve paylaşılan çalışma zamanını yüklemek için kullanılan betik.

## <a name="synopsis"></a>Özeti

Windows:

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-Runtime] [-DryRun] [-NoPath] [-Verbose] [-AzureFeed] [-UncachedFeed] [-NoCdn] [-FeedCredential] [-ProxyAddress] [-ProxyUseDefaultCredentials] [-SkipNonVersionedFiles] [-Help]`

macOS/Linux:

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--runtime] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--uncached-feed] [--no-cdn] [--feed-credential] [--runtime-id] [--skip-non-versioned-files] [--help]`

## <a name="description"></a>Açıklama

`dotnet-install` Betikler, .NET Core CLI araçlarını ve paylaşılan çalışma zamanını içeren .NET Core SDK yönetici olmayan yüklemesini gerçekleştirmek için kullanılır.

[.NET Core ana web sitesinde](https://dot.net)barındırılan kararlı sürümü kullanmanızı öneririz. Betiklerin doğrudan yolları şunlardır:

- <https://dot.net/v1/dotnet-install.sh>(Bash, UNIX)
- <https://dot.net/v1/dotnet-install.ps1>(PowerShell, Windows)

Bu betiklerin temel kullanışlılığı Otomasyon senaryolarında ve yönetici olmayan yüklemelerde bulunur. İki komut dosyası vardır: biri Windows üzerinde çalışan bir PowerShell betiğtir ve diğeri de Linux/macOS üzerinde çalışan bir bash komut dosyasıdır. Her iki komut dosyası da aynı davranışa sahiptir. Bash betiği Ayrıca PowerShell anahtarlarını okur, bu sayede PowerShell anahtarlarını Linux/macOS sistemlerinde betiği ile birlikte kullanabilirsiniz.

Yükleme betikleri, ZIP/tarbol dosyasını CLı derleme bırakmalarından indirir ve varsayılan konuma ya da tarafından `-InstallDir|--install-dir`belirtilen bir konuma yüklemeye devam edebilir. Varsayılan olarak, yükleme betikleri SDK 'Yı indirir ve yükler. Yalnızca paylaşılan çalışma zamanını elde etmek istiyorsanız, `--runtime` bağımsız değişkenini belirtin.

Komut dosyası varsayılan olarak, geçerli oturum için $PATH yüklemesi konumunu ekler. `--no-path` Bağımsız değişkenini belirterek bu varsayılan davranışı geçersiz kılın.

Betiği çalıştırmadan önce gerekli [bağımlılıkları](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)yükler.

`--version` Bağımsız değişkenini kullanarak belirli bir sürümü yükleyebilirsiniz. Sürüm üç bölümlü bir sürüm olarak belirtilmelidir (örneğin, 1.0.0-13232). Sağlanmazsa, `latest` sürümünü kullanır.

## <a name="options"></a>Seçenekler

- **`-Channel <CHANNEL>`**

  Yükleme için kaynak kanalını belirtir. Olası değerler şunlardır:

  - `Current`-En güncel sürüm.
  - `LTS`-Uzun süreli destek kanalı (desteklenen en güncel sürüm).
  - Belirli bir yayını temsil eden X. Y biçimindeki iki bölümlü sürüm (örneğin, `2.0` veya `1.0`).
  - Dal adı. Örneğin `release/2.0.0` `master` ,, veya (gecelik yayınlar için). `release/2.0.0-preview2`

  Varsayılan değer `LTS` şeklindedir. .NET destek kanalları hakkında daha fazla bilgi için bkz. [.net destek ilkesi](https://www.microsoft.com/net/platform/support-policy#dotnet-core) sayfası.

- **`-Version <VERSION>`**

  Belirli bir derleme sürümünü temsil eder. Olası değerler şunlardır:

  - `latest`-Kanalda en son derleme ( `-Channel` seçeneğiyle kullanılır).
  - `coherent`-Kanalda en son tutarlı derleme; en son kararlı paket birleşimini kullanır (dal adı `-Channel` seçenekleriyle kullanılır).
  - Belirli bir derleme sürümünü temsil eden X. Y. Z biçimindeki üç bölümden oluşan sürüm; `-Channel` seçeneğinin yerini alır. Örneğin: `2.0.0-preview2-006120`

  Belirtilmemişse, `-Version` varsayılan olarak `latest`olur.

- **`-InstallDir <DIRECTORY>`**

  Yükleme yolunu belirtir. Dizin yoksa oluşturulur. Varsayılan değer *%LocalAppData%\microsoft\dotnet*değeridir. İkili dosyalar doğrudan bu dizine yerleştirilir.

- **`-Architecture <ARCHITECTURE>`**

  Yüklenecek .NET Core ikililerinin mimarisi. Olası değerler şunlardır `<auto>` `amd64` ,,`x64`,, ve .`arm` `x86` `arm64` Varsayılan değer `<auto>`, çalışmakta olan işletim sistemi mimarisini temsil eder.

- **`-SharedRuntime`**

  > [!NOTE]
  > Bu parametre artık kullanılmıyor ve betiğin gelecekteki bir sürümünde kaldırılabilir. Önerilen alternatif `Runtime` , seçenektir.

  Tüm SDK 'Yı değil yalnızca paylaşılan çalışma zamanı bitlerini kurar. Bu, belirtmeye `-Runtime dotnet`eşdeğerdir.

- **`-Runtime <RUNTIME>`**

  Tüm SDK 'Yı değil yalnızca paylaşılan çalışma zamanını kurar. Olası değerler şunlardır:

  - `dotnet``Microsoft.NETCore.App` -paylaşılan çalışma zamanı.
  - `aspnetcore``Microsoft.AspNetCore.App` -paylaşılan çalışma zamanı.

- **`-DryRun`**

  Ayarlanırsa, betik yüklemeyi gerçekleştirmez. Bunun yerine, .NET Core CLI Şu anda istenen sürümünü tutarlı bir şekilde yüklemek için kullanılacak komut satırını görüntüler. Örneğin, sürümünü `latest`belirtirseniz, bu komutun bir yapı betiğine göre belirleyici olarak kullanılabilmesi için belirli bir sürümle birlikte bir bağlantı görüntüler. Ayrıca, kendiniz yüklemeyi veya indirmeyi tercih ediyorsanız ikilinin konumunu da görüntüler.

- **`-NoPath`**

  Ayarlanırsa, yükleme klasörü geçerli oturum için yola aktarılmaz. Varsayılan olarak, komut dosyası yolu değiştirir ve bu, CLı araçlarının yüklemeden hemen sonra kullanılabilmesini sağlar.

- **`-Verbose`**

  Tanılama bilgilerini görüntüler.

- **`-AzureFeed`**

  Yükleyicideki Azure akışına ait URL 'YI belirtir. Bu değeri değiştirmemenizi öneririz. Varsayılan değer `https://dotnetcli.azureedge.net/dotnet` şeklindedir.

- **`-UncachedFeed`**

  Bu yükleyici tarafından kullanılan önbelleğe alınmamış akışın URL 'sini değiştirmeye izin verir. Bu değeri değiştirmemenizi öneririz.

- **`-NoCdn`**

  [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) ile indirmeyi devre dışı bırakır ve önbelleğe alınmamış akışı doğrudan kullanır.

- **`-FeedCredential`**

  Azure akışına eklemek için sorgu dizesi olarak kullanılır. Bu, URL 'nin genel olmayan BLOB depolama hesaplarını kullanmak üzere değiştirilmesini sağlar.

- **`-ProxyAddress`**

  Ayarlanırsa, yükleyici Web istekleri yaparken proxy 'yi kullanır. (Yalnızca Windows için geçerlidir)

- **`ProxyUseDefaultCredentials`**

  Ayarlanırsa, yükleyici proxy adresini kullanırken geçerli kullanıcının kimlik bilgilerini kullanır. (Yalnızca Windows için geçerlidir)

- **`-SkipNonVersionedFiles`**

  Zaten varsa *DotNet. exe*gibi sürümlenmemiş dosyaları yüklemeyi atlar.

- **`-Help`**

  Betiğe yönelik yardım yazdırır.

## <a name="examples"></a>Örnekler

- En son uzun süreli desteklenen (LTS) sürümü varsayılan konuma yükler:

  Windows:

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  macOS/Linux:

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- 2,0 kanaldan en son sürümü belirtilen konuma yükler:

  Windows:

  ```powershell
  ./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli
  ```

  macOS/Linux:

  ```bash
  ./dotnet-install.sh --channel 2.0 --install-dir ~/cli
  ```

- Paylaşılan çalışma zamanının 1.1.0 sürümünü yükler:

  Windows:

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 1.1.0
  ```

  macOS/Linux:

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 1.1.0
  ```

- Bir kurumsal proxy 'nin arkasında betiği alma ve 2.1.2 'yi sürümünü yüklemeye (yalnızca Windows):

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- Tek bir Oluşturucu örnek .NET Core CLI betiği alın ve yüklemeyi yapın:

  Windows:

  ```powershell
  @powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  macOS/Linux:

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core yayınları](https://github.com/dotnet/core/releases)
- [.NET Core çalışma zamanı ve SDK indirme Arşivi](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
