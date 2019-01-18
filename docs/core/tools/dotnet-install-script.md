---
title: DotNet yükleme betikleri
description: .NET Core CLI araçları ve paylaşılan çalışma zamanı'nı yüklemek için dotnet-yükleme betikleri hakkında bilgi edinin.
ms.date: 01/16/2019
ms.openlocfilehash: 5b266d484aae482d79674660417a834f03d53e4c
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362837"
---
# <a name="dotnet-install-scripts-reference"></a>DotNet yükleme komut başvurusu

## <a name="name"></a>Ad

`dotnet-install.ps1` | `dotnet-install.sh` -.NET Core CLI araçları ve paylaşılan çalışma zamanı'nı yüklemek için kullanılan komut dosyası.

## <a name="synopsis"></a>Synopsis

Windows:

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-Runtime] [-DryRun] [-NoPath] [-Verbose] [-AzureFeed] [-UncachedFeed] [-NoCdn] [-FeedCredential] [-ProxyAddress] [-ProxyUseDefaultCredentials] [-SkipNonVersionedFiles] [-Help]`

macOS/Linux:

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--runtime] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--uncached-feed] [--no-cdn] [--feed-credential] [--runtime-id] [--skip-non-versioned-files] [--help]`

## <a name="description"></a>Açıklama

`dotnet-install` Betikleri, .NET Core CLI araçları ve paylaşılan çalışma zamanı içeren .NET Core SDK'sı yönetici olmayan bir yüklemesini gerçekleştirmek için kullanılır.

Üzerinde barındırılan kararlı bir sürüm kullanmanızı öneririz [.NET Core ana Web sitesi](https://dot.net). Komut dosyalarını doğrudan yolları şunlardır:

* <https://dot.net/v1/dotnet-install.sh> (bash, UNIX)
* <https://dot.net/v1/dotnet-install.ps1> (Powershell, Windows)

Bu komut dosyaları ana kullanışlılığını Otomasyon senaryoları ve yönetici olmayan yüklemeleri kullanılabilir. İki betik vardır: bir Windows üzerinde çalışan bir PowerShell Betiği ve diğer Linux/Macos'ta çalışır bir bash komut dosyasıdır. Her iki komut dosyaları aynı davranışa sahip. Linux/macOS sistemlerde betiğiyle PowerShell anahtarları kullanabilmeniz için bash betiğini de PowerShell anahtarları okur.

Yükleme betikleri CLI yapı bırakma öğelerini ZIP/tarball dosyasını indirin ve varsayılan konumda veya tarafından belirtilen bir konumda yükleme işlemine devam `-InstallDir|--install-dir`. Varsayılan olarak, yükleme betikleri SDK'sını indirin ve yükleyin. Yalnızca paylaşılan çalışma zamanı elde etmek istiyorsanız, belirtin `--shared-runtime` bağımsız değişken.

Varsayılan olarak, betik geçerli oturum için $PATH için yükleme konumu ekler. Bu varsayılan davranışı geçersiz kılma belirterek `--no-path` bağımsız değişken.

Betiği çalıştırmadan önce gerekli yükleme [bağımlılıkları](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).

Belirli bir sürümünü kullanarak bir yükleyebilirsiniz `--version` bağımsız değişken. Sürüm, üç bölümden sürümü (örneğin, 1.0.0-13232) belirtilmelidir. Sağlanmazsa, kullandığı `latest` sürümü.

## <a name="options"></a>Seçenekler

* **`-Channel <CHANNEL>`**

  Yükleme için kaynak kanalı belirtir. Olası değerler şunlardır:

  * `Current` -En son sürüm.
  * `LTS` -Uzun süreli destek kanalı (en son desteklenen sürüm).
  * İki parçalı sürümü belirli bir yayınını temsil eden X.Y biçiminde (örneğin, `2.0` veya `1.0`).
  * Dal adı. Örneğin, `release/2.0.0`, `release/2.0.0-preview2`, veya `master` (için gecelik sürümleri için).

  Varsayılan değer `LTS` şeklindedir. .NET Destek kanalları hakkında daha fazla bilgi için bkz. [.NET desteği İlkesi](https://www.microsoft.com/net/platform/support-policy#dotnet-core) sayfası.

* **`-Version <VERSION>`**

  Belirli bir yapı sürümünü temsil eder. Olası değerler şunlardır:

  * `latest` -Kanal en son derleme (ile kullanılan `-Channel` seçeneği).
  * `coherent` -Tutarlı yapıyı kanalındaki son; en son kararlı paket kullanır (Dal adı ile kullanılan `-Channel` seçenekleri).
  * Üç bölümlü sürüm X.Y.Z biçiminde temsil eden belirli bir yapı sürümü; yerine geçen `-Channel` seçeneği. Örneğin: `2.0.0-preview2-006120`

  Belirtilmezse, `-Version` varsayılan olarak `latest`.

* **`-InstallDir <DIRECTORY>`**

  Yükleme yolunu belirtir. Dizin yoksa oluşturulur. Varsayılan değer *%LocalAppData%\Microsoft\dotnet*. İkili dosyaları, doğrudan bu dizine yerleştirilir.

* **`-Architecture <ARCHITECTURE>`**

  .NET Core ikili dosyaları yüklemek için Mimari. Olası değerler `<auto>`, `amd64`, `x64`, `x86`, `arm64`, ve `arm`. Varsayılan değer `<auto>`, şu anda çalışan işletim sistemi mimarisi temsil eder.

* **`-SharedRuntime`**

  > [!NOTE]
  > Bu parametre kullanılmıyor ve betik gelecek bir sürümünde kaldırılabilir. Önerilen alternatif `Runtime` seçeneği.

  Tüm SDK yalnızca paylaşılan çalışma zamanı BITS yükler. Bu belirtmeye eşdeğerdir `-Runtime dotnet`.

* **`-Runtime <RUNTIME>`**

  Yalnızca paylaşılan çalışma zamanı, tüm SDK yükler. Olası değerler şunlardır:

  * `dotnet` - `Microsoft.NETCore.App` paylaşılan çalışma zamanı.
  * `aspnetcore` - `Microsoft.AspNetCore.App` paylaşılan çalışma zamanı.

* **`-DryRun`**

  Ayarlanırsa, komut dosyası yükleme gerçekleştiremiyor varsa. Bunun yerine, .NET Core CLI'ın şu anda istenen sürüm tutarlı bir şekilde yüklemek için kullanılacak hangi komut satırı görüntüler. Örneğin, sürüm belirtirseniz `latest`, böylece bu komut, bir derleme betikte belirleyici kullanılabilir belirli bir sürümünü içeren bir bağlantı gösterir. Yüklemek veya kendiniz indirmek isterseniz de ikili dosyanın konumunu görüntüler.

* **`-NoPath`**

  Kümesi, yükleme klasörünün yolu geçerli oturum için veriliyorsa değil. Varsayılan olarak, komut dosyası CLI araçları yüklendikten sonra hemen kullanılabilmesini YOLUNU değiştirir.

* **`-Verbose`**

  Tanılama bilgilerini görüntüler.

* **`-AzureFeed`**

  Yükleyici için akış URL'sini Azure belirtir. Bu değer değiştirmemenizi öneririz. Varsayılan değer `https://dotnetcli.azureedge.net/dotnet` şeklindedir.

* **`-UncachedFeed`**

  Bu yükleyici tarafından kullanılan önbelleğe alınmamış akış URL'sini değiştirilmesine izin verir. Bu değer değiştirmemenizi öneririz.

* **`-NoCdn`**

  İçinden indirme devre dışı bırakır [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) ve önbelleğe alınmamış akışı doğrudan kullanır.

* **`-FeedCredential`**

  Akış Azure'a eklenecek sorgu dizesi olarak kullanılır. Genel olmayan blob depolama hesaplarını kullanmak için URL'nin değiştirilmesini sağlar.

* **`-ProxyAddress`**

  Kümesi, yükleyici web istekleri yaparken proxy kullanıyorsa. (Yalnızca Windows için geçerlidir)

* **`ProxyUseDefaultCredentials`**

  Proxy adresi kullanılırken geçerli kullanıcının kimlik bilgilerini ayarlama, yükleyici kullanıyorsa. (Yalnızca Windows için geçerlidir)

* **`-SkipNonVersionedFiles`**

  Sürüm bilgisi olmayan dosyaları gibi yükleme atlar *dotnet.exe*, zaten mevcut.

* **`-Help`**

  Komut için Yardım yazdırır.

## <a name="examples"></a>Örnekler

* Desteklenen en son uzun vadeli (LTS) sürüm varsayılan konuma yükleyin:

  Windows:

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  macOS/Linux:

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

* En son sürümü 2.0 kanaldan belirtilen konuma yükleyin:

  Windows:

  ```powershell
  ./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli
  ```

  macOS/Linux:

  ```bash
  ./dotnet-install.sh --channel 2.0 --install-dir ~/cli
  ```

* Paylaşılan çalışma zamanı yükleme 1.1.0 sürümü:

  Windows:

  ```powershell
  ./dotnet-install.ps1 -SharedRuntime -Version 1.1.0
  ```

  macOS/Linux:

  ```bash
  ./dotnet-install.sh --shared-runtime --version 1.1.0
  ```

* Betiği almak ve 2.1.2'yi yükleyin (yalnızca Windows) kurumsal bir proxy'nin arkasında sürümü:

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

* Betiği almak ve .NET Core CLI one-liner örnekleri yükleyin:

  Windows:

  ```powershell
  @powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -useb 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  macOS/Linux:

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a>Ayrıca bkz.

* [.NET core sürümleri](https://github.com/dotnet/core/releases)
* [Arşiv .NET core çalışma zamanı ve SDK'sını indirin](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
