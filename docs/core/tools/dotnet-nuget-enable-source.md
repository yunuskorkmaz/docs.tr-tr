---
title: dotnet nuget etkinleştirmek kaynak komutu
description: Dotnet nuget enable kaynak komutu NuGet yapılandırma dosyalarınızda varolan bir kaynağı etkinleştirin.
ms.date: 03/20/2020
ms.openlocfilehash: 1f18e7db6a6c8631bb432676dd97dabfad5b0ab8
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148563"
---
# <a name="dotnet-nuget-enable-source"></a>dotnet nuget etkinleştirmek kaynak

**Bu makale şu şekildedir:** ✔️ .NET Core 3.1.200 SDK ve sonraki sürümler

## <a name="name"></a>Adı

`dotnet nuget enable source`- Bir NuGet kaynağını etkinleştirin.

## <a name="synopsis"></a>Özet

```dotnetcli
dotnet nuget enable source <NAME> [--configfile]
dotnet nuget enable source [-h|--help]
```

## <a name="description"></a>Açıklama

Komut, `dotnet nuget enable source` NuGet yapılandırma dosyalarınızda varolan bir kaynağı etkinleştirir.

## <a name="arguments"></a>Bağımsız Değişkenler

- **`NAME`**

  Kaynağın adı.

## <a name="options"></a>Seçenekler

- **`--configfile`**

  NuGet yapılandırma dosyası. Belirtilirse, yalnızca bu dosyadaki ayarlar kullanılır. Belirtilmemişse, geçerli dizindeki yapılandırma dosyaları hiyerarşisi kullanılır. Daha fazla bilgi için [Ortak NuGet Yapılandırmaları'na](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior)bakın.

## <a name="examples"></a>Örnekler

- Adı olan bir `mySource`kaynağı etkinleştirin:

  ```dotnetcli
  dotnet nuget enable source mySource
  ```

## <a name="see-also"></a>Ayrıca bkz.

- [NuGet.config dosyalarındaki paket kaynak bölümleri](/nuget/reference/nuget-config-file#package-source-sections)

- [kaynaklar komutu (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
