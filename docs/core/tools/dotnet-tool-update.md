---
title: dotnet araç güncelleme komutu
description: Dotnet araç güncelleştirme komutu makinenizde belirtilen .NET Core aracını güncelleştirir.
ms.date: 02/14/2020
ms.openlocfilehash: 6176846dbe8e2a91d9c6959dede15718d8f983b2
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463295"
---
# <a name="dotnet-tool-update"></a>dotnet tool update

**Bu makale şu şekilde dir:** ✔️ .NET Core 2.1 SDK ve sonraki sürümler

## <a name="name"></a>Adı

`dotnet tool update`- Makinenizde belirtilen [.NET Core aracını](global-tools.md) güncelleştirir.

## <a name="synopsis"></a>Özet

```dotnetcli
dotnet tool update <PACKAGE_NAME> -g|--global
    [--configfile <FILE>] [--framework <FRAMEWORK>]
    [-v|--verbosity <LEVEL>] [--add-source <SOURCE>]

dotnet tool update <PACKAGE_NAME> --tool-path <PATH>
    [--configfile <FILE>] [--framework <FRAMEWORK>]
    [-v|--verbosity <LEVEL>] [--add-source <SOURCE>]

dotnet tool update <PACKAGE_NAME>
    [--configfile <FILE>] [--framework <FRAMEWORK>]
    [-v|--verbosity <LEVEL>] [--add-source <SOURCE>]

dotnet tool update -h|--help
```

## <a name="description"></a>Açıklama

Komut, `dotnet tool update` makinenizdeki .NET Core araçlarını paketin en son kararlı sürümüne güncellemeniz için bir yol sağlar. Komut, bir aracı etkin bir şekilde güncelleyerek bir aracı yükler ve yeniden yükler. Komutu kullanmak için aşağıdaki seçeneklerden birini belirtirsiniz:

* Varsayılan konumda yüklü olan genel bir aracı güncelleştirmek `--global` için,
* Özel bir konumda yüklenen genel bir aracı güncelleştirmek `--tool-path` için seçeneği kullanın.
* Yerel bir aracı güncelleştirmek için, seçenekleri `--global` ve seçenekleri `--tool-path` atleyin.

**Yerel araçlar .NET Core SDK 3.0 ile başlayarak kullanılabilir.**

## <a name="arguments"></a>Bağımsız Değişkenler

- **`PACKAGE_NAME`**

  Güncelleştirilen .NET Core global aracını içeren NuGet paketinin adı/kimliği. Paket adını [dotnet araç listesi](dotnet-tool-list.md) komutunu kullanarak bulabilirsiniz.

## <a name="options"></a>Seçenekler

- **`--add-source <SOURCE>`**

  Yükleme sırasında kullanmak üzere ek bir NuGet paket kaynağı ekler.

- **`--configfile <FILE>`**

  NuGet yapılandırması (*nuget.config*) dosyasını kullanmak.

- **`--framework <FRAMEWORK>`**

  Aracı güncelleştirmek için [hedef çerçeveyi](../../standard/frameworks.md) belirtir.

- **`-g|--global`**

  Güncelleştirmenin kullanıcı çapında bir araç için olduğunu belirtir. `--tool-path` Seçenekle birleştirilemeyiz. Her ikisini `--global` de `--tool-path` atlayarak ve güncellenecek aracın yerel bir araç olduğunu belirtir.

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`--tool-path <PATH>`**

  Genel aracın yüklendiği yeri belirtir. PATH mutlak veya göreceli olabilir. `--global` Seçenekle birleştirilemeyiz. Her ikisini `--global` de `--tool-path` atlayarak ve güncellenecek aracın yerel bir araç olduğunu belirtir.

- **`-v|--verbosity <LEVEL>`**

  Komutun ayrıntılı düzeyini ayarlar. İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve .

## <a name="examples"></a>Örnekler

- **`dotnet tool update -g dotnetsay`**

  [Noktanetsay](https://www.nuget.org/packages/dotnetsay/) global aracını güncelleştirir.

- **`dotnet tool update dotnetsay --tool-path c:\global-tools`**

  Belirli bir Windows dizininde bulunan [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global aracını güncelleştirir.

- **`dotnet tool update dotnetsay --tool-path ~/bin`**

  Belirli bir Linux/macOS dizininde bulunan [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global aracını güncelleştirir.

- **`dotnet tool update dotnetsay`**

  Geçerli dizin için yüklenen [dotnetsay](https://www.nuget.org/packages/dotnetsay/) yerel aracını güncelleştirir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Çekirdek araçları](global-tools.md)
- [Öğretici: .NET Core CLI'yi kullanarak bir .NET Core global aracı yükleyin ve kullanın](global-tools-how-to-use.md)
- [Öğretici: .NET Core CLI'yi kullanarak bir .NET Core yerel aracı nı yükleyin ve kullanın](local-tools-how-to-use.md)
