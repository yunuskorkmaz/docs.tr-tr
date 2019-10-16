---
title: IOF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
ms.openlocfilehash: c4c4cbf74cb17cf43e79c42ff42d1e68122fd534
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319713"
---
# <a name="isof-entity-sql"></a><span data-ttu-id="2fc07-102">IOF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="2fc07-102">ISOF (Entity SQL)</span></span>
<span data-ttu-id="2fc07-103">Bir ifadenin türünün belirtilen türde mi yoksa alt türlerinden biri mi olduğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="2fc07-103">Determines whether the type of an expression is of the specified type or one of its subtypes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fc07-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2fc07-104">Syntax</span></span>  
  
```sql  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="2fc07-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="2fc07-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="2fc07-106">Türünü belirleyecek geçerli bir sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="2fc07-106">Any valid query expression to determine the type of.</span></span>  
  
 <span data-ttu-id="2fc07-107">BAŞLATıLMADı</span><span class="sxs-lookup"><span data-stu-id="2fc07-107">NOT</span></span>  
 <span data-ttu-id="2fc07-108">EDM 'yi geçersiz kılar. ' Nin Boolean sonucu.</span><span class="sxs-lookup"><span data-stu-id="2fc07-108">Negates the EDM.Boolean result of IS OF.</span></span>  
  
 <span data-ttu-id="2fc07-109">YALNıZCA</span><span class="sxs-lookup"><span data-stu-id="2fc07-109">ONLY</span></span>  
 <span data-ttu-id="2fc07-110">@No__t-0 ' ın, yalnızca `expression` ' in `type` tipinde olması ve alt türlerinden herhangi biri olmaması durumunda olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2fc07-110">Specifies that IS OF returns `true` only if `expression` is of type `type` and not any of one its subtypes.</span></span>  
  
 `type`  
 <span data-ttu-id="2fc07-111">@No__t-0 ' dan test edilecek tür.</span><span class="sxs-lookup"><span data-stu-id="2fc07-111">The type to test `expression` against.</span></span> <span data-ttu-id="2fc07-112">Tür ad alanı nitelenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2fc07-112">The type must be namespace-qualified.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2fc07-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2fc07-113">Return Value</span></span>  
 <span data-ttu-id="2fc07-114">@no__t `expression`, T türünde ise ve T bir temel tür ya da türetilmiş bir tür `type`; çalışma zamanında `expression` null ise null; Aksi takdirde, @no__t 4.</span><span class="sxs-lookup"><span data-stu-id="2fc07-114">`true` if `expression` is of type T and T is either a base type, or a derived type of `type`; null if `expression` is null at runtime; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2fc07-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2fc07-115">Remarks</span></span>  
 <span data-ttu-id="2fc07-116">@No__t-0 ve `expression IS NOT OF (ONLY type)` ifadeleri sırasıyla `NOT (expression IS OF (type))` ve `NOT (expression IS OF (ONLY type))` ile eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="2fc07-116">The expressions `expression IS NOT OF (type)` and `expression IS NOT OF (ONLY type)` are syntactically equivalent to `NOT (expression IS OF (type))` and `NOT (expression IS OF (ONLY type))`, respectively.</span></span>  
  
 <span data-ttu-id="2fc07-117">Aşağıdaki tabloda, bazı tipik ve köşe desenleri üzerinde `IS OF` işlecinin davranışı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2fc07-117">The following table shows the behavior of `IS OF` operator over some typical- and corner patterns.</span></span> <span data-ttu-id="2fc07-118">Sağlayıcı çağrılmadan önce istemci tarafında tüm özel durumlar atılır:</span><span class="sxs-lookup"><span data-stu-id="2fc07-118">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="2fc07-119">Desen</span><span class="sxs-lookup"><span data-stu-id="2fc07-119">Pattern</span></span>|<span data-ttu-id="2fc07-120">Davranış</span><span class="sxs-lookup"><span data-stu-id="2fc07-120">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="2fc07-121">null (EntityType)</span><span class="sxs-lookup"><span data-stu-id="2fc07-121">null IS OF (EntityType)</span></span>|<span data-ttu-id="2fc07-122">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="2fc07-122">Throws</span></span>|  
|<span data-ttu-id="2fc07-123">null (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="2fc07-123">null IS OF (ComplexType)</span></span>|<span data-ttu-id="2fc07-124">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="2fc07-124">Throws</span></span>|  
|<span data-ttu-id="2fc07-125">null (RowType)</span><span class="sxs-lookup"><span data-stu-id="2fc07-125">null IS OF (RowType)</span></span>|<span data-ttu-id="2fc07-126">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="2fc07-126">Throws</span></span>|  
|<span data-ttu-id="2fc07-127">DAVRAN (EntityType olarak null), (EntityType)</span><span class="sxs-lookup"><span data-stu-id="2fc07-127">TREAT (null AS EntityType) IS OF (EntityType)</span></span>|<span data-ttu-id="2fc07-128">DBNull döndürür</span><span class="sxs-lookup"><span data-stu-id="2fc07-128">Returns DBNull</span></span>|  
|<span data-ttu-id="2fc07-129">DAVRAN (ComplexType olarak null), (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="2fc07-129">TREAT (null AS ComplexType) IS OF (ComplexType)</span></span>|<span data-ttu-id="2fc07-130">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="2fc07-130">Throws</span></span>|  
|<span data-ttu-id="2fc07-131">DEĞERLENDIR (RowType olarak null), (RowType)</span><span class="sxs-lookup"><span data-stu-id="2fc07-131">TREAT (null AS RowType) IS OF (RowType)</span></span>|<span data-ttu-id="2fc07-132">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="2fc07-132">Throws</span></span>|  
|<span data-ttu-id="2fc07-133">EntityType (EntityType)</span><span class="sxs-lookup"><span data-stu-id="2fc07-133">EntityType IS OF (EntityType)</span></span>|<span data-ttu-id="2fc07-134">True/false döndürür</span><span class="sxs-lookup"><span data-stu-id="2fc07-134">Returns true/false</span></span>|  
|<span data-ttu-id="2fc07-135">ComplexType (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="2fc07-135">ComplexType IS OF (ComplexType)</span></span>|<span data-ttu-id="2fc07-136">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="2fc07-136">Throws</span></span>|  
|<span data-ttu-id="2fc07-137">RowType, (RowType)</span><span class="sxs-lookup"><span data-stu-id="2fc07-137">RowType IS OF (RowType)</span></span>|<span data-ttu-id="2fc07-138">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="2fc07-138">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2fc07-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="2fc07-139">Example</span></span>  
 <span data-ttu-id="2fc07-140">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgusu, bir sorgu ifadesinin türünü tespit etmek için işleç ' i kullanır ve ardından bir nesneyi, bir nesne türünü Onsitekurs türünde bir nesne koleksiyonuna dönüştürmek için DEĞERLENDIR işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2fc07-140">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS OF operator to determine the type of a query expression, and then uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="2fc07-141">Sorgu, [okul modelini](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))temel alır.</span><span class="sxs-lookup"><span data-stu-id="2fc07-141">The query is based on the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 <span data-ttu-id="2fc07-142">[! Code-SQL [DP EntityServices kavramları # TREAT_ISOF] ~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices kavramları/TSQL/EntitySql. SQL # TREAT_ISOF)]</span><span class="sxs-lookup"><span data-stu-id="2fc07-142">[!code-sql[DP EntityServices Concepts#TREAT_ISOF]~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#treat_isof)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fc07-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2fc07-143">See also</span></span>

- [<span data-ttu-id="2fc07-144">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="2fc07-144">Entity SQL Reference</span></span>](entity-sql-reference.md)
