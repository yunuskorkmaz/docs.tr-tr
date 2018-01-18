---
title: "Toplama işlevleri (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: acfd3149-f519-4c6e-8fe1-b21d243a0e58
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e1ed9a7532269a149f6f522e8fe9c6161e1aae27
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="aggregate-functions-entity-sql"></a><span data-ttu-id="16db2-102">Toplama işlevleri (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="16db2-102">Aggregate Functions (Entity SQL)</span></span>
<span data-ttu-id="16db2-103">Bir toplama skaler bir koleksiyona bir grup işleminin bir parçası olarak toplar bir dil yapıdır.</span><span class="sxs-lookup"><span data-stu-id="16db2-103">An aggregate is a language construct that condenses a collection into a scalar as a part of a group operation.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="16db2-104">Toplamlar iki biçimde getirir:</span><span class="sxs-lookup"><span data-stu-id="16db2-104"> aggregates come in two forms:</span></span>  
  
-   [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="16db2-105">bir ifadede herhangi bir yerde kullanılan işlevler koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="16db2-105"> collection functions that may be used anywhere in an expression.</span></span> <span data-ttu-id="16db2-106">Bu toplama işlevleri tahminleri ve hareket koşulları üzerinde koleksiyonları kullanarak içerir.</span><span class="sxs-lookup"><span data-stu-id="16db2-106">This includes using aggregate functions in projections and predicates that act on collections.</span></span> <span data-ttu-id="16db2-107">Koleksiyon işlevlerdir Toplamaların belirtme tercih edilen modu [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="16db2-107">Collection functions are the preferred mode of specifying aggregates in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
-   <span data-ttu-id="16db2-108">GROUP BY yan tümcesi bulunan sorgu ifadelerinde Grup toplar.</span><span class="sxs-lookup"><span data-stu-id="16db2-108">Group aggregates in query expressions that have a GROUP BY clause.</span></span> <span data-ttu-id="16db2-109">Olarak [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], Grup toplamalar DISTINCT ve tüm değiştiricileri birleşik giriş olarak kabul edin.</span><span class="sxs-lookup"><span data-stu-id="16db2-109">As in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], group aggregates accept DISTINCT and ALL as modifiers to the aggregate input.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="16db2-110">İlk ifade bir toplama işlevi olarak yorumlamaya çalışır ve ifade bir SELECT deyimi bağlamında, yorumlar, bir grup toplama olarak.</span><span class="sxs-lookup"><span data-stu-id="16db2-110"> first tries to interpret an expression as a collection function and if the expression is in the context of a SELECT expression it interprets it as a group aggregate.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="16db2-111">adlı özel bir toplama işleci tanımlar [GROUPPARTITION](../../../../../../docs/framework/data/adonet/ef/language-reference/grouppartition-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="16db2-111"> defines a special aggregate operator called [GROUPPARTITION](../../../../../../docs/framework/data/adonet/ef/language-reference/grouppartition-entity-sql.md).</span></span> <span data-ttu-id="16db2-112">Bu işleç gruplandırılmış giriş ayarlamak için bir başvuru sağlar.</span><span class="sxs-lookup"><span data-stu-id="16db2-112">This operator enables you to get a reference to the grouped input set.</span></span> <span data-ttu-id="16db2-113">GROUP BY yan tümcesi sonuçlarını Grup toplama veya toplama işlevleri başka yerde kullanıldığı bu sorgular, gruplandırma daha gelişmiş sağlar.</span><span class="sxs-lookup"><span data-stu-id="16db2-113">This allows more advanced grouping queries, where the results of the GROUP BY clause can be used in places other than group aggregate or collection functions.</span></span>  
  
## <a name="collection-functions"></a><span data-ttu-id="16db2-114">Toplama işlevleri</span><span class="sxs-lookup"><span data-stu-id="16db2-114">Collection Functions</span></span>  
 <span data-ttu-id="16db2-115">Toplama işlevleri koleksiyonlar üzerinde çalışır ve skaler bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="16db2-115">Collection functions operate on collections and return a scalar value.</span></span> <span data-ttu-id="16db2-116">Örneğin, varsa `orders` tüm oluşan bir koleksiyondur `orders`, aşağıdaki ifade en erken sevk tarihi hesaplayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="16db2-116">For example, if `orders` is a collection of all `orders`, you can calculate the earliest ship date with the following expression:</span></span>  
  
 `min(select value o.ShipDate from LOB.Orders as o)`  
  
## <a name="group-aggregates"></a><span data-ttu-id="16db2-117">Grup toplar</span><span class="sxs-lookup"><span data-stu-id="16db2-117">Group Aggregates</span></span>  
 <span data-ttu-id="16db2-118">Grup toplamları GROUP BY yan tümcesi tarafından tanımlanan bir grup sonucu üzerinden hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="16db2-118">Group aggregates are calculated over a group result as defined by the GROUP BY clause.</span></span> <span data-ttu-id="16db2-119">GROUP BY yan tümcesi gruplar halinde veri bölümler.</span><span class="sxs-lookup"><span data-stu-id="16db2-119">The GROUP BY clause partitions data  into groups.</span></span> <span data-ttu-id="16db2-120">Her grup için sonuç, toplama işlevi uygulanır ve ayrı bir toplama giriş toplama hesaplama olarak her grupta öğeleri kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="16db2-120">For each group in the result, the aggregate function is applied and a separate aggregate is calculated by using the elements in each group as inputs to the aggregate calculation.</span></span> <span data-ttu-id="16db2-121">GROUP BY yan tümcesi yalnızca ifade adları, toplamalar veya sabit ifadeler gruplandırma bir SELECT ifadesinde kullanıldığında sahip, projeksiyon bulunması veya BY yan tümcesi sipariş.</span><span class="sxs-lookup"><span data-stu-id="16db2-121">When a GROUP BY clause is used in a SELECT expression, only grouping expression names, aggregates, or constant expressions may be present in the projection, HAVING, or ORDER BY clause.</span></span>  
  
 <span data-ttu-id="16db2-122">Aşağıdaki örnekte, her ürün için sipariş edilen ortalama miktarı hesaplar.</span><span class="sxs-lookup"><span data-stu-id="16db2-122">The following example calculates the average quantity ordered for each product.</span></span>  
  
 `select p, avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `group by ol.Product as p`  
  
 <span data-ttu-id="16db2-123">Bir açık GROUP BY yan tümcesi olmadan birleşik bir grup seçin ifadesinde olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="16db2-123">It is possible to have a group aggregate without an explicit GROUP BY clause in the SELECT expression.</span></span> <span data-ttu-id="16db2-124">Tüm öğeler tek bir grup, bir sabit üzerinde alan bir gruplama belirtmenin durumuna eşdeğer olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="16db2-124">All elements will be treated as a single group, equivalent to the case of specifying a grouping based on a constant.</span></span>  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol group by 1`  
  
 <span data-ttu-id="16db2-125">GROUP BY yan tümcesinde kullanılan ifadeleri, WHERE yan tümcesi ifade görünür olacak aynı ad çözümleme kapsamı kullanarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="16db2-125">Expressions used in the GROUP BY clause are evaluated by using the same name-resolution scope that would be visible to the WHERE clause expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16db2-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="16db2-126">See Also</span></span>  
 [<span data-ttu-id="16db2-127">İşlevler</span><span class="sxs-lookup"><span data-stu-id="16db2-127">Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
