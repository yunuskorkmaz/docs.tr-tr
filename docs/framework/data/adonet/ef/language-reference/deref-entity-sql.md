---
title: DEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
ms.openlocfilehash: 27fc23a2be47ea00eff20aa8d2f559af5ae90387
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833899"
---
# <a name="deref-entity-sql"></a><span data-ttu-id="c1994-102">DEREF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c1994-102">DEREF (Entity SQL)</span></span>
<span data-ttu-id="c1994-103">Başvuru değerine başvurur ve başvurunun sonucunu üretir.</span><span class="sxs-lookup"><span data-stu-id="c1994-103">Dereferences a reference value and produces the result of that dereference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1994-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c1994-104">Syntax</span></span>  
  
```sql  
SELECT DEREF ( o.expression ) FROM Table AS o;
```  
  
## <a name="arguments"></a><span data-ttu-id="c1994-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="c1994-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="c1994-106">Bir koleksiyon döndüren geçerli bir sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="c1994-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1994-107">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="c1994-107">Return Value</span></span>  
 <span data-ttu-id="c1994-108">Başvurulan varlığın değeri.</span><span class="sxs-lookup"><span data-stu-id="c1994-108">The value of the entity that is referenced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1994-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c1994-109">Remarks</span></span>  
 <span data-ttu-id="c1994-110">DEREF işleci bir başvuru değerine başvurur ve başvurunun sonucunu üretir.</span><span class="sxs-lookup"><span data-stu-id="c1994-110">The DEREF operator dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="c1994-111">Örneğin, `r`, ref @ no__t-1T > türünde bir başvuru ise, `Deref(r)` `r` tarafından başvurulan varlığı veren `T` türünde bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="c1994-111">For example, if `r` is a reference of type ref\<T>, `Deref(r)` is an expression of type `T` that yields the entity referenced by `r`.</span></span> <span data-ttu-id="c1994-112">Başvuru değeri null ise veya tehlike varsa (yani, başvurunun hedefi yoksa), DEREF işlecinin sonucu null olur.</span><span class="sxs-lookup"><span data-stu-id="c1994-112">If the reference value is null, or is dangling (that is, the target of the reference does not exist), the result of the DEREF operator is null.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1994-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="c1994-113">Example</span></span>  
 <span data-ttu-id="c1994-114">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgusu, başvuru değeri başvurusu yapmak ve bu başvurunun sonucunu üretmek için DEREF işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c1994-114">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the DEREF operator to dereference a reference value and produce the result of that dereference.</span></span> <span data-ttu-id="c1994-115">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="c1994-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="c1994-116">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="c1994-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="c1994-117">[Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="c1994-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="c1994-118">Aşağıdaki sorguyu Executeprimitivettypeınfo sorgu yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="c1994-118">Pass the following query as an argument to the ExecutePrimitiveTypeQuery method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#DEREF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#deref)]  
  
## <a name="see-also"></a><span data-ttu-id="c1994-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1994-119">See also</span></span>

- [<span data-ttu-id="c1994-120">Entity SQL başvurusu</span><span class="sxs-lookup"><span data-stu-id="c1994-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="c1994-121">REF</span><span class="sxs-lookup"><span data-stu-id="c1994-121">REF</span></span>](ref-entity-sql.md)
- [<span data-ttu-id="c1994-122">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="c1994-122">CREATEREF</span></span>](createref-entity-sql.md)
- [<span data-ttu-id="c1994-123">ANAHTAR</span><span class="sxs-lookup"><span data-stu-id="c1994-123">KEY</span></span>](key-entity-sql.md)
- [<span data-ttu-id="c1994-124">Null yapılabilir yapılandırılmış türler</span><span class="sxs-lookup"><span data-stu-id="c1994-124">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
