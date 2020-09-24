---
title: EXCEPT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 69cc23e5-3f8f-4b49-b20e-2f84ff11c80d
ms.openlocfilehash: 6797f8038a83533b5a6bd41ad402daec7abdc7de
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148066"
---
# <a name="except-entity-sql"></a><span data-ttu-id="1b4ee-102">EXCEPT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="1b4ee-102">EXCEPT (Entity SQL)</span></span>

<span data-ttu-id="1b4ee-103">Sorgu ifadesinden, EXCEPT işleneninin sağına doğru döndürülmüyor harıç, EXCEPT işlecinin soluna ait herhangi bir farklı değerin bir koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="1b4ee-103">Returns a collection of any distinct values from the query expression to the left of the EXCEPT operand that are not also returned from the query expression to the right of the EXCEPT operand.</span></span> <span data-ttu-id="1b4ee-104">Tüm ifadeler aynı türde veya ortak bir temel veya türetilmiş türde olmalıdır `expression` .</span><span class="sxs-lookup"><span data-stu-id="1b4ee-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b4ee-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1b4ee-105">Syntax</span></span>  
  
```sql  
expression EXCEPT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="1b4ee-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="1b4ee-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="1b4ee-107">Başka bir sorgu ifadesinden döndürülen koleksiyonla karşılaştırmak için bir koleksiyon döndüren geçerli bir sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="1b4ee-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1b4ee-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1b4ee-108">Return Value</span></span>  

 <span data-ttu-id="1b4ee-109">Aynı türde veya ortak bir temel ya da türetilmiş türden bir koleksiyon `expression` .</span><span class="sxs-lookup"><span data-stu-id="1b4ee-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b4ee-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1b4ee-110">Remarks</span></span>  

 <span data-ttu-id="1b4ee-111">EXCEPT, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set işleçlerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="1b4ee-111">EXCEPT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="1b4ee-112">Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] küme işleçleri soldan sağa değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="1b4ee-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="1b4ee-113">Aşağıdaki tabloda, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set işleçlerinin önceliği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1b4ee-113">The following table shows the precedence of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
|<span data-ttu-id="1b4ee-114">Önceliği</span><span class="sxs-lookup"><span data-stu-id="1b4ee-114">Precedence</span></span>|<span data-ttu-id="1b4ee-115">İşleçler</span><span class="sxs-lookup"><span data-stu-id="1b4ee-115">Operators</span></span>|  
|----------------|---------------|  
|<span data-ttu-id="1b4ee-116">En yüksek</span><span class="sxs-lookup"><span data-stu-id="1b4ee-116">Highest</span></span>|<span data-ttu-id="1b4ee-117">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="1b4ee-117">INTERSECT</span></span>|  
||<span data-ttu-id="1b4ee-118">UNION</span><span class="sxs-lookup"><span data-stu-id="1b4ee-118">UNION</span></span><br /><br /> <span data-ttu-id="1b4ee-119">TÜMÜNÜ TOPLA</span><span class="sxs-lookup"><span data-stu-id="1b4ee-119">UNION ALL</span></span>|  
||<span data-ttu-id="1b4ee-120">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="1b4ee-120">EXCEPT</span></span>|  
|<span data-ttu-id="1b4ee-121">Minimum</span><span class="sxs-lookup"><span data-stu-id="1b4ee-121">Lowest</span></span>|<span data-ttu-id="1b4ee-122">EXISTS</span><span class="sxs-lookup"><span data-stu-id="1b4ee-122">EXISTS</span></span><br /><br /> <span data-ttu-id="1b4ee-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="1b4ee-123">OVERLAPS</span></span><br /><br /> <span data-ttu-id="1b4ee-124">FLATTEN</span><span class="sxs-lookup"><span data-stu-id="1b4ee-124">FLATTEN</span></span><br /><br /> <span data-ttu-id="1b4ee-125">SET</span><span class="sxs-lookup"><span data-stu-id="1b4ee-125">SET</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1b4ee-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="1b4ee-126">Example</span></span>  

 <span data-ttu-id="1b4ee-127">Aşağıdaki Entity SQL sorgusu, iki sorgu ifadesinin farklı değerlerinin bir koleksiyonunu döndürmek için EXCEPT işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1b4ee-127">The following Entity SQL query uses the EXCEPT operator to return a collection of any distinct values from two query expressions.</span></span> <span data-ttu-id="1b4ee-128">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="1b4ee-128">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="1b4ee-129">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="1b4ee-129">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="1b4ee-130">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="1b4ee-130">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="1b4ee-131">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="1b4ee-131">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#EXCEPT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#except)]  
  
## <a name="see-also"></a><span data-ttu-id="1b4ee-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b4ee-132">See also</span></span>

- [<span data-ttu-id="1b4ee-133">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="1b4ee-133">Entity SQL Reference</span></span>](entity-sql-reference.md)
