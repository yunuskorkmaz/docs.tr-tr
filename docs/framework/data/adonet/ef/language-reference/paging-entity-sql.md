---
title: Sayfalama (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ba4f334d-03e5-4a7b-9d42-628f4639b9a2
ms.openlocfilehash: 42f685e0b84109f3099b501b2a75e681af1ea1bb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177481"
---
# <a name="paging-entity-sql"></a><span data-ttu-id="ce227-102">Sayfalama (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ce227-102">Paging (Entity SQL)</span></span>

<span data-ttu-id="ce227-103">Fiziksel sayfalama, [order by](order-by-entity-sql.md) yan tümcesindeki [SKIP](skip-entity-sql.md) ve [LIMIT](limit-entity-sql.md) alt yan tümceleri kullanılarak gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ce227-103">Physical paging can be performed by using the [SKIP](skip-entity-sql.md) and [LIMIT](limit-entity-sql.md) sub-clauses in the [ORDER BY](order-by-entity-sql.md) clause.</span></span> <span data-ttu-id="ce227-104">Fiziksel disk belleği kullanımını kesin bir şekilde gerçekleştirmek için atla ve SıNıRLA ' yı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ce227-104">To perform physical paging deterministically, you should use SKIP and LIMIT.</span></span> <span data-ttu-id="ce227-105">Sonuç olarak sonuçdaki satır sayısını belirleyici olmayan bir şekilde kısıtlamak istiyorsanız, [en üst](top-entity-sql.md)' i kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ce227-105">If you only want to restrict the number of rows in the result in a non-deterministic way, you should use [TOP](top-entity-sql.md).</span></span> <span data-ttu-id="ce227-106">TOP ve SKIP/LIMIT birbirini dışlıyor.</span><span class="sxs-lookup"><span data-stu-id="ce227-106">TOP and SKIP/LIMIT are mutually exclusive.</span></span>  
  
## <a name="top-overview"></a><span data-ttu-id="ce227-107">EN üst genel bakış</span><span class="sxs-lookup"><span data-stu-id="ce227-107">TOP Overview</span></span>  

 <span data-ttu-id="ce227-108">SELECT yan tümcesi isteğe bağlı ALL/DISTINCT değiştiricisinden sonra isteğe bağlı bir TOP Sub yan tümcesine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="ce227-108">The SELECT clause can have an optional TOP sub-clause following the optional ALL/DISTINCT modifier.</span></span> <span data-ttu-id="ce227-109">TOP alt yan tümcesi, sorgu sonucundan yalnızca ilk satır kümesinin döndürüleceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ce227-109">The TOP sub-clause specifies that only the first set of rows will be returned from the query result.</span></span> <span data-ttu-id="ce227-110">Daha fazla bilgi için bkz. [top](top-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="ce227-110">For more information, see [TOP](top-entity-sql.md).</span></span>  
  
## <a name="skip-and-limit-overview"></a><span data-ttu-id="ce227-111">Atla ve SıNıRLA genel bakış</span><span class="sxs-lookup"><span data-stu-id="ce227-111">SKIP And LIMIT Overview</span></span>  

 <span data-ttu-id="ce227-112">Atla ve SıNıRLA ORDER BY yan tümcesinin bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="ce227-112">SKIP and LIMIT are part of the ORDER BY clause.</span></span> <span data-ttu-id="ce227-113">ORDER BY yan tümcesinde bir SKIP ifadesi alt yan tümcesi varsa, sonuçlar sıralama belirtimine göre sıralanır ve sonuç kümesi, atlama ifadesinden hemen sonra gelen bir sonraki satırdan başlayan satırları içerir.</span><span class="sxs-lookup"><span data-stu-id="ce227-113">If a SKIP expression sub-clause is present in a ORDER BY clause, the results will be sorted according to the sort specification and the result set will include row(s) starting from the next row immediately after the SKIP expression.</span></span> <span data-ttu-id="ce227-114">Örneğin, 5 ' i atlamak ilk beş satırı atlar ve altıncı satırdan ileriye geri dönecektir.</span><span class="sxs-lookup"><span data-stu-id="ce227-114">For example, SKIP 5 will skip the first five rows and return from the sixth row forward.</span></span> <span data-ttu-id="ce227-115">Bir sınır ifadesi alt yan tümcesi ORDER BY yan tümcesinde mevcutsa, sorgu sıralama belirtimine göre sıralanır ve sonuç olarak satır sayısı sınır ifadesi ile kısıtlanır.</span><span class="sxs-lookup"><span data-stu-id="ce227-115">If a LIMIT expression sub-clause is present in an ORDER BY clause, the query will be sorted according to the sort specification and the resulting number of rows will be restricted by the LIMIT expression.</span></span> <span data-ttu-id="ce227-116">Örneğin, sınır 5, sonuç kümesini beş örnek veya satır olarak kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="ce227-116">For instance, LIMIT 5 will restrict the result set to five instances or rows.</span></span> <span data-ttu-id="ce227-117">ATLAMA ve SıNıRıN birlikte kullanılması gerekmez; yalnızca SKIP veya ORDER BY yan tümcesiyle SıNıRLA ' yı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ce227-117">SKIP and LIMIT do not have to be used together; you can use just SKIP or just LIMIT with ORDER BY clause.</span></span> <span data-ttu-id="ce227-118">Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:</span><span class="sxs-lookup"><span data-stu-id="ce227-118">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="ce227-119">ŞIMDILIK</span><span class="sxs-lookup"><span data-stu-id="ce227-119">SKIP</span></span>](skip-entity-sql.md)  
  
- [<span data-ttu-id="ce227-120">SıNıRLı</span><span class="sxs-lookup"><span data-stu-id="ce227-120">LIMIT</span></span>](limit-entity-sql.md)  
  
- [<span data-ttu-id="ce227-121">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="ce227-121">ORDER BY</span></span>](order-by-entity-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="ce227-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce227-122">See also</span></span>

- [<span data-ttu-id="ce227-123">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="ce227-123">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="ce227-124">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ce227-124">Entity SQL Overview</span></span>](entity-sql-overview.md)
- <span data-ttu-id="ce227-125">[Nasıl yapılır: sorgu sonuçları aracılığıyla sayfa oluşturma](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ce227-125">[How to: Page Through Query Results](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>
