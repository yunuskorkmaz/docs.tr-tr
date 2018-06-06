---
title: DotNet aracı yükleme komutunu - .NET Core CLI
description: Dotnet araç belirtilen .NET Core genel aracı komut yükler makinenize yükleyin.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: f3068848910d6672a10ecfb639bac8e18a72818d
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34697293"
---
# <a name="dotnet-tool-install"></a>DotNet aracı yükleme

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Ad

`dotnet tool install` -Yükler belirtilen [.NET Core genel aracı](global-tools.md) makinenizde.

## <a name="synopsis"></a>Özet

```
dotnet tool install <PACKAGE_NAME> <-g|--global> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> <--tool-path> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <-h|--help>
```

## <a name="description"></a>Açıklama

`dotnet tool install` Komutu, makinenizde .NET Core genel araçları yüklemeniz için bir yol sağlar. Komutunu kullanmak için ya da kullanıcı genelinde yükleme kullanarak istediğiniz belirtmek zorunda `--global` seçeneği veya kullanarak yüklemek için bir yol belirtin `--tool-path` seçeneği.

Genel araçları yüklü aşağıdaki dizinlerindeki varsayılan olarak belirttiğiniz zaman `-g` (veya `--global`) seçeneği:

| İŞLETİM SİSTEMİ          | Yol                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

## <a name="arguments"></a>Arguments

`PACKAGE_NAME`

.NET Core genel yüklemek için Aracı'nı içeren NuGet paketi adı/kimliği.

## <a name="options"></a>Seçenekler

`--add-source <SOURCE>`

Yükleme sırasında kullanmak için ek bir NuGet paketi kaynağı ekler.

`--configfile <FILE>`

NuGet yapılandırması (*nuget.config*) kullanmak üzere bir dosya.

`--framework <FRAMEWORK>`

Belirtir [hedef framework](../../standard/frameworks.md) için Aracı'nı yüklemek için. Varsayılan olarak, .NET Core SDK en uygun hedef Framework'ü seçmek çalışır.

`-g|--global`

Yükleme kullanıcı geniş olduğunu belirtir. Birleştirilemez `--tool-path` seçeneği. Bu seçeneği belirtmezseniz, belirtmeniz gerekir `--tool-path` seçeneği.

`-h|--help`

Komutu için kısa bir Yardım yazdırır.

`--tool-path <PATH>`

Genel aracın yükleneceği konumu belirtir. YOL, mutlak veya göreli olabilir. YOL yoksa, komut onu oluşturmaya çalışır. Birleştirilemez `--global` seçeneği. Bu seçeneği belirtmezseniz, belirtmeniz gerekir `--global` seçeneği.

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyi ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.

`--version <VERSION_NUMBER>`

Yüklemek için aracı sürümü. Varsayılan olarak, en son kararlı Paket sürümü yüklenir. Önizleme veya aracın eski sürümlerini yüklemek için bu seçeneği kullanın.

## <a name="examples"></a>Örnekler

Yükler [dotnetsay](https://www.nuget.org/packages/dotnetsay/) genel araç varsayılan konumda:

`dotnet tool install -g dotnetsay`

Yükler [dotnetsay](https://www.nuget.org/packages/dotnetsay/) genel aracını kullanarak belirli bir Windows klasörü:

`dotnet tool install dotnetsay --tool-path c:\global-tools`

Yükler [dotnetsay](https://www.nuget.org/packages/dotnetsay/) belirli bir Linux/macOS klasördeki genel aracı:

`dotnet tool install dotnetsay --tool-path ~/bin`

2.0.0 sürümünü yükler [dotnetsay](https://www.nuget.org/packages/dotnetsay/) genel aracı:

`dotnet tool install -g dotnetsay --version 2.0.0`

## <a name="see-also"></a>Ayrıca bkz.

[.NET core genel araçları](global-tools.md)