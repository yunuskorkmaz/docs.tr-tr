---
title: '|| (VEYA) (Varlık SQL)'
ms.date: 03/30/2017
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
ms.openlocfilehash: 8c93e68095a0e0ff63532f53152f166d6c3d047c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150099"
---
# <a name="-or-entity-sql"></a><span data-ttu-id="cd434-102">|| (VEYA) (Varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="cd434-102">|| (OR) (Entity SQL)</span></span>
<span data-ttu-id="cd434-103">İki `Boolean` ifadeyi birleştirir.</span><span class="sxs-lookup"><span data-stu-id="cd434-103">Combines two `Boolean` expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd434-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cd434-104">Syntax</span></span>  
  
```sql  
boolean_expression OR boolean_expression  
-- or
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="cd434-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="cd434-105">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="cd434-106">Bir . döndüren geçerli ifadeler `Boolean`</span><span class="sxs-lookup"><span data-stu-id="cd434-106">Any valid expression that returns a `Boolean`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cd434-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cd434-107">Return Value</span></span>  
 <span data-ttu-id="cd434-108">`true`koşullardan biri olduğunda; `true` aksi `false`takdirde, .</span><span class="sxs-lookup"><span data-stu-id="cd434-108">`true` when either of the conditions is `true`; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd434-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cd434-109">Remarks</span></span>  
 <span data-ttu-id="cd434-110">OR mantıksal [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir işleçtir.</span><span class="sxs-lookup"><span data-stu-id="cd434-110">OR is an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] logical operator.</span></span> <span data-ttu-id="cd434-111">İki koşulu birleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cd434-111">It is used to combine two conditions.</span></span> <span data-ttu-id="cd434-112">Bir bildirimde birden fazla mantıksal işleç kullanıldığında, OR işleçleri AND işleçlerinden sonra değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="cd434-112">When more than one logical operator is used in a statement, OR operators are evaluated after AND operators.</span></span> <span data-ttu-id="cd434-113">Ancak, parantez kullanarak değerlendirme sırasını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cd434-113">However, you can change the order of evaluation by using parentheses.</span></span>  
  
 <span data-ttu-id="cd434-114">Çift dikey çubuklar (&#124;&#124;) OR işleciyle aynı işlevsellik tesahiptir.</span><span class="sxs-lookup"><span data-stu-id="cd434-114">Double vertical bars (&#124;&#124;) have the same functionality as the OR operator.</span></span>  
  
 <span data-ttu-id="cd434-115">Aşağıdaki tabloda olası giriş değerleri ve dönüş türleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cd434-115">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="cd434-116">TRUE</span><span class="sxs-lookup"><span data-stu-id="cd434-116">TRUE</span></span>|<span data-ttu-id="cd434-117">TRUE</span><span class="sxs-lookup"><span data-stu-id="cd434-117">TRUE</span></span>|<span data-ttu-id="cd434-118">TRUE</span><span class="sxs-lookup"><span data-stu-id="cd434-118">TRUE</span></span>|  
|`FALSE`|<span data-ttu-id="cd434-119">TRUE</span><span class="sxs-lookup"><span data-stu-id="cd434-119">TRUE</span></span>|<span data-ttu-id="cd434-120">FALSE</span><span class="sxs-lookup"><span data-stu-id="cd434-120">FALSE</span></span>|<span data-ttu-id="cd434-121">NULL</span><span class="sxs-lookup"><span data-stu-id="cd434-121">NULL</span></span>|  
|`NULL`|<span data-ttu-id="cd434-122">TRUE</span><span class="sxs-lookup"><span data-stu-id="cd434-122">TRUE</span></span>|<span data-ttu-id="cd434-123">NULL</span><span class="sxs-lookup"><span data-stu-id="cd434-123">NULL</span></span>|<span data-ttu-id="cd434-124">NULL</span><span class="sxs-lookup"><span data-stu-id="cd434-124">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="cd434-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="cd434-125">Example</span></span>  
 <span data-ttu-id="cd434-126">Aşağıdaki Entity SQL sorgusu, iki `Boolean` ifadeyi birleştirmek için OR işlecikullanır.</span><span class="sxs-lookup"><span data-stu-id="cd434-126">The following Entity SQL query uses the OR operator to combine two `Boolean` expressions.</span></span> <span data-ttu-id="cd434-127">Sorgu AdventureWorks Satış Modeli dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cd434-127">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="cd434-128">Bu sorguyı derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="cd434-128">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="cd434-129">[YapısalTürü Sonuçları Döndüren Bir Sorguyu Yürütme: Nasıl Yapılır'daki](../how-to-execute-a-query-that-returns-structuraltype-results.md)yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="cd434-129">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="cd434-130">Aşağıdaki sorguyu bağımsız değişken `ExecuteStructuralTypeQuery` olarak yönteme geçirin:</span><span class="sxs-lookup"><span data-stu-id="cd434-130">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts 2#OR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#or)]  
  
## <a name="see-also"></a><span data-ttu-id="cd434-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd434-131">See also</span></span>

- [<span data-ttu-id="cd434-132">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="cd434-132">Entity SQL Reference</span></span>](entity-sql-reference.md)
