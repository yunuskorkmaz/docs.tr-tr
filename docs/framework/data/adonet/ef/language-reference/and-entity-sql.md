---
title: '&amp;&amp; (VE) (Varlık SQL)'
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: eab05f7454f8ebc88ed29030503bfa96d0c70756
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59308438"
---
# <a name="ampamp-and-entity-sql"></a><span data-ttu-id="31163-102">&amp;&amp; (VE) (Varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="31163-102">&amp;&amp; (AND) (Entity SQL)</span></span>
<span data-ttu-id="31163-103">Döndürür `true` her iki ifade ise `true`; Aksi takdirde `false` veya `NULL`.</span><span class="sxs-lookup"><span data-stu-id="31163-103">Returns `true` if both expressions are `true`; otherwise, `false` or `NULL`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31163-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="31163-104">Syntax</span></span>  
  
```  
boolean_expression AND boolean_expression  
or  
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="31163-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="31163-105">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="31163-106">Bir Boole değeri döndüren herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="31163-106">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31163-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="31163-107">Remarks</span></span>  
 <span data-ttu-id="31163-108">Çift işaretlerini (& &) ve işleç aynı işlevselliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="31163-108">Double ampersands (&&) have the same functionality as the AND operator.</span></span>  
  
 <span data-ttu-id="31163-109">Aşağıdaki tabloda olası giriş değerleri gösterir ve dönüş türleri.</span><span class="sxs-lookup"><span data-stu-id="31163-109">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="31163-110">TRUE</span><span class="sxs-lookup"><span data-stu-id="31163-110">TRUE</span></span>|<span data-ttu-id="31163-111">FALSE</span><span class="sxs-lookup"><span data-stu-id="31163-111">FALSE</span></span>|<span data-ttu-id="31163-112">NULL</span><span class="sxs-lookup"><span data-stu-id="31163-112">NULL</span></span>|  
|`FALSE`|<span data-ttu-id="31163-113">FALSE</span><span class="sxs-lookup"><span data-stu-id="31163-113">FALSE</span></span>|<span data-ttu-id="31163-114">FALSE</span><span class="sxs-lookup"><span data-stu-id="31163-114">FALSE</span></span>|<span data-ttu-id="31163-115">FALSE</span><span class="sxs-lookup"><span data-stu-id="31163-115">FALSE</span></span>|  
|`NULL`|<span data-ttu-id="31163-116">NULL</span><span class="sxs-lookup"><span data-stu-id="31163-116">NULL</span></span>|<span data-ttu-id="31163-117">FALSE</span><span class="sxs-lookup"><span data-stu-id="31163-117">FALSE</span></span>|<span data-ttu-id="31163-118">NULL</span><span class="sxs-lookup"><span data-stu-id="31163-118">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="31163-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="31163-119">Example</span></span>  
 <span data-ttu-id="31163-120">Aşağıdaki varlık SQL sorgusu ve işlecini kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="31163-120">The following Entity SQL query demonstrates how to use the AND operator.</span></span> <span data-ttu-id="31163-121">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="31163-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="31163-122">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="31163-122">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="31163-123">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="31163-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="31163-124">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="31163-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a><span data-ttu-id="31163-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31163-125">See also</span></span>

- [<span data-ttu-id="31163-126">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="31163-126">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
