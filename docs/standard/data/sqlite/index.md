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
# <a name="microsoftdatasqlite-overview"></a><span data-ttu-id="d991d-103">Microsoft. Data. SQLite genel bakış</span><span class="sxs-lookup"><span data-stu-id="d991d-103">Microsoft.Data.Sqlite overview</span></span>

<span data-ttu-id="d991d-104">Microsoft. Data. SQLite, SQLite için hafif bir [ADO.net](../../../framework/data/adonet/index.md) sağlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="d991d-104">Microsoft.Data.Sqlite is a lightweight [ADO.NET](../../../framework/data/adonet/index.md) provider for SQLite.</span></span> <span data-ttu-id="d991d-105">SQLite için [Entity Framework Core](/ef/core/) sağlayıcısı, bu kitaplığın üzerine kurulmuştur.</span><span class="sxs-lookup"><span data-stu-id="d991d-105">The [Entity Framework Core](/ef/core/) provider for SQLite is built on top of this library.</span></span> <span data-ttu-id="d991d-106">Ancak, bağımsız olarak veya diğer veri erişimi kitaplıklarıyla da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d991d-106">However, it can also be used independently or with other data access libraries.</span></span>

## <a name="installation"></a><span data-ttu-id="d991d-107">Yükleme</span><span class="sxs-lookup"><span data-stu-id="d991d-107">Installation</span></span>

<span data-ttu-id="d991d-108">En son kararlı sürüm [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite)'de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d991d-108">The latest stable version is available on [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite).</span></span>

### <a name="net-core-cli"></a>[<span data-ttu-id="d991d-109">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="d991d-109">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite
```

### <a name="visual-studio"></a>[<span data-ttu-id="d991d-110">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d991d-110">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite
```

---

## <a name="usage"></a><span data-ttu-id="d991d-111">Kullanım</span><span class="sxs-lookup"><span data-stu-id="d991d-111">Usage</span></span>

<span data-ttu-id="d991d-112">Bu kitaplık bağlantılar, komutlar, veri okuyucuları vb. için ortak ADO.NET soyutlamalarını uygular.</span><span class="sxs-lookup"><span data-stu-id="d991d-112">This library implements the common ADO.NET abstractions for connections, commands, data readers, and so on.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_HelloWorld)]

## <a name="see-also"></a><span data-ttu-id="d991d-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d991d-113">See also</span></span>

* [<span data-ttu-id="d991d-114">Bağlantı dizeleri</span><span class="sxs-lookup"><span data-stu-id="d991d-114">Connection strings</span></span>](connection-strings.md)
* [<span data-ttu-id="d991d-115">API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="d991d-115">API Reference</span></span>](../../../../api/index.md?view=msdata-sqlite-3.0)
* [<span data-ttu-id="d991d-116">SQL Söz Dizimi</span><span class="sxs-lookup"><span data-stu-id="d991d-116">SQL Syntax</span></span>](https://www.sqlite.org/lang.html)
