---
title: IOF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
ms.openlocfilehash: 3cbbc9b6feda1bde104ed2c95d4dca274b090028
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202285"
---
# <a name="isof-entity-sql"></a><span data-ttu-id="6a91e-102">IOF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="6a91e-102">ISOF (Entity SQL)</span></span>

<span data-ttu-id="6a91e-103">Bir ifadenin türünün belirtilen türde mi yoksa alt türlerinden biri mi olduğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="6a91e-103">Determines whether the type of an expression is of the specified type or one of its subtypes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a91e-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6a91e-104">Syntax</span></span>  
  
```sql  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="6a91e-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="6a91e-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="6a91e-106">Türünü belirleyecek geçerli bir sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="6a91e-106">Any valid query expression to determine the type of.</span></span>  
  
 <span data-ttu-id="6a91e-107">NOT</span><span class="sxs-lookup"><span data-stu-id="6a91e-107">NOT</span></span>  
 <span data-ttu-id="6a91e-108">EDM 'yi geçersiz kılar. ' Nin Boolean sonucu.</span><span class="sxs-lookup"><span data-stu-id="6a91e-108">Negates the EDM.Boolean result of IS OF.</span></span>  
  
 <span data-ttu-id="6a91e-109">YALNıZCA</span><span class="sxs-lookup"><span data-stu-id="6a91e-109">ONLY</span></span>  
 <span data-ttu-id="6a91e-110">ÖĞESININ `true` yalnızca `expression` türü ise `type` ve alt türlerinden HERHANGI biri değilse, bu döndürdüğünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="6a91e-110">Specifies that IS OF returns `true` only if `expression` is of type `type` and not any of one its subtypes.</span></span>  
  
 `type`  
 <span data-ttu-id="6a91e-111">Sınanacak tür `expression` .</span><span class="sxs-lookup"><span data-stu-id="6a91e-111">The type to test `expression` against.</span></span> <span data-ttu-id="6a91e-112">Tür ad alanı nitelenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6a91e-112">The type must be namespace-qualified.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6a91e-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6a91e-113">Return Value</span></span>  

 <span data-ttu-id="6a91e-114">`true` Eğer `expression` t ve t türünde ise, bir temel tür ya da türetilmiş bir tür `type` ; `expression` çalışma zamanında null ise null; Aksi durumda, `false` .</span><span class="sxs-lookup"><span data-stu-id="6a91e-114">`true` if `expression` is of type T and T is either a base type, or a derived type of `type`; null if `expression` is null at runtime; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a91e-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6a91e-115">Remarks</span></span>  

 <span data-ttu-id="6a91e-116">İfadeler `expression IS NOT OF (type)` ve `expression IS NOT OF (ONLY type)` `NOT (expression IS OF (type))` sırasıyla ve ile aynıdır `NOT (expression IS OF (ONLY type))` .</span><span class="sxs-lookup"><span data-stu-id="6a91e-116">The expressions `expression IS NOT OF (type)` and `expression IS NOT OF (ONLY type)` are syntactically equivalent to `NOT (expression IS OF (type))` and `NOT (expression IS OF (ONLY type))`, respectively.</span></span>  
  
 <span data-ttu-id="6a91e-117">Aşağıdaki tabloda, `IS OF` bazı tipik ve köşe desenlerinde işlecin davranışı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6a91e-117">The following table shows the behavior of `IS OF` operator over some typical- and corner patterns.</span></span> <span data-ttu-id="6a91e-118">Sağlayıcı çağrılmadan önce istemci tarafında tüm özel durumlar atılır:</span><span class="sxs-lookup"><span data-stu-id="6a91e-118">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="6a91e-119">Desen</span><span class="sxs-lookup"><span data-stu-id="6a91e-119">Pattern</span></span>|<span data-ttu-id="6a91e-120">Davranış</span><span class="sxs-lookup"><span data-stu-id="6a91e-120">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="6a91e-121">null (EntityType)</span><span class="sxs-lookup"><span data-stu-id="6a91e-121">null IS OF (EntityType)</span></span>|<span data-ttu-id="6a91e-122">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="6a91e-122">Throws</span></span>|  
|<span data-ttu-id="6a91e-123">null (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="6a91e-123">null IS OF (ComplexType)</span></span>|<span data-ttu-id="6a91e-124">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="6a91e-124">Throws</span></span>|  
|<span data-ttu-id="6a91e-125">null (RowType)</span><span class="sxs-lookup"><span data-stu-id="6a91e-125">null IS OF (RowType)</span></span>|<span data-ttu-id="6a91e-126">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="6a91e-126">Throws</span></span>|  
|<span data-ttu-id="6a91e-127">DAVRAN (EntityType olarak null), (EntityType)</span><span class="sxs-lookup"><span data-stu-id="6a91e-127">TREAT (null AS EntityType) IS OF (EntityType)</span></span>|<span data-ttu-id="6a91e-128">DBNull döndürür</span><span class="sxs-lookup"><span data-stu-id="6a91e-128">Returns DBNull</span></span>|  
|<span data-ttu-id="6a91e-129">DAVRAN (ComplexType olarak null), (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="6a91e-129">TREAT (null AS ComplexType) IS OF (ComplexType)</span></span>|<span data-ttu-id="6a91e-130">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="6a91e-130">Throws</span></span>|  
|<span data-ttu-id="6a91e-131">DEĞERLENDIR (RowType olarak null), (RowType)</span><span class="sxs-lookup"><span data-stu-id="6a91e-131">TREAT (null AS RowType) IS OF (RowType)</span></span>|<span data-ttu-id="6a91e-132">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="6a91e-132">Throws</span></span>|  
|<span data-ttu-id="6a91e-133">EntityType (EntityType)</span><span class="sxs-lookup"><span data-stu-id="6a91e-133">EntityType IS OF (EntityType)</span></span>|<span data-ttu-id="6a91e-134">True/false döndürür</span><span class="sxs-lookup"><span data-stu-id="6a91e-134">Returns true/false</span></span>|  
|<span data-ttu-id="6a91e-135">ComplexType (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="6a91e-135">ComplexType IS OF (ComplexType)</span></span>|<span data-ttu-id="6a91e-136">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="6a91e-136">Throws</span></span>|  
|<span data-ttu-id="6a91e-137">RowType, (RowType)</span><span class="sxs-lookup"><span data-stu-id="6a91e-137">RowType IS OF (RowType)</span></span>|<span data-ttu-id="6a91e-138">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="6a91e-138">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6a91e-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="6a91e-139">Example</span></span>  

 <span data-ttu-id="6a91e-140">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, bir sorgu ifadesinin türünü tespit etmek için işleç ' i kullanır ve sonra bir nesne türünü, Onsitekurs türünde bir nesne koleksiyonuna dönüştürmek IÇIN değerlendir işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="6a91e-140">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS OF operator to determine the type of a query expression, and then uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="6a91e-141">Sorgu, [okul modelini](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))temel alır.</span><span class="sxs-lookup"><span data-stu-id="6a91e-141">The query is based on the [School Model](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 <span data-ttu-id="6a91e-142">[! Code-SQL [DP EntityServices kavramları # TREAT_ISOF] ~/Samples/Snippets/TSQL/VS_Snippets_Data/DP entityservices kavramları/TSQL/EntitySql. SQL # treat_isof)]</span><span class="sxs-lookup"><span data-stu-id="6a91e-142">[!code-sql[DP EntityServices Concepts#TREAT_ISOF]~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#treat_isof)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a91e-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a91e-143">See also</span></span>

- [<span data-ttu-id="6a91e-144">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="6a91e-144">Entity SQL Reference</span></span>](entity-sql-reference.md)
