---
title: DEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
ms.openlocfilehash: c0c975ab5cf2761496db6efa1f88f409aa1b1abd
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148223"
---
# <a name="deref-entity-sql"></a><span data-ttu-id="a9c4f-102">DEREF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a9c4f-102">DEREF (Entity SQL)</span></span>

<span data-ttu-id="a9c4f-103">Başvuru değerine başvurur ve başvurunun sonucunu üretir.</span><span class="sxs-lookup"><span data-stu-id="a9c4f-103">Dereferences a reference value and produces the result of that dereference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9c4f-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a9c4f-104">Syntax</span></span>  
  
```sql  
SELECT DEREF ( o.expression ) FROM Table AS o;
```  
  
## <a name="arguments"></a><span data-ttu-id="a9c4f-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="a9c4f-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="a9c4f-106">Bir koleksiyon döndüren geçerli bir sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="a9c4f-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9c4f-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a9c4f-107">Return Value</span></span>  

 <span data-ttu-id="a9c4f-108">Başvurulan varlığın değeri.</span><span class="sxs-lookup"><span data-stu-id="a9c4f-108">The value of the entity that is referenced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9c4f-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a9c4f-109">Remarks</span></span>  

 <span data-ttu-id="a9c4f-110">DEREF işleci bir başvuru değerine başvurur ve başvurunun sonucunu üretir.</span><span class="sxs-lookup"><span data-stu-id="a9c4f-110">The DEREF operator dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="a9c4f-111">Örneğin, `r` başvuru türü başvurusu ise \<T> , `Deref(r)` tarafından başvurulan varlığı veren türünde bir ifadedir `T` `r` .</span><span class="sxs-lookup"><span data-stu-id="a9c4f-111">For example, if `r` is a reference of type ref\<T>, `Deref(r)` is an expression of type `T` that yields the entity referenced by `r`.</span></span> <span data-ttu-id="a9c4f-112">Başvuru değeri null ise veya tehlike varsa (yani, başvurunun hedefi yoksa), DEREF işlecinin sonucu null olur.</span><span class="sxs-lookup"><span data-stu-id="a9c4f-112">If the reference value is null, or is dangling (that is, the target of the reference does not exist), the result of the DEREF operator is null.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9c4f-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="a9c4f-113">Example</span></span>  

 <span data-ttu-id="a9c4f-114">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, başvuru değeri başvurusu yapmak ve bu başvurunun sonucunu üretmek IÇIN DEREF işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a9c4f-114">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the DEREF operator to dereference a reference value and produce the result of that dereference.</span></span> <span data-ttu-id="a9c4f-115">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="a9c4f-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a9c4f-116">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="a9c4f-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="a9c4f-117">[Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="a9c4f-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="a9c4f-118">Aşağıdaki sorguyu Executeprimitivettypeınfo sorgu yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="a9c4f-118">Pass the following query as an argument to the ExecutePrimitiveTypeQuery method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#DEREF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#deref)]  
  
## <a name="see-also"></a><span data-ttu-id="a9c4f-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9c4f-119">See also</span></span>

- [<span data-ttu-id="a9c4f-120">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="a9c4f-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="a9c4f-121">REF</span><span class="sxs-lookup"><span data-stu-id="a9c4f-121">REF</span></span>](ref-entity-sql.md)
- [<span data-ttu-id="a9c4f-122">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="a9c4f-122">CREATEREF</span></span>](createref-entity-sql.md)
- [<span data-ttu-id="a9c4f-123">ANAHTAR</span><span class="sxs-lookup"><span data-stu-id="a9c4f-123">KEY</span></span>](key-entity-sql.md)
- [<span data-ttu-id="a9c4f-124">Null Değer Atanabilir Yapılandırılmış Türler</span><span class="sxs-lookup"><span data-stu-id="a9c4f-124">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
