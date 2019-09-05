---
title: ÜST (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4a4a0954-82e2-4eae-bcaf-7c4552f3532d
ms.openlocfilehash: 8b55519b7f95deb6463af4c0a6a2a53975e5b5a2
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248980"
---
# <a name="top-entity-sql"></a><span data-ttu-id="92467-102">ÜST (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="92467-102">TOP (Entity SQL)</span></span>

<span data-ttu-id="92467-103">SELECT yan tümcesi isteğe bağlı ALL/DISTINCT değiştiricisinden sonra isteğe bağlı bir TOP Sub yan tümcesine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="92467-103">The SELECT clause can have an optional TOP sub-clause following the optional ALL/DISTINCT modifier.</span></span> <span data-ttu-id="92467-104">TOP alt yan tümcesi, sorgu sonucundan yalnızca ilk satır kümesinin döndürüleceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="92467-104">The TOP sub-clause specifies that only the first set of rows will be returned from the query result.</span></span>

## <a name="syntax"></a><span data-ttu-id="92467-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="92467-105">Syntax</span></span>

```
[ TOP (n) ]
```

## <a name="arguments"></a><span data-ttu-id="92467-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="92467-106">Arguments</span></span>

<span data-ttu-id="92467-107">`n`Döndürülecek satır sayısını belirten sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="92467-107">`n` The numeric expression that specifies the number of rows to be returned.</span></span> <span data-ttu-id="92467-108">`n`tek bir sayısal sabit değer veya tek bir parametre olabilir.</span><span class="sxs-lookup"><span data-stu-id="92467-108">`n` could be a single numeric literal or a single parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="92467-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="92467-109">Remarks</span></span>

<span data-ttu-id="92467-110">ÜSTTEKI ifade tek bir sayısal sabit değer veya tek bir parametre olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="92467-110">The TOP expression must be either a single numeric literal or a single parameter.</span></span> <span data-ttu-id="92467-111">Sabit bir değişmez değer kullanılırsa, değişmez değer türü Edm. Int64 (Byte, int16, Int32 veya Int64) veya Edm. Int64 'e yükseltilebilir bir tür ile eşlenen herhangi bir sağlayıcı türü olmalıdır ve değeri sıfırdan büyük veya sıfıra eşit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="92467-111">If a constant literal is used, the literal type must be implicitly promotable to Edm.Int64 (byte, int16, int32 or int64 or any provider type that maps to a type that is promotable to Edm.Int64) and its value must be greater than or equal to zero.</span></span> <span data-ttu-id="92467-112">Aksi takdirde bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="92467-112">Otherwise an exception will be raised.</span></span> <span data-ttu-id="92467-113">Bir parametre bir ifade olarak kullanılıyorsa, parametre türü de Edm. Int64 öğesine örtülü olarak yükseltilebilir olmalıdır, ancak parametre değerleri geç sınırlanmış olduğundan derleme sırasında gerçek parametre değerinin doğrulaması olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="92467-113">If a parameter is used as an expression, the parameter type must also be implicitly promotable to Edm.Int64, but there will be no validation of the actual parameter value during compilation because the parameter values are late bounded.</span></span>

<span data-ttu-id="92467-114">Aşağıda bir sabit üst ifadeye örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="92467-114">The following is an example of constant TOP expression:</span></span>

```sql
select distinct top(10) c.a1, c.a2 from T as a
```

<span data-ttu-id="92467-115">Aşağıda parametreli üst ifadeye örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="92467-115">The following is an example of parameterized TOP expression:</span></span>

```sql
select distinct top(@topParam) c.a1, c.a2 from T as a
```

<span data-ttu-id="92467-116">Sorgu sıralanmadığı takdirde TOP belirleyici değildir.</span><span class="sxs-lookup"><span data-stu-id="92467-116">TOP is non-deterministic unless the query is sorted.</span></span> <span data-ttu-id="92467-117">Belirleyici bir sonuca ihtiyacınız varsa [order by](order-by-entity-sql.md) yan tümcesindeki [SKIP](skip-entity-sql.md) ve [LIMIT](limit-entity-sql.md) alt tümcesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="92467-117">If you require a deterministic result, use the [SKIP](skip-entity-sql.md) and [LIMIT](limit-entity-sql.md) sub-clauses in the [ORDER BY](order-by-entity-sql.md) clause.</span></span> <span data-ttu-id="92467-118">TOP ve SKIP/LIMIT birbirini dışlıyor.</span><span class="sxs-lookup"><span data-stu-id="92467-118">The TOP and SKIP/LIMIT are mutually exclusive.</span></span>

## <a name="example"></a><span data-ttu-id="92467-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="92467-119">Example</span></span>

<span data-ttu-id="92467-120">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, sorgu sonucundan döndürülecek en üstteki bir satırı belirtmek için üst öğesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="92467-120">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the TOP to specify the top one row to be returned from the query result.</span></span> <span data-ttu-id="92467-121">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="92467-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="92467-122">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="92467-122">To compile and run this query, follow these steps:</span></span>

1. <span data-ttu-id="92467-123">[Aşağıdaki adımları uygulayın: StructuralType sonuçları](../how-to-execute-a-query-that-returns-structuraltype-results.md)döndüren bir sorgu yürütün.</span><span class="sxs-lookup"><span data-stu-id="92467-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>

2. <span data-ttu-id="92467-124">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="92467-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>

    [!code-csharp[DP EntityServices Concepts 2#TOP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#top)]

## <a name="see-also"></a><span data-ttu-id="92467-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92467-125">See also</span></span>

- [<span data-ttu-id="92467-126">SELECT</span><span class="sxs-lookup"><span data-stu-id="92467-126">SELECT</span></span>](select-entity-sql.md)
- [<span data-ttu-id="92467-127">SKIP</span><span class="sxs-lookup"><span data-stu-id="92467-127">SKIP</span></span>](skip-entity-sql.md)
- [<span data-ttu-id="92467-128">LIMIT</span><span class="sxs-lookup"><span data-stu-id="92467-128">LIMIT</span></span>](limit-entity-sql.md)
- [<span data-ttu-id="92467-129">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="92467-129">ORDER BY</span></span>](order-by-entity-sql.md)
- [<span data-ttu-id="92467-130">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="92467-130">Entity SQL Reference</span></span>](entity-sql-reference.md)
