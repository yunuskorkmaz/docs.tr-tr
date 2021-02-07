---
description: 'Hakkında daha fazla bilgi edinin: &amp; &amp; (ve) (Entity SQL)'
title: "&amp;&amp; ' (Entity SQL)"
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: 14fc6bc3f58ac78cb9806a7f421db87bbad048ae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697185"
---
# <a name="ampamp-and-entity-sql"></a><span data-ttu-id="004d5-103">&amp;&amp; ' (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="004d5-103">&amp;&amp; (AND) (Entity SQL)</span></span>

<span data-ttu-id="004d5-104">`true`Her iki ifade de varsa döndürür `true` ; Aksi takdirde `false` veya `NULL` .</span><span class="sxs-lookup"><span data-stu-id="004d5-104">Returns `true` if both expressions are `true`; otherwise, `false` or `NULL`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="004d5-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="004d5-105">Syntax</span></span>  
  
```csharp  
boolean_expression AND boolean_expression
```

<span data-ttu-id="004d5-106">veya</span><span class="sxs-lookup"><span data-stu-id="004d5-106">or</span></span>  

```csharp
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="004d5-107">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="004d5-107">Arguments</span></span>  

 `boolean_expression`  
 <span data-ttu-id="004d5-108">Boolean döndüren geçerli bir ifade.</span><span class="sxs-lookup"><span data-stu-id="004d5-108">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="004d5-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="004d5-109">Remarks</span></span>  

 <span data-ttu-id="004d5-110">Çift ve + işaretleri (&&) ve işleciyle aynı işlevselliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="004d5-110">Double ampersands (&&) have the same functionality as the AND operator.</span></span>  
  
 <span data-ttu-id="004d5-111">Aşağıdaki tabloda olası giriş değerleri ve dönüş türleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="004d5-111">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="004d5-112">TRUE</span><span class="sxs-lookup"><span data-stu-id="004d5-112">TRUE</span></span>|<span data-ttu-id="004d5-113">FALSE</span><span class="sxs-lookup"><span data-stu-id="004d5-113">FALSE</span></span>|<span data-ttu-id="004d5-114">NULL</span><span class="sxs-lookup"><span data-stu-id="004d5-114">NULL</span></span>|  
|`FALSE`|<span data-ttu-id="004d5-115">FALSE</span><span class="sxs-lookup"><span data-stu-id="004d5-115">FALSE</span></span>|<span data-ttu-id="004d5-116">FALSE</span><span class="sxs-lookup"><span data-stu-id="004d5-116">FALSE</span></span>|<span data-ttu-id="004d5-117">FALSE</span><span class="sxs-lookup"><span data-stu-id="004d5-117">FALSE</span></span>|  
|`NULL`|<span data-ttu-id="004d5-118">NULL</span><span class="sxs-lookup"><span data-stu-id="004d5-118">NULL</span></span>|<span data-ttu-id="004d5-119">FALSE</span><span class="sxs-lookup"><span data-stu-id="004d5-119">FALSE</span></span>|<span data-ttu-id="004d5-120">NULL</span><span class="sxs-lookup"><span data-stu-id="004d5-120">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="004d5-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="004d5-121">Example</span></span>  

 <span data-ttu-id="004d5-122">Aşağıdaki Entity SQL sorgusu, ve işlecinin nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="004d5-122">The following Entity SQL query demonstrates how to use the AND operator.</span></span> <span data-ttu-id="004d5-123">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="004d5-123">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="004d5-124">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="004d5-124">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="004d5-125">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="004d5-125">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="004d5-126">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="004d5-126">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a><span data-ttu-id="004d5-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="004d5-127">See also</span></span>

- [<span data-ttu-id="004d5-128">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="004d5-128">Entity SQL Reference</span></span>](entity-sql-reference.md)
