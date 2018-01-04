---
title: "|| (VEYA) (Varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 1f606d01c12ce3f5d9d4ff8720b06511a64347f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="-or-entity-sql"></a><span data-ttu-id="a2ea8-102">|| (VEYA) (Varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="a2ea8-102">|| (OR) (Entity SQL)</span></span>
<span data-ttu-id="a2ea8-103">İki birleştirir `Boolean` ifadeler.</span><span class="sxs-lookup"><span data-stu-id="a2ea8-103">Combines two `Boolean` expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2ea8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a2ea8-104">Syntax</span></span>  
  
```  
boolean_expression OR boolean_expression  
or   
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="a2ea8-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a2ea8-105">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="a2ea8-106">Döndüren herhangi bir geçerli ifadeler bir `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="a2ea8-106">Any valid expression that returns a `Boolean`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a2ea8-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a2ea8-107">Return Value</span></span>  
 <span data-ttu-id="a2ea8-108">`true`koşullardan biri olduğunda `true`; Aksi halde, `false`.</span><span class="sxs-lookup"><span data-stu-id="a2ea8-108">`true` when either of the conditions is `true`; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2ea8-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a2ea8-109">Remarks</span></span>  
 <span data-ttu-id="a2ea8-110">VEYA bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] mantıksal işleç.</span><span class="sxs-lookup"><span data-stu-id="a2ea8-110">OR is an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] logical operator.</span></span> <span data-ttu-id="a2ea8-111">İki koşul birleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a2ea8-111">It is used to combine two conditions.</span></span> <span data-ttu-id="a2ea8-112">Birden fazla mantıksal işleç bir deyimde kullanıldığında veya işleçler ve işleçler sonra değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="a2ea8-112">When more than one logical operator is used in a statement, OR operators are evaluated after AND operators.</span></span> <span data-ttu-id="a2ea8-113">Ancak, parantez kullanarak Değerlendirme sırasını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2ea8-113">However, you can change the order of evaluation by using parentheses.</span></span>  
  
 <span data-ttu-id="a2ea8-114">Çift dikey çubuk (&#124; &#124;) veya işlecini aynı işlevselliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a2ea8-114">Double vertical bars (&#124;&#124;) have the same functionality as the OR operator.</span></span>  
  
 <span data-ttu-id="a2ea8-115">Aşağıdaki tabloda olası giriş değerleri gösterir ve dönüş türleri.</span><span class="sxs-lookup"><span data-stu-id="a2ea8-115">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="a2ea8-116">TRUE</span><span class="sxs-lookup"><span data-stu-id="a2ea8-116">TRUE</span></span>|<span data-ttu-id="a2ea8-117">TRUE</span><span class="sxs-lookup"><span data-stu-id="a2ea8-117">TRUE</span></span>|<span data-ttu-id="a2ea8-118">TRUE</span><span class="sxs-lookup"><span data-stu-id="a2ea8-118">TRUE</span></span>|  
|`FALSE`|<span data-ttu-id="a2ea8-119">TRUE</span><span class="sxs-lookup"><span data-stu-id="a2ea8-119">TRUE</span></span>|<span data-ttu-id="a2ea8-120">FALSE</span><span class="sxs-lookup"><span data-stu-id="a2ea8-120">FALSE</span></span>|<span data-ttu-id="a2ea8-121">NULL</span><span class="sxs-lookup"><span data-stu-id="a2ea8-121">NULL</span></span>|  
|`NULL`|<span data-ttu-id="a2ea8-122">TRUE</span><span class="sxs-lookup"><span data-stu-id="a2ea8-122">TRUE</span></span>|<span data-ttu-id="a2ea8-123">NULL</span><span class="sxs-lookup"><span data-stu-id="a2ea8-123">NULL</span></span>|<span data-ttu-id="a2ea8-124">NULL</span><span class="sxs-lookup"><span data-stu-id="a2ea8-124">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a2ea8-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2ea8-125">Example</span></span>  
 <span data-ttu-id="a2ea8-126">İki birleştirmek için aşağıdaki varlık SQL sorgusunu veya işlecini kullanan `Boolean` ifadeler.</span><span class="sxs-lookup"><span data-stu-id="a2ea8-126">The following Entity SQL query uses the OR operator to combine two `Boolean` expressions.</span></span> <span data-ttu-id="a2ea8-127">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="a2ea8-127">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a2ea8-128">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="a2ea8-128">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="a2ea8-129">Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="a2ea8-129">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="a2ea8-130">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="a2ea8-130">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#OR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#or)]  
  
## <a name="see-also"></a><span data-ttu-id="a2ea8-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a2ea8-131">See Also</span></span>  
 [<span data-ttu-id="a2ea8-132">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="a2ea8-132">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
