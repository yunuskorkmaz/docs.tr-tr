---
title: DotNet NuGet kaynağı Kaldır komutu
description: DotNet NuGet Remove Source komutu, var olan bir kaynağı NuGet yapılandırma dosyalarınızda kaldırır.
ms.date: 03/20/2020
ms.openlocfilehash: b5575c31c0008d6e3e5a2e52906a076614217dd0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537904"
---
# <a name="dotnet-nuget-remove-source"></a>dotnet nuget remove source

**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 3.1.200 SDK ve sonraki sürümleri

## <a name="name"></a>Name

`dotnet nuget remove source` -Bir NuGet kaynağını kaldırın.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet nuget remove source <NAME> [--configfile <FILE>]

dotnet nuget remove source -h|--help
```

## <a name="description"></a>Description

`dotnet nuget remove source`Komut varolan bir kaynağı NuGet yapılandırma dosyalarından kaldırır.

## <a name="arguments"></a>Arguments

- **`NAME`**

  Kaynağın adı.

## <a name="options"></a>Seçenekler

- **`--configfile`**

  NuGet yapılandırma dosyası. Belirtilmişse, yalnızca bu dosyadaki ayarlar kullanılacaktır. Belirtilmemişse, geçerli dizinden yapılandırma dosyalarının hiyerarşisi kullanılacaktır. Daha fazla bilgi için bkz. [ortak NuGet yapılandırması](/nuget/consume-packages/configuring-nuget-behavior).

## <a name="examples"></a>Örnekler

- Şu ada sahip bir kaynağı Kaldır `mySource` :

  ```dotnetcli
  dotnet nuget remove source mySource
  ```

## <a name="see-also"></a>Ayrıca bkz.

- [NuGet.config dosyalardaki paket kaynak bölümleri](/nuget/reference/nuget-config-file#package-source-sections)

- [Sources komutu (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
