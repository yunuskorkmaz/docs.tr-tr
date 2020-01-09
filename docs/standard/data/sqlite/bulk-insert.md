---
title: Toplu ekleme
ms.date: 12/13/2019
description: Veritabanında çok sayıda değişiklik yaparken kullanabileceğiniz performans ipuçları.
ms.openlocfilehash: 9d87d5c8d70f8e70479f9aa02b7802f73b88de9e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447043"
---
# <a name="bulk-insert"></a>Toplu ekleme

SQLite, verileri toplu olarak eklemek için özel bir yol içermez. Veri eklerken veya güncelleştirirken en iyi performansı elde etmek için aşağıdakileri yapın:

- Bir işlem kullanın.
- Aynı Parametreli komutu yeniden kullanın. Sonraki yürütmeler birinciden derlemeyi yeniden kullanacaktır.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BulkInsertSample/Program.cs?name=snippet_BulkInsert)]
