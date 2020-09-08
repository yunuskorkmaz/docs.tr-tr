---
title: Zaman uyumsuz sınırlamalar
ms.date: 09/04/2020
description: Zaman uyumsuz API 'lerin ve bunun yerine kullanabileceğiniz bazı alternatiflere ilişkin sınırlamaları açıklar.
ms.openlocfilehash: 8b14fcfeb12d331d8d43ca6d77332007a12ae5dc
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89516001"
---
# <a name="async-limitations"></a><span data-ttu-id="39928-103">Zaman uyumsuz sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="39928-103">Async limitations</span></span>

<span data-ttu-id="39928-104">SQLite zaman uyumsuz g/ç 'yi desteklemez.</span><span class="sxs-lookup"><span data-stu-id="39928-104">SQLite doesn't support asynchronous I/O.</span></span> <span data-ttu-id="39928-105">Zaman uyumsuz ADO.NET Yöntemler Microsoft. Data. SQLite içinde zaman uyumlu olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="39928-105">Async ADO.NET methods will execute synchronously in Microsoft.Data.Sqlite.</span></span> <span data-ttu-id="39928-106">Bunları çağırmadan kaçının.</span><span class="sxs-lookup"><span data-stu-id="39928-106">Avoid calling them.</span></span>

<span data-ttu-id="39928-107">Bunun yerine, performansı ve Eşzamanlılığını artırmak için [paylaşılan bir önbellek](connection-strings.md#cache) ve [sonradan yazma günlüğü](https://www.sqlite.org/wal.html) kullanın.</span><span class="sxs-lookup"><span data-stu-id="39928-107">Instead, use a [shared cache](connection-strings.md#cache) and [write-ahead logging](https://www.sqlite.org/wal.html) to improve performance and concurrency.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/AsyncSample/Program.cs?name=snippet_WAL)]

> [!TIP]
> <span data-ttu-id="39928-108">[Entity Framework Core](/ef/core/)kullanılarak oluşturulan veritabanlarında, önceden yazma günlüğü varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="39928-108">Write-ahead logging is enabled by default on databases created using [Entity Framework Core](/ef/core/).</span></span>
