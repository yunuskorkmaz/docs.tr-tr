---
title: IOF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
ms.openlocfilehash: 3b746a82f72fc7f42f9d91ddd0a7d6f4f86ac0bb
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250571"
---
# <a name="isof-entity-sql"></a><span data-ttu-id="5d391-102">IOF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="5d391-102">ISOF (Entity SQL)</span></span>
<span data-ttu-id="5d391-103">Bir ifadenin türünün belirtilen türde mi yoksa alt türlerinden biri mi olduğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="5d391-103">Determines whether the type of an expression is of the specified type or one of its subtypes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d391-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5d391-104">Syntax</span></span>  
  
```  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="5d391-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="5d391-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="5d391-106">Türünü belirleyecek geçerli bir sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="5d391-106">Any valid query expression to determine the type of.</span></span>  
  
 <span data-ttu-id="5d391-107">DEĞİL</span><span class="sxs-lookup"><span data-stu-id="5d391-107">NOT</span></span>  
 <span data-ttu-id="5d391-108">EDM 'yi geçersiz kılar. ' Nin Boolean sonucu.</span><span class="sxs-lookup"><span data-stu-id="5d391-108">Negates the EDM.Boolean result of IS OF.</span></span>  
  
 <span data-ttu-id="5d391-109">YALNIZCA</span><span class="sxs-lookup"><span data-stu-id="5d391-109">ONLY</span></span>  
 <span data-ttu-id="5d391-110">Öğesinin `true` yalnızcatürü`type` ise ve alt türlerinden herhangi biri değilse, bu döndürdüğünü belirtir. `expression`</span><span class="sxs-lookup"><span data-stu-id="5d391-110">Specifies that IS OF returns `true` only if `expression` is of type `type` and not any of one its subtypes.</span></span>  
  
 `type`  
 <span data-ttu-id="5d391-111">Sınanacak `expression` tür.</span><span class="sxs-lookup"><span data-stu-id="5d391-111">The type to test `expression` against.</span></span> <span data-ttu-id="5d391-112">Tür ad alanı nitelenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5d391-112">The type must be namespace-qualified.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5d391-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5d391-113">Return Value</span></span>  
 <span data-ttu-id="5d391-114">`true`Eğer `expression` t ve t türünde ise, bir temel tür ya da türetilmiş bir `type`tür; çalışma zamanında null ise null `expression` ; Aksi durumda, `false`.</span><span class="sxs-lookup"><span data-stu-id="5d391-114">`true` if `expression` is of type T and T is either a base type, or a derived type of `type`; null if `expression` is null at runtime; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d391-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5d391-115">Remarks</span></span>  
 <span data-ttu-id="5d391-116">İfadeler `expression IS NOT OF (type)` ve `expression IS NOT OF (ONLY type)` sırasıyla `NOT (expression IS OF (type))` ve ile`NOT (expression IS OF (ONLY type))`aynıdır.</span><span class="sxs-lookup"><span data-stu-id="5d391-116">The expressions `expression IS NOT OF (type)` and `expression IS NOT OF (ONLY type)` are syntactically equivalent to `NOT (expression IS OF (type))` and `NOT (expression IS OF (ONLY type))`, respectively.</span></span>  
  
 <span data-ttu-id="5d391-117">Aşağıdaki tabloda, bazı tipik ve köşe `IS OF` desenlerinde işlecin davranışı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5d391-117">The following table shows the behavior of `IS OF` operator over some typical- and corner patterns.</span></span> <span data-ttu-id="5d391-118">Sağlayıcı çağrılmadan önce istemci tarafında tüm özel durumlar atılır:</span><span class="sxs-lookup"><span data-stu-id="5d391-118">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="5d391-119">Desen</span><span class="sxs-lookup"><span data-stu-id="5d391-119">Pattern</span></span>|<span data-ttu-id="5d391-120">Davranış</span><span class="sxs-lookup"><span data-stu-id="5d391-120">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="5d391-121">null (EntityType)</span><span class="sxs-lookup"><span data-stu-id="5d391-121">null IS OF (EntityType)</span></span>|<span data-ttu-id="5d391-122">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="5d391-122">Throws</span></span>|  
|<span data-ttu-id="5d391-123">null (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="5d391-123">null IS OF (ComplexType)</span></span>|<span data-ttu-id="5d391-124">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="5d391-124">Throws</span></span>|  
|<span data-ttu-id="5d391-125">null (RowType)</span><span class="sxs-lookup"><span data-stu-id="5d391-125">null IS OF (RowType)</span></span>|<span data-ttu-id="5d391-126">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="5d391-126">Throws</span></span>|  
|<span data-ttu-id="5d391-127">DAVRAN (EntityType olarak null), (EntityType)</span><span class="sxs-lookup"><span data-stu-id="5d391-127">TREAT (null AS EntityType) IS OF (EntityType)</span></span>|<span data-ttu-id="5d391-128">DBNull döndürür</span><span class="sxs-lookup"><span data-stu-id="5d391-128">Returns DBNull</span></span>|  
|<span data-ttu-id="5d391-129">DAVRAN (ComplexType olarak null), (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="5d391-129">TREAT (null AS ComplexType) IS OF (ComplexType)</span></span>|<span data-ttu-id="5d391-130">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="5d391-130">Throws</span></span>|  
|<span data-ttu-id="5d391-131">DEĞERLENDIR (RowType olarak null), (RowType)</span><span class="sxs-lookup"><span data-stu-id="5d391-131">TREAT (null AS RowType) IS OF (RowType)</span></span>|<span data-ttu-id="5d391-132">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="5d391-132">Throws</span></span>|  
|<span data-ttu-id="5d391-133">EntityType (EntityType)</span><span class="sxs-lookup"><span data-stu-id="5d391-133">EntityType IS OF (EntityType)</span></span>|<span data-ttu-id="5d391-134">True/false döndürür</span><span class="sxs-lookup"><span data-stu-id="5d391-134">Returns true/false</span></span>|  
|<span data-ttu-id="5d391-135">ComplexType (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="5d391-135">ComplexType IS OF (ComplexType)</span></span>|<span data-ttu-id="5d391-136">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="5d391-136">Throws</span></span>|  
|<span data-ttu-id="5d391-137">RowType, (RowType)</span><span class="sxs-lookup"><span data-stu-id="5d391-137">RowType IS OF (RowType)</span></span>|<span data-ttu-id="5d391-138">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="5d391-138">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5d391-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="5d391-139">Example</span></span>  
 <span data-ttu-id="5d391-140">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, bir sorgu ifadesinin türünü tespit etmek için işleç ' i kullanır ve sonra bir nesne türünü, onsitekurs türünde bir nesne koleksiyonuna dönüştürmek için değerlendir işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="5d391-140">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS OF operator to determine the type of a query expression, and then uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="5d391-141">Sorgu, [okul modelini](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))temel alır.</span><span class="sxs-lookup"><span data-stu-id="5d391-141">The query is based on the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## <a name="see-also"></a><span data-ttu-id="5d391-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d391-142">See also</span></span>

- [<span data-ttu-id="5d391-143">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="5d391-143">Entity SQL Reference</span></span>](entity-sql-reference.md)
