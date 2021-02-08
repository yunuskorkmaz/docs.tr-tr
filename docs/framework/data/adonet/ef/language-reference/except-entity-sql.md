---
description: 'Hakkında daha fazla bilgi edinin: EXCEPT (Entity SQL)'
title: EXCEPT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 69cc23e5-3f8f-4b49-b20e-2f84ff11c80d
ms.openlocfilehash: fd66d8dc6e22a73afbfd27e6eb1fd6c8bb9d3475
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786400"
---
# <a name="except-entity-sql"></a><span data-ttu-id="dcde8-103">EXCEPT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="dcde8-103">EXCEPT (Entity SQL)</span></span>

<span data-ttu-id="dcde8-104">Sorgu ifadesinden, EXCEPT işleneninin sağına doğru döndürülmüyor harıç, EXCEPT işlecinin soluna ait herhangi bir farklı değerin bir koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="dcde8-104">Returns a collection of any distinct values from the query expression to the left of the EXCEPT operand that are not also returned from the query expression to the right of the EXCEPT operand.</span></span> <span data-ttu-id="dcde8-105">Tüm ifadeler aynı türde veya ortak bir temel veya türetilmiş türde olmalıdır `expression` .</span><span class="sxs-lookup"><span data-stu-id="dcde8-105">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcde8-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="dcde8-106">Syntax</span></span>  
  
```sql  
expression EXCEPT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="dcde8-107">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="dcde8-107">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="dcde8-108">Başka bir sorgu ifadesinden döndürülen koleksiyonla karşılaştırmak için bir koleksiyon döndüren geçerli bir sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="dcde8-108">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dcde8-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="dcde8-109">Return Value</span></span>  

 <span data-ttu-id="dcde8-110">Aynı türde veya ortak bir temel ya da türetilmiş türden bir koleksiyon `expression` .</span><span class="sxs-lookup"><span data-stu-id="dcde8-110">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dcde8-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dcde8-111">Remarks</span></span>  

 <span data-ttu-id="dcde8-112">EXCEPT, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set işleçlerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="dcde8-112">EXCEPT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="dcde8-113">Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] küme işleçleri soldan sağa değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="dcde8-113">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="dcde8-114">Aşağıdaki tabloda, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set işleçlerinin önceliği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="dcde8-114">The following table shows the precedence of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
|<span data-ttu-id="dcde8-115">Önceliği</span><span class="sxs-lookup"><span data-stu-id="dcde8-115">Precedence</span></span>|<span data-ttu-id="dcde8-116">İşleçler</span><span class="sxs-lookup"><span data-stu-id="dcde8-116">Operators</span></span>|  
|----------------|---------------|  
|<span data-ttu-id="dcde8-117">En yüksek</span><span class="sxs-lookup"><span data-stu-id="dcde8-117">Highest</span></span>|<span data-ttu-id="dcde8-118">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="dcde8-118">INTERSECT</span></span>|  
||<span data-ttu-id="dcde8-119">UNION</span><span class="sxs-lookup"><span data-stu-id="dcde8-119">UNION</span></span><br /><br /> <span data-ttu-id="dcde8-120">TÜMÜNÜ TOPLA</span><span class="sxs-lookup"><span data-stu-id="dcde8-120">UNION ALL</span></span>|  
||<span data-ttu-id="dcde8-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="dcde8-121">EXCEPT</span></span>|  
|<span data-ttu-id="dcde8-122">Minimum</span><span class="sxs-lookup"><span data-stu-id="dcde8-122">Lowest</span></span>|<span data-ttu-id="dcde8-123">EXISTS</span><span class="sxs-lookup"><span data-stu-id="dcde8-123">EXISTS</span></span><br /><br /> <span data-ttu-id="dcde8-124">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="dcde8-124">OVERLAPS</span></span><br /><br /> <span data-ttu-id="dcde8-125">FLATTEN</span><span class="sxs-lookup"><span data-stu-id="dcde8-125">FLATTEN</span></span><br /><br /> <span data-ttu-id="dcde8-126">SET</span><span class="sxs-lookup"><span data-stu-id="dcde8-126">SET</span></span>|  
  
## <a name="example"></a><span data-ttu-id="dcde8-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="dcde8-127">Example</span></span>  

 <span data-ttu-id="dcde8-128">Aşağıdaki Entity SQL sorgusu, iki sorgu ifadesinin farklı değerlerinin bir koleksiyonunu döndürmek için EXCEPT işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="dcde8-128">The following Entity SQL query uses the EXCEPT operator to return a collection of any distinct values from two query expressions.</span></span> <span data-ttu-id="dcde8-129">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="dcde8-129">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="dcde8-130">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="dcde8-130">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="dcde8-131">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="dcde8-131">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="dcde8-132">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="dcde8-132">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#EXCEPT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#except)]  
  
## <a name="see-also"></a><span data-ttu-id="dcde8-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dcde8-133">See also</span></span>

- [<span data-ttu-id="dcde8-134">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="dcde8-134">Entity SQL Reference</span></span>](entity-sql-reference.md)
