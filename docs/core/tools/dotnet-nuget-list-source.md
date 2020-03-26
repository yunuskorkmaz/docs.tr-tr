---
title: dotnet nuget listesi kaynak komutu
description: Dotnet nuget listesi kaynak komutu, NuGet yapılandırma dosyalarınızdaki tüm varolan kaynakları listeler.
ms.date: 03/20/2020
ms.openlocfilehash: 4d7bc3dbd3ab5eb14c1ebf592044b685d28355cd
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148577"
---
# <a name="dotnet-nuget-list-source"></a>dotnet nuget listesi kaynak

**Bu makale şu şekildedir:** ✔️ .NET Core 3.1.200 SDK ve sonraki sürümler

## <a name="name"></a>Adı

`dotnet nuget list source`- Tüm yapılandırılan NuGet kaynaklarını listeler.

## <a name="synopsis"></a>Özet

```dotnetcli
dotnet nuget list source [--format] [--configfile]
dotnet nuget list source [-h|--help]
```

## <a name="description"></a>Açıklama

Komut, `dotnet nuget list source` NuGet yapılandırma dosyalarınızdaki tüm varolan kaynakları listeler.

## <a name="options"></a>Seçenekler

- **`--configfile`**

  NuGet yapılandırma dosyası. Belirtilirse, yalnızca bu dosyadaki ayarlar kullanılır. Belirtilmemişse, geçerli dizindeki yapılandırma dosyaları hiyerarşisi kullanılır. Daha fazla bilgi için [Ortak NuGet Yapılandırmaları'na](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior)bakın.

- **`--format`**

  Liste komutu çıktısının `Detailed` biçimi: (varsayılan) ve `Short`.

## <a name="examples"></a>Örnekler

- Geçerli dizinden yapılandırılan kaynakları listele:

  ```dotnetcli
  dotnet nuget list source
  ```

## <a name="see-also"></a>Ayrıca bkz.

- [NuGet.config dosyalarındaki paket kaynak bölümleri](/nuget/reference/nuget-config-file#package-source-sections)

- [kaynaklar komutu (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
