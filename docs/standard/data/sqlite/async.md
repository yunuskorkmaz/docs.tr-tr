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
# <a name="async-limitations"></a>Zaman uyumsuz sınırlamalar

SQLite zaman uyumsuz g/ç 'yi desteklemez. Zaman uyumsuz ADO.NET Yöntemler Microsoft. Data. SQLite içinde zaman uyumlu olarak yürütülür. Bunları çağırmadan kaçının.

Bunun yerine, performansı ve Eşzamanlılığını artırmak için [paylaşılan bir önbellek](connection-strings.md#cache) ve [sonradan yazma günlüğü](https://www.sqlite.org/wal.html) kullanın.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/AsyncSample/Program.cs?name=snippet_WAL)]

> [!TIP]
> [Entity Framework Core](/ef/core/)kullanılarak oluşturulan veritabanlarında, önceden yazma günlüğü varsayılan olarak etkindir.
