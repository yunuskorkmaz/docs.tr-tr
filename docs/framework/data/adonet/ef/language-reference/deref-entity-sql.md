---
title: DEREF (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
ms.openlocfilehash: f64580e5ca34bf094d6019e994f40f11ed9586cd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506920"
---
# <a name="deref-entity-sql"></a><span data-ttu-id="0b5de-102">DEREF (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="0b5de-102">DEREF (Entity SQL)</span></span>
<span data-ttu-id="0b5de-103">Bir başvuru değeri ve bu sonucu başvuru oluşturur başvurusunu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0b5de-103">Dereferences a reference value and produces the result of that dereference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b5de-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0b5de-104">Syntax</span></span>  
  
```  
SELECT DEREF ( o.expression ) from Table as o;  
```  
  
## <a name="arguments"></a><span data-ttu-id="0b5de-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0b5de-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="0b5de-106">Bir koleksiyon döndürür herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="0b5de-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0b5de-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0b5de-107">Return Value</span></span>  
 <span data-ttu-id="0b5de-108">Başvurulan varlık değeri.</span><span class="sxs-lookup"><span data-stu-id="0b5de-108">The value of the entity that is referenced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b5de-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0b5de-109">Remarks</span></span>  
 <span data-ttu-id="0b5de-110">DEREF işleci bir başvuru değeri ve bu sonucu başvuru oluşturur başvurusunu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0b5de-110">The DEREF operator dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="0b5de-111">Örneğin, varsa `r` türü ref başvurudur\<T >, `Deref(r)` türündeki bir ifade `T` tarafından başvurulan varlık verir `r`.</span><span class="sxs-lookup"><span data-stu-id="0b5de-111">For example, if `r` is a reference of type ref\<T>, `Deref(r)` is an expression of type `T` that yields the entity referenced by `r`.</span></span> <span data-ttu-id="0b5de-112">Başvuru değeri null veya sarkan olduğu (yani, başvuru hedefinin yok), DEREF işlecinin sonucunu null.</span><span class="sxs-lookup"><span data-stu-id="0b5de-112">If the reference value is null, or is dangling (that is, the target of the reference does not exist), the result of the DEREF operator is null.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b5de-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="0b5de-113">Example</span></span>  
 <span data-ttu-id="0b5de-114">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu DEREF işleci bir başvuru değeri ve ürettiği sonucu, başvuru başvuru için kullanır.</span><span class="sxs-lookup"><span data-stu-id="0b5de-114">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the DEREF operator to dereference a reference value and produce the result of that dereference.</span></span> <span data-ttu-id="0b5de-115">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="0b5de-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="0b5de-116">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="0b5de-116">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="0b5de-117">Verilen yordamı izleyin [nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="0b5de-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="0b5de-118">Aşağıdaki sorguda ExecutePrimitiveTypeQuery yönteme bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="0b5de-118">Pass the following query as an argument to the ExecutePrimitiveTypeQuery method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#DEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#deref)]  
  
## <a name="see-also"></a><span data-ttu-id="0b5de-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b5de-119">See also</span></span>
- [<span data-ttu-id="0b5de-120">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="0b5de-120">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="0b5de-121">REF</span><span class="sxs-lookup"><span data-stu-id="0b5de-121">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)
- [<span data-ttu-id="0b5de-122">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="0b5de-122">CREATEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)
- [<span data-ttu-id="0b5de-123">KEY</span><span class="sxs-lookup"><span data-stu-id="0b5de-123">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)
- [<span data-ttu-id="0b5de-124">Null Değer Atanabilir Yapılandırılmış Türler</span><span class="sxs-lookup"><span data-stu-id="0b5de-124">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
