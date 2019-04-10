---
title: VARLIKTAKİ (SQL)
ms.date: 03/30/2017
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
ms.openlocfilehash: f4fa8cbc07513321e59b93503b59af172c0a6f05
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211328"
---
# <a name="in-entity-sql"></a><span data-ttu-id="3d2c3-102">VARLIKTAKİ (SQL)</span><span class="sxs-lookup"><span data-stu-id="3d2c3-102">IN (Entity SQL)</span></span>
<span data-ttu-id="3d2c3-103">Değer bir koleksiyondaki herhangi bir değer ile eşleşip eşleşmediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="3d2c3-103">Determines whether a value matches any value in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d2c3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3d2c3-104">Syntax</span></span>  
  
```  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="3d2c3-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="3d2c3-105">Arguments</span></span>  
 `value`  
 <span data-ttu-id="3d2c3-106">Eşleştirilecek değer döndüren herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="3d2c3-106">Any valid expression that returns the value to match.</span></span>  
  
 <span data-ttu-id="3d2c3-107">[NOT]</span><span class="sxs-lookup"><span data-stu-id="3d2c3-107">[ NOT ]</span></span>  
 <span data-ttu-id="3d2c3-108">Belirten `Boolean` IN sonucu tasarruflarını.</span><span class="sxs-lookup"><span data-stu-id="3d2c3-108">Specifies that the `Boolean` result of IN be negated.</span></span>  
  
 `expression`  
 <span data-ttu-id="3d2c3-109">Test etmek için bir eşleşme için koleksiyonu döndüren herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="3d2c3-109">Any valid expression that returns the collection to test for a match.</span></span> <span data-ttu-id="3d2c3-110">Tüm ifadeler aynı türde veya ortak bir temel veya türetilmiş tür olarak olmalıdır `value`.</span><span class="sxs-lookup"><span data-stu-id="3d2c3-110">All expressions must be of the same type or of a common base or derived type as `value`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3d2c3-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3d2c3-111">Return Value</span></span>  
 `true` <span data-ttu-id="3d2c3-112">değer koleksiyonda bulunursa; değer null ise null ya da koleksiyonu null; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="3d2c3-112">if the value is found in the collection; null if the value is null or the collection is null; otherwise, `false`.</span></span> <span data-ttu-id="3d2c3-113">NOT ın kullanarak inç sonuçlarını geçersiz hale getirir.</span><span class="sxs-lookup"><span data-stu-id="3d2c3-113">Using NOT IN negates the results of IN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d2c3-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="3d2c3-114">Example</span></span>  
 <span data-ttu-id="3d2c3-115">Aşağıdaki varlık SQL sorgusu ın işleci bir değer bir koleksiyondaki herhangi bir değer ile eşleşip eşleşmediğini belirlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="3d2c3-115">The following Entity SQL query uses the IN operator to determine whether a value matches any value in a collection.</span></span> <span data-ttu-id="3d2c3-116">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="3d2c3-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="3d2c3-117">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="3d2c3-117">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="3d2c3-118">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="3d2c3-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="3d2c3-119">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="3d2c3-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#IN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#in)]  
  
## <a name="see-also"></a><span data-ttu-id="3d2c3-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d2c3-120">See also</span></span>

- [<span data-ttu-id="3d2c3-121">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="3d2c3-121">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
