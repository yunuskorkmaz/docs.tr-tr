---
title: DotNet yükleme betikleri
description: .NET Core CLI araçlarını ve paylaşılan çalışma zamanı yükleme dotnet yükleme betikleri hakkında bilgi edinin.
author: blackdwarf
ms.author: mairaw
ms.date: 09/11/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 96336df087ea2ad01584010f0715ad31e079b663
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-install-scripts-reference"></a>DotNet yükleme komut başvurusu

## <a name="name"></a>Ad

`dotnet-install.ps1` | `dotnet-install.sh` -.NET Core CLI araçlarını ve paylaşılan çalışma zamanı'nı yüklemek için kullanılan komut dosyası.

## <a name="synopsis"></a>Özet

Windows:

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-DryRun] [-NoPath] [-AzureFeed] [-ProxyAddress] [--Verbose] [--Help]`

macOS/Linux:

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--shared-runtime] [--dry-run] [--no-path] [--azure-feed] [--verbose] [--help]`

## <a name="description"></a>Açıklama

`dotnet-install` Komut dosyaları, .NET Core CLI araçlarını ve paylaşılan çalışma zamanı içeren .NET Core SDK yönetici olmayan yüklemesini gerçekleştirmek için kullanılır.

Üzerinde barındırılan kararlı sürümünü kullanmanızı öneririz [.NET Core ana Web sitesi](https://dot.net). Komut dosyalarını doğrudan yolları şunlardır:

* https://dot.net/v1/dotnet-install.sh (bash, UNIX)
* https://dot.net/v1/dotnet-install.ps1 (Powershell, Windows)

Bu komut dosyalarını ana yararlılığı Otomasyon senaryoları ve yönetici olmayan yüklemeleri de sağlanır. İki komut vardır: Windows üzerinde çalışan bir PowerShell Betiği biridir. Diğer komut dosyası Linux/macOS üzerinde çalıştığı bir bash komut dosyasıdır. Her iki komut dosyasını aynı davranışı sahiptir. Linux/macOS sistemlerde komut dosyasıyla PowerShell anahtarları kullanabilmeniz için bash komut dosyası ayrıca PowerShell anahtarları okur. 

Yükleme betikleri CLI derleme bırakma işlemlerine ZIP/tarball dosyasını indirin ve varsayılan konumda veya tarafından belirtilen bir konumda yüklemeye devam `-InstallDir|--install-dir`. Varsayılan olarak, yükleme betikleri SDK'sını indirin ve yükleyin. Yalnızca paylaşılan çalışma zamanı elde etmek istiyorsanız, belirtin `--shared-runtime` bağımsız değişkeni. 

Varsayılan olarak, geçerli oturum için $PATH için yükleme konumu betik ekler. Belirterek bu varsayılan davranışı geçersiz kılma `--no-path` bağımsız değişkeni. 

Komut dosyasını çalıştırmadan önce gerekli yükleme [bağımlılıkları](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).

Belirli bir sürüm kullanarak yükleyebilirsiniz `--version` bağımsız değişkeni. Sürüm 3 parçalı sürümü (örneğin, 1.0.0-13232) belirtilmelidir. Belirtilmezse, kullanır `latest` sürümü.

## <a name="options"></a>Seçenekler

`-Channel <CHANNEL>`

Yükleme için kaynak kanalı belirtir. Olası değerler şunlardır:

- `Current` -Geçerli sürüm
- `LTS` -Uzun vadeli bir destek kanalıyla (geçerli desteklenen sürüm)
- İki parçalı sürümü belirli bir sürüm temsil eden X.Y biçiminde (örneğin, `2.0` veya `1.0`)
- Dal adı [Örneğin, `release/2.0.0`, `release/2.0.0-preview2`, veya `master` için en son `master` şube (gecelik sürümleri "kenar taşmasını")]

Varsayılan değer `LTS` şeklindedir. .NET Destek kanallarını hakkında daha fazla bilgi için bkz: [.NET Core destek ömrü](https://www.microsoft.com/net/core/support) konu.

`-Version <VERSION>`

Özel Yapı sürümünü temsil eder. Olası değerler şunlardır:

- `latest` -En yeni kanal oluştur (ile kullanılan `-Channel` seçeneği)
- `coherent` -Son tutarlı yapı kanalda; en son kararlı paket birlikte kullanır (şube adı ile kullanılan `-Channel` seçenekleri)
- Belirli bir temsil eden X.Y.Z biçiminde üç bölümlük sürüm yapı sürümü; yerine geçen `-Channel` seçeneği. Örneğin: `2.0.0-preview2-006120`

Atlanırsa, `-Version` varsayılan olarak `latest`.

`-InstallDir <DIRECTORY>`

Yükleme yolu belirtir. Dizin yoksa oluşturulur. Varsayılan değer *LocalAppData %\.dotnet*. İkili dosyaları doğrudan dizindeki yerleştirilir unutmayın.

`-Architecture <ARCHITECTURE>`

Yüklemek için .NET Core ikili dosyaları mimarisi. Olası değerler şunlardır: `auto`, `x64`, ve `x86`. Varsayılan değer `auto`, şu anda çalışan işletim sistemi mimarisi temsil eder.

`-SharedRuntime`

Ayarlama, bu anahtarı paylaşılan çalışma zamanı yükleme sınırlar durumunda. Tüm SDK yüklü değil.

`-DryRun`

Ayarlama, komut dosyası yüklemesi; gerçekleştiremiyor varsa ancak bunun yerine, tutarlı bir şekilde .NET Core CLI'ın şu anda istenen sürümünü yüklemek için kullanılacak hangi komut satırı görüntüler. Sürüm belirtirseniz, örneğin `latest`, böylece bu komut bir yapı komut dosyasında belirleyici biçimde kullanılabilir belirli sürümünü içeren bir bağlantı gösterir. Yükleme veya kendiniz indirmek isterseniz de ikilinin konumu görüntüler.

`-NoPath`

Ayarlama, önek/InstallDir dışarı aktarılmaz varsa yolu geçerli oturum için. Varsayılan olarak, CLI araçlarını hemen yüklendikten sonra kullanılabilir hale getirir yolu komut dosyasını değiştirecektir.

`-AzureFeed`

Azure URL'si için yükleyici akış belirtir. Bu değeri değiştirmek önerilmez. Varsayılan, `https://dotnetcli.azureedge.net/dotnet` değeridir.

`-ProxyAddress`

Ayarlama, yükleyici web isteklerini yaparken proxy kullanıyorsa. (Yalnızca Windows için geçerlidir)

`--verbose`

Tanılama bilgileri görüntüler.

`--help`

Komut dosyası için Yardım yazdırır.

## <a name="examples"></a>Örnekler

En son uzun vadeli desteklenen (LTS) sürüm, varsayılan konuma geri yükleyin:

Windows:

`./dotnet-install.ps1 -Channel LTS`

macOS/Linux:

`./dotnet-install.sh --channel LTS`

En son sürümü 2.0 kanala belirtilen konuma yükleyin:

Windows:

`./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli`

macOS/Linux:

`./dotnet-install.sh --channel 2.0 --install-dir ~/cli`

Paylaşılan çalışma zamanı yükleme 1.1.0 sürümü:

Windows:

`./dotnet-install.ps1 -SharedRuntime -Version 1.1.0`

macOS/Linux:

`./dotnet-install.sh --shared-runtime --version 1.1.0`

Komut dosyasını edinmek ve .NET Core CLI one-liner örnekleri yükleyin:

Windows:

`@powershell -NoProfile -ExecutionPolicy unrestricted -Command "&([scriptblock]::Create((Invoke-WebRequest -useb 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"`

macOS/Linux:

`curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>`

## <a name="see-also"></a>Ayrıca bkz.

[.NET core serbest bırakır](https://github.com/dotnet/core/releases)   
[.NET çekirdeği çalışma zamanı ve SDK arşivi indir](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
