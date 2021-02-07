---
description: 'Daha fazla bilgi edinin: DEREF (Entity SQL)'
title: DEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
ms.openlocfilehash: 9d0f29123c1459c6eab21ea9cd860b5c9e77f591
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724732"
---
# <a name="deref-entity-sql"></a><span data-ttu-id="2f0f1-103">DEREF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="2f0f1-103">DEREF (Entity SQL)</span></span>

<span data-ttu-id="2f0f1-104">Başvuru değerine başvurur ve başvurunun sonucunu üretir.</span><span class="sxs-lookup"><span data-stu-id="2f0f1-104">Dereferences a reference value and produces the result of that dereference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f0f1-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2f0f1-105">Syntax</span></span>  
  
```sql  
SELECT DEREF ( o.expression ) FROM Table AS o;
```  
  
## <a name="arguments"></a><span data-ttu-id="2f0f1-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="2f0f1-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="2f0f1-107">Bir koleksiyon döndüren geçerli bir sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="2f0f1-107">Any valid query expression that returns a collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2f0f1-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2f0f1-108">Return Value</span></span>  

 <span data-ttu-id="2f0f1-109">Başvurulan varlığın değeri.</span><span class="sxs-lookup"><span data-stu-id="2f0f1-109">The value of the entity that is referenced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f0f1-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2f0f1-110">Remarks</span></span>  

 <span data-ttu-id="2f0f1-111">DEREF işleci bir başvuru değerine başvurur ve başvurunun sonucunu üretir.</span><span class="sxs-lookup"><span data-stu-id="2f0f1-111">The DEREF operator dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="2f0f1-112">Örneğin, `r` başvuru türü başvurusu ise \<T> , `Deref(r)` tarafından başvurulan varlığı veren türünde bir ifadedir `T` `r` .</span><span class="sxs-lookup"><span data-stu-id="2f0f1-112">For example, if `r` is a reference of type ref\<T>, `Deref(r)` is an expression of type `T` that yields the entity referenced by `r`.</span></span> <span data-ttu-id="2f0f1-113">Başvuru değeri null ise veya tehlike varsa (yani, başvurunun hedefi yoksa), DEREF işlecinin sonucu null olur.</span><span class="sxs-lookup"><span data-stu-id="2f0f1-113">If the reference value is null, or is dangling (that is, the target of the reference does not exist), the result of the DEREF operator is null.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f0f1-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="2f0f1-114">Example</span></span>  

 <span data-ttu-id="2f0f1-115">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, başvuru değeri başvurusu yapmak ve bu başvurunun sonucunu üretmek IÇIN DEREF işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2f0f1-115">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the DEREF operator to dereference a reference value and produce the result of that dereference.</span></span> <span data-ttu-id="2f0f1-116">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="2f0f1-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="2f0f1-117">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="2f0f1-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="2f0f1-118">[Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="2f0f1-118">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="2f0f1-119">Aşağıdaki sorguyu Executeprimitivettypeınfo sorgu yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="2f0f1-119">Pass the following query as an argument to the ExecutePrimitiveTypeQuery method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#DEREF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#deref)]  
  
## <a name="see-also"></a><span data-ttu-id="2f0f1-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f0f1-120">See also</span></span>

- [<span data-ttu-id="2f0f1-121">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="2f0f1-121">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="2f0f1-122">REF</span><span class="sxs-lookup"><span data-stu-id="2f0f1-122">REF</span></span>](ref-entity-sql.md)
- [<span data-ttu-id="2f0f1-123">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="2f0f1-123">CREATEREF</span></span>](createref-entity-sql.md)
- [<span data-ttu-id="2f0f1-124">ANAHTAR</span><span class="sxs-lookup"><span data-stu-id="2f0f1-124">KEY</span></span>](key-entity-sql.md)
- [<span data-ttu-id="2f0f1-125">Null Değer Atanabilir Yapılandırılmış Türler</span><span class="sxs-lookup"><span data-stu-id="2f0f1-125">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
