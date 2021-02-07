---
description: ': DEĞERLENDIR (Entity SQL) hakkında daha fazla bilgi'
title: IŞLE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b77f156-55de-4cb4-8154-87f707d4c635
ms.openlocfilehash: 3f014cac631d246b35d145cdb80c9aa6ac401524
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673433"
---
# <a name="treat-entity-sql"></a><span data-ttu-id="c426a-103">IŞLE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c426a-103">TREAT (Entity SQL)</span></span>

<span data-ttu-id="c426a-104">Belirli bir temel türdeki bir nesneyi belirtilen türetilmiş türün bir nesnesi olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="c426a-104">Treats an object of a particular base type as an object of the specified derived type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c426a-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c426a-105">Syntax</span></span>  
  
```sql  
TREAT ( expression as type)  
```  
  
## <a name="arguments"></a><span data-ttu-id="c426a-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="c426a-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="c426a-107">Bir varlık döndüren geçerli bir sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="c426a-107">Any valid query expression that returns an entity.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c426a-108">Belirtilen ifadenin türü, belirtilen veri türünün bir alt türü olmalıdır veya veri türü, ifadenin türünün bir alt türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c426a-108">The type of the specified expression must be a subtype of the specified data type, or the data type must be a subtype of the type of expression.</span></span>  
  
 `type`  
 <span data-ttu-id="c426a-109">Bir varlık türü.</span><span class="sxs-lookup"><span data-stu-id="c426a-109">An entity type.</span></span> <span data-ttu-id="c426a-110">Tür bir ad alanı tarafından nitelenmelidir.</span><span class="sxs-lookup"><span data-stu-id="c426a-110">The type must be qualified by a namespace.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c426a-111">Belirtilen ifade, belirtilen veri türünün bir alt türü olmalıdır veya veri türü ifadenin bir alt türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c426a-111">The specified expression must be a subtype of the specified data type, or the data type must be a subtype of the expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c426a-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c426a-112">Return Value</span></span>  

 <span data-ttu-id="c426a-113">Belirtilen veri türünde bir değer.</span><span class="sxs-lookup"><span data-stu-id="c426a-113">A value of the specified data type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c426a-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c426a-114">Remarks</span></span>  

 <span data-ttu-id="c426a-115">IŞLE ilgili sınıflar arasında yukarı atama gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c426a-115">TREAT is used to perform upcasting between related classes.</span></span> <span data-ttu-id="c426a-116">Örneğin, `Employee` ve p türünden türetürse `Person` `Person` , `TREAT(p AS NamespaceName.Employee)` genel bir örneği ' a aktarır `Person` `Employee` ; Yani, p 'yi kabul etmenizi sağlar `Employee` .</span><span class="sxs-lookup"><span data-stu-id="c426a-116">For example, if `Employee` derives from `Person` and p is of type `Person`, `TREAT(p AS NamespaceName.Employee)` upcasts a generic `Person` instance to `Employee`; that is, it allows you to treat p as `Employee`.</span></span>  
  
 <span data-ttu-id="c426a-117">DEĞERLENDIR, aşağıdaki gibi bir sorgu yapabileceğiniz devralma senaryolarında kullanılır:</span><span class="sxs-lookup"><span data-stu-id="c426a-117">TREAT is used in inheritance scenarios where you can do a query like the following:</span></span>  
  
```sql  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)
```  
  
 <span data-ttu-id="c426a-118">Bu sorgu `Person` , varlıkları `Employee` türüne aktarır.</span><span class="sxs-lookup"><span data-stu-id="c426a-118">This query upcasts `Person` entities to the `Employee` type.</span></span> <span data-ttu-id="c426a-119">P değeri gerçekten tür değilse `Employee` , ifade değeri verir `null` .</span><span class="sxs-lookup"><span data-stu-id="c426a-119">If the value of p is not actually of type `Employee`, the expression yields the value `null`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c426a-120">Belirtilen ifade, `Employee` belirtilen veri türünün bir alt türü olmalıdır `Person` veya veri türü ifadenin bir alt türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c426a-120">The specified expression `Employee` must be a subtype of the specified data type `Person`, or the data type must be a subtype of the expression.</span></span> <span data-ttu-id="c426a-121">Aksi takdirde, ifade derleme zamanı hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="c426a-121">Otherwise, the expression will result in a compile-time error.</span></span>  
  
 <span data-ttu-id="c426a-122">Aşağıdaki tabloda, bazı tipik desenler ve bazı daha az ortak desenler üzerinde işleme davranışı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c426a-122">The following table shows the behavior of treat over some typical patterns and some less common patterns.</span></span> <span data-ttu-id="c426a-123">Sağlayıcı çağrılmadan önce istemci tarafında tüm özel durumlar atılır:</span><span class="sxs-lookup"><span data-stu-id="c426a-123">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="c426a-124">Desen</span><span class="sxs-lookup"><span data-stu-id="c426a-124">Pattern</span></span>|<span data-ttu-id="c426a-125">Davranış</span><span class="sxs-lookup"><span data-stu-id="c426a-125">Behavior</span></span>|  
|-------------|--------------|  
|`TREAT (null AS EntityType)`|<span data-ttu-id="c426a-126">`DbNull` döndürür.</span><span class="sxs-lookup"><span data-stu-id="c426a-126">Returns `DbNull`.</span></span>|  
|`TREAT (null AS ComplexType)`|<span data-ttu-id="c426a-127">Bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c426a-127">Throws an exception.</span></span>|  
|`TREAT (null AS RowType)`|<span data-ttu-id="c426a-128">Bir özel durum oluşturur/</span><span class="sxs-lookup"><span data-stu-id="c426a-128">Throws an exception/</span></span>|  
|`TREAT (EntityType AS EntityType)`|<span data-ttu-id="c426a-129">`EntityType`Veya döndürür `null` .</span><span class="sxs-lookup"><span data-stu-id="c426a-129">Returns `EntityType` or `null`.</span></span>|  
|`TREAT (ComplexType AS ComplexType)`|<span data-ttu-id="c426a-130">Bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c426a-130">Throws an exception.</span></span>|  
|`TREAT (RowType AS RowType)`|<span data-ttu-id="c426a-131">Bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c426a-131">Throws an exception.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c426a-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="c426a-132">Example</span></span>  

 <span data-ttu-id="c426a-133">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, bir nesne türünü Onsitekurs türünde bir nesne koleksiyonuna dönüştürmek IÇIN değerlendir işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c426a-133">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="c426a-134">Sorgu, [okul modelini](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))temel alır.</span><span class="sxs-lookup"><span data-stu-id="c426a-134">The query is based on the [School Model](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 [!code-sql[DP EntityServices Concepts#TREAT_ISOF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#treat_isof)]  
  
## <a name="see-also"></a><span data-ttu-id="c426a-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c426a-135">See also</span></span>

- [<span data-ttu-id="c426a-136">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="c426a-136">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="c426a-137">Null Değer Atanabilir Yapılandırılmış Türler</span><span class="sxs-lookup"><span data-stu-id="c426a-137">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
