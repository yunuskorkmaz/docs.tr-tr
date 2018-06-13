---
title: DEREF (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
ms.openlocfilehash: ee3877ca256eb3847b0284ac2a7362a4a60aad48
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761486"
---
# <a name="deref-entity-sql"></a><span data-ttu-id="6eabe-102">DEREF (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="6eabe-102">DEREF (Entity SQL)</span></span>
<span data-ttu-id="6eabe-103">Bir başvuru değer ve başvuru sonucu, üretir dereferences.</span><span class="sxs-lookup"><span data-stu-id="6eabe-103">Dereferences a reference value and produces the result of that dereference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6eabe-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6eabe-104">Syntax</span></span>  
  
```  
SELECT DEREF ( o.expression ) from Table as o;  
```  
  
## <a name="arguments"></a><span data-ttu-id="6eabe-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="6eabe-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="6eabe-106">Bir koleksiyon döndürür herhangi bir geçerli sorgu ifade.</span><span class="sxs-lookup"><span data-stu-id="6eabe-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6eabe-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6eabe-107">Return Value</span></span>  
 <span data-ttu-id="6eabe-108">Başvurulan varlık değeri.</span><span class="sxs-lookup"><span data-stu-id="6eabe-108">The value of the entity that is referenced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6eabe-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6eabe-109">Remarks</span></span>  
 <span data-ttu-id="6eabe-110">DEREF işleci bir başvuru değer ve başvuru sonucu, üretir dereferences.</span><span class="sxs-lookup"><span data-stu-id="6eabe-110">The DEREF operator dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="6eabe-111">Örneğin, varsa `r` türü ref başvurudur\<T >, `Deref``(r)` ifade türü olan `T` tarafından başvurulan varlık verir `r`.</span><span class="sxs-lookup"><span data-stu-id="6eabe-111">For example, if `r` is a reference of type ref\<T>, `Deref``(r)` is an expression of type `T` that yields the entity referenced by `r`.</span></span> <span data-ttu-id="6eabe-112">Başvuru değeri null veya sarkan değil (diğer bir deyişle, başvuru hedef için yok), DEREF işleci sonuç NULL'dur.</span><span class="sxs-lookup"><span data-stu-id="6eabe-112">If the reference value is null, or is dangling (that is, the target of the reference does not exist), the result of the DEREF operator is null.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6eabe-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="6eabe-113">Example</span></span>  
 <span data-ttu-id="6eabe-114">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu başvuru değer ve başvuru sonucu, üretim başvurulacak DEREF işleci kullanır.</span><span class="sxs-lookup"><span data-stu-id="6eabe-114">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the DEREF operator to dereference a reference value and produce the result of that dereference.</span></span> <span data-ttu-id="6eabe-115">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="6eabe-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="6eabe-116">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="6eabe-116">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="6eabe-117">Yordamı izleyin [nasıl yapılır: Sorgu döndürür PrimitiveType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="6eabe-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="6eabe-118">Aşağıdaki sorgu bağımsız değişken olarak ExecutePrimitiveTypeQuery yönteme geçirin:</span><span class="sxs-lookup"><span data-stu-id="6eabe-118">Pass the following query as an argument to the ExecutePrimitiveTypeQuery method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#DEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#deref)]  
  
## <a name="see-also"></a><span data-ttu-id="6eabe-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6eabe-119">See Also</span></span>  
 [<span data-ttu-id="6eabe-120">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="6eabe-120">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="6eabe-121">REF</span><span class="sxs-lookup"><span data-stu-id="6eabe-121">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)  
 [<span data-ttu-id="6eabe-122">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="6eabe-122">CREATEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
 [<span data-ttu-id="6eabe-123">KEY</span><span class="sxs-lookup"><span data-stu-id="6eabe-123">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
 [<span data-ttu-id="6eabe-124">Null Değer Atanabilir Yapılandırılmış Türler</span><span class="sxs-lookup"><span data-stu-id="6eabe-124">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
