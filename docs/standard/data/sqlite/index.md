---
title: Genel Bakış
ms.date: 12/13/2019
description: Microsoft. Data. SQLite öğesine genel bakış
ms.openlocfilehash: 7c952848f7e7ea04f11fe9340f77a1f376a1be07
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552446"
---
# <a name="microsoftdatasqlite-overview"></a>Microsoft. Data. SQLite genel bakış

Microsoft. Data. SQLite, SQLite için hafif bir [ADO.net](../../../framework/data/adonet/index.md) sağlayıcısıdır. SQLite için [Entity Framework Core](/ef/core/) sağlayıcısı, bu kitaplığın üzerine kurulmuştur. Ancak, bağımsız olarak veya diğer veri erişimi kitaplıklarıyla da kullanılabilir.

## <a name="installation"></a>Yükleme

En son kararlı sürüm [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite)'de kullanılabilir.

### <a name="net-core-cli"></a>[.NET Core CLI](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite
```

### <a name="visual-studio"></a>[Visual Studio](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite
```

---

## <a name="usage"></a>Kullanım

Bu kitaplık bağlantılar, komutlar, veri okuyucuları vb. için ortak ADO.NET soyutlamalarını uygular.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_HelloWorld)]

## <a name="see-also"></a>Ayrıca bkz.

* [Bağlantı dizeleri](connection-strings.md)
* [API Başvurusu](../../../../api/index.md?view=msdata-sqlite-3.0)
* [SQL Söz Dizimi](https://www.sqlite.org/lang.html)
