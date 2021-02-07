---
description: 'Hakkında daha fazla bilgi edinin: (Entity SQL)'
title: IÇINDE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
ms.openlocfilehash: 234ed15430e44d12d4ca7c98fcb4a7bc03d117f9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748602"
---
# <a name="in-entity-sql"></a><span data-ttu-id="177b5-103">IÇINDE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="177b5-103">IN (Entity SQL)</span></span>

<span data-ttu-id="177b5-104">Bir değerin bir koleksiyondaki herhangi bir değerle eşleşip eşleşmediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="177b5-104">Determines whether a value matches any value in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="177b5-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="177b5-105">Syntax</span></span>  
  
```sql  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="177b5-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="177b5-106">Arguments</span></span>  

 `value`  
 <span data-ttu-id="177b5-107">Eşleştirilecek değeri döndüren geçerli bir ifade.</span><span class="sxs-lookup"><span data-stu-id="177b5-107">Any valid expression that returns the value to match.</span></span>  
  
 <span data-ttu-id="177b5-108">BAŞLATıLMADı</span><span class="sxs-lookup"><span data-stu-id="177b5-108">[ NOT ]</span></span>  
 <span data-ttu-id="177b5-109">Sonucunun, IÇINDE olduğunu belirtir `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="177b5-109">Specifies that the `Boolean` result of IN be negated.</span></span>  
  
 `expression`  
 <span data-ttu-id="177b5-110">Bir eşleşme için test edilecek koleksiyonu döndüren geçerli bir ifade.</span><span class="sxs-lookup"><span data-stu-id="177b5-110">Any valid expression that returns the collection to test for a match.</span></span> <span data-ttu-id="177b5-111">Tüm ifadeler aynı türde veya ortak bir temel veya türetilmiş türde olmalıdır `value` .</span><span class="sxs-lookup"><span data-stu-id="177b5-111">All expressions must be of the same type or of a common base or derived type as `value`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="177b5-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="177b5-112">Return Value</span></span>  

 <span data-ttu-id="177b5-113">`true` değer koleksiyonda bulunursa; değer null ise veya koleksiyon null ise null; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="177b5-113">`true` if the value is found in the collection; null if the value is null or the collection is null; otherwise, `false`.</span></span> <span data-ttu-id="177b5-114">IÇINDE DEĞIL kullanılması, IÇINDEKI sonuçlarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="177b5-114">Using NOT IN negates the results of IN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="177b5-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="177b5-115">Example</span></span>  

 <span data-ttu-id="177b5-116">Aşağıdaki Entity SQL sorgusu, bir değerin bir koleksiyondaki herhangi bir değerle eşleşip eşleşmediğini anlamak için ın işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="177b5-116">The following Entity SQL query uses the IN operator to determine whether a value matches any value in a collection.</span></span> <span data-ttu-id="177b5-117">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="177b5-117">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="177b5-118">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="177b5-118">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="177b5-119">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="177b5-119">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="177b5-120">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="177b5-120">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#IN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#in)]  
  
## <a name="see-also"></a><span data-ttu-id="177b5-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="177b5-121">See also</span></span>

- [<span data-ttu-id="177b5-122">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="177b5-122">Entity SQL Reference</span></span>](entity-sql-reference.md)
