---
title: DotNet aracı install komutu
description: DotNet aracı yükleme komutu, makinenizde belirtilen .NET Core küresel aracını yükler.
ms.date: 05/29/2018
ms.openlocfilehash: d6f691117e93a39c9837b282dca19e452515c80a
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117474"
---
# <a name="dotnet-tool-install"></a>dotnet tool install

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Ad

`dotnet tool install`-Makinenizde belirtilen [.NET Core küresel aracını](global-tools.md) yükleme.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet tool install <PACKAGE_NAME> <-g|--global> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> <--tool-path> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <-h|--help>
```

## <a name="description"></a>Açıklama

Bu `dotnet tool install` komut, makinenizde .NET Core küresel araçları yüklemenizi sağlayan bir yol sağlar. Komutunu kullanmak için, `--global` seçeneğini kullanarak Kullanıcı genelindeki bir yüklemeyi istediğinizi veya `--tool-path` seçeneğini kullanarak yüklemek için bir yol belirtmenizi belirtmeniz gerekir.

Genel araçlar, `-g` (veya `--global`) seçeneğini belirttiğinizde varsayılan olarak aşağıdaki dizinlere yüklenir:

| OS          | Yol                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

## <a name="arguments"></a>Arguments

`PACKAGE_NAME`

Yüklenecek .NET Core küresel aracını içeren NuGet paketinin adı/KIMLIĞI.

## <a name="options"></a>Seçenekler

`--add-source <SOURCE>`

Yükleme sırasında kullanmak üzere ek bir NuGet paketi kaynağı ekler.

`--configfile <FILE>`

Kullanılacak NuGet yapılandırma (*NuGet. config*) dosyası.

`--framework <FRAMEWORK>`

Aracının yükleneceği [hedef çerçeveyi](../../standard/frameworks.md) belirtir. .NET Core SDK, varsayılan olarak en uygun hedef Framework 'ü seçmaya çalışır.

`-g|--global`

Yüklemenin Kullanıcı genelinde olduğunu belirtir. `--tool-path` Seçeneğiyle birleştirilemez. Bu seçeneği belirtmezseniz, `--tool-path` seçeneğini belirtmeniz gerekir.

`-h|--help`

Komut için kısa bir yardım yazdırır.

`--tool-path <PATH>`

Genel aracın yükleneceği konumu belirtir. YOL mutlak veya göreli olabilir. YOL yoksa, komut onu oluşturmaya çalışır. `--global` Seçeneğiyle birleştirilemez. Bu seçeneği belirtmezseniz, `--global` seçeneğini belirtmeniz gerekir.

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]` `m[inimal]` ,`n[ormal]`,, ve .`diag[nostic]` `d[etailed]`

`--version <VERSION_NUMBER>`

Yüklenecek aracın sürümü. Varsayılan olarak, en son kararlı paket sürümü yüklenir. Aracının önizlemesini veya eski sürümlerini yüklemek için bu seçeneği kullanın.

## <a name="examples"></a>Örnekler

[Dotnetsay](https://www.nuget.org/packages/dotnetsay/) genel aracını varsayılan konuma yüklenir:

`dotnet tool install -g dotnetsay`

Özel bir Windows klasörüne [dotnetdeyin](https://www.nuget.org/packages/dotnetsay/) genel aracını yükleme:

`dotnet tool install dotnetsay --tool-path c:\global-tools`

Belirli bir Linux/macOS klasörüne [dotnetdeyin](https://www.nuget.org/packages/dotnetsay/) genel aracını yükleme:

`dotnet tool install dotnetsay --tool-path ~/bin`

[Dotnetsay](https://www.nuget.org/packages/dotnetsay/) küresel aracının 2.0.0 sürümünü kurar:

`dotnet tool install -g dotnetsay --version 2.0.0`

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core küresel araçları](global-tools.md)
