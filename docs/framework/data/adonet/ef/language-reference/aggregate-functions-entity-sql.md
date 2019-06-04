---
title: Toplama işlevleri (varlık SQL)
ms.date: 03/30/2017
ms.assetid: acfd3149-f519-4c6e-8fe1-b21d243a0e58
ms.openlocfilehash: b01c7dca675e79c61b87bcc1fb30455286db3118
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489969"
---
# <a name="aggregate-functions-entity-sql"></a><span data-ttu-id="b0c50-102">Toplama işlevleri (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="b0c50-102">Aggregate Functions (Entity SQL)</span></span>
<span data-ttu-id="b0c50-103">Toplama, bir skaler bir koleksiyona bir grup işleminin bir parçası olarak basit bir dil yapıdır.</span><span class="sxs-lookup"><span data-stu-id="b0c50-103">An aggregate is a language construct that condenses a collection into a scalar as a part of a group operation.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="b0c50-104">iki biçimde toplamlar gelir:</span><span class="sxs-lookup"><span data-stu-id="b0c50-104">aggregates come in two forms:</span></span>  
  
- [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="b0c50-105">bir ifadede herhangi bir yere kullanılabilir işlevler koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="b0c50-105">collection functions that may be used anywhere in an expression.</span></span> <span data-ttu-id="b0c50-106">Bu toplama işlevleri projeksiyonlar ve hareket doğrulamaları koleksiyonlarda kullanarak içerir.</span><span class="sxs-lookup"><span data-stu-id="b0c50-106">This includes using aggregate functions in projections and predicates that act on collections.</span></span> <span data-ttu-id="b0c50-107">Koleksiyon işlevlerdir toplamalar belirtme tercih edilen modu [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b0c50-107">Collection functions are the preferred mode of specifying aggregates in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
- <span data-ttu-id="b0c50-108">GROUP BY yan tümcesine sahip sorgu ifadelerinde Grup toplar.</span><span class="sxs-lookup"><span data-stu-id="b0c50-108">Group aggregates in query expressions that have a GROUP BY clause.</span></span> <span data-ttu-id="b0c50-109">Transact-SQL olduğu gibi Grup toplamları DISTINCT ve tüm değiştiricilere birleşik giriş olarak kabul edin.</span><span class="sxs-lookup"><span data-stu-id="b0c50-109">As in Transact-SQL, group aggregates accept DISTINCT and ALL as modifiers to the aggregate input.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="b0c50-110">ifade bir toplama işlevi olarak yorumlamak ilk olarak çalışır ve deyim bir SELECT deyimi bağlamında, yorumlar, bir grup toplama.</span><span class="sxs-lookup"><span data-stu-id="b0c50-110">first tries to interpret an expression as a collection function and if the expression is in the context of a SELECT expression it interprets it as a group aggregate.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="b0c50-111">olarak adlandırılan özel bir toplama işleci tanımlar [GROUPPARTITION](../../../../../../docs/framework/data/adonet/ef/language-reference/grouppartition-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="b0c50-111">defines a special aggregate operator called [GROUPPARTITION](../../../../../../docs/framework/data/adonet/ef/language-reference/grouppartition-entity-sql.md).</span></span> <span data-ttu-id="b0c50-112">Bu işleç, gruplandırılmış giriş kümesinde bir başvuru almak sağlar.</span><span class="sxs-lookup"><span data-stu-id="b0c50-112">This operator enables you to get a reference to the grouped input set.</span></span> <span data-ttu-id="b0c50-113">GROUP BY yan tümcesinin sonuçlarını grubu toplama veya toplama işlevleri başka yerde nerede kullanılabilir bu daha gelişmiş sorgular, gruplandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="b0c50-113">This allows more advanced grouping queries, where the results of the GROUP BY clause can be used in places other than group aggregate or collection functions.</span></span>  
  
## <a name="collection-functions"></a><span data-ttu-id="b0c50-114">Toplama işlevleri</span><span class="sxs-lookup"><span data-stu-id="b0c50-114">Collection Functions</span></span>  
 <span data-ttu-id="b0c50-115">Toplama işlevleri koleksiyonlarda çalışır ve bir skaler değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="b0c50-115">Collection functions operate on collections and return a scalar value.</span></span> <span data-ttu-id="b0c50-116">Örneğin, varsa `orders` tüm oluşan bir koleksiyondur `orders`, sevk tarihten şu ifadeyle hesaplayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b0c50-116">For example, if `orders` is a collection of all `orders`, you can calculate the earliest ship date with the following expression:</span></span>  
  
 `min(select value o.ShipDate from LOB.Orders as o)`  
  
## <a name="group-aggregates"></a><span data-ttu-id="b0c50-117">Grup toplamları</span><span class="sxs-lookup"><span data-stu-id="b0c50-117">Group Aggregates</span></span>  
 <span data-ttu-id="b0c50-118">Grup toplamalar, GROUP BY yan tümcesi tarafından tanımlanan bir grup sonucu üzerinden hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="b0c50-118">Group aggregates are calculated over a group result as defined by the GROUP BY clause.</span></span> <span data-ttu-id="b0c50-119">GROUP BY yan tümcesi veri gruplara böler.</span><span class="sxs-lookup"><span data-stu-id="b0c50-119">The GROUP BY clause partitions data  into groups.</span></span> <span data-ttu-id="b0c50-120">Her grup için sonuç, toplama işlevi uygulanır ve ayrı bir toplama toplam hesaplaması için girdi olarak her gruba öğeleri kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="b0c50-120">For each group in the result, the aggregate function is applied and a separate aggregate is calculated by using the elements in each group as inputs to the aggregate calculation.</span></span> <span data-ttu-id="b0c50-121">GROUP BY yan tümcesi ifade adlarının, toplamlar ve sabit ifadeler yalnızca gruplandırma seçin ifadesinde kullanıldığında sahip, projeksiyonda bulunması veya ORDER BY yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="b0c50-121">When a GROUP BY clause is used in a SELECT expression, only grouping expression names, aggregates, or constant expressions may be present in the projection, HAVING, or ORDER BY clause.</span></span>  
  
 <span data-ttu-id="b0c50-122">Aşağıdaki örnek, her ürün için sıralı ortalama miktarı hesaplar.</span><span class="sxs-lookup"><span data-stu-id="b0c50-122">The following example calculates the average quantity ordered for each product.</span></span>  
  
 `select p, avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `group by ol.Product as p`  
  
 <span data-ttu-id="b0c50-123">Bir açık GROUP BY yan tümcesi olmadan toplama grubu SELECT deyimini olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="b0c50-123">It is possible to have a group aggregate without an explicit GROUP BY clause in the SELECT expression.</span></span> <span data-ttu-id="b0c50-124">Tüm öğeleri, eşdeğer bir sabit üzerinde temel alan bir gruplama belirtme kullanım durumu için tek bir grup olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="b0c50-124">All elements will be treated as a single group, equivalent to the case of specifying a grouping based on a constant.</span></span>  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol group by 1`  
  
 <span data-ttu-id="b0c50-125">WHERE yan tümcesi ifade görünür olur aynı ad çözümleme kapsamı kullanarak GROUP BY yan tümcesinde kullanılan ifadeler değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="b0c50-125">Expressions used in the GROUP BY clause are evaluated by using the same name-resolution scope that would be visible to the WHERE clause expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0c50-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0c50-126">See also</span></span>

- [<span data-ttu-id="b0c50-127">İşlevler</span><span class="sxs-lookup"><span data-stu-id="b0c50-127">Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
