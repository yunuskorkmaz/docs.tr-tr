---
title: Çoklu küme (Entity SQL)
ms.date: 03/30/2017
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
ms.openlocfilehash: 222be86db434b5d41c7b0536d271a3750b6afbe8
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319590"
---
# <a name="multiset-entity-sql"></a><span data-ttu-id="6b66e-102">Çoklu küme (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="6b66e-102">MULTISET (Entity SQL)</span></span>
<span data-ttu-id="6b66e-103">Bir değer listesinden bir çoklu küme örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6b66e-103">Creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="6b66e-104">Çoklu küme oluşturucudaki tüm değerler `T`uyumlu türde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6b66e-104">All the values in the MULTISET constructor must be of a compatible type `T`.</span></span> <span data-ttu-id="6b66e-105">Boş çok kümeli oluşturuculara izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="6b66e-105">Empty multiset constructors are not allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b66e-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6b66e-106">Syntax</span></span>  
  
```sql  
MULTISET ( expression [{, expression }] )  
-- or  
{ expression [{, expression }] }  
```  
  
## <a name="arguments"></a><span data-ttu-id="6b66e-107">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="6b66e-107">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="6b66e-108">Herhangi bir geçerli değer listesi.</span><span class="sxs-lookup"><span data-stu-id="6b66e-108">Any valid list of values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b66e-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6b66e-109">Return Value</span></span>  
 <span data-ttu-id="6b66e-110">\<T > türünde bir koleksiyon.</span><span class="sxs-lookup"><span data-stu-id="6b66e-110">A collection of type MULTISET\<T>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b66e-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6b66e-111">Remarks</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="6b66e-112">üç tür Oluşturucu sağlar: satır oluşturucular, nesne oluşturucular ve çoklu küme (veya koleksiyon) oluşturucuları.</span><span class="sxs-lookup"><span data-stu-id="6b66e-112">provides three kinds of constructors: row constructors, object constructors, and multiset (or collection) constructors.</span></span> <span data-ttu-id="6b66e-113">Daha fazla bilgi için bkz. [tür](constructing-types-entity-sql.md)oluşturma.</span><span class="sxs-lookup"><span data-stu-id="6b66e-113">For more information, see [Constructing Types](constructing-types-entity-sql.md).</span></span>  
  
 <span data-ttu-id="6b66e-114">Çoklu küme Oluşturucu bir değer listesinden bir çoklu küme örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6b66e-114">The multiset constructor creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="6b66e-115">Oluşturucudaki tüm değerler uyumlu türde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6b66e-115">All the values in the constructor must be of a compatible type.</span></span>  
  
 <span data-ttu-id="6b66e-116">Örneğin, aşağıdaki ifade tamsayı olan bir çok küme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6b66e-116">For example, the following expression creates a multiset of integers.</span></span>  
  
 `MULTISET(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
> [!NOTE]
> <span data-ttu-id="6b66e-117">İç içe yerleştirilmiş çoklu küme sabit değerleri yalnızca bir kaydırma çoklu kümeli tek bir çoklu küme öğesi olduğunda desteklenir; Örneğin, `{{1, 2, 3}}`.</span><span class="sxs-lookup"><span data-stu-id="6b66e-117">Nested multiset literals are only supported when a wrapping multiset has a single multiset element; for example, `{{1, 2, 3}}`.</span></span> <span data-ttu-id="6b66e-118">Kaydırma çoklu kümeli birden çok çoklu küme öğesine (örneğin, `{{1, 2}, {3, 4}}`) sahip olduğunda, iç içe yerleştirilmiş çoklu küme sabit değerleri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="6b66e-118">When the wrapping multiset has multiple multiset elements (for example, `{{1, 2}, {3, 4}}`), nested multiset literals are not supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b66e-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="6b66e-119">Example</span></span>  
 <span data-ttu-id="6b66e-120">Aşağıdaki Entity SQL sorgusu, bir değer listesinden bir çoklu küme örneği oluşturmak için çoklu küme işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="6b66e-120">The following Entity SQL query uses the MULTISET operator to create an instance of a multiset from a list of values.</span></span> <span data-ttu-id="6b66e-121">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="6b66e-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="6b66e-122">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="6b66e-122">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="6b66e-123">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="6b66e-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="6b66e-124">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="6b66e-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#MULTISET](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#multiset)]  
  
## <a name="see-also"></a><span data-ttu-id="6b66e-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b66e-125">See also</span></span>

- [<span data-ttu-id="6b66e-126">Oluşturma Türleri</span><span class="sxs-lookup"><span data-stu-id="6b66e-126">Constructing Types</span></span>](constructing-types-entity-sql.md)
- [<span data-ttu-id="6b66e-127">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="6b66e-127">Entity SQL Reference</span></span>](entity-sql-reference.md)
