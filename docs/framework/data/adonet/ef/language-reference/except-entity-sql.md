---
title: EXCEPT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 69cc23e5-3f8f-4b49-b20e-2f84ff11c80d
ms.openlocfilehash: c4df8c2b72ee60a425c98c64a13a1e2d43d4506e
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833856"
---
# <a name="except-entity-sql"></a><span data-ttu-id="f61f2-102">EXCEPT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f61f2-102">EXCEPT (Entity SQL)</span></span>
<span data-ttu-id="f61f2-103">Sorgu ifadesinden, EXCEPT işleneninin sağına doğru döndürülmüyor harıç, EXCEPT işlecinin soluna ait herhangi bir farklı değerin bir koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="f61f2-103">Returns a collection of any distinct values from the query expression to the left of the EXCEPT operand that are not also returned from the query expression to the right of the EXCEPT operand.</span></span> <span data-ttu-id="f61f2-104">Tüm ifadeler aynı türde veya ortak bir temel ya da türetilmiş türden `expression` olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f61f2-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f61f2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f61f2-105">Syntax</span></span>  
  
```sql  
expression EXCEPT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="f61f2-106">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="f61f2-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="f61f2-107">Başka bir sorgu ifadesinden döndürülen koleksiyonla karşılaştırmak için bir koleksiyon döndüren geçerli bir sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="f61f2-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f61f2-108">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="f61f2-108">Return Value</span></span>  
 <span data-ttu-id="f61f2-109">Aynı türde veya ortak bir temel ya da türetilmiş türden bir koleksiyon `expression` olarak.</span><span class="sxs-lookup"><span data-stu-id="f61f2-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f61f2-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f61f2-110">Remarks</span></span>  
 <span data-ttu-id="f61f2-111">EXCEPT [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kümesi işleçlerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="f61f2-111">EXCEPT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="f61f2-112">Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kümesi işleçleri soldan sağa değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="f61f2-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="f61f2-113">Aşağıdaki tabloda [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kümesi işleçlerinin önceliği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f61f2-113">The following table shows the precedence of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
|<span data-ttu-id="f61f2-114">Ayarlarından</span><span class="sxs-lookup"><span data-stu-id="f61f2-114">Precedence</span></span>|<span data-ttu-id="f61f2-115">İşleçler</span><span class="sxs-lookup"><span data-stu-id="f61f2-115">Operators</span></span>|  
|----------------|---------------|  
|<span data-ttu-id="f61f2-116">En Yüksek</span><span class="sxs-lookup"><span data-stu-id="f61f2-116">Highest</span></span>|<span data-ttu-id="f61f2-117">KESIŞ</span><span class="sxs-lookup"><span data-stu-id="f61f2-117">INTERSECT</span></span>|  
||<span data-ttu-id="f61f2-118">UNION</span><span class="sxs-lookup"><span data-stu-id="f61f2-118">UNION</span></span><br /><br /> <span data-ttu-id="f61f2-119">TÜMÜNÜ TOPLA</span><span class="sxs-lookup"><span data-stu-id="f61f2-119">UNION ALL</span></span>|  
||<span data-ttu-id="f61f2-120">KULLANıLDıKLARı</span><span class="sxs-lookup"><span data-stu-id="f61f2-120">EXCEPT</span></span>|  
|<span data-ttu-id="f61f2-121">En Düşük</span><span class="sxs-lookup"><span data-stu-id="f61f2-121">Lowest</span></span>|<span data-ttu-id="f61f2-122">BULUNUR</span><span class="sxs-lookup"><span data-stu-id="f61f2-122">EXISTS</span></span><br /><br /> <span data-ttu-id="f61f2-123">ÇAKıŞ</span><span class="sxs-lookup"><span data-stu-id="f61f2-123">OVERLAPS</span></span><br /><br /> <span data-ttu-id="f61f2-124">LEŞTIREBILIR</span><span class="sxs-lookup"><span data-stu-id="f61f2-124">FLATTEN</span></span><br /><br /> <span data-ttu-id="f61f2-125">KURMAK</span><span class="sxs-lookup"><span data-stu-id="f61f2-125">SET</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f61f2-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="f61f2-126">Example</span></span>  
 <span data-ttu-id="f61f2-127">Aşağıdaki Entity SQL sorgusu, iki sorgu ifadesinin farklı değerlerinin bir koleksiyonunu döndürmek için EXCEPT işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f61f2-127">The following Entity SQL query uses the EXCEPT operator to return a collection of any distinct values from two query expressions.</span></span> <span data-ttu-id="f61f2-128">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="f61f2-128">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="f61f2-129">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="f61f2-129">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="f61f2-130">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="f61f2-130">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="f61f2-131">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="f61f2-131">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#EXCEPT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#except)]  
  
## <a name="see-also"></a><span data-ttu-id="f61f2-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f61f2-132">See also</span></span>

- [<span data-ttu-id="f61f2-133">Entity SQL başvurusu</span><span class="sxs-lookup"><span data-stu-id="f61f2-133">Entity SQL Reference</span></span>](entity-sql-reference.md)
