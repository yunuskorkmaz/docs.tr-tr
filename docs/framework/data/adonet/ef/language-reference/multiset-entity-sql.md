---
title: MULTISET (varlık SQL)
ms.date: 03/30/2017
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
ms.openlocfilehash: 64069e1bf2af61748a9e23a469dcdbc74fa9fac7
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53128992"
---
# <a name="multiset-entity-sql"></a><span data-ttu-id="2bf60-102">MULTISET (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="2bf60-102">MULTISET (Entity SQL)</span></span>
<span data-ttu-id="2bf60-103">Değerler listesinden bir çoklu küme örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2bf60-103">Creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="2bf60-104">MULTISET Oluşturucu tüm değerleri uyumlu bir tür olmalıdır `T`.</span><span class="sxs-lookup"><span data-stu-id="2bf60-104">All the values in the MULTISET constructor must be of a compatible type `T`.</span></span> <span data-ttu-id="2bf60-105">Boş çoklu küme oluşturuculara izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="2bf60-105">Empty multiset constructors are not allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bf60-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2bf60-106">Syntax</span></span>  
  
```  
MULTISET ( expression [{, expression }] )  
or  
{ expression [{, expression }] }  
```  
  
## <a name="arguments"></a><span data-ttu-id="2bf60-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="2bf60-107">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="2bf60-108">Tüm geçerli değerlerin listesi.</span><span class="sxs-lookup"><span data-stu-id="2bf60-108">Any valid list of values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2bf60-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2bf60-109">Return Value</span></span>  
 <span data-ttu-id="2bf60-110">MULTISET türündeki bir koleksiyon\<T >.</span><span class="sxs-lookup"><span data-stu-id="2bf60-110">A collection of type MULTISET\<T>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2bf60-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2bf60-111">Remarks</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="2bf60-112">üç tür oluşturucular sağlar: satır Oluşturucular, nesne oluşturucuları ve oluşturucular multiset (veya koleksiyonu).</span><span class="sxs-lookup"><span data-stu-id="2bf60-112">provides three kinds of constructors: row constructors, object constructors, and multiset (or collection) constructors.</span></span> <span data-ttu-id="2bf60-113">Daha fazla bilgi için [oluşturma türleri](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="2bf60-113">For more information, see [Constructing Types](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span></span>  
  
 <span data-ttu-id="2bf60-114">Multıset Oluşturucu değerler listesinden bir çoklu küme örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2bf60-114">The multiset constructor creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="2bf60-115">Oluşturucu içinde tüm değerleri uyumlu bir tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2bf60-115">All the values in the constructor must be of a compatible type.</span></span>  
  
 <span data-ttu-id="2bf60-116">Örneğin, aşağıdaki ifade, bir çoklu küme tamsayı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2bf60-116">For example, the following expression creates a multiset of integers.</span></span>  
  
 `MULTISET(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
> [!NOTE]
>  <span data-ttu-id="2bf60-117">İç içe geçmiş multiset değişmez değerleri, yalnızca bir kaydırma çoklu küme, tek bir çok kümeli öğe olduğunda desteklenir; Örneğin, `{{1, 2, 3}}`.</span><span class="sxs-lookup"><span data-stu-id="2bf60-117">Nested multiset literals are only supported when a wrapping multiset has a single multiset element; for example, `{{1, 2, 3}}`.</span></span> <span data-ttu-id="2bf60-118">Kaydırma çoklu küme, birden fazla çok kümeli öğe olduğunda (örneğin, `{{1, 2}, {3, 4}}`), iç içe geçmiş multiset değişmez değerleri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="2bf60-118">When the wrapping multiset has multiple multiset elements (for example, `{{1, 2}, {3, 4}}`), nested multiset literals are not supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bf60-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="2bf60-119">Example</span></span>  
 <span data-ttu-id="2bf60-120">Aşağıdaki varlık SQL sorgusu MULTISET işleci değerler listesinden bir çoklu küme örneği oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="2bf60-120">The following Entity SQL query uses the MULTISET operator to create an instance of a multiset from a list of values.</span></span> <span data-ttu-id="2bf60-121">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="2bf60-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="2bf60-122">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="2bf60-122">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="2bf60-123">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="2bf60-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="2bf60-124">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="2bf60-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTISET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiset)]  
  
## <a name="see-also"></a><span data-ttu-id="2bf60-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2bf60-125">See Also</span></span>  
 [<span data-ttu-id="2bf60-126">Oluşturma Türleri</span><span class="sxs-lookup"><span data-stu-id="2bf60-126">Constructing Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
 [<span data-ttu-id="2bf60-127">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="2bf60-127">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
