---
title: VAR (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d28ead43-4afb-4bdc-af64-efd2e05005d7
ms.openlocfilehash: 44f128a292b013fd3a3a80efdd2d10a63e3cfb07
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833831"
---
# <a name="exists-entity-sql"></a><span data-ttu-id="73361-102">VAR (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="73361-102">EXISTS (Entity SQL)</span></span>
<span data-ttu-id="73361-103">Bir koleksiyonun boş olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="73361-103">Determines if a collection is empty.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73361-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="73361-104">Syntax</span></span>  
  
```sql  
[NOT] EXISTS ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="73361-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="73361-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="73361-106">Bir koleksiyon döndüren geçerli bir ifade.</span><span class="sxs-lookup"><span data-stu-id="73361-106">Any valid expression that returns a collection.</span></span>  
  
 <span data-ttu-id="73361-107">BAŞLATıLMADı</span><span class="sxs-lookup"><span data-stu-id="73361-107">NOT</span></span>  
 <span data-ttu-id="73361-108">Sonucunun var olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="73361-108">Specifies that the result of EXISTS be negated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73361-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="73361-109">Return Value</span></span>  
 <span data-ttu-id="73361-110">koleksiyon boş değilse, `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="73361-110">`true` if the collection is not empty; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73361-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="73361-111">Remarks</span></span>  
 <span data-ttu-id="73361-112">VAR [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kümesi işleçlerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="73361-112">EXISTS is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="73361-113">Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kümesi işleçleri soldan sağa değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="73361-113">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="73361-114">@No__t-0 kümesi işleçleri için öncelik bilgisi için, bkz. [except](except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="73361-114">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="73361-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="73361-115">Example</span></span>  
 <span data-ttu-id="73361-116">Aşağıdaki Entity SQL sorgusu, koleksiyonun boş olup olmadığını anlamak için EXISTS işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="73361-116">The following Entity SQL query uses the EXISTS operator to determine whether the collection is empty.</span></span> <span data-ttu-id="73361-117">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="73361-117">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="73361-118">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="73361-118">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="73361-119">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="73361-119">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="73361-120">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="73361-120">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#EXISTS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#exists)]  
  
## <a name="see-also"></a><span data-ttu-id="73361-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73361-121">See also</span></span>

- [<span data-ttu-id="73361-122">Entity SQL başvurusu</span><span class="sxs-lookup"><span data-stu-id="73361-122">Entity SQL Reference</span></span>](entity-sql-reference.md)
