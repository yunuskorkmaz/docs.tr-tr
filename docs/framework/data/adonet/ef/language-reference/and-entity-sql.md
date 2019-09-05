---
title: "&amp;&amp;' (Entity SQL)"
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: 02e404b73e5a9a9c3963e2d2b58ab7592afabc13
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251309"
---
# <a name="ampamp-and-entity-sql"></a><span data-ttu-id="ed710-102">&amp;&amp;' (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ed710-102">&amp;&amp; (AND) (Entity SQL)</span></span>
<span data-ttu-id="ed710-103">Her `true` iki `false` `NULL`ifade de varsa döndürür ;Aksitakdirdeveya.`true`</span><span class="sxs-lookup"><span data-stu-id="ed710-103">Returns `true` if both expressions are `true`; otherwise, `false` or `NULL`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed710-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ed710-104">Syntax</span></span>  
  
```  
boolean_expression AND boolean_expression  
or  
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="ed710-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ed710-105">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="ed710-106">Boolean döndüren geçerli bir ifade.</span><span class="sxs-lookup"><span data-stu-id="ed710-106">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed710-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ed710-107">Remarks</span></span>  
 <span data-ttu-id="ed710-108">Çift ve işareti (& &), ve işleciyle aynı işlevselliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ed710-108">Double ampersands (&&) have the same functionality as the AND operator.</span></span>  
  
 <span data-ttu-id="ed710-109">Aşağıdaki tabloda olası giriş değerleri ve dönüş türleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ed710-109">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="ed710-110">TRUE</span><span class="sxs-lookup"><span data-stu-id="ed710-110">TRUE</span></span>|<span data-ttu-id="ed710-111">YANLÝÞ</span><span class="sxs-lookup"><span data-stu-id="ed710-111">FALSE</span></span>|<span data-ttu-id="ed710-112">NULL</span><span class="sxs-lookup"><span data-stu-id="ed710-112">NULL</span></span>|  
|`FALSE`|<span data-ttu-id="ed710-113">YANLÝÞ</span><span class="sxs-lookup"><span data-stu-id="ed710-113">FALSE</span></span>|<span data-ttu-id="ed710-114">YANLÝÞ</span><span class="sxs-lookup"><span data-stu-id="ed710-114">FALSE</span></span>|<span data-ttu-id="ed710-115">YANLÝÞ</span><span class="sxs-lookup"><span data-stu-id="ed710-115">FALSE</span></span>|  
|`NULL`|<span data-ttu-id="ed710-116">NULL</span><span class="sxs-lookup"><span data-stu-id="ed710-116">NULL</span></span>|<span data-ttu-id="ed710-117">YANLÝÞ</span><span class="sxs-lookup"><span data-stu-id="ed710-117">FALSE</span></span>|<span data-ttu-id="ed710-118">NULL</span><span class="sxs-lookup"><span data-stu-id="ed710-118">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ed710-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="ed710-119">Example</span></span>  
 <span data-ttu-id="ed710-120">Aşağıdaki Entity SQL sorgusu, ve işlecinin nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="ed710-120">The following Entity SQL query demonstrates how to use the AND operator.</span></span> <span data-ttu-id="ed710-121">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="ed710-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ed710-122">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="ed710-122">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="ed710-123">[Aşağıdaki adımları uygulayın: StructuralType sonuçları](../how-to-execute-a-query-that-returns-structuraltype-results.md)döndüren bir sorgu yürütün.</span><span class="sxs-lookup"><span data-stu-id="ed710-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="ed710-124">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="ed710-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a><span data-ttu-id="ed710-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed710-125">See also</span></span>

- [<span data-ttu-id="ed710-126">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="ed710-126">Entity SQL Reference</span></span>](entity-sql-reference.md)
