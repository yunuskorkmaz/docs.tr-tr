---
title: Genel bakış
ms.date: 12/13/2019
description: Microsoft. Data. SQLite öğesine genel bakış
ms.openlocfilehash: a5dc1366cc0ddfcd5501e26bf2a994456bcd5d98
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447232"
---
# <a name="microsoftdatasqlite-overview"></a>Microsoft. Data. SQLite genel bakış

Microsoft. Data. SQLite, SQLite için hafif bir [ADO.net](../../../framework/data/adonet/index.md) sağlayıcısıdır. SQLite için [Entity Framework Core](/ef/core/) sağlayıcısı, bu kitaplığın üzerine kurulmuştur. Ancak, bağımsız olarak veya diğer veri erişimi kitaplıklarıyla da kullanılabilir.

## <a name="installation"></a>Yükleme

En son kararlı sürüm [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite)'de kullanılabilir.

### <a name="net-core-clitabnetcore-cli"></a>[.NET Core CLI](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite
```

### <a name="visual-studiotabvisual-studio"></a>[Visual Studio](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite
```

---

## <a name="usage"></a>Kullanım

Bu kitaplık bağlantılar, komutlar, veri okuyucuları vb. için ortak ADO.NET soyutlamalarını uygular.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_HelloWorld)]

## <a name="see-also"></a>Ayrıca bkz.

* [Bağlantı dizeleri](connection-strings.md)
* [API Başvurusu](/dotnet/api/?view=msdata-sqlite-3.0.0)
* [SQL Söz Dizimi](https://www.sqlite.org/lang.html)
