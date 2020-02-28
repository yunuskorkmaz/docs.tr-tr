---
title: DotNet Aracı güncelleştirme komutu
description: DotNet Aracı güncelleştirme komutu makinenizde belirtilen .NET Core aracını güncelleştirir.
ms.date: 02/14/2020
ms.openlocfilehash: 80e807a0fc06ad762334f888e701f6d9c448369a
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156952"
---
# <a name="dotnet-tool-update"></a>dotnet tool update

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri

## <a name="name"></a>Adı

`dotnet tool update`-makinenizde belirtilen [.NET Core aracını](global-tools.md) güncelleştirir.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet tool update <PACKAGE_NAME> <-g|--global> [--configfile] [--framework] [-v|--verbosity] [--add-source]
dotnet tool update <PACKAGE_NAME> <--tool-path> [--configfile] [--framework] [-v|--verbosity] [--add-source]
dotnet tool update <PACKAGE_NAME> [--configfile] [--framework] [-v|--verbosity] [--add-source]
dotnet tool update <-h|--help>
```

## <a name="description"></a>Açıklama

`dotnet tool update` komutu, makinenizde .NET Core araçlarını paketin en son kararlı sürümüne güncelleştirmeniz için bir yol sağlar. Komut, bir aracı kaldırır ve etkin bir şekilde güncelleştiren bir araç yükler. Komutunu kullanmak için aşağıdaki seçeneklerden birini belirtin:

* Varsayılan konumda yüklü olan küresel bir aracı güncelleştirmek için `--global` seçeneğini kullanın
* Özel bir konuma yüklenmiş olan küresel bir aracı güncelleştirmek için `--tool-path` seçeneğini kullanın.
* Yerel bir aracı güncelleştirmek için `--global` ve `--tool-path` seçeneklerini atlayın.

**Yerel araçlar .NET Core SDK 3,0 ' den başlayarak kullanılabilir.**

## <a name="arguments"></a>Bağımsız Değişkenler

- **`PACKAGE_NAME`**

  Güncelleştirilecek .NET Core küresel aracını içeren NuGet paketinin adı/KIMLIĞI. [DotNet araç listesi](dotnet-tool-list.md) komutunu kullanarak paket adını bulabilirsiniz.

## <a name="options"></a>Seçenekler

- **`--add-source <SOURCE>`**

  Yükleme sırasında kullanmak üzere ek bir NuGet paketi kaynağı ekler.

- **`--configfile <FILE>`**

  Kullanılacak NuGet yapılandırma (*NuGet. config*) dosyası.

- **`--framework <FRAMEWORK>`**

  Aracının güncelleştirilmesi için [hedef çerçeveyi](../../standard/frameworks.md) belirtir.

- **`-g|--global`**

  Güncelleştirmenin Kullanıcı genelindeki bir araç için olduğunu belirtir. `--tool-path` seçeneği ile birleştirilemez. `--global` ve `--tool-path` her ikisi de kullanılmazsa, güncellenen aracın yerel bir araç olduğunu belirtir.

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`--tool-path <PATH>`**

  Genel aracın yüklendiği konumu belirtir. YOL mutlak veya göreli olabilir. `--global` seçeneği ile birleştirilemez. `--global` ve `--tool-path` her ikisi de kullanılmazsa, güncellenen aracın yerel bir araç olduğunu belirtir.

- **`-v|--verbosity <LEVEL>`**

  Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.

## <a name="examples"></a>Örnekler

- **`dotnet tool update -g dotnetsay`**

  [Dotnetsay](https://www.nuget.org/packages/dotnetsay/) küresel aracını güncelleştirir.

- **`dotnet tool update dotnetsay --tool-path c:\global-tools`**

  Belirli bir Windows dizininde bulunan [dotnetdeyin](https://www.nuget.org/packages/dotnetsay/) küresel aracı 'nı güncelleştirir.

- **`dotnet tool update dotnetsay --tool-path ~/bin`**

  Belirli bir Linux/macOS dizininde bulunan [dotnetdeyin](https://www.nuget.org/packages/dotnetsay/) küresel aracı 'nı güncelleştirir.

- **`dotnet tool update dotnetsay`**

  Geçerli dizin için yüklenen [dotnetsöyleme](https://www.nuget.org/packages/dotnetsay/) yerel aracını güncelleştirir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core araçları](global-tools.md)
