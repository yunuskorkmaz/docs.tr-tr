---
title: DotNet aracı install komutu
description: DotNet aracı yükleme komutu, makinenizde belirtilen .NET aracını yükler.
ms.date: 02/14/2020
ms.openlocfilehash: 5cdc0e16c964a639ebae25ac5075f186af4a9842
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105010"
---
# <a name="dotnet-tool-install"></a>dotnet tool install

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri

## <a name="name"></a>Name

`dotnet tool install` -Makinenizde belirtilen [.NET aracını](global-tools.md) yükleme.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet tool install <PACKAGE_NAME> -g|--global
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install <PACKAGE_NAME> --tool-path <PATH>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install <PACKAGE_NAME>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install -h|--help
```

## <a name="description"></a>Açıklama

Bu `dotnet tool install` komut, makinenizde .NET araçları yüklemenizi sağlayan bir yol sağlar. Komutunu kullanmak için aşağıdaki yükleme seçeneklerinden birini belirtin:

* Genel bir aracı varsayılan konuma yüklemek için `--global` seçeneğini kullanın.
* Bir genel aracı özel bir konuma yüklemek için `--tool-path` seçeneğini kullanın.
* Yerel bir araç yüklemek için `--global` ve `--tool-path` seçeneklerini atlayın.

**Yerel araçlar .NET Core SDK 3,0 ' den başlayarak kullanılabilir.**

Veya seçeneğini belirttiğinizde, genel araçlar varsayılan olarak aşağıdaki dizinlere yüklenir `-g` `--global` :

| İşletim Sistemi          | Yol                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

Yerel araçlar, geçerli dizinin altındaki bir *. config* dizinindeki *dotnet-tools.js* dosyasına eklenir. Henüz bir bildirim dosyası yoksa, aşağıdaki komutu çalıştırarak oluşturun:

```dotnetcli
dotnet new tool-manifest
```

Daha fazla bilgi için bkz. [yerel araç yüklemesi](global-tools.md#install-a-local-tool).

## <a name="arguments"></a>Bağımsız değişkenler

- **`PACKAGE_NAME`**

  Yüklenecek .NET aracını içeren NuGet paketinin adı/KIMLIĞI.

## <a name="options"></a>Seçenekler

- **`--add-source <SOURCE>`**

  Yükleme sırasında kullanmak üzere ek bir NuGet paketi kaynağı ekler.

- **`--configfile <FILE>`**

  Kullanılacak NuGet yapılandırma (*nuget.config*) dosyası.

- **`--framework <FRAMEWORK>`**

  Aracının yükleneceği [hedef çerçeveyi](../../standard/frameworks.md) belirtir. .NET SDK varsayılan olarak en uygun hedef çerçeveyi seçmenizi dener.

- **`-g|--global`**

  Yüklemenin Kullanıcı genelinde olduğunu belirtir. `--tool-path`Seçeneğiyle birleştirilemez. Her ikisini de atlayarak `--global` `--tool-path` bir yerel araç yüklemesi belirtilir.

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`--tool-path <PATH>`**

  Genel aracın yükleneceği konumu belirtir. YOL mutlak veya göreli olabilir. YOL yoksa, komut onu oluşturmaya çalışır. Her ikisini de atlayarak `--global` `--tool-path` bir yerel araç yüklemesi belirtilir.

- **`-v|--verbosity <LEVEL>`**

  Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` .

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

- [.NET araçları](global-tools.md)
- [Öğretici: .NET CLı kullanarak .NET genel aracını yükleyip kullanma](global-tools-how-to-use.md)
- [Öğretici: .NET CLı kullanarak .NET yerel aracını yükleyip kullanma](local-tools-how-to-use.md)
