---
title: "ÜST (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a4a0954-82e2-4eae-bcaf-7c4552f3532d
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 56eec4ccd8083afb8c91ea5d31e444b322736191
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="top-entity-sql"></a><span data-ttu-id="ed56d-102">ÜST (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="ed56d-102">TOP (Entity SQL)</span></span>
<span data-ttu-id="ed56d-103">SELECT yan tümcesi, isteğe bağlı tüm/DISTINCT değiştiricisi izleyen bir isteğe bağlı TOP alt yan tümcesinin olabilir.</span><span class="sxs-lookup"><span data-stu-id="ed56d-103">The SELECT clause can have an optional TOP sub-clause following the optional ALL/DISTINCT modifier.</span></span> <span data-ttu-id="ed56d-104">TOP alt yan tümcesi, yalnızca ilk satır kümesini sorgu sonuç döndürülür belirtir.</span><span class="sxs-lookup"><span data-stu-id="ed56d-104">The TOP sub-clause specifies that only the first set of rows will be returned from the query result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed56d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ed56d-105">Syntax</span></span>  
  
```  
[ TOP (n) ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="ed56d-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="ed56d-106">Arguments</span></span>  
 `n`  
 <span data-ttu-id="ed56d-107">Sayısal ifade döndürülecek satır sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ed56d-107">The numeric expression that specifies the number of rows to be returned.</span></span> <span data-ttu-id="ed56d-108">`n`tek bir sayısal dize veya tek bir parametre olabilir.</span><span class="sxs-lookup"><span data-stu-id="ed56d-108">`n` could be a single numeric literal or a single parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed56d-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ed56d-109">Remarks</span></span>  
 <span data-ttu-id="ed56d-110">TOP ifadesi tek sayısal sabit değer ya da tek bir parametre olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ed56d-110">The TOP expression must be either a single numeric literal or a single parameter.</span></span> <span data-ttu-id="ed56d-111">Bir sabit değişmez değeri kullanılırsa, değişmez değer türü örtük olarak yükseltilebilir EDM.Int64 (bayt, int16, int32 veya Int64 veya EDM.Int64 için yükseltilebilir türü eşlendiği herhangi bir sağlayıcı türü) için olmalıdır ve değeri sıfırdan büyük veya sıfıra eşit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ed56d-111">If a constant literal is used, the literal type must be implicitly promotable to Edm.Int64 (byte, int16, int32 or int64 or any provider type that maps to a type that is promotable to Edm.Int64) and its value must be greater than or equal to zero.</span></span> <span data-ttu-id="ed56d-112">Aksi takdirde bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ed56d-112">Otherwise an exception will be raised.</span></span> <span data-ttu-id="ed56d-113">Bir ifade olarak kullanılan bir parametre, parametre türü de EDM.Int64 için örtük olarak yükseltilebilir olmalıdır, ancak parametre değerlerini geç ilişkisindeki çünkü asıl parametre değerinin hiçbir doğrulama derleme sırasında olacaktır.</span><span class="sxs-lookup"><span data-stu-id="ed56d-113">If a parameter is used as an expression, the parameter type must also be implicitly promotable to Edm.Int64, but there will be no validation of the actual parameter value during compilation because the parameter values are late bounded.</span></span>  
  
 <span data-ttu-id="ed56d-114">Sabit TOP ifadesi örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="ed56d-114">The following is an example of constant TOP expression:</span></span>  
  
 `select distinct top(10) c.a1, c.a2 from T as a`  
  
 <span data-ttu-id="ed56d-115">Parametreli TOP ifadesi örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="ed56d-115">The following is an example of parametrized TOP expression:</span></span>  
  
 `select distinct top(@topParam) c.a1, c.a2 from T as a`  
  
 <span data-ttu-id="ed56d-116">Sorgu sıralanmış sürece üst belirleyici değildir.</span><span class="sxs-lookup"><span data-stu-id="ed56d-116">TOP is non-deterministic unless the query is sorted.</span></span> <span data-ttu-id="ed56d-117">Belirleyici bir sonuç gerekiyorsa kullanın [atla](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) ve [sınırı](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) alt yan tümceleri içinde [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="ed56d-117">If you require a deterministic result, use the [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) and [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) sub-clauses in the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) clause.</span></span> <span data-ttu-id="ed56d-118">TOP ve SKIP/LIMIT karşılıklı olarak birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="ed56d-118">The TOP and SKIP/LIMIT are mutually exclusive.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed56d-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="ed56d-119">Example</span></span>  
 <span data-ttu-id="ed56d-120">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu üst sorgu sonuç döndürülecek üst bir satır belirlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="ed56d-120">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the TOP to specify the top one row to be returned from the query result.</span></span> <span data-ttu-id="ed56d-121">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="ed56d-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ed56d-122">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="ed56d-122">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="ed56d-123">Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="ed56d-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="ed56d-124">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="ed56d-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#TOP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#top)]  
  
## <a name="see-also"></a><span data-ttu-id="ed56d-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ed56d-125">See Also</span></span>  
 [<span data-ttu-id="ed56d-126">SELECT</span><span class="sxs-lookup"><span data-stu-id="ed56d-126">SELECT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)  
 [<span data-ttu-id="ed56d-127">SKIP</span><span class="sxs-lookup"><span data-stu-id="ed56d-127">SKIP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
 [<span data-ttu-id="ed56d-128">LIMIT</span><span class="sxs-lookup"><span data-stu-id="ed56d-128">LIMIT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
 [<span data-ttu-id="ed56d-129">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="ed56d-129">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
 [<span data-ttu-id="ed56d-130">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="ed56d-130">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
