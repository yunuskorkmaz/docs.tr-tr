---
title: IÇINDE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
ms.openlocfilehash: e46db63600b6baa03697615a2f5eb9240f55d15e
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833688"
---
# <a name="in-entity-sql"></a><span data-ttu-id="0540e-102">IÇINDE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="0540e-102">IN (Entity SQL)</span></span>
<span data-ttu-id="0540e-103">Bir değerin bir koleksiyondaki herhangi bir değerle eşleşip eşleşmediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="0540e-103">Determines whether a value matches any value in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0540e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0540e-104">Syntax</span></span>  
  
```sql  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="0540e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0540e-105">Arguments</span></span>  
 `value`  
 <span data-ttu-id="0540e-106">Eşleştirilecek değeri döndüren geçerli bir ifade.</span><span class="sxs-lookup"><span data-stu-id="0540e-106">Any valid expression that returns the value to match.</span></span>  
  
 <span data-ttu-id="0540e-107">BAŞLATıLMADı</span><span class="sxs-lookup"><span data-stu-id="0540e-107">[ NOT ]</span></span>  
 <span data-ttu-id="0540e-108">Öğesinin `Boolean` sonucunun bir arada olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0540e-108">Specifies that the `Boolean` result of IN be negated.</span></span>  
  
 `expression`  
 <span data-ttu-id="0540e-109">Bir eşleşme için test edilecek koleksiyonu döndüren geçerli bir ifade.</span><span class="sxs-lookup"><span data-stu-id="0540e-109">Any valid expression that returns the collection to test for a match.</span></span> <span data-ttu-id="0540e-110">Tüm ifadeler aynı türde veya ortak bir temel ya da türetilmiş türden `value` olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0540e-110">All expressions must be of the same type or of a common base or derived type as `value`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0540e-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0540e-111">Return Value</span></span>  
 <span data-ttu-id="0540e-112">değer koleksiyonda bulunursa, `true`; değer null ise veya koleksiyon null ise null; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="0540e-112">`true` if the value is found in the collection; null if the value is null or the collection is null; otherwise, `false`.</span></span> <span data-ttu-id="0540e-113">IÇINDE DEĞIL kullanılması, IÇINDEKI sonuçlarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="0540e-113">Using NOT IN negates the results of IN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0540e-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="0540e-114">Example</span></span>  
 <span data-ttu-id="0540e-115">Aşağıdaki Entity SQL sorgusu, bir değerin bir koleksiyondaki herhangi bir değerle eşleşip eşleşmediğini anlamak için ın işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0540e-115">The following Entity SQL query uses the IN operator to determine whether a value matches any value in a collection.</span></span> <span data-ttu-id="0540e-116">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="0540e-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="0540e-117">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="0540e-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="0540e-118">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="0540e-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="0540e-119">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="0540e-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#IN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#in)]  
  
## <a name="see-also"></a><span data-ttu-id="0540e-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0540e-120">See also</span></span>

- [<span data-ttu-id="0540e-121">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="0540e-121">Entity SQL Reference</span></span>](entity-sql-reference.md)
