---
title: DotNet NuGet kaynak komutunu etkinleştir
description: DotNet NuGet kaynak komutu, NuGet yapılandırma dosyalarınızda var olan bir kaynağı etkinleştirir.
ms.date: 03/20/2020
ms.openlocfilehash: b727844dd7d7cc82476e94a3f0ec4ecc6559d5ed
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537940"
---
# <a name="dotnet-nuget-enable-source"></a>dotnet nuget enable source

**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 3.1.200 SDK ve sonraki sürümleri

## <a name="name"></a>Name

`dotnet nuget enable source` -Bir NuGet kaynağını etkinleştirin.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet nuget enable source <NAME> [--configfile <FILE>]

dotnet nuget enable source -h|--help
```

## <a name="description"></a>Description

`dotnet nuget enable source`Komut, NuGet yapılandırma dosyalarınızda var olan bir kaynağı mümkün bir şekilde sunar.

## <a name="arguments"></a>Arguments

- **`NAME`**

  Kaynağın adı.

## <a name="options"></a>Seçenekler

- **`--configfile <FILE>`**

  NuGet yapılandırma dosyası. Belirtilmişse, yalnızca bu dosyadaki ayarlar kullanılacaktır. Belirtilmemişse, geçerli dizinden yapılandırma dosyalarının hiyerarşisi kullanılacaktır. Daha fazla bilgi için bkz. [ortak NuGet yapılandırması](/nuget/consume-packages/configuring-nuget-behavior).

## <a name="examples"></a>Örnekler

- Şu ada sahip bir kaynağı etkinleştirin `mySource` :

  ```dotnetcli
  dotnet nuget enable source mySource
  ```

## <a name="see-also"></a>Ayrıca bkz.

- [NuGet.config dosyalardaki paket kaynak bölümleri](/nuget/reference/nuget-config-file#package-source-sections)

- [Sources komutu (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
