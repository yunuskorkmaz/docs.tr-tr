---
description: 'Hakkında daha fazla bilgi edinin: | | VEYA (Entity SQL)'
title: '|| VEYA (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
ms.openlocfilehash: 83af0211de1dd86b057237c36312e3ce33a3512a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696340"
---
# <a name="-or-entity-sql"></a><span data-ttu-id="b849a-103">|| VEYA (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="b849a-103">|| (OR) (Entity SQL)</span></span>

<span data-ttu-id="b849a-104">İki `Boolean` ifadeyi birleştirir.</span><span class="sxs-lookup"><span data-stu-id="b849a-104">Combines two `Boolean` expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b849a-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b849a-105">Syntax</span></span>  
  
```sql  
boolean_expression OR boolean_expression  
-- or
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="b849a-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="b849a-106">Arguments</span></span>  

 `boolean_expression`  
 <span data-ttu-id="b849a-107">Döndüren geçerli bir ifade `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="b849a-107">Any valid expression that returns a `Boolean`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b849a-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b849a-108">Return Value</span></span>  

 <span data-ttu-id="b849a-109">`true` koşullardan biri olduğunda `true` ; Aksi durumda, `false` .</span><span class="sxs-lookup"><span data-stu-id="b849a-109">`true` when either of the conditions is `true`; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b849a-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b849a-110">Remarks</span></span>  

 <span data-ttu-id="b849a-111">VEYA mantıksal bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçtir.</span><span class="sxs-lookup"><span data-stu-id="b849a-111">OR is an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] logical operator.</span></span> <span data-ttu-id="b849a-112">İki koşulu birleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b849a-112">It is used to combine two conditions.</span></span> <span data-ttu-id="b849a-113">Bir ifadede birden çok mantıksal operatör kullanıldığında veya işleçler ve işleçlerden sonra değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="b849a-113">When more than one logical operator is used in a statement, OR operators are evaluated after AND operators.</span></span> <span data-ttu-id="b849a-114">Ancak, parantez kullanarak değerlendirmenin sırasını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b849a-114">However, you can change the order of evaluation by using parentheses.</span></span>  
  
 <span data-ttu-id="b849a-115">Çift dikey çubuklar (&#124;&#124;) veya işleciyle aynı işlevlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b849a-115">Double vertical bars (&#124;&#124;) have the same functionality as the OR operator.</span></span>  
  
 <span data-ttu-id="b849a-116">Aşağıdaki tabloda olası giriş değerleri ve dönüş türleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b849a-116">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="b849a-117">TRUE</span><span class="sxs-lookup"><span data-stu-id="b849a-117">TRUE</span></span>|<span data-ttu-id="b849a-118">TRUE</span><span class="sxs-lookup"><span data-stu-id="b849a-118">TRUE</span></span>|<span data-ttu-id="b849a-119">TRUE</span><span class="sxs-lookup"><span data-stu-id="b849a-119">TRUE</span></span>|  
|`FALSE`|<span data-ttu-id="b849a-120">TRUE</span><span class="sxs-lookup"><span data-stu-id="b849a-120">TRUE</span></span>|<span data-ttu-id="b849a-121">FALSE</span><span class="sxs-lookup"><span data-stu-id="b849a-121">FALSE</span></span>|<span data-ttu-id="b849a-122">NULL</span><span class="sxs-lookup"><span data-stu-id="b849a-122">NULL</span></span>|  
|`NULL`|<span data-ttu-id="b849a-123">TRUE</span><span class="sxs-lookup"><span data-stu-id="b849a-123">TRUE</span></span>|<span data-ttu-id="b849a-124">NULL</span><span class="sxs-lookup"><span data-stu-id="b849a-124">NULL</span></span>|<span data-ttu-id="b849a-125">NULL</span><span class="sxs-lookup"><span data-stu-id="b849a-125">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b849a-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="b849a-126">Example</span></span>  

 <span data-ttu-id="b849a-127">Aşağıdaki Entity SQL sorgusu iki ifadeyi birleştirmek için OR işlecini kullanır `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="b849a-127">The following Entity SQL query uses the OR operator to combine two `Boolean` expressions.</span></span> <span data-ttu-id="b849a-128">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="b849a-128">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="b849a-129">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="b849a-129">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="b849a-130">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="b849a-130">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="b849a-131">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="b849a-131">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts 2#OR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#or)]  
  
## <a name="see-also"></a><span data-ttu-id="b849a-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b849a-132">See also</span></span>

- [<span data-ttu-id="b849a-133">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="b849a-133">Entity SQL Reference</span></span>](entity-sql-reference.md)
