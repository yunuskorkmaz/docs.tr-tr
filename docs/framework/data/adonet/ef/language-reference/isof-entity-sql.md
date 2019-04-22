---
title: ISOF (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
ms.openlocfilehash: 097d6e7d452ee62a2c8934d2c5fcfdddbeaffc73
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59195754"
---
# <a name="isof-entity-sql"></a><span data-ttu-id="8e309-102">ISOF (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="8e309-102">ISOF (Entity SQL)</span></span>
<span data-ttu-id="8e309-103">Belirtilen tür veya onun alt türlerinden birini bir ifadenin türü olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="8e309-103">Determines whether the type of an expression is of the specified type or one of its subtypes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e309-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8e309-104">Syntax</span></span>  
  
```  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="8e309-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8e309-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="8e309-106">Türünü belirlemek için tüm geçerli sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="8e309-106">Any valid query expression to determine the type of.</span></span>  
  
 <span data-ttu-id="8e309-107">DEĞİL</span><span class="sxs-lookup"><span data-stu-id="8e309-107">NOT</span></span>  
 <span data-ttu-id="8e309-108">EDM olumsuz duruma getirir. Boolean sonucu olduğundan.</span><span class="sxs-lookup"><span data-stu-id="8e309-108">Negates the EDM.Boolean result of IS OF.</span></span>  
  
 <span data-ttu-id="8e309-109">YALNIZCA</span><span class="sxs-lookup"><span data-stu-id="8e309-109">ONLY</span></span>  
 <span data-ttu-id="8e309-110">OLDUĞUNDAN, döndüren belirtir `true` yalnızca `expression` türünde `type` ve herhangi bir alt türleri.</span><span class="sxs-lookup"><span data-stu-id="8e309-110">Specifies that IS OF returns `true` only if `expression` is of type `type` and not any of one its subtypes.</span></span>  
  
 `type`  
 <span data-ttu-id="8e309-111">Sınanacak tür `expression` karşı.</span><span class="sxs-lookup"><span data-stu-id="8e309-111">The type to test `expression` against.</span></span> <span data-ttu-id="8e309-112">İsim uzayıyla nitelenmiş tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8e309-112">The type must be namespace-qualified.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8e309-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8e309-113">Return Value</span></span>  
 <span data-ttu-id="8e309-114">`true` varsa `expression` olan türü T, T bir taban türü veya türetilmiş bir tür ise `type`; null ise `expression` çalışma zamanında null; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="8e309-114">`true` if `expression` is of type T and T is either a base type, or a derived type of `type`; null if `expression` is null at runtime; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e309-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8e309-115">Remarks</span></span>  
 <span data-ttu-id="8e309-116">İfadeleri `expression IS NOT OF (type)` ve `expression IS NOT OF (ONLY type)` sözdizimsel olarak eşdeğer `NOT (expression IS OF (type))` ve `NOT (expression IS OF (ONLY type))`sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="8e309-116">The expressions `expression IS NOT OF (type)` and `expression IS NOT OF (ONLY type)` are syntactically equivalent to `NOT (expression IS OF (type))` and `NOT (expression IS OF (ONLY type))`, respectively.</span></span>  
  
 <span data-ttu-id="8e309-117">Aşağıdaki tabloda davranışını gösteren `IS OF` bazı tipik ve köşe desenleri üzerinden işleci.</span><span class="sxs-lookup"><span data-stu-id="8e309-117">The following table shows the behavior of `IS OF` operator over some typical- and corner patterns.</span></span> <span data-ttu-id="8e309-118">Sağlayıcı çağrılır önce tüm istemci tarafında özel durumlar:</span><span class="sxs-lookup"><span data-stu-id="8e309-118">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="8e309-119">Desen</span><span class="sxs-lookup"><span data-stu-id="8e309-119">Pattern</span></span>|<span data-ttu-id="8e309-120">Davranış</span><span class="sxs-lookup"><span data-stu-id="8e309-120">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="8e309-121">null olduğundan, (EntityType)</span><span class="sxs-lookup"><span data-stu-id="8e309-121">null IS OF (EntityType)</span></span>|<span data-ttu-id="8e309-122">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="8e309-122">Throws</span></span>|  
|<span data-ttu-id="8e309-123">null olduğundan, (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="8e309-123">null IS OF (ComplexType)</span></span>|<span data-ttu-id="8e309-124">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="8e309-124">Throws</span></span>|  
|<span data-ttu-id="8e309-125">null olduğundan, (RowType)</span><span class="sxs-lookup"><span data-stu-id="8e309-125">null IS OF (RowType)</span></span>|<span data-ttu-id="8e309-126">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="8e309-126">Throws</span></span>|  
|<span data-ttu-id="8e309-127">KABUL (null AS EntityType) olduğundan, (EntityType)</span><span class="sxs-lookup"><span data-stu-id="8e309-127">TREAT (null AS EntityType) IS OF (EntityType)</span></span>|<span data-ttu-id="8e309-128">DBNull döndürür</span><span class="sxs-lookup"><span data-stu-id="8e309-128">Returns DBNull</span></span>|  
|<span data-ttu-id="8e309-129">KABUL (null AS ComplexType) olduğundan, (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="8e309-129">TREAT (null AS ComplexType) IS OF (ComplexType)</span></span>|<span data-ttu-id="8e309-130">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="8e309-130">Throws</span></span>|  
|<span data-ttu-id="8e309-131">KABUL (null AS RowType) olduğundan, (RowType)</span><span class="sxs-lookup"><span data-stu-id="8e309-131">TREAT (null AS RowType) IS OF (RowType)</span></span>|<span data-ttu-id="8e309-132">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="8e309-132">Throws</span></span>|  
|<span data-ttu-id="8e309-133">EntityType olan (EntityType),</span><span class="sxs-lookup"><span data-stu-id="8e309-133">EntityType IS OF (EntityType)</span></span>|<span data-ttu-id="8e309-134">True/false döndürür</span><span class="sxs-lookup"><span data-stu-id="8e309-134">Returns true/false</span></span>|  
|<span data-ttu-id="8e309-135">ComplexType olduğu (ComplexType),</span><span class="sxs-lookup"><span data-stu-id="8e309-135">ComplexType IS OF (ComplexType)</span></span>|<span data-ttu-id="8e309-136">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="8e309-136">Throws</span></span>|  
|<span data-ttu-id="8e309-137">RowType olduğu (RowType),</span><span class="sxs-lookup"><span data-stu-id="8e309-137">RowType IS OF (RowType)</span></span>|<span data-ttu-id="8e309-138">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="8e309-138">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8e309-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e309-139">Example</span></span>  
 <span data-ttu-id="8e309-140">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu olan işlecini bir sorgu ifadesinde türü belirlemek için kullanır ve ardından OnsiteCourse türünden nesnelerin bir koleksiyonunu kurs türdeki bir nesneyi dönüştürmek için kabul işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8e309-140">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS OF operator to determine the type of a query expression, and then uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="8e309-141">Sorgu dayanır [Okul modeli](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="8e309-141">The query is based on the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## <a name="see-also"></a><span data-ttu-id="8e309-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e309-142">See also</span></span>

- [<span data-ttu-id="8e309-143">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="8e309-143">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
