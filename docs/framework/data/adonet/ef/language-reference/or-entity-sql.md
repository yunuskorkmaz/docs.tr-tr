---
title: '|| (VEYA) (Varlık SQL)'
ms.date: 03/30/2017
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
ms.openlocfilehash: 3ceaf33d8baba9776008cddcbe2e2d70f13fe089
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141290"
---
# <a name="-or-entity-sql"></a><span data-ttu-id="8dd21-102">|| (VEYA) (Varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="8dd21-102">|| (OR) (Entity SQL)</span></span>
<span data-ttu-id="8dd21-103">İki birleştirir `Boolean` ifadeler.</span><span class="sxs-lookup"><span data-stu-id="8dd21-103">Combines two `Boolean` expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dd21-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8dd21-104">Syntax</span></span>  
  
```  
boolean_expression OR boolean_expression  
or   
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="8dd21-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8dd21-105">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="8dd21-106">Döndüren herhangi bir geçerli ifade bir `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="8dd21-106">Any valid expression that returns a `Boolean`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8dd21-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8dd21-107">Return Value</span></span>  
 `true` <span data-ttu-id="8dd21-108">koşullardan biri olduğunda `true`; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="8dd21-108">when either of the conditions is `true`; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8dd21-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8dd21-109">Remarks</span></span>  
 <span data-ttu-id="8dd21-110">VEYA bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] mantıksal işleç.</span><span class="sxs-lookup"><span data-stu-id="8dd21-110">OR is an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] logical operator.</span></span> <span data-ttu-id="8dd21-111">İki koşul birleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8dd21-111">It is used to combine two conditions.</span></span> <span data-ttu-id="8dd21-112">Bir deyimde birden fazla mantıksal işleç kullanıldığında, OR işleçlerini sonra ve işleçler değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="8dd21-112">When more than one logical operator is used in a statement, OR operators are evaluated after AND operators.</span></span> <span data-ttu-id="8dd21-113">Ancak, parantezler kullanarak Değerlendirme sırasını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8dd21-113">However, you can change the order of evaluation by using parentheses.</span></span>  
  
 <span data-ttu-id="8dd21-114">Çift dikey çubuk (&#124;&#124;) OR işleci aynı işlevselliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8dd21-114">Double vertical bars (&#124;&#124;) have the same functionality as the OR operator.</span></span>  
  
 <span data-ttu-id="8dd21-115">Aşağıdaki tabloda olası giriş değerleri gösterir ve dönüş türleri.</span><span class="sxs-lookup"><span data-stu-id="8dd21-115">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="8dd21-116">TRUE</span><span class="sxs-lookup"><span data-stu-id="8dd21-116">TRUE</span></span>|<span data-ttu-id="8dd21-117">TRUE</span><span class="sxs-lookup"><span data-stu-id="8dd21-117">TRUE</span></span>|<span data-ttu-id="8dd21-118">TRUE</span><span class="sxs-lookup"><span data-stu-id="8dd21-118">TRUE</span></span>|  
|`FALSE`|<span data-ttu-id="8dd21-119">TRUE</span><span class="sxs-lookup"><span data-stu-id="8dd21-119">TRUE</span></span>|<span data-ttu-id="8dd21-120">FALSE</span><span class="sxs-lookup"><span data-stu-id="8dd21-120">FALSE</span></span>|<span data-ttu-id="8dd21-121">NULL</span><span class="sxs-lookup"><span data-stu-id="8dd21-121">NULL</span></span>|  
|`NULL`|<span data-ttu-id="8dd21-122">TRUE</span><span class="sxs-lookup"><span data-stu-id="8dd21-122">TRUE</span></span>|<span data-ttu-id="8dd21-123">NULL</span><span class="sxs-lookup"><span data-stu-id="8dd21-123">NULL</span></span>|<span data-ttu-id="8dd21-124">NULL</span><span class="sxs-lookup"><span data-stu-id="8dd21-124">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8dd21-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="8dd21-125">Example</span></span>  
 <span data-ttu-id="8dd21-126">Aşağıdaki varlık SQL sorgusu OR işleci iki birleştirmek için kullanır. `Boolean` ifadeler.</span><span class="sxs-lookup"><span data-stu-id="8dd21-126">The following Entity SQL query uses the OR operator to combine two `Boolean` expressions.</span></span> <span data-ttu-id="8dd21-127">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="8dd21-127">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="8dd21-128">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="8dd21-128">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="8dd21-129">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="8dd21-129">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="8dd21-130">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="8dd21-130">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#OR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#or)]  
  
## <a name="see-also"></a><span data-ttu-id="8dd21-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8dd21-131">See also</span></span>

- [<span data-ttu-id="8dd21-132">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="8dd21-132">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
