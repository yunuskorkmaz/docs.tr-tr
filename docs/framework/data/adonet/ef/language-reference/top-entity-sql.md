---
title: ÜST (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 4a4a0954-82e2-4eae-bcaf-7c4552f3532d
ms.openlocfilehash: e7c6cf6b67dc3af29f7ca8fb22af419235a9b833
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879768"
---
# <a name="top-entity-sql"></a><span data-ttu-id="b4d33-102">ÜST (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="b4d33-102">TOP (Entity SQL)</span></span>

<span data-ttu-id="b4d33-103">SELECT yan tümcesi, isteğe bağlı tüm/DISTINCT değiştirici izleyen bir isteğe bağlı TOP alt yan tümcesinin olabilir.</span><span class="sxs-lookup"><span data-stu-id="b4d33-103">The SELECT clause can have an optional TOP sub-clause following the optional ALL/DISTINCT modifier.</span></span> <span data-ttu-id="b4d33-104">TOP alt yan tümcesi yalnızca ilk satır kümesini sorgu sonuç döndüren belirtir.</span><span class="sxs-lookup"><span data-stu-id="b4d33-104">The TOP sub-clause specifies that only the first set of rows will be returned from the query result.</span></span>

## <a name="syntax"></a><span data-ttu-id="b4d33-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b4d33-105">Syntax</span></span>

```
[ TOP (n) ]
```

## <a name="arguments"></a><span data-ttu-id="b4d33-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="b4d33-106">Arguments</span></span>

<span data-ttu-id="b4d33-107">`n` Sayısal ifade döndürülecek satır sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b4d33-107">`n` The numeric expression that specifies the number of rows to be returned.</span></span> <span data-ttu-id="b4d33-108">`n` tek bir sayısal değişmez değerin veya tek bir parametre olabilir.</span><span class="sxs-lookup"><span data-stu-id="b4d33-108">`n` could be a single numeric literal or a single parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="b4d33-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b4d33-109">Remarks</span></span>

<span data-ttu-id="b4d33-110">TOP ifadesi tek sayısal sabit değer ya da tek bir parametre olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b4d33-110">The TOP expression must be either a single numeric literal or a single parameter.</span></span> <span data-ttu-id="b4d33-111">Sabit bir hazır değer kullandıysanız, değişmez değer türü örtük olarak promotable EDM.Int64 (byte, Int16, Int32 veya Int64 veya promotable için EDM.Int64 türüne eşlenen herhangi bir sağlayıcı türü) için ve değeri büyük veya sıfıra eşit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b4d33-111">If a constant literal is used, the literal type must be implicitly promotable to Edm.Int64 (byte, int16, int32 or int64 or any provider type that maps to a type that is promotable to Edm.Int64) and its value must be greater than or equal to zero.</span></span> <span data-ttu-id="b4d33-112">Aksi takdirde bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b4d33-112">Otherwise an exception will be raised.</span></span> <span data-ttu-id="b4d33-113">Bir parametre bir ifade kullanılırsa, parametre türü de EDM.Int64 için örtük olarak promotable olmalı, ancak parametre değerlerini geç sınırlanmış çünkü derleme sırasında gerçek parametre değerinin hiçbir doğrulama olacaktır.</span><span class="sxs-lookup"><span data-stu-id="b4d33-113">If a parameter is used as an expression, the parameter type must also be implicitly promotable to Edm.Int64, but there will be no validation of the actual parameter value during compilation because the parameter values are late bounded.</span></span>

<span data-ttu-id="b4d33-114">Sabit üst ifadesi örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="b4d33-114">The following is an example of constant TOP expression:</span></span>

```sql
select distinct top(10) c.a1, c.a2 from T as a
```

<span data-ttu-id="b4d33-115">Parametreli TOP ifadesi örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="b4d33-115">The following is an example of parameterized TOP expression:</span></span>

```sql
select distinct top(@topParam) c.a1, c.a2 from T as a
```

<span data-ttu-id="b4d33-116">Sorgu sıralanmış sürece üst belirleyici değildir.</span><span class="sxs-lookup"><span data-stu-id="b4d33-116">TOP is non-deterministic unless the query is sorted.</span></span> <span data-ttu-id="b4d33-117">Kararlı bir sonuç gerekiyorsa kullanın [atla](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) ve [sınırı](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) alt yan tümceleri içinde [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="b4d33-117">If you require a deterministic result, use the [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) and [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) sub-clauses in the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) clause.</span></span> <span data-ttu-id="b4d33-118">TOP ve SKIP/LIMIT birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="b4d33-118">The TOP and SKIP/LIMIT are mutually exclusive.</span></span>

## <a name="example"></a><span data-ttu-id="b4d33-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="b4d33-119">Example</span></span>

<span data-ttu-id="b4d33-120">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, sorgu sonucu döndürülecek bir en üst satır belirlemek için üst kullanır.</span><span class="sxs-lookup"><span data-stu-id="b4d33-120">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the TOP to specify the top one row to be returned from the query result.</span></span> <span data-ttu-id="b4d33-121">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="b4d33-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="b4d33-122">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="b4d33-122">To compile and run this query, follow these steps:</span></span>

1. <span data-ttu-id="b4d33-123">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="b4d33-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>

2. <span data-ttu-id="b4d33-124">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="b4d33-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>

    [!code-csharp[DP EntityServices Concepts 2#TOP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#top)]

## <a name="see-also"></a><span data-ttu-id="b4d33-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4d33-125">See also</span></span>

- [<span data-ttu-id="b4d33-126">SELECT</span><span class="sxs-lookup"><span data-stu-id="b4d33-126">SELECT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)
- [<span data-ttu-id="b4d33-127">SKIP</span><span class="sxs-lookup"><span data-stu-id="b4d33-127">SKIP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)
- [<span data-ttu-id="b4d33-128">LIMIT</span><span class="sxs-lookup"><span data-stu-id="b4d33-128">LIMIT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)
- [<span data-ttu-id="b4d33-129">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="b4d33-129">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)
- [<span data-ttu-id="b4d33-130">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="b4d33-130">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
