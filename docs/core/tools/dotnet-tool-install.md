---
title: dotnet aracı yükleme komutu
description: Dotnet araç yükleme komutu makinenize belirtilen .NET Core aracını yükler.
ms.date: 02/14/2020
ms.openlocfilehash: 723d25caa6009288dbb55d55f173b04d7b983450
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463357"
---
# <a name="dotnet-tool-install"></a>dotnet tool install

**Bu makale şu şekilde dir:** ✔️ .NET Core 2.1 SDK ve sonraki sürümler

## <a name="name"></a>Adı

`dotnet tool install`- Belirtilen [.NET Core aracını](global-tools.md) makinenize yükler.

## <a name="synopsis"></a>Özet

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

Komut, `dotnet tool install` makinenize .NET Core araçlarını yüklemeniz için bir yol sağlar. Komutu kullanmak için aşağıdaki yükleme seçeneklerinden birini belirtirsiniz:

* Varsayılan konuma genel bir araç yüklemek `--global` için seçeneği kullanın.
* Genel bir aracı özel bir konuma `--tool-path` yüklemek için seçeneği kullanın.
* Yerel bir araç yüklemek için, `--global` `--tool-path` ve seçenekleri atla.

**Yerel araçlar .NET Core SDK 3.0 ile başlayarak kullanılabilir.**

Genel araçlar, aşağıdaki dizinlerde varsayılan olarak veya `-g` `--global` seçeneği belirttiğiniz zaman yüklenir:

| İşletim Sistemi          | Yol                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

Yerel araçlar, geçerli dizini altında *bir .config* dizinindeki *bir araç bildirimi.json* dosyasına eklenir. Bir bildirim dosyası henüz yoksa, aşağıdaki komutu çalıştırarak dosyayı oluşturun:

```dotnetcli
dotnet new tool-manifest
```

Daha fazla bilgi için [bkz.](global-tools.md#install-a-local-tool)

## <a name="arguments"></a>Bağımsız Değişkenler

- **`PACKAGE_NAME`**

  Yüklemek için .NET Core aracını içeren NuGet paketinin adı/kimliği.

## <a name="options"></a>Seçenekler

- **`add-source <SOURCE>`**

  Yükleme sırasında kullanmak üzere ek bir NuGet paket kaynağı ekler.

- **`configfile <FILE>`**

  NuGet yapılandırması (*nuget.config*) dosyasını kullanmak.

- **`framework <FRAMEWORK>`**

  Aracı yüklemek için [hedef çerçeveyi](../../standard/frameworks.md) belirtir. Varsayılan olarak, .NET Core SDK en uygun hedef çerçeveyi seçmeye çalışır.

- **`-g|--global`**

  Yüklemenin kullanıcı genelinde olduğunu belirtir. `--tool-path` Seçenekle birleştirilemeyiz. Her ikisini `--global` de `--tool-path` atlayarak yerel bir araç yüklemesi belirtir.

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`tool-path <PATH>`**

  Genel Araç'ın yüklenmesi gereken yeri belirtir. PATH mutlak veya göreceli olabilir. PATH yoksa, komut onu oluşturmaya çalışır. Her ikisini `--global` de `--tool-path` atlayarak yerel bir araç yüklemesi belirtir.

- **`-v|--verbosity <LEVEL>`**

  Komutun ayrıntılı düzeyini ayarlar. İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve .

- **`--version <VERSION_NUMBER>`**

  Yüklemek için aracın sürümü. Varsayılan olarak, en son kararlı paket sürümü yüklenir. Aracın önizlemesini veya eski sürümlerini yüklemek için bu seçeneği kullanın.

## <a name="examples"></a>Örnekler

- **`dotnet tool install -g dotnetsay`**

  Varsayılan konumda genel bir araç olarak [dotnetsay](https://www.nuget.org/packages/dotnetsay/) yükler.

- **`dotnet tool install dotnetsay --tool-path c:\global-tools`**

  Belirli bir Windows dizininde genel bir araç olarak [dotnetsay](https://www.nuget.org/packages/dotnetsay/) yükler.

- **`dotnet tool install dotnetsay --tool-path ~/bin`**

  Belirli bir Linux/macOS dizininde global bir araç olarak [dotnetsay](https://www.nuget.org/packages/dotnetsay/) yükler.

- **`dotnet tool install -g dotnetsay --version 2.0.0`**

  Genel bir araç olarak [dotnetsay](https://www.nuget.org/packages/dotnetsay/) sürüm 2.0.0 yükler.

- **`dotnet tool install dotnetsay`**

  Geçerli dizin için yerel bir araç olarak [dotnetsay](https://www.nuget.org/packages/dotnetsay/) yükler.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Çekirdek araçları](global-tools.md)
- [Öğretici: .NET Core CLI'yi kullanarak bir .NET Core global aracı yükleyin ve kullanın](global-tools-how-to-use.md)
- [Öğretici: .NET Core CLI'yi kullanarak bir .NET Core yerel aracı nı yükleyin ve kullanın](local-tools-how-to-use.md)
