---
title: "&amp;&amp; ' (Entity SQL)"
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: 86ff43f8ed20c5696d15e21284394c3cb63200e3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198047"
---
# <a name="ampamp-and-entity-sql"></a><span data-ttu-id="07cc1-102">&amp;&amp; ' (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="07cc1-102">&amp;&amp; (AND) (Entity SQL)</span></span>

<span data-ttu-id="07cc1-103">`true`Her iki ifade de varsa döndürür `true` ; Aksi takdirde `false` veya `NULL` .</span><span class="sxs-lookup"><span data-stu-id="07cc1-103">Returns `true` if both expressions are `true`; otherwise, `false` or `NULL`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07cc1-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="07cc1-104">Syntax</span></span>  
  
```csharp  
boolean_expression AND boolean_expression
```

<span data-ttu-id="07cc1-105">veya</span><span class="sxs-lookup"><span data-stu-id="07cc1-105">or</span></span>  

```csharp
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="07cc1-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="07cc1-106">Arguments</span></span>  

 `boolean_expression`  
 <span data-ttu-id="07cc1-107">Boolean döndüren geçerli bir ifade.</span><span class="sxs-lookup"><span data-stu-id="07cc1-107">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07cc1-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="07cc1-108">Remarks</span></span>  

 <span data-ttu-id="07cc1-109">Çift ve + işaretleri (&&) ve işleciyle aynı işlevselliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="07cc1-109">Double ampersands (&&) have the same functionality as the AND operator.</span></span>  
  
 <span data-ttu-id="07cc1-110">Aşağıdaki tabloda olası giriş değerleri ve dönüş türleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="07cc1-110">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="07cc1-111">TRUE</span><span class="sxs-lookup"><span data-stu-id="07cc1-111">TRUE</span></span>|<span data-ttu-id="07cc1-112">FALSE</span><span class="sxs-lookup"><span data-stu-id="07cc1-112">FALSE</span></span>|<span data-ttu-id="07cc1-113">NULL</span><span class="sxs-lookup"><span data-stu-id="07cc1-113">NULL</span></span>|  
|`FALSE`|<span data-ttu-id="07cc1-114">FALSE</span><span class="sxs-lookup"><span data-stu-id="07cc1-114">FALSE</span></span>|<span data-ttu-id="07cc1-115">FALSE</span><span class="sxs-lookup"><span data-stu-id="07cc1-115">FALSE</span></span>|<span data-ttu-id="07cc1-116">FALSE</span><span class="sxs-lookup"><span data-stu-id="07cc1-116">FALSE</span></span>|  
|`NULL`|<span data-ttu-id="07cc1-117">NULL</span><span class="sxs-lookup"><span data-stu-id="07cc1-117">NULL</span></span>|<span data-ttu-id="07cc1-118">FALSE</span><span class="sxs-lookup"><span data-stu-id="07cc1-118">FALSE</span></span>|<span data-ttu-id="07cc1-119">NULL</span><span class="sxs-lookup"><span data-stu-id="07cc1-119">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="07cc1-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="07cc1-120">Example</span></span>  

 <span data-ttu-id="07cc1-121">Aşağıdaki Entity SQL sorgusu, ve işlecinin nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="07cc1-121">The following Entity SQL query demonstrates how to use the AND operator.</span></span> <span data-ttu-id="07cc1-122">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="07cc1-122">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="07cc1-123">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="07cc1-123">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="07cc1-124">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="07cc1-124">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="07cc1-125">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="07cc1-125">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a><span data-ttu-id="07cc1-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07cc1-126">See also</span></span>

- [<span data-ttu-id="07cc1-127">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="07cc1-127">Entity SQL Reference</span></span>](entity-sql-reference.md)
