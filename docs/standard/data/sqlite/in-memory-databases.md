---
title: Bellek içi veritabanları
ms.date: 12/13/2019
description: Bellek içi SQLite veritabanlarını nasıl kullanacağınızı öğrenin.
ms.openlocfilehash: 16a9b6536fbfede203c24b757e96e28e7c49dc05
ms.sourcegitcommit: cbdc0f4fd39172b5191a35200c33d5030774463c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75777411"
---
# <a name="in-memory-databases"></a><span data-ttu-id="37ffa-103">Bellek içi veritabanları</span><span class="sxs-lookup"><span data-stu-id="37ffa-103">In-memory databases</span></span>

<span data-ttu-id="37ffa-104">SQLite bellek içi veritabanları, diskte değil, tamamen bellekte depolanan veritabanlardır.</span><span class="sxs-lookup"><span data-stu-id="37ffa-104">SQLite in-memory databases are databases stored entirely in memory, not on disk.</span></span> <span data-ttu-id="37ffa-105">Bellek içi veritabanı oluşturmak için `:memory:` özel veri kaynağı dosya adı kullanın.</span><span class="sxs-lookup"><span data-stu-id="37ffa-105">Use the special data source filename `:memory:` to create an in-memory database.</span></span> <span data-ttu-id="37ffa-106">Bağlantı kapatıldığında veritabanı silinir.</span><span class="sxs-lookup"><span data-stu-id="37ffa-106">When the connection is closed, the database is deleted.</span></span> <span data-ttu-id="37ffa-107">`:memory:`kullanırken, her bağlantı kendi veritabanını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="37ffa-107">When using `:memory:`, each connection creates its own database.</span></span>

```ConnectionString
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a><span data-ttu-id="37ffa-108">Paylaşılabilir bellek içi veritabanları</span><span class="sxs-lookup"><span data-stu-id="37ffa-108">Shareable in-memory databases</span></span>

<span data-ttu-id="37ffa-109">Bellek içi veritabanları, bağlantı dizesinde `Mode=Memory` ve `Cache=Shared` kullanılarak birden çok bağlantı arasında paylaşılabilir.</span><span class="sxs-lookup"><span data-stu-id="37ffa-109">In-memory databases can be shared between multiple connections by using `Mode=Memory` and `Cache=Shared` in the connection string.</span></span> <span data-ttu-id="37ffa-110">`Data Source` anahtar sözcüğü, bellek içi veritabanına bir ad vermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="37ffa-110">The `Data Source` keyword is used to give the in-memory database a name.</span></span> <span data-ttu-id="37ffa-111">Aynı adı kullanan bağlantı dizeleri aynı bellek içi veritabanına erişir.</span><span class="sxs-lookup"><span data-stu-id="37ffa-111">Connection strings using the same name will access the same in-memory database.</span></span> <span data-ttu-id="37ffa-112">En az bir bağlantı açık kaldığı sürece veritabanı devam eder.</span><span class="sxs-lookup"><span data-stu-id="37ffa-112">The database persists as long as at least one connection to it remains open.</span></span> <span data-ttu-id="37ffa-113">GitHub 'da kullanılabilir olduğunu gösteren bir [örnek](https://github.com/dotnet/samples/blob/master/snippets/standard/data/sqlite/InMemorySample/Program.cs) .</span><span class="sxs-lookup"><span data-stu-id="37ffa-113">A [sample](https://github.com/dotnet/samples/blob/master/snippets/standard/data/sqlite/InMemorySample/Program.cs) demonstrating this is available on GitHub.</span></span>

```ConnectionString
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
