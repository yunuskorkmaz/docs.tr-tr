---
title: dotnet nuget kaldırmak kaynak komutu
description: Kaynak komutunu kaldır komutu dotnet nuget'i NuGet yapılandırma dosyalarınızdan varolan bir kaynağı kaldırır.
ms.date: 03/20/2020
ms.openlocfilehash: 65c97b98ab50121fb4ebc184da65f021c16e0634
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148542"
---
# <a name="dotnet-nuget-remove-source"></a>dotnet nuget kaynak kaldırmak

**Bu makale şu şekildedir:** ✔️ .NET Core 3.1.200 SDK ve sonraki sürümler

## <a name="name"></a>Adı

`dotnet nuget remove source`- NuGet kaynağını kaldırın.

## <a name="synopsis"></a>Özet

```dotnetcli
dotnet nuget remove source <NAME> [--configfile]
dotnet nuget remove source [-h|--help]
```

## <a name="description"></a>Açıklama

Komut, `dotnet nuget remove source` Varolan bir kaynağı NuGet yapılandırma dosyalarınızdan kaldırır.

## <a name="arguments"></a>Bağımsız Değişkenler

- **`NAME`**

  Kaynağın adı.

## <a name="options"></a>Seçenekler

- **`--configfile`**

  NuGet yapılandırma dosyası. Belirtilirse, yalnızca bu dosyadaki ayarlar kullanılır. Belirtilmemişse, geçerli dizindeki yapılandırma dosyaları hiyerarşisi kullanılır. Daha fazla bilgi için [Ortak NuGet Yapılandırmaları'na](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior)bakın.

## <a name="examples"></a>Örnekler

- Adı olan bir `mySource`kaynağı kaldırın:

  ```dotnetcli
  dotnet nuget remove source mySource
  ```

## <a name="see-also"></a>Ayrıca bkz.

- [NuGet.config dosyalarındaki paket kaynak bölümleri](/nuget/reference/nuget-config-file#package-source-sections)

- [kaynaklar komutu (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
