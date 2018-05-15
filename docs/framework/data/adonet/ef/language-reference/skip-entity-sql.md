---
title: Atla (varlık SQL)
ms.date: 03/30/2017
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
ms.openlocfilehash: 3b63ca6ade93331b9d1c3ef3e8de15ed520864dc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="skip-entity-sql"></a><span data-ttu-id="f3766-102">Atla (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="f3766-102">SKIP (Entity SQL)</span></span>
<span data-ttu-id="f3766-103">Fiziksel disk belleği ORDER BY yan tümcesinde SKIP alt yan tümcesinin kullanarak gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3766-103">You can perform physical paging by using the SKIP sub-clause in the ORDER BY clause.</span></span> <span data-ttu-id="f3766-104">Atla ayrı olarak from ORDER BY yan tümcesi kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f3766-104">SKIP cannot be used separately from the ORDER BY clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3766-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f3766-105">Syntax</span></span>  
  
```  
[ SKIP n ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="f3766-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="f3766-106">Arguments</span></span>  
 `n`  
 <span data-ttu-id="f3766-107">Atlanacak öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="f3766-107">The number of items to skip.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3766-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f3766-108">Remarks</span></span>  
 <span data-ttu-id="f3766-109">SKIP ifadesi alt yan ORDER BY yan tümcesinde varsa, sonuçları sıralama belirtimine göre sıralanır ve sonuç kümesi satır hemen sonra SKIP ifadesi sonraki satırdan başlayarak dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="f3766-109">If a SKIP expression sub-clause is present in an ORDER BY clause, the results will be sorted according the sort specification and the result set will include rows starting from the next row immediately after the SKIP expression.</span></span> <span data-ttu-id="f3766-110">Örneğin, Atla 5 ilk beş satırını atlar ve İleri altıncı satırdaki döndürür.</span><span class="sxs-lookup"><span data-stu-id="f3766-110">For example, SKIP 5 will skip the first five rows and return from the sixth row forward.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f3766-111">Bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu üst değiştirici ve SKIP alt yan tümcesinin aynı sorgu ifadesinde mevcut olup olmadığını geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="f3766-111">An [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query is invalid if both the TOP modifier and the SKIP sub-clause are present in the same query expression.</span></span> <span data-ttu-id="f3766-112">Sorgu TOP ifadesi için sınır ifade değiştirerek yazılması.</span><span class="sxs-lookup"><span data-stu-id="f3766-112">The query should be rewritten by changing the TOP expression to the LIMIT expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f3766-113">İçinde [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)], anahtar olmayan sütunlarda ORDER BY ile Atla kullanarak hatalı sonuçlar döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="f3766-113">In [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)], using SKIP with ORDER BY on non-key columns might return incorrect results.</span></span> <span data-ttu-id="f3766-114">Anahtar olmayan sütun yinelenen verileri varsa satır belirtilen sayıdan daha fazla atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="f3766-114">More than the specified number of rows might be skipped if the non-key column has duplicate data in it.</span></span> <span data-ttu-id="f3766-115">Nasıl Atla için çevrilir nedeniyle budur [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f3766-115">This is due to how SKIP is translated for [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)].</span></span> <span data-ttu-id="f3766-116">Örneğin, aşağıdaki kodda beşten fazla satır, atlanabilir `E.NonKeyColumn` yinelenen değerleri içeriyor:</span><span class="sxs-lookup"><span data-stu-id="f3766-116">For example, in the following code more than five rows might be skipped if `E.NonKeyColumn` has duplicate values:</span></span>  
>   
>  `SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L`  
  
 <span data-ttu-id="f3766-117">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] İçinde sorgu [bu](https://msdn.microsoft.com/library/bb738702\(v=vs.100\).aspx#_ESQL) örnek bir SELECT deyiminde döndürülen nesne üzerinde kullanılan sıralama düzenini belirlemek için Atla ile ORDER BY işleci kullanır.</span><span class="sxs-lookup"><span data-stu-id="f3766-117">The  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query in [this](https://msdn.microsoft.com/library/bb738702\(v=vs.100\).aspx#_ESQL) example uses the ORDER BY operator with SKIP to specify the sort order used on objects returned in a SELECT statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3766-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f3766-118">See Also</span></span>  
 [<span data-ttu-id="f3766-119">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="f3766-119">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
 [<span data-ttu-id="f3766-120">Nasıl yapılır: sonuçları sorgu aracılığıyla sayfası</span><span class="sxs-lookup"><span data-stu-id="f3766-120">How to: Page Through Query Results</span></span>](http://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)  
 [<span data-ttu-id="f3766-121">Disk Belleği</span><span class="sxs-lookup"><span data-stu-id="f3766-121">Paging</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)  
 [<span data-ttu-id="f3766-122">TOP</span><span class="sxs-lookup"><span data-stu-id="f3766-122">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
