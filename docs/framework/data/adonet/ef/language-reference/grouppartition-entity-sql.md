---
title: GROUPPARTITION (varlık SQL)
ms.date: 03/30/2017
ms.assetid: d0482e9b-086c-451c-9dfa-ccb024a9efb6
ms.openlocfilehash: 9f0f917380e6422da753282216529580f87f1a1a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774731"
---
# <a name="grouppartition-entity-sql"></a><span data-ttu-id="61872-102">GROUPPARTITION (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="61872-102">GROUPPARTITION (Entity SQL)</span></span>
<span data-ttu-id="61872-103">Toplama ilişkili olduğunu geçerli grubu bölümü öngörülen bağımsız değişken değerleri koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="61872-103">Returns a collection of argument values that are projected off the current group partition to which the aggregate is related.</span></span> <span data-ttu-id="61872-104">`GroupPartition` Toplama grup tabanlı bir toplama ve hiçbir koleksiyon tabanlı bir biçimde.</span><span class="sxs-lookup"><span data-stu-id="61872-104">The `GroupPartition` aggregate is a group-based aggregate and has no collection-based form.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61872-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="61872-105">Syntax</span></span>  
  
```  
GROUPPARTITION( [ALL|DISTINCT] expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="61872-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="61872-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="61872-107">Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ifade.</span><span class="sxs-lookup"><span data-stu-id="61872-107">Any [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61872-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="61872-108">Remarks</span></span>  
 <span data-ttu-id="61872-109">Aşağıdaki sorgu, ürün ve sipariş satırı miktarları her ürün başına koleksiyonunu bir liste oluşturur:</span><span class="sxs-lookup"><span data-stu-id="61872-109">The following query produces a list of products and a collection of order line quantities per each product:</span></span>  
  
```  
select p, GroupPartition(ol.Quantity) from LOB.OrderLines as ol  
  group by ol.Product as p  
```  
  
 <span data-ttu-id="61872-110">Aşağıdaki iki sorguları anlamsal olarak eşit:</span><span class="sxs-lookup"><span data-stu-id="61872-110">The following two queries are semantically equal:</span></span>  
  
```  
select p, Sum(GroupPartition(ol.Quantity)) from LOB.OrderLines as ol  
  group by ol.Product as p  
select p, Sum(ol.Quantity) from LOB.OrderLines as ol  
  group by ol.Product as p  
```  
  
 <span data-ttu-id="61872-111">`GROUPPARTITION` İşleci, kullanıcı tanımlı toplama işlevleri ile birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="61872-111">The `GROUPPARTITION` operator can be used in conjunction with user-defined aggregate functions.</span></span>  
  
 <span data-ttu-id="61872-112">`GROUPPARTITION` Gruplandırılmış giriş kümesinde bir başvuru tutan bir özel toplama işlecidir.</span><span class="sxs-lookup"><span data-stu-id="61872-112">`GROUPPARTITION` is a special aggregate operator that holds a reference to the grouped input set.</span></span> <span data-ttu-id="61872-113">Bu başvuru, sorguda GROUP BY kapsamında olduğu her yerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="61872-113">This reference can be used anywhere in the query where GROUP BY is in scope.</span></span> <span data-ttu-id="61872-114">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="61872-114">For example,</span></span>  
  
```  
select p, GroupPartition(ol.Quantity) from LOB.OrderLines as ol group by ol.Product as p  
```  
  
 <span data-ttu-id="61872-115">Bir normal GROUP BY, gruplandırma sonuçlarını gizlidir.</span><span class="sxs-lookup"><span data-stu-id="61872-115">With a regular GROUP BY, the results of the grouping are hidden.</span></span> <span data-ttu-id="61872-116">Bu gibi durumlarda, sonuçları yalnızca bir toplama işlevinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61872-116">You can only use the results in an aggregate function.</span></span> <span data-ttu-id="61872-117">Gruplandırma sonuçlarını görmek için gruplandırma ve bir alt sorgu kullanarak giriş sonuçları ilişkilendirin gerekir.</span><span class="sxs-lookup"><span data-stu-id="61872-117">In order to see the results of the grouping, you have to correlate the results of the grouping and the input set by using a subquery.</span></span> <span data-ttu-id="61872-118">Aşağıdaki iki sorguları eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="61872-118">The following two queries are equivalent:</span></span>  
  
```  
select p, (select q from GroupPartition(ol.Quantity) as q) from LOB.OrderLines as ol group by ol.Product as p  
select p, (select ol.Quantity as q from LOB.OrderLines as ol2 where ol2.Product = p) from LOB.OrderLines as ol group by ol.Product as p  
```  
  
 <span data-ttu-id="61872-119">Örnekte görüldüğü gibi toplama GROUPPARTITION işleci sonra GROUPING set giriş için bir başvuru almak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="61872-119">As seen from the example, the GROUPPARTITION aggregate operator makes it easier to get a reference to the input set after the grouping.</span></span>  
  
 <span data-ttu-id="61872-120">GROUPPARTITION işleci belirtebilirsiniz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleç bir ifadede giriş kullandığınızda `expression` parametresi.</span><span class="sxs-lookup"><span data-stu-id="61872-120">The GROUPPARTITION operator can specify any [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression in the operator input when you use the `expression` parameter.</span></span>  
  
 <span data-ttu-id="61872-121">Örneği için tüm Grup bölümüne aşağıdaki giriş ifadelerin geçerli şunlardır:</span><span class="sxs-lookup"><span data-stu-id="61872-121">For instance all of the following input expressions to the group partition are valid:</span></span>  
  
```  
select groupkey, GroupPartition(b) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(1) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(a + b) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition({a + b}) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition({42}) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(b > a) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
```  
  
## <a name="example"></a><span data-ttu-id="61872-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="61872-122">Example</span></span>  
 <span data-ttu-id="61872-123">Aşağıdaki örnek, GROUP BY yan tümcesi ile GROUPPARTITION yan tümcesini kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="61872-123">The following example shows how to use the GROUPPARTITION clause with the GROUP BY clause.</span></span> <span data-ttu-id="61872-124">GROUP BY yan tümcesi grupları `SalesOrderHeader` varlıklar tarafından kendi `Contact`.</span><span class="sxs-lookup"><span data-stu-id="61872-124">The GROUP BY clause groups `SalesOrderHeader` entities by their `Contact`.</span></span> <span data-ttu-id="61872-125">GROUPPARTITION yan tümcesi sonra projeleri `TotalDue` ondalık bir koleksiyonda bunun sonucunda, her grup için özellik.</span><span class="sxs-lookup"><span data-stu-id="61872-125">The GROUPPARTITION clause then projects the `TotalDue` property for each group, resulting in a collection of decimals.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]
