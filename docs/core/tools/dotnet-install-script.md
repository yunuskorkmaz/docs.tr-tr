---
title: DotNet yükleme betikleri
description: .NET Core CLI araçları ve paylaşılan çalışma zamanı'nı yüklemek için dotnet-yükleme betikleri hakkında bilgi edinin.
author: blackdwarf
ms.author: mairaw
ms.date: 09/11/2017
ms.openlocfilehash: 8d1c6ebb30bd45575bb61206799c9c3e5c47ff0c
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44140703"
---
# <a name="dotnet-install-scripts-reference"></a>DotNet yükleme komut başvurusu

## <a name="name"></a>Ad

`dotnet-install.ps1` | `dotnet-install.sh` -.NET Core CLI araçları ve paylaşılan çalışma zamanı'nı yüklemek için kullanılan komut dosyası.

## <a name="synopsis"></a>Özeti

Windows:

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-DryRun] [-NoPath] [-AzureFeed] [-ProxyAddress] [--Verbose] [--Help]`

macOS/Linux:

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--shared-runtime] [--dry-run] [--no-path] [--azure-feed] [--verbose] [--help]`

## <a name="description"></a>Açıklama

`dotnet-install` Betikleri, .NET Core CLI araçları ve paylaşılan çalışma zamanı içeren .NET Core SDK'sı yönetici olmayan bir yüklemesini gerçekleştirmek için kullanılır.

Üzerinde barındırılan kararlı bir sürüm kullanmanızı öneririz [.NET Core ana Web sitesi](https://dot.net). Komut dosyalarını doğrudan yolları şunlardır:

* https://dot.net/v1/dotnet-install.sh (bash, UNIX)
* https://dot.net/v1/dotnet-install.ps1 (Powershell, Windows)

Bu komut dosyaları ana kullanışlılığını Otomasyon senaryoları ve yönetici olmayan yüklemeleri kullanılabilir. İki betik vardır: Windows üzerinde çalışan bir PowerShell Betiği biridir. Diğer betik Linux/macOS üzerinde çalışan bir bash komut dosyasıdır. Her iki komut dosyaları aynı davranışa sahip. Linux/macOS sistemlerde betiğiyle PowerShell anahtarları kullanabilmeniz için bash betiğini de PowerShell anahtarları okur.

Yükleme betikleri CLI yapı bırakma öğelerini ZIP/tarball dosyasını indirin ve varsayılan konumda veya tarafından belirtilen bir konumda yükleme işlemine devam `-InstallDir|--install-dir`. Varsayılan olarak, yükleme betikleri SDK'sını indirin ve yükleyin. Yalnızca paylaşılan çalışma zamanı elde etmek istiyorsanız, belirtin `--shared-runtime` bağımsız değişken.

Varsayılan olarak, betik geçerli oturum için $PATH için yükleme konumu ekler. Bu varsayılan davranışı geçersiz kılma belirterek `--no-path` bağımsız değişken.

Betiği çalıştırmadan önce gerekli yükleme [bağımlılıkları](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).

Belirli bir sürümünü kullanarak bir yükleyebilirsiniz `--version` bağımsız değişken. Sürüm 3 parçalı sürümü (örneğin, 1.0.0-13232) belirtilmelidir. Atlanırsa, kullandığı `latest` sürümü.

## <a name="options"></a>Seçenekler

`-Channel <CHANNEL>`

Yükleme için kaynak kanalı belirtir. Olası değerler şunlardır:

- `Current` -Geçerli sürüm
- `LTS` -Uzun süreli destek kanalı (geçerli desteklenen sürüm)
- İki parçalı sürümü belirli bir yayınını temsil eden X.Y biçiminde (örneğin, `2.0` veya `1.0`)
- Dal adı [örneğin `release/2.0.0`, `release/2.0.0-preview2`, veya `master` için en son `master` dal (gecelik sürümleri "edge taşmasını")]

Varsayılan değer `LTS` şeklindedir. .NET Destek kanalları hakkında daha fazla bilgi için bkz. [.NET Core destek yaşam döngüsü](https://www.microsoft.com/net/core/support) konu.

`-Version <VERSION>`

Belirli bir yapı sürümünü temsil eder. Olası değerler şunlardır:

- `latest` -Kanal en son derleme (ile kullanılan `-Channel` seçeneği)
- `coherent` -Tutarlı yapıyı kanalındaki son; en son kararlı paket kullanır (Dal adı ile kullanılan `-Channel` seçenekleri)
- Üç bölümlü sürüm X.Y.Z biçiminde temsil eden belirli bir yapı sürümü; yerine geçen `-Channel` seçeneği. Örneğin: `2.0.0-preview2-006120`

Atlanırsa, `-Version` varsayılan olarak `latest`.

`-InstallDir <DIRECTORY>`

Yükleme yolunu belirtir. Dizin yoksa oluşturulur. Varsayılan değer *% LocalAppData %\.dotnet*. İkili dosyaları doğrudan dizine yerleştirilir unutmayın.

`-Architecture <ARCHITECTURE>`

.NET Core ikili dosyaları yüklemek için Mimari. Olası değerler `auto`, `x64`, ve `x86`. Varsayılan değer `auto`, şu anda çalışan işletim sistemi mimarisi temsil eder.

`-SharedRuntime`

Ayarlanırsa, bu anahtarı paylaşılan çalışma zamanı yükleme sınırları varsa. Tüm SDK'sı yüklü değil.

`-DryRun`

Ayarlanırsa, komut dosyası yükleme; gerçekleştiremiyor varsa Ancak, bunun yerine, .NET Core CLI'ın şu anda istenen sürüm tutarlı bir şekilde yüklemek için kullanılacak hangi komut satırını gösterir. Sürüm belirtirseniz, örneğin `latest`, böylece bu komut, bir derleme betikte belirleyici kullanılabilir belirli bir sürümünü içeren bir bağlantı gösterir. Yüklemek veya kendiniz indirmek isterseniz de ikili dosyanın konumunu görüntüler.

`-NoPath`

Ayarlanırsa, ön eki/ınstalldır değil verilir, yolu geçerli oturum için. Varsayılan olarak, komut dosyası CLI araçları yüklendikten sonra hemen kullanılabilmesini YOLUNU değiştirir.

`-AzureFeed`

Yükleyici için akış URL'sini Azure belirtir. Bu değeri değiştirmeniz önerilmez. Varsayılan, `https://dotnetcli.azureedge.net/dotnet` değeridir.

`-ProxyAddress`

Kümesi, yükleyici web istekleri yaparken proxy kullanıyorsa. (Yalnızca Windows için geçerlidir)

`--verbose`

Tanılama bilgilerini görüntüler.

`--help`

Komut için Yardım yazdırır.

## <a name="examples"></a>Örnekler

Desteklenen en son uzun vadeli (LTS) sürüm varsayılan konuma yükleyin:

Windows:

`./dotnet-install.ps1 -Channel LTS`

macOS/Linux:

`./dotnet-install.sh --channel LTS`

En son sürümü 2.0 kanaldan belirtilen konuma yükleyin:

Windows:

`./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli`

macOS/Linux:

`./dotnet-install.sh --channel 2.0 --install-dir ~/cli`

Paylaşılan çalışma zamanı yükleme 1.1.0 sürümü:

Windows:

`./dotnet-install.ps1 -SharedRuntime -Version 1.1.0`

macOS/Linux:

`./dotnet-install.sh --shared-runtime --version 1.1.0`

Betiği almak ve .NET Core CLI one-liner örnekleri yükleyin:

Windows:

`@powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -useb 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"`

macOS/Linux:

`curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>`

## <a name="see-also"></a>Ayrıca bkz.

* [.NET core sürümleri](https://github.com/dotnet/core/releases)
* [Arşiv .NET core çalışma zamanı ve SDK'sını indirin](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
