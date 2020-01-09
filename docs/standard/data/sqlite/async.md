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
# <a name="async-limitations"></a>Zaman uyumsuz sınırlamalar

SQLite zaman uyumsuz g/ç 'yi desteklemez. Zaman uyumsuz ADO.NET Yöntemler Microsoft. Data. SQLite içinde zaman uyumlu olarak yürütülür. Bunları çağırmadan kaçının.

Bunun yerine, performansı ve Eşzamanlılığını artırmak için [yazma öncesi günlüğü](https://www.sqlite.org/wal.html) kullanın.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/AsyncSample/Program.cs?name=snippet_WAL)]

> [!TIP]
> [Entity Framework Core](/ef/core/)kullanılarak oluşturulan veritabanlarında, önceden yazma günlüğü varsayılan olarak etkindir.
