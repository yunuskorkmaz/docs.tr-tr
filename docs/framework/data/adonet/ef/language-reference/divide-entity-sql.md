---
title: '- (Bölme) (Varlık SQL)'
ms.date: 03/30/2017
ms.assetid: ef48c368-f3ed-4275-8ada-4e9649781262
ms.openlocfilehash: 38feaf4509ea2ed2838efe4daa257cdff144e863
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147703"
---
# <a name="-divide-entity-sql"></a><span data-ttu-id="824b0-102">/ (Bölme (varlık SQL))</span><span class="sxs-lookup"><span data-stu-id="824b0-102">/ (Divide) (Entity SQL)</span></span>
<span data-ttu-id="824b0-103">Bir sayıyı bir başkası tarafından böler.</span><span class="sxs-lookup"><span data-stu-id="824b0-103">Divides one number by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="824b0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="824b0-104">Syntax</span></span>  
  
```  
dividend / divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="824b0-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="824b0-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="824b0-106">Bölmek için sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="824b0-106">The numeric expression to divide.</span></span> <span data-ttu-id="824b0-107">`dividend` sayısal veri türleri herhangi birinin herhangi bir geçerli ifade var.</span><span class="sxs-lookup"><span data-stu-id="824b0-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="824b0-108">Bölünenin bölüneceği sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="824b0-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="824b0-109">`divisor` sayısal veri türleri herhangi birinin herhangi bir geçerli ifade var.</span><span class="sxs-lookup"><span data-stu-id="824b0-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="824b0-110">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="824b0-110">Result Types</span></span>  
 <span data-ttu-id="824b0-111">Bu iki bağımsız değişken örtük tür yükseltme sonuçlarından veri türü.</span><span class="sxs-lookup"><span data-stu-id="824b0-111">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="824b0-112">Örtük tür yükseltme hakkında daha fazla bilgi için bkz: [tür sistemi](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="824b0-112">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="824b0-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="824b0-113">Example</span></span>  
 <span data-ttu-id="824b0-114">Aşağıdaki varlık SQL sorgusu kullanır / aritmetik bir başkası tarafından bölme işleci.</span><span class="sxs-lookup"><span data-stu-id="824b0-114">The following Entity SQL query uses the / arithmetic operator to divide one number by another.</span></span> <span data-ttu-id="824b0-115">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="824b0-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="824b0-116">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="824b0-116">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="824b0-117">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="824b0-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="824b0-118">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="824b0-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#DIVIDE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#divide)]  
  
## <a name="see-also"></a><span data-ttu-id="824b0-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="824b0-119">See Also</span></span>  
 [<span data-ttu-id="824b0-120">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="824b0-120">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
