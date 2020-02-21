---
title: DotNet aracı geri yükleme komutu
description: DotNet aracı geri yükleme komutu, makinenizde geçerli dizin için kapsamdaki .NET Core yerel araçları yükler.
ms.date: 02/14/2020
ms.openlocfilehash: 2900d431987661a9232ceed10d9a424093f8be45
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543910"
---
# <a name="dotnet-tool-restore"></a>DotNet aracı geri yükleme

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 3,0 SDK ve sonraki sürümleri

## <a name="name"></a>Adı

`dotnet tool restore`-makinenizde geçerli dizin için kapsamdaki .NET Core yerel araçları yüklenir.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet tool restore <PACKAGE_NAME> [--configfile] [--add-source] [tool-manifest] [--disable-parallel] [--ignore-failed-sources] [--no-cache] [-interactive] [-v|--verbosity]
dotnet tool restore <-h|--help>
```

## <a name="description"></a>Açıklama

`dotnet tool restore` komutu, geçerli dizinin kapsamındaki araç bildirim dosyasını bulur ve içinde listelenen araçları kurar. Bildirim dosyaları hakkında daha fazla bilgi için bkz. [yerel araç yükleyip](global-tools.md#install-a-local-tool) [yerel bir araç çağırma](global-tools.md#invoke-a-local-tool).

## <a name="arguments"></a>Bağımsız Değişkenler

- **`PACKAGE_NAME`**

Yüklenecek .NET Core aracını içeren NuGet paketinin adı/KIMLIĞI.

## <a name="options"></a>Seçenekler

- **`--configfile <FILE>`**

  Kullanılacak NuGet yapılandırma (*NuGet. config*) dosyası.

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

  Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.

## <a name="example"></a>Örnek

- **`dotnet tool restore`**

  Geçerli dizin için yerel araçları geri yükler.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core araçları](global-tools.md)
