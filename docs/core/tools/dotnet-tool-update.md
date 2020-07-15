---
title: DotNet Aracı güncelleştirme komutu
description: DotNet Aracı güncelleştirme komutu makinenizde belirtilen .NET Core aracını güncelleştirir.
ms.date: 07/08/2020
ms.openlocfilehash: a212fbb40af68019c1bc9a63963d960292be6b08
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86308877"
---
# <a name="dotnet-tool-update"></a>dotnet tool update

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri

## <a name="name"></a>Name

`dotnet tool update`-Makinenizde belirtilen [.NET Core aracını](global-tools.md) güncelleştirir.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet tool update <PACKAGE_ID> -g|--global
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--disable-parallel] [--framework <FRAMEWORK>]
    [--ignore-failed-sources] [--interactive] [--no-cache]
    [-v|--verbosity <LEVEL>] [--version <VERSION>]

dotnet tool update <PACKAGE_ID> --tool-path <PATH>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--disable-parallel] [--framework <FRAMEWORK>]
    [--ignore-failed-sources] [--interactive] [--no-cache]
    [-v|--verbosity <LEVEL>] [--version <VERSION>]

dotnet tool update <PACKAGE_ID> --local
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--disable-parallel] [--framework <FRAMEWORK>]
    [--ignore-failed-sources] [--interactive] [--no-cache]
    [--tool-manifest <PATH>]
    [-v|--verbosity <LEVEL>] [--version <VERSION>]

dotnet tool update -h|--help
```

## <a name="description"></a>Description

Bu `dotnet tool update` komut, makinenizde .NET Core araçlarını paketin en son kararlı sürümüne güncelleştirmeniz için bir yol sağlar. Komut, bir aracı kaldırır ve etkin bir şekilde güncelleştiren bir araç yükler. Komutunu kullanmak için aşağıdaki seçeneklerden birini belirtin:

* Varsayılan konumda yüklü olan küresel bir aracı güncelleştirmek için, seçeneğini kullanın. `--global`
* Özel bir konuma yüklenmiş olan küresel bir aracı güncelleştirmek için `--tool-path` seçeneğini kullanın.
* Yerel bir aracı güncelleştirmek için `--local` seçeneğini kullanın.

**Yerel araçlar .NET Core SDK 3,0 ' den başlayarak kullanılabilir.**

## <a name="arguments"></a>Arguments

- **`PACKAGE_ID`**

  Güncelleştirilecek .NET Core küresel aracını içeren NuGet paketinin adı/KIMLIĞI. [DotNet araç listesi](dotnet-tool-list.md) komutunu kullanarak paket adını bulabilirsiniz.

## <a name="options"></a>Seçenekler

- **`--add-source <SOURCE>`**

  Yükleme sırasında kullanmak üzere ek bir NuGet paketi kaynağı ekler.

- **`--configfile <FILE>`**

  Kullanılacak NuGet yapılandırma (*nuget.config*) dosyası.

- **`--disable-parallel`**

  Paralel olarak birden çok projenin geri yüklenmesini engelleyin.

- **`--framework <FRAMEWORK>`**

  Aracının güncelleştirilmesi için [hedef çerçeveyi](../../standard/frameworks.md) belirtir.

- **`--ignore-failed-sources`**

  Paket kaynağı başarısızlıklarını uyarı olarak değerlendirin.

- **`--interactive`**

  Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir (örneğin, kimlik doğrulamasını tamamlamaya).

- **`--local`**

  Aracı ve yerel araç bildirimini güncelleştirin. `--global`Seçeneği veya seçeneği ile birleştirilemez `--tool-path` .

- **`--no-cache`**

  Paketleri ve HTTP isteklerini önbelleğe vermeyin.

- **`--tool-manifest <PATH>`**

  Bildirim dosyasının yolu.

- **`--tool-path <PATH>`**

  Genel aracın yüklendiği konumu belirtir. YOL mutlak veya göreli olabilir. `--global`Seçeneğiyle birleştirilemez. Her ikisini de atlayarak, `--global` `--tool-path` güncelleşmiş olan aracın yerel bir araç olduğunu belirtir.

- **`--version <VERSION>`**

  Güncelleştirilecek araç paketinin sürüm aralığı. Bu, sürümleri düşürme için kullanılamaz, `uninstall` önce yeni sürümlere sahip olmalısınız.

- **`-g|--global`**

  Güncelleştirmenin Kullanıcı genelindeki bir araç için olduğunu belirtir. `--tool-path`Seçeneğiyle birleştirilemez. Her ikisini de atlayarak, `--global` `--tool-path` güncelleşmiş olan aracın yerel bir araç olduğunu belirtir.

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`-v|--verbosity <LEVEL>`**

  Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` .

## <a name="examples"></a>Örnekler

- **`dotnet tool update -g dotnetsay`**

  [Dotnetsay](https://www.nuget.org/packages/dotnetsay/) küresel aracını güncelleştirir.

- **`dotnet tool update dotnetsay --tool-path c:\global-tools`**

  Belirli bir Windows dizininde bulunan [dotnetdeyin](https://www.nuget.org/packages/dotnetsay/) küresel aracı 'nı güncelleştirir.

- **`dotnet tool update dotnetsay --tool-path ~/bin`**

  Belirli bir Linux/macOS dizininde bulunan [dotnetdeyin](https://www.nuget.org/packages/dotnetsay/) küresel aracı 'nı güncelleştirir.

- **`dotnet tool update dotnetsay`**

  Geçerli dizin için yüklenen [dotnetsöyleme](https://www.nuget.org/packages/dotnetsay/) yerel aracını güncelleştirir.

- **`dotnet tool update -g dotnetsay --version 2.0.*`**

  [Dotnetsöyleyin](https://www.nuget.org/packages/dotnetsay/) küresel aracını en son düzeltme eki sürümüne, ana sürümüne `2` ve ikincil sürümüne günceller `0` .

- **`dotnet tool update -g dotnetsay --version (2.0.*,2.1.4)`**

  [Dotnetdeyin](https://www.nuget.org/packages/dotnetsay/) küresel aracı 'nı belirtilen aralıktaki en düşük sürümle güncelleştirir `(> 2.0.0 && < 2.1.4)` , sürüm `2.1.0` yüklenir. Anlamsal sürüm oluşturma aralıkları hakkında daha fazla bilgi için bkz. [NuGet paketleme sürümü aralıkları](/nuget/concepts/package-versioning#version-ranges).

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core araçları](global-tools.md)
- [Anlamsal sürüm oluşturma](https://semver.org)
- [Öğretici: .NET Core CLI kullanarak .NET Core küresel aracı 'nı yükleyip kullanın](global-tools-how-to-use.md)
- [Öğretici: .NET Core CLI kullanarak bir .NET Core yerel aracı yükleyip kullanın](local-tools-how-to-use.md)
