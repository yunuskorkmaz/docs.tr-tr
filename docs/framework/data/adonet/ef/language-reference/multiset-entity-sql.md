---
title: Çoklu küme (Entity SQL)
ms.date: 03/30/2017
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
ms.openlocfilehash: abdcce0e98c924052e07b9001d7dd92051c13747
ms.sourcegitcommit: 38999dc0ec4f7c4404de5ce0951b64c55997d9ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/02/2021
ms.locfileid: "99427040"
---
# <a name="multiset-entity-sql"></a><span data-ttu-id="3efbe-102">Çoklu küme (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="3efbe-102">MULTISET (Entity SQL)</span></span>

<span data-ttu-id="3efbe-103">Bir değer listesinden bir çoklu küme örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3efbe-103">Creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="3efbe-104">Çoklu küme oluşturucudaki tüm değerler uyumlu türde olmalıdır `T` .</span><span class="sxs-lookup"><span data-stu-id="3efbe-104">All the values in the MULTISET constructor must be of a compatible type `T`.</span></span> <span data-ttu-id="3efbe-105">Boş çok kümeli oluşturuculara izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="3efbe-105">Empty multiset constructors are not allowed.</span></span>

## <a name="syntax"></a><span data-ttu-id="3efbe-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3efbe-106">Syntax</span></span>

```sql
MULTISET ( expression [{, expression }] )
-- or
{ expression [{, expression }] }
```

## <a name="arguments"></a><span data-ttu-id="3efbe-107">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="3efbe-107">Arguments</span></span>

`expression`  
 <span data-ttu-id="3efbe-108">Herhangi bir geçerli değer listesi.</span><span class="sxs-lookup"><span data-stu-id="3efbe-108">Any valid list of values.</span></span>

## <a name="return-value"></a><span data-ttu-id="3efbe-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3efbe-109">Return Value</span></span>

<span data-ttu-id="3efbe-110">Çoklu küme türünde bir koleksiyon \<T> .</span><span class="sxs-lookup"><span data-stu-id="3efbe-110">A collection of type MULTISET\<T>.</span></span>

## <a name="remarks"></a><span data-ttu-id="3efbe-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3efbe-111">Remarks</span></span>

<!-- markdownlint-disable DOCSMD001 -->

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="3efbe-112">Üç tür Oluşturucu sağlar: satır oluşturucular, nesne oluşturucular ve çoklu küme (veya koleksiyon) oluşturucuları.</span><span class="sxs-lookup"><span data-stu-id="3efbe-112">provides three kinds of constructors: row constructors, object constructors, and multiset (or collection) constructors.</span></span> <span data-ttu-id="3efbe-113">Daha fazla bilgi için bkz. [tür](constructing-types-entity-sql.md)oluşturma.</span><span class="sxs-lookup"><span data-stu-id="3efbe-113">For more information, see [Constructing Types](constructing-types-entity-sql.md).</span></span>

<span data-ttu-id="3efbe-114">Çoklu küme Oluşturucu bir değer listesinden bir çoklu küme örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3efbe-114">The multiset constructor creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="3efbe-115">Oluşturucudaki tüm değerler uyumlu türde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3efbe-115">All the values in the constructor must be of a compatible type.</span></span>

<span data-ttu-id="3efbe-116">Örneğin, aşağıdaki ifade tamsayı olan bir çok küme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3efbe-116">For example, the following expression creates a multiset of integers.</span></span>

`MULTISET(1, 2, 3)`

`{1, 2, 3}`

> [!NOTE]
> <span data-ttu-id="3efbe-117">İç içe yerleştirilmiş çoklu küme sabit değerleri yalnızca bir kaydırma çoklu kümeli tek bir çoklu küme öğesi olduğunda desteklenir; Örneğin, `{{1, 2, 3}}` .</span><span class="sxs-lookup"><span data-stu-id="3efbe-117">Nested multiset literals are only supported when a wrapping multiset has a single multiset element; for example, `{{1, 2, 3}}`.</span></span> <span data-ttu-id="3efbe-118">Kaydırma çoklu kümeli birden çok çoklu küme öğesine (örneğin,) sahip olduğunda `{{1, 2}, {3, 4}}` , iç içe yerleştirilmiş çoklu küme sabit değerleri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="3efbe-118">When the wrapping multiset has multiple multiset elements (for example, `{{1, 2}, {3, 4}}`), nested multiset literals are not supported.</span></span>

## <a name="example"></a><span data-ttu-id="3efbe-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="3efbe-119">Example</span></span>

<span data-ttu-id="3efbe-120">Aşağıdaki Entity SQL sorgusu, bir değer listesinden bir çoklu küme örneği oluşturmak için çoklu küme işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="3efbe-120">The following Entity SQL query uses the MULTISET operator to create an instance of a multiset from a list of values.</span></span> <span data-ttu-id="3efbe-121">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="3efbe-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="3efbe-122">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="3efbe-122">To compile and run this query, follow these steps:</span></span>

1. <span data-ttu-id="3efbe-123">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="3efbe-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>

2. <span data-ttu-id="3efbe-124">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="3efbe-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>

[!code-sql[DP EntityServices Concepts#MULTISET](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#multiset)]

## <a name="see-also"></a><span data-ttu-id="3efbe-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3efbe-125">See also</span></span>

- [<span data-ttu-id="3efbe-126">Oluşturma Türleri</span><span class="sxs-lookup"><span data-stu-id="3efbe-126">Constructing Types</span></span>](constructing-types-entity-sql.md)
- [<span data-ttu-id="3efbe-127">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="3efbe-127">Entity SQL Reference</span></span>](entity-sql-reference.md)
