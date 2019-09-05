---
title: '|| VEYA (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
ms.openlocfilehash: c88e041638fbe6f32717ce9c4f9c2ff6fb56d803
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249768"
---
# <a name="-or-entity-sql"></a><span data-ttu-id="86a5b-102">|| VEYA (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="86a5b-102">|| (OR) (Entity SQL)</span></span>
<span data-ttu-id="86a5b-103">İki `Boolean` ifadeyi birleştirir.</span><span class="sxs-lookup"><span data-stu-id="86a5b-103">Combines two `Boolean` expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86a5b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86a5b-104">Syntax</span></span>  
  
```  
boolean_expression OR boolean_expression  
or   
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="86a5b-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="86a5b-105">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="86a5b-106">Döndüren geçerli bir `Boolean`ifade.</span><span class="sxs-lookup"><span data-stu-id="86a5b-106">Any valid expression that returns a `Boolean`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="86a5b-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="86a5b-107">Return Value</span></span>  
 <span data-ttu-id="86a5b-108">`true`koşullardan `true`biri olduğunda; Aksi durumda, `false`.</span><span class="sxs-lookup"><span data-stu-id="86a5b-108">`true` when either of the conditions is `true`; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86a5b-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="86a5b-109">Remarks</span></span>  
 <span data-ttu-id="86a5b-110">Veya mantıksal bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçtir.</span><span class="sxs-lookup"><span data-stu-id="86a5b-110">OR is an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] logical operator.</span></span> <span data-ttu-id="86a5b-111">İki koşulu birleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="86a5b-111">It is used to combine two conditions.</span></span> <span data-ttu-id="86a5b-112">Bir ifadede birden çok mantıksal operatör kullanıldığında veya işleçler ve işleçlerden sonra değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="86a5b-112">When more than one logical operator is used in a statement, OR operators are evaluated after AND operators.</span></span> <span data-ttu-id="86a5b-113">Ancak, parantez kullanarak değerlendirmenin sırasını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86a5b-113">However, you can change the order of evaluation by using parentheses.</span></span>  
  
 <span data-ttu-id="86a5b-114">Çift dikey çubuklar (&#124;&#124;), or işleciyle aynı işlevselliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="86a5b-114">Double vertical bars (&#124;&#124;) have the same functionality as the OR operator.</span></span>  
  
 <span data-ttu-id="86a5b-115">Aşağıdaki tabloda olası giriş değerleri ve dönüş türleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="86a5b-115">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="86a5b-116">TRUE</span><span class="sxs-lookup"><span data-stu-id="86a5b-116">TRUE</span></span>|<span data-ttu-id="86a5b-117">TRUE</span><span class="sxs-lookup"><span data-stu-id="86a5b-117">TRUE</span></span>|<span data-ttu-id="86a5b-118">TRUE</span><span class="sxs-lookup"><span data-stu-id="86a5b-118">TRUE</span></span>|  
|`FALSE`|<span data-ttu-id="86a5b-119">TRUE</span><span class="sxs-lookup"><span data-stu-id="86a5b-119">TRUE</span></span>|<span data-ttu-id="86a5b-120">YANLÝÞ</span><span class="sxs-lookup"><span data-stu-id="86a5b-120">FALSE</span></span>|<span data-ttu-id="86a5b-121">NULL</span><span class="sxs-lookup"><span data-stu-id="86a5b-121">NULL</span></span>|  
|`NULL`|<span data-ttu-id="86a5b-122">TRUE</span><span class="sxs-lookup"><span data-stu-id="86a5b-122">TRUE</span></span>|<span data-ttu-id="86a5b-123">NULL</span><span class="sxs-lookup"><span data-stu-id="86a5b-123">NULL</span></span>|<span data-ttu-id="86a5b-124">NULL</span><span class="sxs-lookup"><span data-stu-id="86a5b-124">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="86a5b-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="86a5b-125">Example</span></span>  
 <span data-ttu-id="86a5b-126">Aşağıdaki Entity SQL sorgusu iki `Boolean` ifadeyi birleştirmek için or işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="86a5b-126">The following Entity SQL query uses the OR operator to combine two `Boolean` expressions.</span></span> <span data-ttu-id="86a5b-127">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="86a5b-127">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="86a5b-128">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="86a5b-128">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="86a5b-129">[Aşağıdaki adımları uygulayın: StructuralType sonuçları](../how-to-execute-a-query-that-returns-structuraltype-results.md)döndüren bir sorgu yürütün.</span><span class="sxs-lookup"><span data-stu-id="86a5b-129">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="86a5b-130">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="86a5b-130">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#OR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#or)]  
  
## <a name="see-also"></a><span data-ttu-id="86a5b-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86a5b-131">See also</span></span>

- [<span data-ttu-id="86a5b-132">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="86a5b-132">Entity SQL Reference</span></span>](entity-sql-reference.md)
