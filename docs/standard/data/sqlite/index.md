---
title: Genel Bakış
ms.date: 12/13/2019
description: Microsoft. Data. SQLite öğesine genel bakış
ms.openlocfilehash: e84c68f0615f187e8dea7ab87ac917c0ad796a1c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77543605"
---
# <a name="microsoftdatasqlite-overview"></a><span data-ttu-id="363bf-103">Microsoft. Data. SQLite genel bakış</span><span class="sxs-lookup"><span data-stu-id="363bf-103">Microsoft.Data.Sqlite overview</span></span>

<span data-ttu-id="363bf-104">Microsoft. Data. SQLite, SQLite için hafif bir [ADO.net](../../../framework/data/adonet/index.md) sağlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="363bf-104">Microsoft.Data.Sqlite is a lightweight [ADO.NET](../../../framework/data/adonet/index.md) provider for SQLite.</span></span> <span data-ttu-id="363bf-105">SQLite için [Entity Framework Core](/ef/core/) sağlayıcısı, bu kitaplığın üzerine kurulmuştur.</span><span class="sxs-lookup"><span data-stu-id="363bf-105">The [Entity Framework Core](/ef/core/) provider for SQLite is built on top of this library.</span></span> <span data-ttu-id="363bf-106">Ancak, bağımsız olarak veya diğer veri erişimi kitaplıklarıyla da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="363bf-106">However, it can also be used independently or with other data access libraries.</span></span>

## <a name="installation"></a><span data-ttu-id="363bf-107">Yükleme</span><span class="sxs-lookup"><span data-stu-id="363bf-107">Installation</span></span>

<span data-ttu-id="363bf-108">En son kararlı sürüm [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite)'de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="363bf-108">The latest stable version is available on [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite).</span></span>

### <a name="net-core-cli"></a>[<span data-ttu-id="363bf-109">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="363bf-109">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite
```

### <a name="visual-studio"></a>[<span data-ttu-id="363bf-110">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="363bf-110">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite
```

---

## <a name="usage"></a><span data-ttu-id="363bf-111">Kullanım</span><span class="sxs-lookup"><span data-stu-id="363bf-111">Usage</span></span>

<span data-ttu-id="363bf-112">Bu kitaplık bağlantılar, komutlar, veri okuyucuları vb. için ortak ADO.NET soyutlamalarını uygular.</span><span class="sxs-lookup"><span data-stu-id="363bf-112">This library implements the common ADO.NET abstractions for connections, commands, data readers, and so on.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_HelloWorld)]

## <a name="see-also"></a><span data-ttu-id="363bf-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="363bf-113">See also</span></span>

* [<span data-ttu-id="363bf-114">Bağlantı dizeleri</span><span class="sxs-lookup"><span data-stu-id="363bf-114">Connection strings</span></span>](connection-strings.md)
* [<span data-ttu-id="363bf-115">API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="363bf-115">API Reference</span></span>](/dotnet/api/?view=msdata-sqlite-3.0)
* [<span data-ttu-id="363bf-116">SQL Söz Dizimi</span><span class="sxs-lookup"><span data-stu-id="363bf-116">SQL Syntax</span></span>](https://www.sqlite.org/lang.html)
