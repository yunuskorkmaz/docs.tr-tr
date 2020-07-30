---
title: DotNet aracı geri yükleme komutu
description: DotNet aracı geri yükleme komutu, makinenizde geçerli dizin için kapsamdaki .NET Core yerel araçları yükler.
ms.date: 02/14/2020
ms.openlocfilehash: ceef3274ec9d337f8c51009d5a8c27e808b14035
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302678"
---
# <a name="dotnet-tool-restore"></a>dotnet tool restore

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 3,0 SDK ve sonraki sürümleri

## <a name="name"></a>Name

`dotnet tool restore`-Makinenizde geçerli dizin için kapsamdaki .NET Core yerel araçları yüklenir.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet tool restore
    [--configfile <FILE>] [--add-source <SOURCE>]
    [tool-manifest <PATH_TO_MANIFEST_FILE>] [--disable-parallel]
    [--ignore-failed-sources] [--no-cache] [--interactive]
    [-v|--verbosity <LEVEL>]

dotnet tool restore -h|--help
```

## <a name="description"></a>Description

`dotnet tool restore`Komutu, geçerli dizinin kapsamındaki araç bildirim dosyasını bulur ve içinde listelenen araçları kurar. Bildirim dosyaları hakkında daha fazla bilgi için bkz. [yerel araç yükleyip](global-tools.md#install-a-local-tool) [yerel bir araç çağırma](global-tools.md#invoke-a-local-tool).

## <a name="options"></a>Seçenekler

- **`--configfile <FILE>`**

  Kullanılacak NuGet yapılandırma (*nuget.config*) dosyası.

- **`--add-source <SOURCE>`**

  Yükleme sırasında kullanmak üzere ek bir NuGet paketi kaynağı ekler.

- **`--tool-manifest <PATH>`**

  Bildirim dosyasının yolu.

- **`--disable-parallel`**

  Paralel olarak birden çok projenin geri yüklenmesini engelleyin.

- **`--ignore-failed-sources`**

  Paket kaynağı başarısızlıklarını uyarı olarak değerlendirin.

- **`--no-cache`**

  Paketleri ve http isteklerini önbelleğe vermeyin.

- **`--interactive`**

  Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir (örneğin, kimlik doğrulamasını tamamlamaya).

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`-v|--verbosity <LEVEL>`**

  Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` .

## <a name="example"></a>Örnek

- **`dotnet tool restore`**

  Geçerli dizin için yerel araçları geri yükler.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core araçları](global-tools.md)
- [Öğretici: .NET Core CLI kullanarak bir .NET Core yerel aracı yükleyip kullanın](local-tools-how-to-use.md)
