---
title: DotNet aracı geri yükleme komutu
description: DotNet aracı geri yükleme komutu, makinenizde geçerli dizin için kapsamdaki .NET yerel araçları 'nı yükler.
ms.date: 02/14/2020
ms.openlocfilehash: 87bdfb77cda361b800f107c565cbbed6ad75ec78
ms.sourcegitcommit: 4d5e25a46aa7cd0d29b4b9227b92987354d444c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98794854"
---
# <a name="dotnet-tool-restore"></a>dotnet tool restore

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 3,0 SDK ve sonraki sürümleri

## <a name="name"></a>Name

`dotnet tool restore` -Geçerli dizin için kapsamdaki .NET yerel araçlarını yükleme.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet tool restore
    [--configfile <FILE>] [--add-source <SOURCE>]
    [--tool-manifest <PATH_TO_MANIFEST_FILE>] [--disable-parallel]
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

- [.NET araçları](global-tools.md)
- [Öğretici: .NET CLı kullanarak .NET yerel aracını yükleyip kullanma](local-tools-how-to-use.md)
