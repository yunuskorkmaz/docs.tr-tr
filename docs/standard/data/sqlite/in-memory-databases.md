---
title: Bellek içi veritabanları
ms.date: 12/13/2019
description: Bellek içi SQLite veritabanlarını nasıl kullanacağınızı öğrenin.
ms.openlocfilehash: 408c81f538e27dcfffad20db74b7809912b7905f
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391214"
---
# <a name="in-memory-databases"></a><span data-ttu-id="e03bb-103">Bellek içi veritabanları</span><span class="sxs-lookup"><span data-stu-id="e03bb-103">In-memory databases</span></span>

<span data-ttu-id="e03bb-104">SQLite bellek içi veritabanları, diskte değil, tamamen bellekte depolanan veritabanlardır.</span><span class="sxs-lookup"><span data-stu-id="e03bb-104">SQLite in-memory databases are databases stored entirely in memory, not on disk.</span></span> <span data-ttu-id="e03bb-105">Bellek içi veritabanı oluşturmak için özel `:memory:` veri kaynağı dosya adını kullanın.</span><span class="sxs-lookup"><span data-stu-id="e03bb-105">Use the special data source filename `:memory:` to create an in-memory database.</span></span> <span data-ttu-id="e03bb-106">Bağlantı kapatıldığında veritabanı silinir.</span><span class="sxs-lookup"><span data-stu-id="e03bb-106">When the connection is closed, the database is deleted.</span></span> <span data-ttu-id="e03bb-107">Kullanırken `:memory:`, her bağlantı kendi veritabanını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e03bb-107">When using `:memory:`, each connection creates its own database.</span></span>

```ConnectionString
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a><span data-ttu-id="e03bb-108">Paylaşılabilir bellek içi veritabanları</span><span class="sxs-lookup"><span data-stu-id="e03bb-108">Shareable in-memory databases</span></span>

<span data-ttu-id="e03bb-109">Bellek içi veritabanları, bağlantı dizesinde ve `Mode=Memory` `Cache=Shared` kullanılarak birden çok bağlantı arasında paylaşılabilir.</span><span class="sxs-lookup"><span data-stu-id="e03bb-109">In-memory databases can be shared between multiple connections by using `Mode=Memory` and `Cache=Shared` in the connection string.</span></span> <span data-ttu-id="e03bb-110">`Data Source` Anahtar sözcüğü, bellek içi veritabanına bir ad vermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e03bb-110">The `Data Source` keyword is used to give the in-memory database a name.</span></span> <span data-ttu-id="e03bb-111">Aynı adı kullanan bağlantı dizeleri aynı bellek içi veritabanına erişir.</span><span class="sxs-lookup"><span data-stu-id="e03bb-111">Connection strings using the same name will access the same in-memory database.</span></span> <span data-ttu-id="e03bb-112">En az bir bağlantı açık kaldığı sürece veritabanı devam eder.</span><span class="sxs-lookup"><span data-stu-id="e03bb-112">The database persists as long as at least one connection to it remains open.</span></span> <span data-ttu-id="e03bb-113">GitHub 'da kullanılabilir olduğunu gösteren bir [örnek](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) .</span><span class="sxs-lookup"><span data-stu-id="e03bb-113">A [sample](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) demonstrating this is available on GitHub.</span></span>

```ConnectionString
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
