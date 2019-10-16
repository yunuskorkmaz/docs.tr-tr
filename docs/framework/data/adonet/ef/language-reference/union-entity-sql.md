---
title: BIRLEŞIM (Entity SQL)
ms.date: 03/30/2017
ms.assetid: df98a4db-b00d-4c8b-bd74-0d285f27e1df
ms.openlocfilehash: a5a20beb0ab55dcbaf2dbbb75801b50ab9ef6722
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319226"
---
# <a name="union-entity-sql"></a><span data-ttu-id="a2144-102">BIRLEŞIM (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a2144-102">UNION (Entity SQL)</span></span>
<span data-ttu-id="a2144-103">İki veya daha fazla sorgunun sonuçlarını tek bir koleksiyonda birleştirir.</span><span class="sxs-lookup"><span data-stu-id="a2144-103">Combines the results of two or more queries into a single collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2144-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a2144-104">Syntax</span></span>  
  
```sql  
expression  
UNION [ ALL ]  
expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="a2144-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a2144-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="a2144-106">Koleksiyon ile birleştirmek için bir koleksiyon döndüren geçerli bir sorgu ifadesi tüm ifadeler aynı türde veya ortak bir temel veya türetilmiş @no__t türde olmalıdır-0.</span><span class="sxs-lookup"><span data-stu-id="a2144-106">Any valid query expression that returns a collection to combine with the collection All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
 <span data-ttu-id="a2144-107">UNION</span><span class="sxs-lookup"><span data-stu-id="a2144-107">UNION</span></span>  
 <span data-ttu-id="a2144-108">Birden çok koleksiyonun birleştirildiğini ve tek bir koleksiyon olarak döndürüleceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a2144-108">Specifies that multiple collections are to be combined and returned as a single collection.</span></span>  
  
 <span data-ttu-id="a2144-109">Bütün</span><span class="sxs-lookup"><span data-stu-id="a2144-109">ALL</span></span>  
 <span data-ttu-id="a2144-110">Birden çok koleksiyonun birleştirildiğini ve yinelemeler dahil olmak üzere tek bir koleksiyon olarak döndürüleceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a2144-110">Specifies that multiple collections are to be combined and returned as a single collection, including duplicates.</span></span> <span data-ttu-id="a2144-111">Belirtilmemişse, yinelemeler sonuç koleksiyonundan kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="a2144-111">If not specified, duplicates are removed from the result collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a2144-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a2144-112">Return Value</span></span>  
 <span data-ttu-id="a2144-113">Aynı türde veya ortak bir temel ya da türetilmiş türden bir koleksiyon `expression` olarak.</span><span class="sxs-lookup"><span data-stu-id="a2144-113">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2144-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a2144-114">Remarks</span></span>  
 <span data-ttu-id="a2144-115">UNION [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kümesi işleçlerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="a2144-115">UNION is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="a2144-116">Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kümesi işleçleri soldan sağa değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="a2144-116">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="a2144-117">@No__t-0 kümesi işleçleri için öncelik bilgisi için, bkz. [except](except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="a2144-117">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2144-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2144-118">Example</span></span>  
 <span data-ttu-id="a2144-119">Aşağıdaki Entity SQL sorgusu, iki sorgunun sonuçlarını tek bir koleksiyonda birleştirmek için UNıON ALL işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a2144-119">The following Entity SQL query uses the UNION ALL operator to combine the results of two queries into a single collection.</span></span> <span data-ttu-id="a2144-120">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="a2144-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a2144-121">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="a2144-121">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="a2144-122">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="a2144-122">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="a2144-123">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="a2144-123">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#UNION](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#union)]  
  
## <a name="see-also"></a><span data-ttu-id="a2144-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2144-124">See also</span></span>

- [<span data-ttu-id="a2144-125">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="a2144-125">Entity SQL Reference</span></span>](entity-sql-reference.md)
