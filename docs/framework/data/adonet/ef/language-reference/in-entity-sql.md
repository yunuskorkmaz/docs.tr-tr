---
title: VARLIKTAKİ (SQL)
ms.date: 03/30/2017
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
ms.openlocfilehash: a8c028bf0fc2890b932c62aa9efe94cab153503d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54693496"
---
# <a name="in-entity-sql"></a><span data-ttu-id="fdeaf-102">VARLIKTAKİ (SQL)</span><span class="sxs-lookup"><span data-stu-id="fdeaf-102">IN (Entity SQL)</span></span>
<span data-ttu-id="fdeaf-103">Değer bir koleksiyondaki herhangi bir değer ile eşleşip eşleşmediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="fdeaf-103">Determines whether a value matches any value in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdeaf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fdeaf-104">Syntax</span></span>  
  
```  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="fdeaf-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="fdeaf-105">Arguments</span></span>  
 `value`  
 <span data-ttu-id="fdeaf-106">Eşleştirilecek değer döndüren herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="fdeaf-106">Any valid expression that returns the value to match.</span></span>  
  
 <span data-ttu-id="fdeaf-107">[NOT]</span><span class="sxs-lookup"><span data-stu-id="fdeaf-107">[ NOT ]</span></span>  
 <span data-ttu-id="fdeaf-108">Belirten `Boolean` IN sonucu tasarruflarını.</span><span class="sxs-lookup"><span data-stu-id="fdeaf-108">Specifies that the `Boolean` result of IN be negated.</span></span>  
  
 `expression`  
 <span data-ttu-id="fdeaf-109">Test etmek için bir eşleşme için koleksiyonu döndüren herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="fdeaf-109">Any valid expression that returns the collection to test for a match.</span></span> <span data-ttu-id="fdeaf-110">Tüm ifadeler aynı türde veya ortak bir temel veya türetilmiş tür olarak olmalıdır `value`.</span><span class="sxs-lookup"><span data-stu-id="fdeaf-110">All expressions must be of the same type or of a common base or derived type as `value`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fdeaf-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fdeaf-111">Return Value</span></span>  
 <span data-ttu-id="fdeaf-112">`true` değer koleksiyonda bulunursa; değer null ise null ya da koleksiyonu null; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="fdeaf-112">`true` if the value is found in the collection; null if the value is null or the collection is null; otherwise, `false`.</span></span> <span data-ttu-id="fdeaf-113">NOT ın kullanarak inç sonuçlarını geçersiz hale getirir.</span><span class="sxs-lookup"><span data-stu-id="fdeaf-113">Using NOT IN negates the results of IN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fdeaf-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="fdeaf-114">Example</span></span>  
 <span data-ttu-id="fdeaf-115">Aşağıdaki varlık SQL sorgusu ın işleci bir değer bir koleksiyondaki herhangi bir değer ile eşleşip eşleşmediğini belirlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="fdeaf-115">The following Entity SQL query uses the IN operator to determine whether a value matches any value in a collection.</span></span> <span data-ttu-id="fdeaf-116">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="fdeaf-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="fdeaf-117">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="fdeaf-117">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="fdeaf-118">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="fdeaf-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="fdeaf-119">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="fdeaf-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#IN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#in)]  
  
## <a name="see-also"></a><span data-ttu-id="fdeaf-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fdeaf-120">See also</span></span>
- [<span data-ttu-id="fdeaf-121">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="fdeaf-121">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
