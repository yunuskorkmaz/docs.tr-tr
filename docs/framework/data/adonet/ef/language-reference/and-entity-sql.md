---
title: '&amp;&amp; (ve) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: be6e7120e6c19714f151aa38a8b9a1355de29d1a
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039960"
---
# <a name="ampamp-and-entity-sql"></a><span data-ttu-id="0f4e7-102">&amp;&amp; (ve) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="0f4e7-102">&amp;&amp; (AND) (Entity SQL)</span></span>
<span data-ttu-id="0f4e7-103">Her iki ifade de `true``true` döndürür; Aksi takdirde, `false` veya `NULL`.</span><span class="sxs-lookup"><span data-stu-id="0f4e7-103">Returns `true` if both expressions are `true`; otherwise, `false` or `NULL`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f4e7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f4e7-104">Syntax</span></span>  
  
```csharp  
boolean_expression AND boolean_expression
```
 
<span data-ttu-id="0f4e7-105">veya</span><span class="sxs-lookup"><span data-stu-id="0f4e7-105">or</span></span>  

```csharp
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="0f4e7-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="0f4e7-106">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="0f4e7-107">Boolean döndüren geçerli bir ifade.</span><span class="sxs-lookup"><span data-stu-id="0f4e7-107">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f4e7-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0f4e7-108">Remarks</span></span>  
 <span data-ttu-id="0f4e7-109">Çift ve işareti (& &), ve işleciyle aynı işlevselliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0f4e7-109">Double ampersands (&&) have the same functionality as the AND operator.</span></span>  
  
 <span data-ttu-id="0f4e7-110">Aşağıdaki tabloda olası giriş değerleri ve dönüş türleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0f4e7-110">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="0f4e7-111">TRUE</span><span class="sxs-lookup"><span data-stu-id="0f4e7-111">TRUE</span></span>|<span data-ttu-id="0f4e7-112">YANLÝÞ</span><span class="sxs-lookup"><span data-stu-id="0f4e7-112">FALSE</span></span>|<span data-ttu-id="0f4e7-113">NULL</span><span class="sxs-lookup"><span data-stu-id="0f4e7-113">NULL</span></span>|  
|`FALSE`|<span data-ttu-id="0f4e7-114">YANLÝÞ</span><span class="sxs-lookup"><span data-stu-id="0f4e7-114">FALSE</span></span>|<span data-ttu-id="0f4e7-115">YANLÝÞ</span><span class="sxs-lookup"><span data-stu-id="0f4e7-115">FALSE</span></span>|<span data-ttu-id="0f4e7-116">YANLÝÞ</span><span class="sxs-lookup"><span data-stu-id="0f4e7-116">FALSE</span></span>|  
|`NULL`|<span data-ttu-id="0f4e7-117">NULL</span><span class="sxs-lookup"><span data-stu-id="0f4e7-117">NULL</span></span>|<span data-ttu-id="0f4e7-118">YANLÝÞ</span><span class="sxs-lookup"><span data-stu-id="0f4e7-118">FALSE</span></span>|<span data-ttu-id="0f4e7-119">NULL</span><span class="sxs-lookup"><span data-stu-id="0f4e7-119">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0f4e7-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f4e7-120">Example</span></span>  
 <span data-ttu-id="0f4e7-121">Aşağıdaki Entity SQL sorgusu, ve işlecinin nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="0f4e7-121">The following Entity SQL query demonstrates how to use the AND operator.</span></span> <span data-ttu-id="0f4e7-122">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="0f4e7-122">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="0f4e7-123">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="0f4e7-123">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="0f4e7-124">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="0f4e7-124">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="0f4e7-125">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="0f4e7-125">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a><span data-ttu-id="0f4e7-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f4e7-126">See also</span></span>

- [<span data-ttu-id="0f4e7-127">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="0f4e7-127">Entity SQL Reference</span></span>](entity-sql-reference.md)
