---
title: dotnet-install scripts
description: .NET Core SDK'yı ve paylaşılan çalışma süresini yüklemek için dotnet yükleme komut dosyaları hakkında bilgi edinin.
ms.date: 01/23/2020
ms.openlocfilehash: 591413a17db577560bd0324995066c8ea7a35895
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463671"
---
# <a name="dotnet-install-scripts-reference"></a>dotnet yükleme komut dosyaları başvurusu

## <a name="name"></a>Adı

`dotnet-install.ps1` | `dotnet-install.sh`- .NET Core SDK'yı ve paylaşılan çalışma süresini yüklemek için kullanılan komut dosyası.

## <a name="synopsis"></a>Özet

Windows:

```powershell
dotnet-install.ps1 [-Architecture <ARCHITECTURE>] [-AzureFeed]
    [-Channel <CHANNEL>] [-DryRun] [-FeedCredential]
    [-InstallDir <DIRECTORY>] [-JSonFile <JSONFILE>]
    [-NoCdn] [-NoPath] [-ProxyAddress]
    [-ProxyUseDefaultCredentials] [-Runtime <RUNTIME>]
    [-SkipNonVersionedFiles] [-UncachedFeed] [-Verbose]
    [-Version <VERSION>]

dotnet-install.ps1 -Help
```

Linux/macO'lar:

```bash
dotnet-install.sh  [--architecture <ARCHITECTURE>] [--azure-feed]
    [--channel <CHANNEL>] [--dry-run] [--feed-credential]
    [--install-dir <DIRECTORY>] [--jsonfile <JSONFILE>]
    [--no-cdn] [--no-path] [--runtime <RUNTIME>] [--runtime-id <RID>]
    [--skip-non-versioned-files] [--uncached-feed] [--verbose]
    [--version <VERSION>]

dotnet-install.sh --help
```

## <a name="description"></a>Açıklama

`dotnet-install` Komut dosyaları,.NET Core CLI ve paylaşılan çalışma süresini içeren .NET Core SDK'nın yönetici olmayan yüklemesini gerçekleştirmek için kullanılır.

Komut dosyalarının kararlı sürümünü kullanmanızı öneririz:

- Bash (Linux/macOS):<https://dot.net/v1/dotnet-install.sh>
- PowerShell (Windows):<https://dot.net/v1/dotnet-install.ps1>

Bu komut dosyalarının temel kullanışlılığı otomasyon senaryoları ve yönetici olmayan yüklemelerdedir. İki komut dosyası vardır: biri Windows'da çalışan bir PowerShell komut dosyası, diğeri ise Linux/macOS üzerinde çalışan bir bash komut dosyasıdır. Her iki komut dosyası da aynı davranışa sahiptir. Bash komut dosyası da PowerShell anahtarları okur, böylece Linux / macOS sistemlerinde komut dosyası ile PowerShell anahtarları kullanabilirsiniz.

Yükleme komut dosyaları, Zip/tarball dosyasını CLI yapılarından indirir ve varsayılan konuma veya tarafından `-InstallDir|--install-dir`belirtilen bir konuma yüklemeye devam eder. Varsayılan olarak, yükleme komut dosyaları SDK'yı karşıdan yükler ve yükler. Yalnızca paylaşılan çalışma süresini elde etmek istiyorsanız, bağımsız değişkeni belirtin. `-Runtime|--runtime`

Varsayılan olarak, komut dosyası yükleme konumunu geçerli oturumun $PATH ekler. `-NoPath|--no-path` Bağımsız değişkeni belirterek bu varsayılan davranışı geçersiz kılın.

Komut dosyasını çalıştırmadan önce, gerekli [bağımlılıkları](../install/dependencies.md)yükleyin.

Bağımsız değişkeni `-Version|--version` kullanarak belirli bir sürümü yükleyebilirsiniz. Sürüm üç bölümlü bir sürüm olarak belirtilmelidir `2.1.0`(örneğin, ). Sağlanmadıysa, `latest` sürümü kullanır.

## <a name="options"></a>Seçenekler

- **`-Architecture|--architecture <ARCHITECTURE>`**

  .NET Çekirdek ikililerinin mimarisini yüklemek. Olası değerler `<auto>` `amd64`, `x64` `x86`, `arm64`, `arm`, , ve . Varsayılan değer, `<auto>`şu anda çalışan işletim sistemi mimarisini temsil eden değerdir.

- **`-AzureFeed|--azure-feed`**

  Azure akışının URL'sini yükleyiciye belirtir. Bu değeri değiştirmemenizi tavsiye ettik. Varsayılan değer: `https://dotnetcli.azureedge.net/dotnet`.

- **`-Channel|--channel <CHANNEL>`**

  Yükleme için kaynak kanalı belirtir. Olası değerler şunlardır:

  - `Current`- En güncel sürüm.
  - `LTS`- Uzun Vadeli Destek kanalı (en güncel desteklenen sürüm).
  - Belirli bir sürümü temsil eden X.Y formatında `2.1` iki `3.0`parçalı sürüm (örneğin, veya).
  - Şube adı: `release/3.1.1xx` örneğin, `master` ya da (gece sürümleri için). Önizleme kanalından bir sürüm yüklemek için bu seçeneği kullanın. [Yükleyiciler ve İkili'lerde](https://github.com/dotnet/core-sdk#installers-and-binaries)listelenen kanalın adını kullanın.

  Varsayılan değer: `LTS`. .NET destek kanalları hakkında daha fazla bilgi için [.NET Destek Politikası](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sayfasına bakın.

- **`-DryRun|--dry-run`**

  Ayarlanırsa, komut dosyası yüklemeyi gerçekleştirmez. Bunun yerine, .NET Core CLI'nin istenen sürümünü tutarlı bir şekilde yüklemek için hangi komut satırını kullanacağını görüntüler. Örneğin, sürüm `latest`belirtirseniz, bu komutun bir yapı komut dosyasında deterministically kullanılabilmesi için belirli sürümile bir bağlantı görüntüler. Ayrıca, kendiniz yüklemeyi veya indirmeyi tercih ederseniz ikilinin konumunu da görüntüler.

- **`-FeedCredential|--feed-credential`**

  Azure akışına eklemek için sorgu dizesi olarak kullanılır. Genel olmayan blob depolama hesaplarını kullanmak için URL'yi değiştirmenize olanak tanır.

- **`-Help|--help`**

  Komut dosyası için yardım yazdırır.

- **`-InstallDir|--install-dir <DIRECTORY>`**

  Yükleme yolunu belirtir. Dizin yoksa oluşturulur. Varsayılan değer *%LocalAppData%\Microsoft\dotnet'tir.* İkili doğrudan bu dizine yerleştirilir.

- **`-JSonFile|--jsonfile <JSONFILE>`**

  SDK sürümünü belirlemek için kullanılacak [global.json](global-json.md) dosyasına giden bir yol belirtir. *global.json* dosyasının bir değeri `sdk:version`olmalıdır.

- **`-NoCdn|--no-cdn`**

  [Azure İçerik Teslim Ağı'ndan (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) indirmeyi devre dışı bırakıp doğrudan önyüklemesiz akışı kullanır.

- **`-NoPath|--no-path`**

  Ayarlanırsa, yükleme klasörü geçerli oturumun yoluna dışa aktarılmaz. Varsayılan olarak, komut dosyası PATH'i değiştirir ve bu da .NET Core CLI'yi yükledikten hemen sonra kullanılabilir hale getirir.

- **`-ProxyAddress`**

  Ayarlanırsa, yükleyici web isteklerini yaparken proxy'yi kullanır. (Yalnızca Windows için geçerlidir.)

- **`ProxyUseDefaultCredentials`**

  Ayarlanırsa, yükleyici proxy adresini kullanırken geçerli kullanıcının kimlik bilgilerini kullanır. (Yalnızca Windows için geçerlidir.)

- **`-Runtime|--runtime <RUNTIME>`**

  SDK'nın tamamını değil, sadece paylaşılan çalışma süresini yükler. Olası değerler şunlardır:

  - `dotnet`- `Microsoft.NETCore.App` paylaşılan çalışma süresi.
  - `aspnetcore`- `Microsoft.AspNetCore.App` paylaşılan çalışma süresi.
  - `windowsdesktop`- `Microsoft.WindowsDesktop.App` paylaşılan çalışma süresi.

- **`--runtime-id <RID>`**

  Araçların yüklendiği [çalışma zamanı tanımlayıcısını](../rid-catalog.md) belirtir. Taşınabilir `linux-x64` Linux için kullanın. (Yalnızca Linux/macOS için geçerlidir.)

- **`-SharedRuntime|--shared-runtime`**

  > [!NOTE]
  > Bu parametre eskidir ve komut dosyasının gelecekteki bir sürümünde kaldırılabilir. Önerilen alternatif `-Runtime|--runtime` seçenektir.

  SDK'nın tamamını değil, paylaşılan çalışma zamanı bitlerini yükler. Bu seçenek belirtmeye `-Runtime|--runtime dotnet`eşdeğerdir.

- **`-SkipNonVersionedFiles|--skip-non-versioned-files`**

  *Dotnet.exe*gibi sürümdışı dosyaları yüklemeyi atlar, zaten varsa.

- **`-UncachedFeed|--uncached-feed`**

  Bu yükleyici tarafından kullanılan cached beslemesi için URL'yi değiştirmenize olanak sağlar. Bu değeri değiştirmemenizi tavsiye ettik.

- **`-Verbose|--verbose`**

  Tanılama bilgilerini görüntüler.

- **`-Version|--version <VERSION>`**

  Belirli bir yapı sürümünü temsil eder. Olası değerler şunlardır:

  - `latest`- Kanalüzerinde son yapı `-Channel` (seçeneği ile birlikte kullanılır).
  - `coherent`- Kanalüzerinde son tutarlı yapı; en son kararlı paket birleşimini `-Channel` kullanır (Şube adı seçenekleriyle kullanılır).
  - X.Y.Z formatında belirli bir yapı sürümünü temsil eden üç parçalı sürüm; seçeneğin yerini `-Channel` adakalır. Örneğin: `2.0.0-preview2-006120`.

  Belirtilmemişse, `-Version` `latest`varsayılan olarak .

## <a name="examples"></a>Örnekler

- En son uzun vadeli desteklenen (LTS) sürümünü varsayılan konuma yükleyin:

  Windows:

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  macOS/Linux:

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- En son sürümü 3.1 kanalından belirtilen konuma yükleyin:

  Windows:

  ```powershell
  ./dotnet-install.ps1 -Channel 3.1 -InstallDir C:\cli
  ```

  macOS/Linux:

  ```bash
  ./dotnet-install.sh --channel 3.1 --install-dir ~/cli
  ```

- Paylaşılan çalışma süresinin 3.0.0 sürümünü yükleyin:

  Windows:

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 3.0.0
  ```

  macOS/Linux:

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 3.0.0
  ```

- Komut dosyası edinin ve bir şirket proxy arkasında 2.1.2 sürümünü yükleyin (yalnızca Windows):

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- Komut dosyası edinin ve .NET Core CLI tek satırlık örnekler yükleyin:

  Windows:

  ```powershell
  # Run a separate PowerShell process because the script calls exit, so it will end the current PowerShell session.
  &powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  macOS/Linux:

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core bültenleri](https://github.com/dotnet/core/releases)
- [.NET Çekirdek Çalışma Süresi ve SDK indirme arşivi](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
