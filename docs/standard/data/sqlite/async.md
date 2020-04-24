---
title: Zaman uyumsuz sınırlamalar
ms.date: 12/13/2019
description: Zaman uyumsuz API 'lerin ve bunun yerine kullanabileceğiniz bazı alternatiflere ilişkin sınırlamaları açıklar.
ms.openlocfilehash: 350237dc5c03023f60e9680e8b9c94aabb62606f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447085"
---
# <a name="async-limitations"></a><span data-ttu-id="f543d-103">Zaman uyumsuz sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="f543d-103">Async limitations</span></span>

<span data-ttu-id="f543d-104">SQLite zaman uyumsuz g/ç 'yi desteklemez.</span><span class="sxs-lookup"><span data-stu-id="f543d-104">SQLite doesn't support asynchronous I/O.</span></span> <span data-ttu-id="f543d-105">Zaman uyumsuz ADO.NET Yöntemler Microsoft. Data. SQLite içinde zaman uyumlu olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="f543d-105">Async ADO.NET methods will execute synchronously in Microsoft.Data.Sqlite.</span></span> <span data-ttu-id="f543d-106">Bunları çağırmadan kaçının.</span><span class="sxs-lookup"><span data-stu-id="f543d-106">Avoid calling them.</span></span>

<span data-ttu-id="f543d-107">Bunun yerine, performansı ve Eşzamanlılığını artırmak için [yazma öncesi günlüğü](https://www.sqlite.org/wal.html) kullanın.</span><span class="sxs-lookup"><span data-stu-id="f543d-107">Instead, use [write-ahead logging](https://www.sqlite.org/wal.html) to improve performance and concurrency.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/AsyncSample/Program.cs?name=snippet_WAL)]

> [!TIP]
> <span data-ttu-id="f543d-108">[Entity Framework Core](/ef/core/)kullanılarak oluşturulan veritabanlarında, önceden yazma günlüğü varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="f543d-108">Write-ahead logging is enabled by default on databases created using [Entity Framework Core](/ef/core/).</span></span>
