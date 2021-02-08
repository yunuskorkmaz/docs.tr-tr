---
description: 'Hakkında daha fazla bilgi edinin: var (Entity SQL)'
title: VAR (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d28ead43-4afb-4bdc-af64-efd2e05005d7
ms.openlocfilehash: c6c5b86616d63b9cc3389365a96c382101463732
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786387"
---
# <a name="exists-entity-sql"></a><span data-ttu-id="1ee3c-103">VAR (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="1ee3c-103">EXISTS (Entity SQL)</span></span>

<span data-ttu-id="1ee3c-104">Bir koleksiyonun boş olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="1ee3c-104">Determines if a collection is empty.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ee3c-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1ee3c-105">Syntax</span></span>  
  
```sql  
[NOT] EXISTS ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="1ee3c-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="1ee3c-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="1ee3c-107">Bir koleksiyon döndüren geçerli bir ifade.</span><span class="sxs-lookup"><span data-stu-id="1ee3c-107">Any valid expression that returns a collection.</span></span>  
  
 <span data-ttu-id="1ee3c-108">NOT</span><span class="sxs-lookup"><span data-stu-id="1ee3c-108">NOT</span></span>  
 <span data-ttu-id="1ee3c-109">Sonucunun var olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1ee3c-109">Specifies that the result of EXISTS be negated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1ee3c-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1ee3c-110">Return Value</span></span>  

 <span data-ttu-id="1ee3c-111">`true` koleksiyon boş değilse, Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="1ee3c-111">`true` if the collection is not empty; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ee3c-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1ee3c-112">Remarks</span></span>  

 <span data-ttu-id="1ee3c-113">EXISTS, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set işleçlerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="1ee3c-113">EXISTS is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="1ee3c-114">Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] küme işleçleri soldan sağa değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="1ee3c-114">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="1ee3c-115">Set işleçleri için öncelik bilgileri için [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bkz. [except](except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="1ee3c-115">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ee3c-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="1ee3c-116">Example</span></span>  

 <span data-ttu-id="1ee3c-117">Aşağıdaki Entity SQL sorgusu, koleksiyonun boş olup olmadığını anlamak için EXISTS işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1ee3c-117">The following Entity SQL query uses the EXISTS operator to determine whether the collection is empty.</span></span> <span data-ttu-id="1ee3c-118">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="1ee3c-118">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="1ee3c-119">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="1ee3c-119">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="1ee3c-120">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="1ee3c-120">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="1ee3c-121">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="1ee3c-121">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#EXISTS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#exists)]  
  
## <a name="see-also"></a><span data-ttu-id="1ee3c-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ee3c-122">See also</span></span>

- [<span data-ttu-id="1ee3c-123">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="1ee3c-123">Entity SQL Reference</span></span>](entity-sql-reference.md)
