---
title: DotNet Aracı güncelleştirme komutu
description: DotNet Aracı güncelleştirme komutu makinenizde belirtilen .NET Core küresel aracını güncelleştirir.
ms.date: 05/29/2018
ms.openlocfilehash: b10ce39c8b9d4df23243bcf672454a455e34eec1
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117528"
---
# <a name="dotnet-tool-update"></a>dotnet tool update

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Ad

`dotnet tool update`-Makinenizde belirtilen [.NET Core küresel aracı](global-tools.md) 'nı güncelleştirir.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet tool update <PACKAGE_NAME> <-g|--global> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <PACKAGE_NAME> <--tool-path> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <-h|--help>
```

## <a name="description"></a>Açıklama

Komut `dotnet tool update` , makinenizde .NET Core küresel araçlarını paketin en son kararlı sürümüne güncelleştirmeniz için bir yol sağlar. Komut, bir aracı kaldırır ve etkin bir şekilde güncelleştiren bir araç yükler. Komutunu kullanmak için, `--global` seçeneğini kullanarak Kullanıcı genelindeki bir yüklemeden bir aracı güncelleştirmek istediğinizi belirtmeniz veya `--tool-path` seçeneği kullanılarak aracın yüklendiği konuma bir yol belirtmeniz gerekir.

## <a name="arguments"></a>Arguments

`PACKAGE_NAME`

Güncelleştirilecek .NET Core küresel aracını içeren NuGet paketinin adı/KIMLIĞI. [DotNet araç listesi](dotnet-tool-list.md) komutunu kullanarak paket adını bulabilirsiniz.

## <a name="options"></a>Seçenekler

`--add-source <SOURCE>`

Yükleme sırasında kullanmak üzere ek bir NuGet paketi kaynağı ekler.

`--configfile <FILE>`

Kullanılacak NuGet yapılandırma (*NuGet. config*) dosyası.

`--framework <FRAMEWORK>`

Aracının güncelleştirilmesi için [hedef çerçeveyi](../../standard/frameworks.md) belirtir.

`-g|--global`

Güncelleştirmenin Kullanıcı genelindeki bir araç için olduğunu belirtir. `--tool-path` Seçeneğiyle birleştirilemez. Bu seçeneği belirtmezseniz, `--tool-path` seçeneğini belirtmeniz gerekir.

`-h|--help`

Komut için kısa bir yardım yazdırır.

`--tool-path <PATH>`

Genel aracın yüklendiği konumu belirtir. YOL mutlak veya göreli olabilir. `--global` Seçeneğiyle birleştirilemez. Bu seçeneği belirtmezseniz, `--global` seçeneğini belirtmeniz gerekir.

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]` `m[inimal]` ,`n[ormal]`,, ve .`diag[nostic]` `d[etailed]`

## <a name="examples"></a>Örnekler

[Dotnetdeyin](https://www.nuget.org/packages/dotnetsay/) genel aracını güncelleştirir:

`dotnet tool update -g dotnetsay`

Belirli bir Windows klasöründe bulunan [dotnetsöyleme](https://www.nuget.org/packages/dotnetsay/) küresel aracını güncelleştirir:

`dotnet tool update dotnetsay --tool-path c:\global-tools`

Belirli bir Linux/macOS klasöründe bulunan [dotnetsay](https://www.nuget.org/packages/dotnetsay/) küresel aracını güncelleştirir:

`dotnet tool update dotnetsay --tool-path ~/bin`

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core küresel araçları](global-tools.md)
