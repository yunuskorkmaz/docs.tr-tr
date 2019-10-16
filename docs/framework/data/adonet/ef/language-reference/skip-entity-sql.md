---
title: Atla (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
ms.openlocfilehash: 75140384823588b8f6785de00b0ab3cd17314a3f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319335"
---
# <a name="skip-entity-sql"></a><span data-ttu-id="7800f-102">Atla (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="7800f-102">SKIP (Entity SQL)</span></span>

<span data-ttu-id="7800f-103">ORDER BY yan tümcesindeki SKIP alt yan tümcesini kullanarak fiziksel sayfalama işlemi gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7800f-103">You can perform physical paging by using the SKIP sub-clause in the ORDER BY clause.</span></span> <span data-ttu-id="7800f-104">SKIP, ORDER BY yan tümcesinde ayrı olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="7800f-104">SKIP cannot be used separately from the ORDER BY clause.</span></span>

## <a name="syntax"></a><span data-ttu-id="7800f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7800f-105">Syntax</span></span>

```sql
[ SKIP n ]
```

## <a name="arguments"></a><span data-ttu-id="7800f-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="7800f-106">Arguments</span></span>

`n` \
<span data-ttu-id="7800f-107">Atlanacak öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="7800f-107">The number of items to skip.</span></span>

## <a name="remarks"></a><span data-ttu-id="7800f-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7800f-108">Remarks</span></span>

<span data-ttu-id="7800f-109">ORDER BY yan tümcesinde bir SKIP ifadesi Sub yan tümcesi varsa, sonuçlar sıralama belirtimine göre sıralanır ve sonuç kümesi, atlama ifadesinden hemen sonra gelen sonraki satırdan başlayan satırları içerir.</span><span class="sxs-lookup"><span data-stu-id="7800f-109">If a SKIP expression sub-clause is present in an ORDER BY clause, the results will be sorted according the sort specification and the result set will include rows starting from the next row immediately after the SKIP expression.</span></span> <span data-ttu-id="7800f-110">Örneğin, 5 ' i atlamak ilk beş satırı atlar ve altıncı satırdan ileriye geri dönecektir.</span><span class="sxs-lookup"><span data-stu-id="7800f-110">For example, SKIP 5 will skip the first five rows and return from the sixth row forward.</span></span>

> [!NOTE]
> <span data-ttu-id="7800f-111">Aynı sorgu ifadesinde hem TOP Modifier hem de SKIP alt yan tümcesi mevcutsa [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgusu geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="7800f-111">An [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query is invalid if both the TOP modifier and the SKIP sub-clause are present in the same query expression.</span></span> <span data-ttu-id="7800f-112">ÜST ifade sınır ifadesine değiştirilerek sorgunun yeniden yazılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7800f-112">The query should be rewritten by changing the TOP expression to the LIMIT expression.</span></span>

> [!NOTE]
> <span data-ttu-id="7800f-113">SQL Server 2000 ' de, anahtar olmayan sütunlarda SıRALAMA ile atla kullanılması yanlış sonuçlar döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="7800f-113">In SQL Server 2000, using SKIP with ORDER BY on non-key columns might return incorrect results.</span></span> <span data-ttu-id="7800f-114">Anahtar olmayan sütunda Yinelenen veriler varsa, belirtilen sayıda satırdan daha fazla satır atlanmayabilir.</span><span class="sxs-lookup"><span data-stu-id="7800f-114">More than the specified number of rows might be skipped if the non-key column has duplicate data in it.</span></span> <span data-ttu-id="7800f-115">Bunun nedeni, atlama 'nin SQL Server 2000 ' de çevrilmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="7800f-115">This is due to how SKIP is translated for SQL Server 2000.</span></span> <span data-ttu-id="7800f-116">Örneğin, aşağıdaki kodda `E.NonKeyColumn` yinelenen değerler varsa beş satırdan daha fazla satır atlanabilir:</span><span class="sxs-lookup"><span data-stu-id="7800f-116">For example, in the following code more than five rows might be skipped if `E.NonKeyColumn` has duplicate values:</span></span>
>
> ```sql
> SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L
> ```

<span data-ttu-id="7800f-117">[Sorgu sonuçları aracılığıyla](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)) [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgusu, Select ifadesinde döndürülen nesnelerde kullanılan sıralama düzenini BELIRTMEK için SKIP Ile order by işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="7800f-117">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query in [How to: Page Through Query Results](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)) uses the ORDER BY operator with SKIP to specify the sort order used on objects returned in a SELECT statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="7800f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7800f-118">See also</span></span>

- [<span data-ttu-id="7800f-119">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="7800f-119">ORDER BY</span></span>](order-by-entity-sql.md)
- <span data-ttu-id="7800f-120">[Nasıl yapılır: sorgu sonuçları aracılığıyla sayfa oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7800f-120">[How to: Page Through Query Results](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>
- [<span data-ttu-id="7800f-121">Disk Belleği</span><span class="sxs-lookup"><span data-stu-id="7800f-121">Paging</span></span>](paging-entity-sql.md)
- [<span data-ttu-id="7800f-122">TOP</span><span class="sxs-lookup"><span data-stu-id="7800f-122">TOP</span></span>](top-entity-sql.md)
