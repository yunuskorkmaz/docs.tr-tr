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
# <a name="bulk-insert"></a><span data-ttu-id="c89b2-103">Toplu ekleme</span><span class="sxs-lookup"><span data-stu-id="c89b2-103">Bulk insert</span></span>

<span data-ttu-id="c89b2-104">SQLite, verileri toplu olarak eklemek için özel bir yol içermez.</span><span class="sxs-lookup"><span data-stu-id="c89b2-104">SQLite doesn't have any special way to bulk insert data.</span></span> <span data-ttu-id="c89b2-105">Veri eklerken veya güncelleştirirken en iyi performansı elde etmek için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="c89b2-105">To get optimal performance when inserting or updating data, ensure that you do the following:</span></span>

- <span data-ttu-id="c89b2-106">Bir işlem kullanın.</span><span class="sxs-lookup"><span data-stu-id="c89b2-106">Use a transaction.</span></span>
- <span data-ttu-id="c89b2-107">Aynı Parametreli komutu yeniden kullanın.</span><span class="sxs-lookup"><span data-stu-id="c89b2-107">Reuse the same parameterized command.</span></span> <span data-ttu-id="c89b2-108">Sonraki yürütmeler birinciden derlemeyi yeniden kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="c89b2-108">Subsequent executions will reuse the compilation of the first one.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BulkInsertSample/Program.cs?name=snippet_BulkInsert)]
