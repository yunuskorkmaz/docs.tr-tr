---
title: Atla (varlık SQL)
ms.date: 03/30/2017
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
ms.openlocfilehash: 467329f74304b64c7fc7ada2920751aba744f76e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54637644"
---
# <a name="skip-entity-sql"></a><span data-ttu-id="9542e-102">Atla (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="9542e-102">SKIP (Entity SQL)</span></span>
<span data-ttu-id="9542e-103">Fiziksel disk belleği SKIP alt yan tümcesi ORDER BY yan tümcesinde kullanarak gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9542e-103">You can perform physical paging by using the SKIP sub-clause in the ORDER BY clause.</span></span> <span data-ttu-id="9542e-104">SKIP ayrı olarak from ORDER BY yan tümcesi kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9542e-104">SKIP cannot be used separately from the ORDER BY clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9542e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9542e-105">Syntax</span></span>  
  
```  
[ SKIP n ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="9542e-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="9542e-106">Arguments</span></span>  
 `n`  
 <span data-ttu-id="9542e-107">Atlanacak öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="9542e-107">The number of items to skip.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9542e-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9542e-108">Remarks</span></span>  
 <span data-ttu-id="9542e-109">ORDER BY yan tümcesinde bir SKIP ifadesi alt yan tümcesi varsa, sonuçları sıralama belirtimine göre sıralanır ve sonraki satırdaki Atla ifadesinden hemen sonra başlayan satırları sonuç kümesini içerir.</span><span class="sxs-lookup"><span data-stu-id="9542e-109">If a SKIP expression sub-clause is present in an ORDER BY clause, the results will be sorted according the sort specification and the result set will include rows starting from the next row immediately after the SKIP expression.</span></span> <span data-ttu-id="9542e-110">Örneğin, Atla 5 ilk beş satırları atlar ve Altıncı satırdan ileriye doğru döndürür.</span><span class="sxs-lookup"><span data-stu-id="9542e-110">For example, SKIP 5 will skip the first five rows and return from the sixth row forward.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9542e-111">Bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu üst değiştiricisi hem SKIP alt yan tümcesi, aynı sorgu ifadesinde mevcut olması durumunda geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="9542e-111">An [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query is invalid if both the TOP modifier and the SKIP sub-clause are present in the same query expression.</span></span> <span data-ttu-id="9542e-112">Sorgu TOP ifadesi sınırı ifade değiştirerek yazılması.</span><span class="sxs-lookup"><span data-stu-id="9542e-112">The query should be rewritten by changing the TOP expression to the LIMIT expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9542e-113">İçinde [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)], anahtar olmayan sütun ORDER BY ile Atla kullanarak hatalı sonuçlar döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="9542e-113">In [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)], using SKIP with ORDER BY on non-key columns might return incorrect results.</span></span> <span data-ttu-id="9542e-114">Anahtar olmayan sütun yinelenen veri varsa birden çok belirtilen sayıda satırı atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="9542e-114">More than the specified number of rows might be skipped if the non-key column has duplicate data in it.</span></span> <span data-ttu-id="9542e-115">Bu nasıl Atla için çevrilir nedeniyle, [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9542e-115">This is due to how SKIP is translated for [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)].</span></span> <span data-ttu-id="9542e-116">Örneğin, aşağıdaki kodda beşten fazla satır varsa atlanabilir `E.NonKeyColumn` yinelenen değerlere sahip:</span><span class="sxs-lookup"><span data-stu-id="9542e-116">For example, in the following code more than five rows might be skipped if `E.NonKeyColumn` has duplicate values:</span></span>  
>   
>  `SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L`  
  
 <span data-ttu-id="9542e-117">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] İçinde sorgu [bu](https://msdn.microsoft.com/library/bb738702\(v=vs.100\).aspx#_ESQL) örnek bir SELECT deyiminde döndürülen nesneler üzerinde kullanılan sıralama düzeni belirlemek için Atla ile ORDER BY işleci kullanır.</span><span class="sxs-lookup"><span data-stu-id="9542e-117">The  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query in [this](https://msdn.microsoft.com/library/bb738702\(v=vs.100\).aspx#_ESQL) example uses the ORDER BY operator with SKIP to specify the sort order used on objects returned in a SELECT statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9542e-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9542e-118">See also</span></span>
- [<span data-ttu-id="9542e-119">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="9542e-119">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)
- [<span data-ttu-id="9542e-120">Nasıl yapılır: Sorgu sonuçları sayfasından</span><span class="sxs-lookup"><span data-stu-id="9542e-120">How to: Page Through Query Results</span></span>](https://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)
- [<span data-ttu-id="9542e-121">Disk Belleği</span><span class="sxs-lookup"><span data-stu-id="9542e-121">Paging</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)
- [<span data-ttu-id="9542e-122">TOP</span><span class="sxs-lookup"><span data-stu-id="9542e-122">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
