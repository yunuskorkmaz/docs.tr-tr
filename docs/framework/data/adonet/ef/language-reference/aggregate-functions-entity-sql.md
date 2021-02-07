---
description: 'Daha fazla bilgi edinin: toplama Işlevleri (Entity SQL)'
title: Toplama Işlevleri (Entity SQL)
ms.date: 03/30/2017
ms.assetid: acfd3149-f519-4c6e-8fe1-b21d243a0e58
ms.openlocfilehash: 077f0f103e739fe893b8aabff38b03e3ef8ebd96
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697263"
---
# <a name="aggregate-functions-entity-sql"></a><span data-ttu-id="7207a-103">Toplama Işlevleri (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="7207a-103">Aggregate Functions (Entity SQL)</span></span>

<span data-ttu-id="7207a-104">Toplama, bir koleksiyonu bir grup işleminin parçası olarak skaler olarak sıkıştırmak için bir dil yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="7207a-104">An aggregate is a language construct that condenses a collection into a scalar as a part of a group operation.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="7207a-105">toplamalar iki biçimde gelir:</span><span class="sxs-lookup"><span data-stu-id="7207a-105">aggregates come in two forms:</span></span>  
  
- [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="7207a-106">bir ifadede herhangi bir yerde kullanılabilecek olan koleksiyon işlevleri.</span><span class="sxs-lookup"><span data-stu-id="7207a-106">collection functions that may be used anywhere in an expression.</span></span> <span data-ttu-id="7207a-107">Bu, toplamalar üzerinde işlem yapan projeksiyonlar ve koşullarda toplama işlevlerinin kullanılmasını içerir.</span><span class="sxs-lookup"><span data-stu-id="7207a-107">This includes using aggregate functions in projections and predicates that act on collections.</span></span> <span data-ttu-id="7207a-108">Koleksiyon işlevleri, içinde toplamalar belirtmenin tercih edilen modudur [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="7207a-108">Collection functions are the preferred mode of specifying aggregates in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
- <span data-ttu-id="7207a-109">GROUP BY yan tümcesine sahip sorgu ifadelerinde grup toplamaları.</span><span class="sxs-lookup"><span data-stu-id="7207a-109">Group aggregates in query expressions that have a GROUP BY clause.</span></span> <span data-ttu-id="7207a-110">Transact-SQL ' de olduğu gibi, Grup toplamaları toplama girişi için DISTINCT ve ALL olarak değiştirici kabul eder.</span><span class="sxs-lookup"><span data-stu-id="7207a-110">As in Transact-SQL, group aggregates accept DISTINCT and ALL as modifiers to the aggregate input.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="7207a-111">İlk olarak bir ifadeyi koleksiyon işlevi olarak yorumlamaya çalışır ve ifade bir SELECT ifadesinin bağlamında ise, bunu bir grup toplaması olarak yorumlar.</span><span class="sxs-lookup"><span data-stu-id="7207a-111">first tries to interpret an expression as a collection function and if the expression is in the context of a SELECT expression it interprets it as a group aggregate.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="7207a-112">[Grouppartition](grouppartition-entity-sql.md)adlı özel bir toplama işleci tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7207a-112">defines a special aggregate operator called [GROUPPARTITION](grouppartition-entity-sql.md).</span></span> <span data-ttu-id="7207a-113">Bu işleç, gruplandırılmış giriş kümesine bir başvuru almanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="7207a-113">This operator enables you to get a reference to the grouped input set.</span></span> <span data-ttu-id="7207a-114">Bu, GROUP BY yan tümcesinin sonuçlarının grup toplama veya toplama işlevleri dışında bir yerde kullanılabileceği daha gelişmiş gruplandırma sorgularına izin verir.</span><span class="sxs-lookup"><span data-stu-id="7207a-114">This allows more advanced grouping queries, where the results of the GROUP BY clause can be used in places other than group aggregate or collection functions.</span></span>  
  
## <a name="collection-functions"></a><span data-ttu-id="7207a-115">Koleksiyon Işlevleri</span><span class="sxs-lookup"><span data-stu-id="7207a-115">Collection Functions</span></span>  

 <span data-ttu-id="7207a-116">Koleksiyon işlevleri koleksiyonlar üzerinde çalışır ve skaler bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="7207a-116">Collection functions operate on collections and return a scalar value.</span></span> <span data-ttu-id="7207a-117">Örneğin, `orders` bir koleksiyonu ise `orders` , en erken sevk tarihini aşağıdaki ifadeyle hesaplayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7207a-117">For example, if `orders` is a collection of all `orders`, you can calculate the earliest ship date with the following expression:</span></span>  
  
 `min(select value o.ShipDate from LOB.Orders as o)`  
  
## <a name="group-aggregates"></a><span data-ttu-id="7207a-118">Grup toplamaları</span><span class="sxs-lookup"><span data-stu-id="7207a-118">Group Aggregates</span></span>  

 <span data-ttu-id="7207a-119">Grup toplamaları GROUP BY yan tümcesi tarafından tanımlanan bir grup sonucu üzerinden hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="7207a-119">Group aggregates are calculated over a group result as defined by the GROUP BY clause.</span></span> <span data-ttu-id="7207a-120">GROUP BY yan tümcesi, verileri gruplar halinde gruplandırır.</span><span class="sxs-lookup"><span data-stu-id="7207a-120">The GROUP BY clause partitions data  into groups.</span></span> <span data-ttu-id="7207a-121">Sonuç içindeki her grup için, toplama işlevi uygulanır ve ayrı bir toplama, her bir gruptaki öğeler toplam hesaplamaya giriş olarak kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="7207a-121">For each group in the result, the aggregate function is applied and a separate aggregate is calculated by using the elements in each group as inputs to the aggregate calculation.</span></span> <span data-ttu-id="7207a-122">Bir GROUP BY yan tümcesi bir SELECT ifadesinde kullanıldığında, Projection, HAVING veya ORDER BY yan tümcesinde yalnızca gruplama ifadesi adları, toplamalar veya sabit ifadeler bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="7207a-122">When a GROUP BY clause is used in a SELECT expression, only grouping expression names, aggregates, or constant expressions may be present in the projection, HAVING, or ORDER BY clause.</span></span>  
  
 <span data-ttu-id="7207a-123">Aşağıdaki örnek, her ürün için sipariş edilen ortalama miktarı hesaplar.</span><span class="sxs-lookup"><span data-stu-id="7207a-123">The following example calculates the average quantity ordered for each product.</span></span>  
  
 `select p, avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `group by ol.Product as p`  
  
 <span data-ttu-id="7207a-124">SELECT ifadesinde açık bir GROUP BY yan tümcesi olmadan bir grup toplaması olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="7207a-124">It is possible to have a group aggregate without an explicit GROUP BY clause in the SELECT expression.</span></span> <span data-ttu-id="7207a-125">Tüm öğeler tek bir grup olarak değerlendirilir, bu da bir sabiti temel alan bir gruplama belirtme durumuna eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="7207a-125">All elements will be treated as a single group, equivalent to the case of specifying a grouping based on a constant.</span></span>  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol group by 1`  
  
 <span data-ttu-id="7207a-126">GROUP BY yan tümcesinde kullanılan ifadeler WHERE yan tümcesi ifadesinde görünür olacak aynı ad çözümleme kapsamı kullanılarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="7207a-126">Expressions used in the GROUP BY clause are evaluated by using the same name-resolution scope that would be visible to the WHERE clause expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7207a-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7207a-127">See also</span></span>

- [<span data-ttu-id="7207a-128">İşlevler</span><span class="sxs-lookup"><span data-stu-id="7207a-128">Functions</span></span>](functions-entity-sql.md)
