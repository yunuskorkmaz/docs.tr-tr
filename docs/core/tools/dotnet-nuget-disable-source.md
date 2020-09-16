---
title: DotNet NuGet kaynak komutunu devre dışı bırak
description: DotNet NuGet kaynak komutu, NuGet yapılandırma dosyalarınızda var olan bir kaynağı devre dışı bırakır.
ms.date: 03/20/2020
ms.openlocfilehash: af37a6589cebaf0501ee5647ebadb83125d0f56e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537957"
---
# <a name="dotnet-nuget-disable-source"></a>dotnet nuget disable source

**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 3.1.200 SDK ve sonraki sürümleri

## <a name="name"></a>Name

`dotnet nuget disable source` -Bir NuGet kaynağını devre dışı bırakın.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet nuget disable source <NAME> [--configfile <FILE>]

dotnet nuget disable source -h|--help
```

## <a name="description"></a>Description

`dotnet nuget disable source`Komut, NuGet yapılandırma dosyalarınızda var olan bir kaynağı devre dışı bırakır.

## <a name="arguments"></a>Arguments

- **`NAME`**

  Kaynağın adı.

## <a name="options"></a>Seçenekler

- **`--configfile <FILE>`**

  NuGet yapılandırma dosyası. Belirtilmişse, yalnızca bu dosyadaki ayarlar kullanılacaktır. Belirtilmemişse, geçerli dizinden yapılandırma dosyalarının hiyerarşisi kullanılacaktır. Daha fazla bilgi için bkz. [ortak NuGet yapılandırması](/nuget/consume-packages/configuring-nuget-behavior).

## <a name="examples"></a>Örnekler

- Şu ada sahip bir kaynağı devre dışı bırak `mySource` :

  ```dotnetcli
  dotnet nuget disable source mySource
  ```

## <a name="see-also"></a>Ayrıca bkz.

- [NuGet.config dosyalardaki paket kaynak bölümleri](/nuget/reference/nuget-config-file#package-source-sections)

- [Sources komutu (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
