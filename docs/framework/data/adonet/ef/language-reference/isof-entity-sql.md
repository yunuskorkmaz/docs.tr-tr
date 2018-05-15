---
title: ISOF (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
ms.openlocfilehash: 7aecb8e2740ffd711278bfd5735c71c2dacf9c3c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="isof-entity-sql"></a><span data-ttu-id="929d8-102">ISOF (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="929d8-102">ISOF (Entity SQL)</span></span>
<span data-ttu-id="929d8-103">İfade türü belirtilen türe veya onun alt türlerinden birini olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="929d8-103">Determines whether the type of an expression is of the specified type or one of its subtypes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="929d8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="929d8-104">Syntax</span></span>  
  
```  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="929d8-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="929d8-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="929d8-106">Türü belirlemek için tüm geçerli sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="929d8-106">Any valid query expression to determine the type of.</span></span>  
  
 <span data-ttu-id="929d8-107">DEĞİL</span><span class="sxs-lookup"><span data-stu-id="929d8-107">NOT</span></span>  
 <span data-ttu-id="929d8-108">EDM üzerindeki geçersiz kılar. Boolean sonucu olduğundan.</span><span class="sxs-lookup"><span data-stu-id="929d8-108">Negates the EDM.Boolean result of IS OF.</span></span>  
  
 <span data-ttu-id="929d8-109">YALNIZCA</span><span class="sxs-lookup"><span data-stu-id="929d8-109">ONLY</span></span>  
 <span data-ttu-id="929d8-110">OLDUĞUNDAN, döndüren belirtir `true` yalnızca `expression` türü `type` ve herhangi bir alt türleri.</span><span class="sxs-lookup"><span data-stu-id="929d8-110">Specifies that IS OF returns `true` only if `expression` is of type `type` and not any of one its subtypes.</span></span>  
  
 `type`  
 <span data-ttu-id="929d8-111">Test etmek için türü `expression` karşı.</span><span class="sxs-lookup"><span data-stu-id="929d8-111">The type to test `expression` against.</span></span> <span data-ttu-id="929d8-112">Türü, ad alanı nitelenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="929d8-112">The type must be namespace-qualified.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="929d8-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="929d8-113">Return Value</span></span>  
 <span data-ttu-id="929d8-114">`true` varsa `expression` olan T ve T bir taban türü veya türetilmiş bir tür türünde `type`; null ise `expression` çalışma zamanında null; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="929d8-114">`true` if `expression` is of type T and T is either a base type, or a derived type of `type`; null if `expression` is null at runtime; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="929d8-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="929d8-115">Remarks</span></span>  
 <span data-ttu-id="929d8-116">İfadeleri `expression IS NOT OF (type)` ve `expression IS NOT OF (ONLY type)` sözdizimsel olarak eşdeğerdir `NOT (expression IS OF (type))` ve `NOT (expression IS OF (ONLY type))`sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="929d8-116">The expressions `expression IS NOT OF (type)` and `expression IS NOT OF (ONLY type)` are syntactically equivalent to `NOT (expression IS OF (type))` and `NOT (expression IS OF (ONLY type))`, respectively.</span></span>  
  
 <span data-ttu-id="929d8-117">Aşağıdaki tabloda davranışını gösterilmektedir `IS OF` bazı tipik - ve köşe desenleri üzerinden işleci.</span><span class="sxs-lookup"><span data-stu-id="929d8-117">The following table shows the behavior of `IS OF` operator over some typical- and corner patterns.</span></span> <span data-ttu-id="929d8-118">Sağlayıcı çağrılır önce tüm istemci tarafındaki özel durumlar:</span><span class="sxs-lookup"><span data-stu-id="929d8-118">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="929d8-119">Desen</span><span class="sxs-lookup"><span data-stu-id="929d8-119">Pattern</span></span>|<span data-ttu-id="929d8-120">Davranış</span><span class="sxs-lookup"><span data-stu-id="929d8-120">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="929d8-121">null olduğundan, (EntityType)</span><span class="sxs-lookup"><span data-stu-id="929d8-121">null IS OF (EntityType)</span></span>|<span data-ttu-id="929d8-122">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="929d8-122">Throws</span></span>|  
|<span data-ttu-id="929d8-123">null olduğundan, (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="929d8-123">null IS OF (ComplexType)</span></span>|<span data-ttu-id="929d8-124">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="929d8-124">Throws</span></span>|  
|<span data-ttu-id="929d8-125">null olduğundan, (RowType)</span><span class="sxs-lookup"><span data-stu-id="929d8-125">null IS OF (RowType)</span></span>|<span data-ttu-id="929d8-126">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="929d8-126">Throws</span></span>|  
|<span data-ttu-id="929d8-127">KABUL (null AS EntityType) olduğundan, (EntityType)</span><span class="sxs-lookup"><span data-stu-id="929d8-127">TREAT (null AS EntityType) IS OF (EntityType)</span></span>|<span data-ttu-id="929d8-128">DBNull döndürür</span><span class="sxs-lookup"><span data-stu-id="929d8-128">Returns DBNull</span></span>|  
|<span data-ttu-id="929d8-129">KABUL (null AS ComplexType) olduğundan, (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="929d8-129">TREAT (null AS ComplexType) IS OF (ComplexType)</span></span>|<span data-ttu-id="929d8-130">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="929d8-130">Throws</span></span>|  
|<span data-ttu-id="929d8-131">KABUL (null AS RowType) olduğundan, (RowType)</span><span class="sxs-lookup"><span data-stu-id="929d8-131">TREAT (null AS RowType) IS OF (RowType)</span></span>|<span data-ttu-id="929d8-132">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="929d8-132">Throws</span></span>|  
|<span data-ttu-id="929d8-133">EntityType olan (ENTİTYTYPE)</span><span class="sxs-lookup"><span data-stu-id="929d8-133">EntityType IS OF (EntityType)</span></span>|<span data-ttu-id="929d8-134">True/false değerini döndürür</span><span class="sxs-lookup"><span data-stu-id="929d8-134">Returns true/false</span></span>|  
|<span data-ttu-id="929d8-135">ComplexType olduğu (COMPLEXTYPE)</span><span class="sxs-lookup"><span data-stu-id="929d8-135">ComplexType IS OF (ComplexType)</span></span>|<span data-ttu-id="929d8-136">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="929d8-136">Throws</span></span>|  
|<span data-ttu-id="929d8-137">RowType olduğu (RowType),</span><span class="sxs-lookup"><span data-stu-id="929d8-137">RowType IS OF (RowType)</span></span>|<span data-ttu-id="929d8-138">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="929d8-138">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="929d8-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="929d8-139">Example</span></span>  
 <span data-ttu-id="929d8-140">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu bir sorgu ifadesinde türü belirlemek için olduğundan, işleci kullanır ve indirmelere türünde bir nesne OnsiteCourse türündeki nesneler koleksiyonuna dönüştürmek için kabul işleci kullanır.</span><span class="sxs-lookup"><span data-stu-id="929d8-140">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS OF operator to determine the type of a query expression, and then uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="929d8-141">Sorgu dayanır [Okul modeli](http://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac).</span><span class="sxs-lookup"><span data-stu-id="929d8-141">The query is based on the [School Model](http://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac).</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## <a name="see-also"></a><span data-ttu-id="929d8-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="929d8-142">See Also</span></span>  
 [<span data-ttu-id="929d8-143">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="929d8-143">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
