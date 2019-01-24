---
title: '&amp;&amp; (VE) (Varlık SQL)'
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: 6ee7987f2801a35fb9669472ce7b237e684f64e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54579673"
---
# <a name="ampamp-and-entity-sql"></a><span data-ttu-id="09d79-102">&amp;&amp; (VE) (Varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="09d79-102">&amp;&amp; (AND) (Entity SQL)</span></span>
<span data-ttu-id="09d79-103">Döndürür `true` her iki ifade ise `true`; Aksi takdirde `false` veya `NULL`.</span><span class="sxs-lookup"><span data-stu-id="09d79-103">Returns `true` if both expressions are `true`; otherwise, `false` or `NULL`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09d79-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="09d79-104">Syntax</span></span>  
  
```  
boolean_expression AND boolean_expression  
or  
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="09d79-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="09d79-105">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="09d79-106">Bir Boole değeri döndüren herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="09d79-106">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09d79-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="09d79-107">Remarks</span></span>  
 <span data-ttu-id="09d79-108">Çift işaretlerini (& &) ve işleç aynı işlevselliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="09d79-108">Double ampersands (&&) have the same functionality as the AND operator.</span></span>  
  
 <span data-ttu-id="09d79-109">Aşağıdaki tabloda olası giriş değerleri gösterir ve dönüş türleri.</span><span class="sxs-lookup"><span data-stu-id="09d79-109">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="09d79-110">TRUE</span><span class="sxs-lookup"><span data-stu-id="09d79-110">TRUE</span></span>|<span data-ttu-id="09d79-111">FALSE</span><span class="sxs-lookup"><span data-stu-id="09d79-111">FALSE</span></span>|<span data-ttu-id="09d79-112">NULL</span><span class="sxs-lookup"><span data-stu-id="09d79-112">NULL</span></span>|  
|`FALSE`|<span data-ttu-id="09d79-113">FALSE</span><span class="sxs-lookup"><span data-stu-id="09d79-113">FALSE</span></span>|<span data-ttu-id="09d79-114">FALSE</span><span class="sxs-lookup"><span data-stu-id="09d79-114">FALSE</span></span>|<span data-ttu-id="09d79-115">FALSE</span><span class="sxs-lookup"><span data-stu-id="09d79-115">FALSE</span></span>|  
|`NULL`|<span data-ttu-id="09d79-116">NULL</span><span class="sxs-lookup"><span data-stu-id="09d79-116">NULL</span></span>|<span data-ttu-id="09d79-117">FALSE</span><span class="sxs-lookup"><span data-stu-id="09d79-117">FALSE</span></span>|<span data-ttu-id="09d79-118">NULL</span><span class="sxs-lookup"><span data-stu-id="09d79-118">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="09d79-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="09d79-119">Example</span></span>  
 <span data-ttu-id="09d79-120">Aşağıdaki varlık SQL sorgusu ve işlecini kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="09d79-120">The following Entity SQL query demonstrates how to use the AND operator.</span></span> <span data-ttu-id="09d79-121">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="09d79-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="09d79-122">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="09d79-122">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="09d79-123">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="09d79-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="09d79-124">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="09d79-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a><span data-ttu-id="09d79-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09d79-125">See also</span></span>
- [<span data-ttu-id="09d79-126">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="09d79-126">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
