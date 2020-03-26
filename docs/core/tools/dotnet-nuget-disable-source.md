---
title: dotnet nuget devre dışı kaynak komutu
description: Dotnet nuget devre dışı kaynak komutu NuGet yapılandırma dosyalarınızdaki varolan bir kaynağı devre dışı kılabilir.
ms.date: 03/20/2020
ms.openlocfilehash: 5aa16c842bcddeead180fdeec3d9dcdda33f7ed9
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148556"
---
# <a name="dotnet-nuget-disable-source"></a>dotnet nuget devre dışı kaynak

**Bu makale şu şekildedir:** ✔️ .NET Core 3.1.200 SDK ve sonraki sürümler

## <a name="name"></a>Adı

`dotnet nuget disable source`- Bir NuGet kaynağını devre dışı kalın.

## <a name="synopsis"></a>Özet

```dotnetcli
dotnet nuget disable source <NAME> [--configfile]
dotnet nuget disable source [-h|--help]
```

## <a name="description"></a>Açıklama

Komut, `dotnet nuget disable source` NuGet yapılandırma dosyalarınızdaki varolan bir kaynağı devre dışı kılabilir.

## <a name="arguments"></a>Bağımsız Değişkenler

- **`NAME`**

  Kaynağın adı.

## <a name="options"></a>Seçenekler

- **`--configfile`**

  NuGet yapılandırma dosyası. Belirtilirse, yalnızca bu dosyadaki ayarlar kullanılır. Belirtilmemişse, geçerli dizindeki yapılandırma dosyaları hiyerarşisi kullanılır. Daha fazla bilgi için [Ortak NuGet Yapılandırmaları'na](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior)bakın.

## <a name="examples"></a>Örnekler

- Adı `mySource`olan bir kaynağı devre dışı:

  ```dotnetcli
  dotnet nuget disable source mySource
  ```

## <a name="see-also"></a>Ayrıca bkz.

- [NuGet.config dosyalarındaki paket kaynak bölümleri](/nuget/reference/nuget-config-file#package-source-sections)

- [kaynaklar komutu (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
