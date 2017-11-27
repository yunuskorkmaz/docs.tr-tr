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
ms.openlocfilehash: 9b1d3d1b07a349ab1a5efb4a7c41f9b9b34fc55f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="top-entity-sql"></a><span data-ttu-id="da0d4-102">ÜST (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="da0d4-102">TOP (Entity SQL)</span></span>
<span data-ttu-id="da0d4-103">SELECT yan tümcesi, isteğe bağlı tüm/DISTINCT değiştiricisi izleyen bir isteğe bağlı TOP alt yan tümcesinin olabilir.</span><span class="sxs-lookup"><span data-stu-id="da0d4-103">The SELECT clause can have an optional TOP sub-clause following the optional ALL/DISTINCT modifier.</span></span> <span data-ttu-id="da0d4-104">TOP alt yan tümcesi, yalnızca ilk satır kümesini sorgu sonuç döndürülür belirtir.</span><span class="sxs-lookup"><span data-stu-id="da0d4-104">The TOP sub-clause specifies that only the first set of rows will be returned from the query result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da0d4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="da0d4-105">Syntax</span></span>  
  
```  
[ TOP (n) ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="da0d4-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="da0d4-106">Arguments</span></span>  
 `n`  
 <span data-ttu-id="da0d4-107">Sayısal ifade döndürülecek satır sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="da0d4-107">The numeric expression that specifies the number of rows to be returned.</span></span> <span data-ttu-id="da0d4-108">`n`tek bir sayısal dize veya tek bir parametre olabilir.</span><span class="sxs-lookup"><span data-stu-id="da0d4-108">`n` could be a single numeric literal or a single parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da0d4-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="da0d4-109">Remarks</span></span>  
 <span data-ttu-id="da0d4-110">TOP ifadesi tek sayısal sabit değer ya da tek bir parametre olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="da0d4-110">The TOP expression must be either a single numeric literal or a single parameter.</span></span> <span data-ttu-id="da0d4-111">Bir sabit değişmez değeri kullanılırsa, değişmez değer türü örtük olarak yükseltilebilir EDM.Int64 (bayt, int16, int32 veya Int64 veya EDM.Int64 için yükseltilebilir türü eşlendiği herhangi bir sağlayıcı türü) için olmalıdır ve değeri sıfırdan büyük veya sıfıra eşit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="da0d4-111">If a constant literal is used, the literal type must be implicitly promotable to Edm.Int64 (byte, int16, int32 or int64 or any provider type that maps to a type that is promotable to Edm.Int64) and its value must be greater than or equal to zero.</span></span> <span data-ttu-id="da0d4-112">Aksi takdirde bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="da0d4-112">Otherwise an exception will be raised.</span></span> <span data-ttu-id="da0d4-113">Bir ifade olarak kullanılan bir parametre, parametre türü de EDM.Int64 için örtük olarak yükseltilebilir olmalıdır, ancak parametre değerlerini geç ilişkisindeki çünkü asıl parametre değerinin hiçbir doğrulama derleme sırasında olacaktır.</span><span class="sxs-lookup"><span data-stu-id="da0d4-113">If a parameter is used as an expression, the parameter type must also be implicitly promotable to Edm.Int64, but there will be no validation of the actual parameter value during compilation because the parameter values are late bounded.</span></span>  
  
 <span data-ttu-id="da0d4-114">Sabit TOP ifadesi örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="da0d4-114">The following is an example of constant TOP expression:</span></span>  
  
 `select distinct top(10) c.a1, c.a2 from T as a`  
  
 <span data-ttu-id="da0d4-115">Parametreli TOP ifadesi örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="da0d4-115">The following is an example of parametrized TOP expression:</span></span>  
  
 `select distinct top(@topParam) c.a1, c.a2 from T as a`  
  
 <span data-ttu-id="da0d4-116">Sorgu sıralanmış sürece üst belirleyici değildir.</span><span class="sxs-lookup"><span data-stu-id="da0d4-116">TOP is non-deterministic unless the query is sorted.</span></span> <span data-ttu-id="da0d4-117">Belirleyici bir sonuç gerekiyorsa kullanın [atla](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) ve [sınırı](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) alt yan tümceleri içinde [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="da0d4-117">If you require a deterministic result, use the [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) and [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) sub-clauses in the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) clause.</span></span> <span data-ttu-id="da0d4-118">TOP ve SKIP/LIMIT karşılıklı olarak birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="da0d4-118">The TOP and SKIP/LIMIT are mutually exclusive.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da0d4-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="da0d4-119">Example</span></span>  
 <span data-ttu-id="da0d4-120">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu üst sorgu sonuç döndürülecek üst bir satır belirlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="da0d4-120">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the TOP to specify the top one row to be returned from the query result.</span></span> <span data-ttu-id="da0d4-121">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="da0d4-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="da0d4-122">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="da0d4-122">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="da0d4-123">Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="da0d4-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="da0d4-124">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="da0d4-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#TOP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#top)]  
  
## <a name="see-also"></a><span data-ttu-id="da0d4-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="da0d4-125">See Also</span></span>  
 [<span data-ttu-id="da0d4-126">SEÇİN</span><span class="sxs-lookup"><span data-stu-id="da0d4-126">SELECT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)  
 [<span data-ttu-id="da0d4-127">ATLA</span><span class="sxs-lookup"><span data-stu-id="da0d4-127">SKIP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
 [<span data-ttu-id="da0d4-128">SINIRI</span><span class="sxs-lookup"><span data-stu-id="da0d4-128">LIMIT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
 [<span data-ttu-id="da0d4-129">SIRALAMA ÖLÇÜTÜ</span><span class="sxs-lookup"><span data-stu-id="da0d4-129">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
 [<span data-ttu-id="da0d4-130">Varlık SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="da0d4-130">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
