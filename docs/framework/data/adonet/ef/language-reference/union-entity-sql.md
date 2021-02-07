---
description: 'Daha fazla bilgi edinin: UNION (Entity SQL)'
title: BIRLEŞIM (Entity SQL)
ms.date: 03/30/2017
ms.assetid: df98a4db-b00d-4c8b-bd74-0d285f27e1df
ms.openlocfilehash: f02b3d76d8c21848b7a1b7ef5e7bbf749aea5c0f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673316"
---
# <a name="union-entity-sql"></a><span data-ttu-id="aaf90-103">BIRLEŞIM (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="aaf90-103">UNION (Entity SQL)</span></span>

<span data-ttu-id="aaf90-104">İki veya daha fazla sorgunun sonuçlarını tek bir koleksiyonda birleştirir.</span><span class="sxs-lookup"><span data-stu-id="aaf90-104">Combines the results of two or more queries into a single collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aaf90-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="aaf90-105">Syntax</span></span>  
  
```sql  
expression  
UNION [ ALL ]  
expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="aaf90-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="aaf90-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="aaf90-107">Koleksiyon ile birleştirmek için bir koleksiyon döndüren geçerli bir sorgu ifadesi tüm ifadeler aynı türde veya ortak temel veya türetilmiş türde olmalıdır `expression` .</span><span class="sxs-lookup"><span data-stu-id="aaf90-107">Any valid query expression that returns a collection to combine with the collection All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
 <span data-ttu-id="aaf90-108">UNION</span><span class="sxs-lookup"><span data-stu-id="aaf90-108">UNION</span></span>  
 <span data-ttu-id="aaf90-109">Birden çok koleksiyonun birleştirildiğini ve tek bir koleksiyon olarak döndürüleceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="aaf90-109">Specifies that multiple collections are to be combined and returned as a single collection.</span></span>  
  
 <span data-ttu-id="aaf90-110">ALL</span><span class="sxs-lookup"><span data-stu-id="aaf90-110">ALL</span></span>  
 <span data-ttu-id="aaf90-111">Birden çok koleksiyonun birleştirildiğini ve yinelemeler dahil olmak üzere tek bir koleksiyon olarak döndürüleceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="aaf90-111">Specifies that multiple collections are to be combined and returned as a single collection, including duplicates.</span></span> <span data-ttu-id="aaf90-112">Belirtilmemişse, yinelemeler sonuç koleksiyonundan kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="aaf90-112">If not specified, duplicates are removed from the result collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aaf90-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="aaf90-113">Return Value</span></span>  

 <span data-ttu-id="aaf90-114">Aynı türde veya ortak bir temel ya da türetilmiş türden bir koleksiyon `expression` .</span><span class="sxs-lookup"><span data-stu-id="aaf90-114">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aaf90-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aaf90-115">Remarks</span></span>  

 <span data-ttu-id="aaf90-116">BIRLEŞIM, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ayarlanan işleçlerden biridir.</span><span class="sxs-lookup"><span data-stu-id="aaf90-116">UNION is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="aaf90-117">Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] küme işleçleri soldan sağa değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="aaf90-117">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="aaf90-118">Set işleçleri için öncelik bilgileri için [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bkz. [except](except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="aaf90-118">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="aaf90-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="aaf90-119">Example</span></span>  

 <span data-ttu-id="aaf90-120">Aşağıdaki Entity SQL sorgusu, iki sorgunun sonuçlarını tek bir koleksiyonda birleştirmek için UNıON ALL işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="aaf90-120">The following Entity SQL query uses the UNION ALL operator to combine the results of two queries into a single collection.</span></span> <span data-ttu-id="aaf90-121">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="aaf90-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="aaf90-122">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="aaf90-122">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="aaf90-123">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="aaf90-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="aaf90-124">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="aaf90-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#UNION](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#union)]  
  
## <a name="see-also"></a><span data-ttu-id="aaf90-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aaf90-125">See also</span></span>

- [<span data-ttu-id="aaf90-126">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="aaf90-126">Entity SQL Reference</span></span>](entity-sql-reference.md)
