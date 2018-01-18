---
title: "GROUPPARTITION (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0482e9b-086c-451c-9dfa-ccb024a9efb6
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 09d4d1e6d2e69d805c316f60e6d6e91d094e68cb
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="grouppartition-entity-sql"></a><span data-ttu-id="04537-102">GROUPPARTITION (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="04537-102">GROUPPARTITION (Entity SQL)</span></span>
<span data-ttu-id="04537-103">Toplama ilişkili olduğunu geçerli Grup bölümünün öngörülen bağımsız değişken değerleri koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="04537-103">Returns a collection of argument values that are projected off the current group partition to which the aggregate is related.</span></span> <span data-ttu-id="04537-104">`GroupPartition` Toplama bir grup tabanlı toplama olduğundan ve hiçbir koleksiyon tabanlı bir biçime sahip.</span><span class="sxs-lookup"><span data-stu-id="04537-104">The `GroupPartition` aggregate is a group-based aggregate and has no collection-based form.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04537-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="04537-105">Syntax</span></span>  
  
```  
GROUPPARTITION( [ALL|DISTINCT] expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="04537-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="04537-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="04537-107">Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ifade.</span><span class="sxs-lookup"><span data-stu-id="04537-107">Any [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04537-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="04537-108">Remarks</span></span>  
 <span data-ttu-id="04537-109">Aşağıdaki sorgu, ürünler ve her ürün başına sipariş satırı miktarları koleksiyonu listesini üretir:</span><span class="sxs-lookup"><span data-stu-id="04537-109">The following query produces a list of products and a collection of order line quantities per each product:</span></span>  
  
```  
select p, GroupPartition(ol.Quantity) from LOB.OrderLines as ol  
  group by ol.Product as p  
```  
  
 <span data-ttu-id="04537-110">Aşağıdaki iki sorgular anlamsal olarak eşit:</span><span class="sxs-lookup"><span data-stu-id="04537-110">The following two queries are semantically equal:</span></span>  
  
```  
select p, Sum(GroupPartition(ol.Quantity)) from LOB.OrderLines as ol  
  group by ol.Product as p  
select p, Sum(ol.Quantity) from LOB.OrderLines as ol  
  group by ol.Product as p  
```  
  
 <span data-ttu-id="04537-111">`GROUPPARTITION` İşleci, kullanıcı tanımlı toplama işlevleri ile birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="04537-111">The `GROUPPARTITION` operator can be used in conjunction with user-defined aggregate functions.</span></span>  
  
 <span data-ttu-id="04537-112">`GROUPPARTITION`Gruplandırılmış giriş kümesine başvuru tutan bir özel toplama işlecidir.</span><span class="sxs-lookup"><span data-stu-id="04537-112">`GROUPPARTITION` is a special aggregate operator that holds a reference to the grouped input set.</span></span> <span data-ttu-id="04537-113">Bu başvuru, sorguya grupla kapsam içinde olduğu herhangi bir yerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="04537-113">This reference can be used anywhere in the query where GROUP BY is in scope.</span></span> <span data-ttu-id="04537-114">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="04537-114">For example,</span></span>  
  
```  
select p, GroupPartition(ol.Quantity) from LOB.OrderLines as ol group by ol.Product as p  
```  
  
 <span data-ttu-id="04537-115">Normal GROUP BY ile gruplandırma sonuçlarını gizlenir.</span><span class="sxs-lookup"><span data-stu-id="04537-115">With a regular GROUP BY, the results of the grouping are hidden.</span></span> <span data-ttu-id="04537-116">Sonuçları bir toplama işlevinde yalnızca kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="04537-116">You can only use the results in an aggregate function.</span></span> <span data-ttu-id="04537-117">Gruplandırma sonuçlarını görmek için gruplandırma ve bir alt sorgu kullanarak ayarlamak giriş sonuçları ilişkilendirmek sahip.</span><span class="sxs-lookup"><span data-stu-id="04537-117">In order to see the results of the grouping, you have to correlate the results of the grouping and the input set by using a subquery.</span></span> <span data-ttu-id="04537-118">Aşağıdaki iki sorgular eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="04537-118">The following two queries are equivalent:</span></span>  
  
```  
select p, (select q from GroupPartition(ol.Quantity) as q) from LOB.OrderLines as ol group by ol.Product as p  
select p, (select ol.Quantity as q from LOB.OrderLines as ol2 where ol2.Product = p) from LOB.OrderLines as ol group by ol.Product as p  
```  
  
 <span data-ttu-id="04537-119">Örnekte görüldüğü gibi GROUPPARTITION Toplama işleci sonra GROUPING set giriş için bir başvuru almak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="04537-119">As seen from the example, the GROUPPARTITION aggregate operator makes it easier to get a reference to the input set after the grouping.</span></span>  
  
 <span data-ttu-id="04537-120">GROUPPARTITION işleci belirtebilirsiniz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işlecindeki ifade giriş kullandığınızda `expression` parametresi.</span><span class="sxs-lookup"><span data-stu-id="04537-120">The GROUPPARTITION operator can specify any [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression in the operator input when you use the `expression` parameter.</span></span>  
  
 <span data-ttu-id="04537-121">Örneği için tüm Grup bölümü aşağıdaki giriş ifadeleri geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="04537-121">For instance all of the following input expressions to the group partition are valid:</span></span>  
  
```  
select groupkey, GroupPartition(b) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(1) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(a + b) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition({a + b}) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition({42}) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(b > a) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
```  
  
## <a name="example"></a><span data-ttu-id="04537-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="04537-122">Example</span></span>  
 <span data-ttu-id="04537-123">Aşağıdaki örnek GROUP BY yan tümcesinde GROUPPARTITION yan tümcesi kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="04537-123">The following example shows how to use the GROUPPARTITION clause with the GROUP BY clause.</span></span> <span data-ttu-id="04537-124">GROUP BY yan tümcesi grupları `SalesOrderHeader` varlıklar tarafından kendi `Contact`.</span><span class="sxs-lookup"><span data-stu-id="04537-124">The GROUP BY clause groups `SalesOrderHeader` entities by their `Contact`.</span></span> <span data-ttu-id="04537-125">GROUPPARTITION yan tümcesi sonra projeleri `TotalDue` ondalık koleksiyonunda kaynaklanan her grup için özelliği.</span><span class="sxs-lookup"><span data-stu-id="04537-125">The GROUPPARTITION clause then projects the `TotalDue` property for each group, resulting in a collection of decimals.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]
