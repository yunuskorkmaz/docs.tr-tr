---
title: DotNet NuGet liste kaynağı komutu
description: DotNet NuGet liste kaynağı komutu, NuGet yapılandırma dosyalarınızda var olan tüm kaynakları listeler.
ms.date: 03/20/2020
ms.openlocfilehash: 071061e32aa1bf888e197ec6bf97f4e4f6859f0b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537905"
---
# <a name="dotnet-nuget-list-source"></a>dotnet nuget list source

**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 3.1.200 SDK ve sonraki sürümleri

## <a name="name"></a>Name

`dotnet nuget list source` -Tüm yapılandırılmış NuGet kaynaklarını listeler.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet nuget list source [--format [Detailed|Short]] [--configfile <FILE>]

dotnet nuget list source -h|--help
```

## <a name="description"></a>Description

`dotnet nuget list source`Komut, NuGet yapılandırma dosyalarınızda var olan tüm kaynakları listeler.

## <a name="options"></a>Seçenekler

- **`--configfile <FILE>`**

  NuGet yapılandırma dosyası. Belirtilmişse, yalnızca bu dosyadaki ayarlar kullanılacaktır. Belirtilmemişse, geçerli dizinden yapılandırma dosyalarının hiyerarşisi kullanılacaktır. Daha fazla bilgi için bkz. [ortak NuGet yapılandırması](/nuget/consume-packages/configuring-nuget-behavior).

- **`--format [Detailed|Short]`**

  List komutunun çıktısının biçimi: `Detailed` (varsayılan) ve `Short` .

## <a name="examples"></a>Örnekler

- Geçerli dizinden yapılandırılmış kaynakları Listele:

  ```dotnetcli
  dotnet nuget list source
  ```

## <a name="see-also"></a>Ayrıca bkz.

- [NuGet.config dosyalardaki paket kaynak bölümleri](/nuget/reference/nuget-config-file#package-source-sections)

- [Sources komutu (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
