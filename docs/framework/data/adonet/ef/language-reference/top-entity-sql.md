---
description: 'Hakkında daha fazla bilgi edinin: TOP (Entity SQL)'
title: ÜST (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4a4a0954-82e2-4eae-bcaf-7c4552f3532d
ms.openlocfilehash: 51e4ce53cff4b47f6f57b6b856ccb09b38e639cf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673446"
---
# <a name="top-entity-sql"></a><span data-ttu-id="551ec-103">ÜST (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="551ec-103">TOP (Entity SQL)</span></span>

<span data-ttu-id="551ec-104">SELECT yan tümcesi isteğe bağlı ALL/DISTINCT değiştiricisinden sonra isteğe bağlı bir TOP Sub yan tümcesine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="551ec-104">The SELECT clause can have an optional TOP sub-clause following the optional ALL/DISTINCT modifier.</span></span> <span data-ttu-id="551ec-105">TOP alt yan tümcesi, sorgu sonucundan yalnızca ilk satır kümesinin döndürüleceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="551ec-105">The TOP sub-clause specifies that only the first set of rows will be returned from the query result.</span></span>

## <a name="syntax"></a><span data-ttu-id="551ec-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="551ec-106">Syntax</span></span>

```sql
[ TOP (n) ]
```

## <a name="arguments"></a><span data-ttu-id="551ec-107">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="551ec-107">Arguments</span></span>

<span data-ttu-id="551ec-108">`n` Döndürülecek satır sayısını belirten sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="551ec-108">`n` The numeric expression that specifies the number of rows to be returned.</span></span> <span data-ttu-id="551ec-109">`n` tek bir sayısal sabit değer veya tek bir parametre olabilir.</span><span class="sxs-lookup"><span data-stu-id="551ec-109">`n` could be a single numeric literal or a single parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="551ec-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="551ec-110">Remarks</span></span>

<span data-ttu-id="551ec-111">ÜSTTEKI ifade tek bir sayısal sabit değer veya tek bir parametre olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="551ec-111">The TOP expression must be either a single numeric literal or a single parameter.</span></span> <span data-ttu-id="551ec-112">Sabit bir değişmez değer kullanılırsa, değişmez değer türü Edm. Int64 (Byte, int16, Int32 veya Int64) veya Edm. Int64 'e yükseltilebilir bir tür ile eşlenen herhangi bir sağlayıcı türü olmalıdır ve değeri sıfırdan büyük veya sıfıra eşit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="551ec-112">If a constant literal is used, the literal type must be implicitly promotable to Edm.Int64 (byte, int16, int32 or int64 or any provider type that maps to a type that is promotable to Edm.Int64) and its value must be greater than or equal to zero.</span></span> <span data-ttu-id="551ec-113">Aksi takdirde, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="551ec-113">Otherwise an exception will be raised.</span></span> <span data-ttu-id="551ec-114">Bir parametre bir ifade olarak kullanılıyorsa, parametre türü de Edm. Int64 öğesine örtülü olarak yükseltilebilir olmalıdır, ancak parametre değerleri geç sınırlanmış olduğundan derleme sırasında gerçek parametre değerinin doğrulaması olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="551ec-114">If a parameter is used as an expression, the parameter type must also be implicitly promotable to Edm.Int64, but there will be no validation of the actual parameter value during compilation because the parameter values are late bounded.</span></span>

<span data-ttu-id="551ec-115">Aşağıda bir sabit üst ifadeye örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="551ec-115">The following is an example of constant TOP expression:</span></span>

```sql
select distinct top(10) c.a1, c.a2 from T as a
```

<span data-ttu-id="551ec-116">Aşağıda parametreli üst ifadeye örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="551ec-116">The following is an example of parameterized TOP expression:</span></span>

```sql
select distinct top(@topParam) c.a1, c.a2 from T as a
```

<span data-ttu-id="551ec-117">Sorgu sıralanmadığı takdirde TOP belirleyici değildir.</span><span class="sxs-lookup"><span data-stu-id="551ec-117">TOP is non-deterministic unless the query is sorted.</span></span> <span data-ttu-id="551ec-118">Belirleyici bir sonuca ihtiyacınız varsa [order by](order-by-entity-sql.md) yan tümcesindeki [SKIP](skip-entity-sql.md) ve [LIMIT](limit-entity-sql.md) alt tümcesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="551ec-118">If you require a deterministic result, use the [SKIP](skip-entity-sql.md) and [LIMIT](limit-entity-sql.md) sub-clauses in the [ORDER BY](order-by-entity-sql.md) clause.</span></span> <span data-ttu-id="551ec-119">TOP ve SKIP/LIMIT birbirini dışlıyor.</span><span class="sxs-lookup"><span data-stu-id="551ec-119">The TOP and SKIP/LIMIT are mutually exclusive.</span></span>

## <a name="example"></a><span data-ttu-id="551ec-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="551ec-120">Example</span></span>

<span data-ttu-id="551ec-121">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, sorgu sonucundan döndürülecek en üstteki bir satırı belirtmek IÇIN üst öğesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="551ec-121">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the TOP to specify the top one row to be returned from the query result.</span></span> <span data-ttu-id="551ec-122">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="551ec-122">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="551ec-123">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="551ec-123">To compile and run this query, follow these steps:</span></span>

1. <span data-ttu-id="551ec-124">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="551ec-124">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>

2. <span data-ttu-id="551ec-125">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="551ec-125">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>

    [!code-sql[DP EntityServices Concepts#TOP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#top)]

## <a name="see-also"></a><span data-ttu-id="551ec-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="551ec-126">See also</span></span>

- [<span data-ttu-id="551ec-127">SELECT</span><span class="sxs-lookup"><span data-stu-id="551ec-127">SELECT</span></span>](select-entity-sql.md)
- [<span data-ttu-id="551ec-128">ŞIMDILIK</span><span class="sxs-lookup"><span data-stu-id="551ec-128">SKIP</span></span>](skip-entity-sql.md)
- [<span data-ttu-id="551ec-129">SıNıRLı</span><span class="sxs-lookup"><span data-stu-id="551ec-129">LIMIT</span></span>](limit-entity-sql.md)
- [<span data-ttu-id="551ec-130">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="551ec-130">ORDER BY</span></span>](order-by-entity-sql.md)
- [<span data-ttu-id="551ec-131">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="551ec-131">Entity SQL Reference</span></span>](entity-sql-reference.md)
