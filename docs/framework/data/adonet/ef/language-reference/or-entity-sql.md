---
title: '|| VEYA (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
ms.openlocfilehash: 6437b17fe1c1277701f06988ef6c02f4caf70e62
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319464"
---
# <a name="-or-entity-sql"></a><span data-ttu-id="2b80c-102">|| VEYA (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="2b80c-102">|| (OR) (Entity SQL)</span></span>
<span data-ttu-id="2b80c-103">İki `Boolean` ifadesini birleştirir.</span><span class="sxs-lookup"><span data-stu-id="2b80c-103">Combines two `Boolean` expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b80c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2b80c-104">Syntax</span></span>  
  
```sql  
boolean_expression OR boolean_expression  
-- or   
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="2b80c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="2b80c-105">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="2b80c-106">@No__t-0 döndüren geçerli bir ifade.</span><span class="sxs-lookup"><span data-stu-id="2b80c-106">Any valid expression that returns a `Boolean`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b80c-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2b80c-107">Return Value</span></span>  
 <span data-ttu-id="2b80c-108">`true`, koşullardan biri `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="2b80c-108">`true` when either of the conditions is `true`; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b80c-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2b80c-109">Remarks</span></span>  
 <span data-ttu-id="2b80c-110">YA da [!INCLUDE[esql](../../../../../../includes/esql-md.md)] mantıksal bir işleçtir.</span><span class="sxs-lookup"><span data-stu-id="2b80c-110">OR is an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] logical operator.</span></span> <span data-ttu-id="2b80c-111">İki koşulu birleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2b80c-111">It is used to combine two conditions.</span></span> <span data-ttu-id="2b80c-112">Bir ifadede birden çok mantıksal operatör kullanıldığında veya işleçler ve işleçlerden sonra değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="2b80c-112">When more than one logical operator is used in a statement, OR operators are evaluated after AND operators.</span></span> <span data-ttu-id="2b80c-113">Ancak, parantez kullanarak değerlendirmenin sırasını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b80c-113">However, you can change the order of evaluation by using parentheses.</span></span>  
  
 <span data-ttu-id="2b80c-114">Çift dikey çubuklar (&#124;&#124;), or işleciyle aynı işlevselliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2b80c-114">Double vertical bars (&#124;&#124;) have the same functionality as the OR operator.</span></span>  
  
 <span data-ttu-id="2b80c-115">Aşağıdaki tabloda olası giriş değerleri ve dönüş türleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2b80c-115">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="2b80c-116">TRUE</span><span class="sxs-lookup"><span data-stu-id="2b80c-116">TRUE</span></span>|<span data-ttu-id="2b80c-117">TRUE</span><span class="sxs-lookup"><span data-stu-id="2b80c-117">TRUE</span></span>|<span data-ttu-id="2b80c-118">TRUE</span><span class="sxs-lookup"><span data-stu-id="2b80c-118">TRUE</span></span>|  
|`FALSE`|<span data-ttu-id="2b80c-119">TRUE</span><span class="sxs-lookup"><span data-stu-id="2b80c-119">TRUE</span></span>|<span data-ttu-id="2b80c-120">YANLÝÞ</span><span class="sxs-lookup"><span data-stu-id="2b80c-120">FALSE</span></span>|<span data-ttu-id="2b80c-121">NULL</span><span class="sxs-lookup"><span data-stu-id="2b80c-121">NULL</span></span>|  
|`NULL`|<span data-ttu-id="2b80c-122">TRUE</span><span class="sxs-lookup"><span data-stu-id="2b80c-122">TRUE</span></span>|<span data-ttu-id="2b80c-123">NULL</span><span class="sxs-lookup"><span data-stu-id="2b80c-123">NULL</span></span>|<span data-ttu-id="2b80c-124">NULL</span><span class="sxs-lookup"><span data-stu-id="2b80c-124">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2b80c-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="2b80c-125">Example</span></span>  
 <span data-ttu-id="2b80c-126">Aşağıdaki Entity SQL sorgusu iki `Boolean` ifadesini birleştirmek için OR işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2b80c-126">The following Entity SQL query uses the OR operator to combine two `Boolean` expressions.</span></span> <span data-ttu-id="2b80c-127">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="2b80c-127">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="2b80c-128">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="2b80c-128">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="2b80c-129">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="2b80c-129">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="2b80c-130">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="2b80c-130">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts 2#OR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#or)]  
  
## <a name="see-also"></a><span data-ttu-id="2b80c-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b80c-131">See also</span></span>

- [<span data-ttu-id="2b80c-132">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="2b80c-132">Entity SQL Reference</span></span>](entity-sql-reference.md)
