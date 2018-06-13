---
title: + (Ekle)
ms.date: 03/30/2017
ms.assetid: 51769b02-a8f7-4177-9e99-bbd10e77092c
ms.openlocfilehash: fcdee9388963553fef377a887d2e07161353f6c5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761733"
---
# <a name="-add"></a><span data-ttu-id="00c1f-102">+ (Ekle)</span><span class="sxs-lookup"><span data-stu-id="00c1f-102">+ (Add)</span></span>
<span data-ttu-id="00c1f-103">İki sayıyı toplar.</span><span class="sxs-lookup"><span data-stu-id="00c1f-103">Adds two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00c1f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="00c1f-104">Syntax</span></span>  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="00c1f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="00c1f-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="00c1f-106">Sayısal veri türleri herhangi birinin geçerli bir ifade.</span><span class="sxs-lookup"><span data-stu-id="00c1f-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="00c1f-107">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="00c1f-107">Result Types</span></span>  
 <span data-ttu-id="00c1f-108">İki bağımsız değişken örtük tür yükseltme sonuçları veri türü.</span><span class="sxs-lookup"><span data-stu-id="00c1f-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="00c1f-109">Örtük tür yükseltme hakkında daha fazla bilgi için bkz: [tür sistemi](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="00c1f-109">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00c1f-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="00c1f-110">Remarks</span></span>  
 <span data-ttu-id="00c1f-111">EDM için. Dize türleri, ek birleştirme olur.</span><span class="sxs-lookup"><span data-stu-id="00c1f-111">For EDM.String types, addition is concatenation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00c1f-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="00c1f-112">Example</span></span>  
 <span data-ttu-id="00c1f-113">Aşağıdaki varlık SQL sorgusu kullanır + iki sayı eklemek için aritmetik işleç.</span><span class="sxs-lookup"><span data-stu-id="00c1f-113">The following Entity SQL query uses the + arithmetic operator to add two numbers.</span></span> <span data-ttu-id="00c1f-114">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="00c1f-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="00c1f-115">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="00c1f-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="00c1f-116">Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="00c1f-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="00c1f-117">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="00c1f-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ADD](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#add)]  
  
## <a name="see-also"></a><span data-ttu-id="00c1f-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="00c1f-118">See Also</span></span>  
 [<span data-ttu-id="00c1f-119">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="00c1f-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="00c1f-120">Kavramsal Model türü (CSDL)</span><span class="sxs-lookup"><span data-stu-id="00c1f-120">Conceptual Model Types (CSDL)</span></span>](http://msdn.microsoft.com/library/987b995f-e429-4569-9559-b4146744def4)
