---
description: 'Hakkında daha fazla bilgi edinin: SKIP (Entity SQL)'
title: Atla (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
ms.openlocfilehash: f4924acae6e351e076b5795cf47d63966ebdcb43
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768018"
---
# <a name="skip-entity-sql"></a><span data-ttu-id="7d434-103">Atla (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="7d434-103">SKIP (Entity SQL)</span></span>

<span data-ttu-id="7d434-104">ORDER BY yan tümcesindeki SKIP alt yan tümcesini kullanarak fiziksel sayfalama işlemi gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d434-104">You can perform physical paging by using the SKIP sub-clause in the ORDER BY clause.</span></span> <span data-ttu-id="7d434-105">SKIP, ORDER BY yan tümcesinde ayrı olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="7d434-105">SKIP cannot be used separately from the ORDER BY clause.</span></span>

## <a name="syntax"></a><span data-ttu-id="7d434-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7d434-106">Syntax</span></span>

```sql
[ SKIP n ]
```

## <a name="arguments"></a><span data-ttu-id="7d434-107">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="7d434-107">Arguments</span></span>

`n` \
<span data-ttu-id="7d434-108">Atlanacak öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="7d434-108">The number of items to skip.</span></span>

## <a name="remarks"></a><span data-ttu-id="7d434-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7d434-109">Remarks</span></span>

<span data-ttu-id="7d434-110">ORDER BY yan tümcesinde bir SKIP ifadesi Sub yan tümcesi varsa, sonuçlar sıralama belirtimine göre sıralanır ve sonuç kümesi, atlama ifadesinden hemen sonra gelen sonraki satırdan başlayan satırları içerir.</span><span class="sxs-lookup"><span data-stu-id="7d434-110">If a SKIP expression sub-clause is present in an ORDER BY clause, the results will be sorted according the sort specification and the result set will include rows starting from the next row immediately after the SKIP expression.</span></span> <span data-ttu-id="7d434-111">Örneğin, 5 ' i atlamak ilk beş satırı atlar ve altıncı satırdan ileriye geri dönecektir.</span><span class="sxs-lookup"><span data-stu-id="7d434-111">For example, SKIP 5 will skip the first five rows and return from the sixth row forward.</span></span>

> [!NOTE]
> <span data-ttu-id="7d434-112">[!INCLUDE[esql](../../../../../../includes/esql-md.md)]Aynı sorgu ifadesinde hem top Modifier hem de SKIP alt yan tümcesi mevcutsa sorgu geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="7d434-112">An [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query is invalid if both the TOP modifier and the SKIP sub-clause are present in the same query expression.</span></span> <span data-ttu-id="7d434-113">ÜST ifade sınır ifadesine değiştirilerek sorgunun yeniden yazılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7d434-113">The query should be rewritten by changing the TOP expression to the LIMIT expression.</span></span>

> [!NOTE]
> <span data-ttu-id="7d434-114">SQL Server 2000 ' de, anahtar olmayan sütunlarda SıRALAMA ile atla kullanılması yanlış sonuçlar döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="7d434-114">In SQL Server 2000, using SKIP with ORDER BY on non-key columns might return incorrect results.</span></span> <span data-ttu-id="7d434-115">Anahtar olmayan sütunda Yinelenen veriler varsa, belirtilen sayıda satırdan daha fazla satır atlanmayabilir.</span><span class="sxs-lookup"><span data-stu-id="7d434-115">More than the specified number of rows might be skipped if the non-key column has duplicate data in it.</span></span> <span data-ttu-id="7d434-116">Bunun nedeni, atlama 'nin SQL Server 2000 ' de çevrilmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="7d434-116">This is due to how SKIP is translated for SQL Server 2000.</span></span> <span data-ttu-id="7d434-117">Örneğin, aşağıdaki kodda yinelenen değerler varsa beş satırdan daha fazla satır atlanabilir `E.NonKeyColumn` :</span><span class="sxs-lookup"><span data-stu-id="7d434-117">For example, in the following code more than five rows might be skipped if `E.NonKeyColumn` has duplicate values:</span></span>
>
> ```sql
> SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L
> ```

<span data-ttu-id="7d434-118">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] [Nasıl yapılır: sorgu sonuçları aracılığıyla yapılan](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)) sorgu, Select ifadesinde döndürülen nesnelerde kullanılan sıralama DÜZENINI belirtmek IÇIN SKIP ile order by işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="7d434-118">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query in [How to: Page Through Query Results](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)) uses the ORDER BY operator with SKIP to specify the sort order used on objects returned in a SELECT statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="7d434-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d434-119">See also</span></span>

- [<span data-ttu-id="7d434-120">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="7d434-120">ORDER BY</span></span>](order-by-entity-sql.md)
- <span data-ttu-id="7d434-121">[Nasıl yapılır: sorgu sonuçları aracılığıyla sayfa oluşturma](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7d434-121">[How to: Page Through Query Results](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>
- [<span data-ttu-id="7d434-122">Sayfalama</span><span class="sxs-lookup"><span data-stu-id="7d434-122">Paging</span></span>](paging-entity-sql.md)
- [<span data-ttu-id="7d434-123">Sayfanın Üstü</span><span class="sxs-lookup"><span data-stu-id="7d434-123">TOP</span></span>](top-entity-sql.md)
