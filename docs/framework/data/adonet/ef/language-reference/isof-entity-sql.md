---
description: 'Hakkında daha fazla bilgi edinin: ıOF (Entity SQL)'
title: IOF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
ms.openlocfilehash: 4a44ddc74ef16ec16285132f6567ca2500e173a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748355"
---
# <a name="isof-entity-sql"></a><span data-ttu-id="9a3e5-103">IOF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="9a3e5-103">ISOF (Entity SQL)</span></span>

<span data-ttu-id="9a3e5-104">Bir ifadenin türünün belirtilen türde mi yoksa alt türlerinden biri mi olduğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="9a3e5-104">Determines whether the type of an expression is of the specified type or one of its subtypes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a3e5-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9a3e5-105">Syntax</span></span>  
  
```sql  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="9a3e5-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="9a3e5-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="9a3e5-107">Türünü belirleyecek geçerli bir sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="9a3e5-107">Any valid query expression to determine the type of.</span></span>  
  
 <span data-ttu-id="9a3e5-108">NOT</span><span class="sxs-lookup"><span data-stu-id="9a3e5-108">NOT</span></span>  
 <span data-ttu-id="9a3e5-109">EDM 'yi geçersiz kılar. ' Nin Boolean sonucu.</span><span class="sxs-lookup"><span data-stu-id="9a3e5-109">Negates the EDM.Boolean result of IS OF.</span></span>  
  
 <span data-ttu-id="9a3e5-110">YALNıZCA</span><span class="sxs-lookup"><span data-stu-id="9a3e5-110">ONLY</span></span>  
 <span data-ttu-id="9a3e5-111">ÖĞESININ `true` yalnızca `expression` türü ise `type` ve alt türlerinden HERHANGI biri değilse, bu döndürdüğünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="9a3e5-111">Specifies that IS OF returns `true` only if `expression` is of type `type` and not any of one its subtypes.</span></span>  
  
 `type`  
 <span data-ttu-id="9a3e5-112">Sınanacak tür `expression` .</span><span class="sxs-lookup"><span data-stu-id="9a3e5-112">The type to test `expression` against.</span></span> <span data-ttu-id="9a3e5-113">Tür ad alanı nitelenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9a3e5-113">The type must be namespace-qualified.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9a3e5-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9a3e5-114">Return Value</span></span>  

 <span data-ttu-id="9a3e5-115">`true` Eğer `expression` t ve t türünde ise, bir temel tür ya da türetilmiş bir tür `type` ; `expression` çalışma zamanında null ise null; Aksi durumda, `false` .</span><span class="sxs-lookup"><span data-stu-id="9a3e5-115">`true` if `expression` is of type T and T is either a base type, or a derived type of `type`; null if `expression` is null at runtime; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a3e5-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9a3e5-116">Remarks</span></span>  

 <span data-ttu-id="9a3e5-117">İfadeler `expression IS NOT OF (type)` ve `expression IS NOT OF (ONLY type)` `NOT (expression IS OF (type))` sırasıyla ve ile aynıdır `NOT (expression IS OF (ONLY type))` .</span><span class="sxs-lookup"><span data-stu-id="9a3e5-117">The expressions `expression IS NOT OF (type)` and `expression IS NOT OF (ONLY type)` are syntactically equivalent to `NOT (expression IS OF (type))` and `NOT (expression IS OF (ONLY type))`, respectively.</span></span>  
  
 <span data-ttu-id="9a3e5-118">Aşağıdaki tabloda, `IS OF` bazı tipik ve köşe desenlerinde işlecin davranışı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9a3e5-118">The following table shows the behavior of `IS OF` operator over some typical- and corner patterns.</span></span> <span data-ttu-id="9a3e5-119">Sağlayıcı çağrılmadan önce istemci tarafında tüm özel durumlar atılır:</span><span class="sxs-lookup"><span data-stu-id="9a3e5-119">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="9a3e5-120">Desen</span><span class="sxs-lookup"><span data-stu-id="9a3e5-120">Pattern</span></span>|<span data-ttu-id="9a3e5-121">Davranış</span><span class="sxs-lookup"><span data-stu-id="9a3e5-121">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="9a3e5-122">null (EntityType)</span><span class="sxs-lookup"><span data-stu-id="9a3e5-122">null IS OF (EntityType)</span></span>|<span data-ttu-id="9a3e5-123">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="9a3e5-123">Throws</span></span>|  
|<span data-ttu-id="9a3e5-124">null (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="9a3e5-124">null IS OF (ComplexType)</span></span>|<span data-ttu-id="9a3e5-125">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="9a3e5-125">Throws</span></span>|  
|<span data-ttu-id="9a3e5-126">null (RowType)</span><span class="sxs-lookup"><span data-stu-id="9a3e5-126">null IS OF (RowType)</span></span>|<span data-ttu-id="9a3e5-127">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="9a3e5-127">Throws</span></span>|  
|<span data-ttu-id="9a3e5-128">DAVRAN (EntityType olarak null), (EntityType)</span><span class="sxs-lookup"><span data-stu-id="9a3e5-128">TREAT (null AS EntityType) IS OF (EntityType)</span></span>|<span data-ttu-id="9a3e5-129">DBNull döndürür</span><span class="sxs-lookup"><span data-stu-id="9a3e5-129">Returns DBNull</span></span>|  
|<span data-ttu-id="9a3e5-130">DAVRAN (ComplexType olarak null), (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="9a3e5-130">TREAT (null AS ComplexType) IS OF (ComplexType)</span></span>|<span data-ttu-id="9a3e5-131">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="9a3e5-131">Throws</span></span>|  
|<span data-ttu-id="9a3e5-132">DEĞERLENDIR (RowType olarak null), (RowType)</span><span class="sxs-lookup"><span data-stu-id="9a3e5-132">TREAT (null AS RowType) IS OF (RowType)</span></span>|<span data-ttu-id="9a3e5-133">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="9a3e5-133">Throws</span></span>|  
|<span data-ttu-id="9a3e5-134">EntityType (EntityType)</span><span class="sxs-lookup"><span data-stu-id="9a3e5-134">EntityType IS OF (EntityType)</span></span>|<span data-ttu-id="9a3e5-135">True/false döndürür</span><span class="sxs-lookup"><span data-stu-id="9a3e5-135">Returns true/false</span></span>|  
|<span data-ttu-id="9a3e5-136">ComplexType (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="9a3e5-136">ComplexType IS OF (ComplexType)</span></span>|<span data-ttu-id="9a3e5-137">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="9a3e5-137">Throws</span></span>|  
|<span data-ttu-id="9a3e5-138">RowType, (RowType)</span><span class="sxs-lookup"><span data-stu-id="9a3e5-138">RowType IS OF (RowType)</span></span>|<span data-ttu-id="9a3e5-139">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="9a3e5-139">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9a3e5-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="9a3e5-140">Example</span></span>  

 <span data-ttu-id="9a3e5-141">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, bir sorgu ifadesinin türünü tespit etmek için işleç ' i kullanır ve sonra bir nesne türünü, Onsitekurs türünde bir nesne koleksiyonuna dönüştürmek IÇIN değerlendir işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9a3e5-141">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS OF operator to determine the type of a query expression, and then uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="9a3e5-142">Sorgu, [okul modelini](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))temel alır.</span><span class="sxs-lookup"><span data-stu-id="9a3e5-142">The query is based on the [School Model](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 <span data-ttu-id="9a3e5-143">[! Code-SQL [DP EntityServices kavramları # TREAT_ISOF] ~/Samples/Snippets/TSQL/VS_Snippets_Data/DP entityservices kavramları/TSQL/EntitySql. SQL # treat_isof)]</span><span class="sxs-lookup"><span data-stu-id="9a3e5-143">[!code-sql[DP EntityServices Concepts#TREAT_ISOF]~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#treat_isof)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a3e5-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a3e5-144">See also</span></span>

- [<span data-ttu-id="9a3e5-145">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="9a3e5-145">Entity SQL Reference</span></span>](entity-sql-reference.md)
