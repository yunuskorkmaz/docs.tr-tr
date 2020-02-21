---
title: DotNet aracı install komutu
description: DotNet aracı yükleme komutu, makinenizde belirtilen .NET Core aracını yükler.
ms.date: 02/14/2020
ms.openlocfilehash: 2705defe9b77009ca1411da28dd86d144ccc19e6
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543475"
---
# <a name="dotnet-tool-install"></a>dotnet tool install

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri

## <a name="name"></a>Adı

`dotnet tool install`-makinenizde belirtilen [.NET Core aracını](global-tools.md) yükleme.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet tool install <PACKAGE_NAME> <-g|--global> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> <--tool-path> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <-h|--help>
```

## <a name="description"></a>Açıklama

`dotnet tool install` komutu, makinenizde .NET Core araçları yüklemenizi sağlayan bir yol sağlar. Komutunu kullanmak için aşağıdaki yükleme seçeneklerinden birini belirtin:

* Genel bir aracı varsayılan konuma yüklemek için `--tool-path` seçeneğini kullanın.
* Bir genel aracı özel bir konuma yüklemek için `--tool-path` seçeneğini kullanın.
* Yerel bir araç yüklemek için `--global` ve `--tool-path` seçeneklerini atlayın.

**Yerel araçlar .NET Core SDK 3,0 ' den başlayarak kullanılabilir.**

`-g` veya `--global` seçeneğini belirttiğinizde, genel araçlar varsayılan olarak aşağıdaki dizinlere yüklenir:

| İşletim Sistemi          | Yol                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

Yerel araçlar, geçerli dizinin altındaki bir *. config* dizininde bulunan bir *araç bildirimi. JSON* dosyasına eklenir. Henüz bir bildirim dosyası yoksa, aşağıdaki komutu çalıştırarak oluşturun:

```dotnetcli
dotnet new tool-manifest
```

Daha fazla bilgi için bkz. [yerel araç yüklemesi](global-tools.md#install-a-local-tool).

## <a name="arguments"></a>Bağımsız Değişkenler

- **`PACKAGE_NAME`**

  Yüklenecek .NET Core aracını içeren NuGet paketinin adı/KIMLIĞI.

## <a name="options"></a>Seçenekler

- **`add-source <SOURCE>`**

  Yükleme sırasında kullanmak üzere ek bir NuGet paketi kaynağı ekler.

- **`configfile <FILE>`**

  Kullanılacak NuGet yapılandırma (*NuGet. config*) dosyası.

- **`framework <FRAMEWORK>`**

  Aracının yükleneceği [hedef çerçeveyi](../../standard/frameworks.md) belirtir. .NET Core SDK, varsayılan olarak en uygun hedef Framework 'ü seçmaya çalışır.

- **`-g|--global`**

  Yüklemenin Kullanıcı genelinde olduğunu belirtir. `--tool-path` seçeneği ile birleştirilemez. `--global` ve `--tool-path` her ikisi de kullanılmazsa yerel bir araç yüklemesi belirtilir. 

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`tool-path <PATH>`**

  Genel aracın yükleneceği konumu belirtir. YOL mutlak veya göreli olabilir. YOL yoksa, komut onu oluşturmaya çalışır. `--global` ve `--tool-path` her ikisi de kullanılmazsa yerel bir araç yüklemesi belirtilir. 

- **`-v|--verbosity <LEVEL>`**

  Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.

- **`--version <VERSION_NUMBER>`**

  Yüklenecek aracın sürümü. Varsayılan olarak, en son kararlı paket sürümü yüklenir. Aracının önizlemesini veya eski sürümlerini yüklemek için bu seçeneği kullanın.

## <a name="examples"></a>Örnekler

- **`dotnet tool install -g dotnetsay`**

  Varsayılan konumda [dotnetdeyin](https://www.nuget.org/packages/dotnetsay/) genel araç olarak yüklenir.

- **`dotnet tool install dotnetsay --tool-path c:\global-tools`**

  Özel bir Windows dizininde [dotnetdeyin](https://www.nuget.org/packages/dotnetsay/) genel bir araç olarak yüklenir.

- **`dotnet tool install dotnetsay --tool-path ~/bin`**

  [Dotnetdeyin](https://www.nuget.org/packages/dotnetsay/) , belirli bir Linux/MacOS dizininde küresel bir araç olarak yüklenir.

- **`dotnet tool install -g dotnetsay --version 2.0.0`**

  [Dotnetme](https://www.nuget.org/packages/dotnetsay/) 'nin 2.0.0 sürümünü küresel bir araç olarak kurar.

- **`dotnet tool install dotnetsay`**

  Geçerli dizin için [dotnetdeyin](https://www.nuget.org/packages/dotnetsay/) 'ı yerel bir araç olarak kurar.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core araçları](global-tools.md)
