---
title: '|| VEYA (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
ms.openlocfilehash: 89c0a92030f2f067d5e5d45b58d475414a224ce4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150810"
---
# <a name="-or-entity-sql"></a><span data-ttu-id="4caa9-102">|| VEYA (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="4caa9-102">|| (OR) (Entity SQL)</span></span>

<span data-ttu-id="4caa9-103">İki `Boolean` ifadeyi birleştirir.</span><span class="sxs-lookup"><span data-stu-id="4caa9-103">Combines two `Boolean` expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4caa9-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="4caa9-104">Syntax</span></span>  
  
```sql  
boolean_expression OR boolean_expression  
-- or
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="4caa9-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="4caa9-105">Arguments</span></span>  

 `boolean_expression`  
 <span data-ttu-id="4caa9-106">Döndüren geçerli bir ifade `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="4caa9-106">Any valid expression that returns a `Boolean`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4caa9-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4caa9-107">Return Value</span></span>  

 <span data-ttu-id="4caa9-108">`true` koşullardan biri olduğunda `true` ; Aksi durumda, `false` .</span><span class="sxs-lookup"><span data-stu-id="4caa9-108">`true` when either of the conditions is `true`; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4caa9-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4caa9-109">Remarks</span></span>  

 <span data-ttu-id="4caa9-110">VEYA mantıksal bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçtir.</span><span class="sxs-lookup"><span data-stu-id="4caa9-110">OR is an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] logical operator.</span></span> <span data-ttu-id="4caa9-111">İki koşulu birleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4caa9-111">It is used to combine two conditions.</span></span> <span data-ttu-id="4caa9-112">Bir ifadede birden çok mantıksal operatör kullanıldığında veya işleçler ve işleçlerden sonra değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="4caa9-112">When more than one logical operator is used in a statement, OR operators are evaluated after AND operators.</span></span> <span data-ttu-id="4caa9-113">Ancak, parantez kullanarak değerlendirmenin sırasını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4caa9-113">However, you can change the order of evaluation by using parentheses.</span></span>  
  
 <span data-ttu-id="4caa9-114">Çift dikey çubuklar (&#124;&#124;) veya işleciyle aynı işlevlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="4caa9-114">Double vertical bars (&#124;&#124;) have the same functionality as the OR operator.</span></span>  
  
 <span data-ttu-id="4caa9-115">Aşağıdaki tabloda olası giriş değerleri ve dönüş türleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4caa9-115">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="4caa9-116">TRUE</span><span class="sxs-lookup"><span data-stu-id="4caa9-116">TRUE</span></span>|<span data-ttu-id="4caa9-117">TRUE</span><span class="sxs-lookup"><span data-stu-id="4caa9-117">TRUE</span></span>|<span data-ttu-id="4caa9-118">TRUE</span><span class="sxs-lookup"><span data-stu-id="4caa9-118">TRUE</span></span>|  
|`FALSE`|<span data-ttu-id="4caa9-119">TRUE</span><span class="sxs-lookup"><span data-stu-id="4caa9-119">TRUE</span></span>|<span data-ttu-id="4caa9-120">FALSE</span><span class="sxs-lookup"><span data-stu-id="4caa9-120">FALSE</span></span>|<span data-ttu-id="4caa9-121">NULL</span><span class="sxs-lookup"><span data-stu-id="4caa9-121">NULL</span></span>|  
|`NULL`|<span data-ttu-id="4caa9-122">TRUE</span><span class="sxs-lookup"><span data-stu-id="4caa9-122">TRUE</span></span>|<span data-ttu-id="4caa9-123">NULL</span><span class="sxs-lookup"><span data-stu-id="4caa9-123">NULL</span></span>|<span data-ttu-id="4caa9-124">NULL</span><span class="sxs-lookup"><span data-stu-id="4caa9-124">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4caa9-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="4caa9-125">Example</span></span>  

 <span data-ttu-id="4caa9-126">Aşağıdaki Entity SQL sorgusu iki ifadeyi birleştirmek için OR işlecini kullanır `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="4caa9-126">The following Entity SQL query uses the OR operator to combine two `Boolean` expressions.</span></span> <span data-ttu-id="4caa9-127">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="4caa9-127">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="4caa9-128">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="4caa9-128">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="4caa9-129">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="4caa9-129">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="4caa9-130">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="4caa9-130">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts 2#OR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#or)]  
  
## <a name="see-also"></a><span data-ttu-id="4caa9-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4caa9-131">See also</span></span>

- [<span data-ttu-id="4caa9-132">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="4caa9-132">Entity SQL Reference</span></span>](entity-sql-reference.md)
