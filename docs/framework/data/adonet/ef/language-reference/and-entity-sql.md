---
title: '&amp;&amp;(VE) (Varlık SQL)'
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: eccad616de287a39c42e986cea84dc22feec7f70
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150523"
---
# <a name="ampamp-and-entity-sql"></a><span data-ttu-id="bd7a3-102">&amp;&amp;(VE) (Varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="bd7a3-102">&amp;&amp; (AND) (Entity SQL)</span></span>
<span data-ttu-id="bd7a3-103">Her `true` iki ifade `true`de varsa döndürür; aksi `false` takdirde, ya da `NULL`.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-103">Returns `true` if both expressions are `true`; otherwise, `false` or `NULL`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd7a3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bd7a3-104">Syntax</span></span>  
  
```csharp  
boolean_expression AND boolean_expression
```

<span data-ttu-id="bd7a3-105">or</span><span class="sxs-lookup"><span data-stu-id="bd7a3-105">or</span></span>  

```csharp
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="bd7a3-106">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="bd7a3-106">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="bd7a3-107">Boolean döndüren geçerli bir ifade.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-107">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd7a3-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bd7a3-108">Remarks</span></span>  
 <span data-ttu-id="bd7a3-109">Çift amperandlar (&&) AND işleci ile aynı işlevsellik vardır.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-109">Double ampersands (&&) have the same functionality as the AND operator.</span></span>  
  
 <span data-ttu-id="bd7a3-110">Aşağıdaki tabloda olası giriş değerleri ve dönüş türleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-110">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="bd7a3-111">TRUE</span><span class="sxs-lookup"><span data-stu-id="bd7a3-111">TRUE</span></span>|<span data-ttu-id="bd7a3-112">FALSE</span><span class="sxs-lookup"><span data-stu-id="bd7a3-112">FALSE</span></span>|<span data-ttu-id="bd7a3-113">NULL</span><span class="sxs-lookup"><span data-stu-id="bd7a3-113">NULL</span></span>|  
|`FALSE`|<span data-ttu-id="bd7a3-114">FALSE</span><span class="sxs-lookup"><span data-stu-id="bd7a3-114">FALSE</span></span>|<span data-ttu-id="bd7a3-115">FALSE</span><span class="sxs-lookup"><span data-stu-id="bd7a3-115">FALSE</span></span>|<span data-ttu-id="bd7a3-116">FALSE</span><span class="sxs-lookup"><span data-stu-id="bd7a3-116">FALSE</span></span>|  
|`NULL`|<span data-ttu-id="bd7a3-117">NULL</span><span class="sxs-lookup"><span data-stu-id="bd7a3-117">NULL</span></span>|<span data-ttu-id="bd7a3-118">FALSE</span><span class="sxs-lookup"><span data-stu-id="bd7a3-118">FALSE</span></span>|<span data-ttu-id="bd7a3-119">NULL</span><span class="sxs-lookup"><span data-stu-id="bd7a3-119">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="bd7a3-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="bd7a3-120">Example</span></span>  
 <span data-ttu-id="bd7a3-121">Aşağıdaki Entity SQL sorgusu, AND işlecinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-121">The following Entity SQL query demonstrates how to use the AND operator.</span></span> <span data-ttu-id="bd7a3-122">Sorgu AdventureWorks Satış Modeli dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-122">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="bd7a3-123">Bu sorguyı derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="bd7a3-123">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="bd7a3-124">[YapısalTürü Sonuçları Döndüren Bir Sorguyu Yürütme: Nasıl Yapılır'daki](../how-to-execute-a-query-that-returns-structuraltype-results.md)yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-124">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="bd7a3-125">Aşağıdaki sorguyu bağımsız değişken `ExecuteStructuralTypeQuery` olarak yönteme geçirin:</span><span class="sxs-lookup"><span data-stu-id="bd7a3-125">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a><span data-ttu-id="bd7a3-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-126">See also</span></span>

- [<span data-ttu-id="bd7a3-127">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="bd7a3-127">Entity SQL Reference</span></span>](entity-sql-reference.md)
