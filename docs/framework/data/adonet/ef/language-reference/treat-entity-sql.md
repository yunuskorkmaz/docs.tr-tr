---
title: IŞLE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b77f156-55de-4cb4-8154-87f707d4c635
ms.openlocfilehash: 566ac875aec17e4d0aa22ec1962053aeb6ae2a2e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558855"
---
# <a name="treat-entity-sql"></a><span data-ttu-id="a0909-102">IŞLE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a0909-102">TREAT (Entity SQL)</span></span>
<span data-ttu-id="a0909-103">Belirli bir temel türdeki bir nesneyi belirtilen türetilmiş türün bir nesnesi olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="a0909-103">Treats an object of a particular base type as an object of the specified derived type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0909-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a0909-104">Syntax</span></span>  
  
```sql  
TREAT ( expression as type)  
```  
  
## <a name="arguments"></a><span data-ttu-id="a0909-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="a0909-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="a0909-106">Bir varlık döndüren geçerli bir sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="a0909-106">Any valid query expression that returns an entity.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a0909-107">Belirtilen ifadenin türü, belirtilen veri türünün bir alt türü olmalıdır veya veri türü, ifadenin türünün bir alt türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a0909-107">The type of the specified expression must be a subtype of the specified data type, or the data type must be a subtype of the type of expression.</span></span>  
  
 `type`  
 <span data-ttu-id="a0909-108">Bir varlık türü.</span><span class="sxs-lookup"><span data-stu-id="a0909-108">An entity type.</span></span> <span data-ttu-id="a0909-109">Tür bir ad alanı tarafından nitelenmelidir.</span><span class="sxs-lookup"><span data-stu-id="a0909-109">The type must be qualified by a namespace.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a0909-110">Belirtilen ifade, belirtilen veri türünün bir alt türü olmalıdır veya veri türü ifadenin bir alt türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a0909-110">The specified expression must be a subtype of the specified data type, or the data type must be a subtype of the expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a0909-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a0909-111">Return Value</span></span>  
 <span data-ttu-id="a0909-112">Belirtilen veri türünde bir değer.</span><span class="sxs-lookup"><span data-stu-id="a0909-112">A value of the specified data type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0909-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a0909-113">Remarks</span></span>  
 <span data-ttu-id="a0909-114">IŞLE ilgili sınıflar arasında yukarı atama gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a0909-114">TREAT is used to perform upcasting between related classes.</span></span> <span data-ttu-id="a0909-115">Örneğin, `Employee` ve p türünden türetürse `Person` `Person` , `TREAT(p AS NamespaceName.Employee)` genel bir örneği ' a aktarır `Person` `Employee` ; Yani, p 'yi kabul etmenizi sağlar `Employee` .</span><span class="sxs-lookup"><span data-stu-id="a0909-115">For example, if `Employee` derives from `Person` and p is of type `Person`, `TREAT(p AS NamespaceName.Employee)` upcasts a generic `Person` instance to `Employee`; that is, it allows you to treat p as `Employee`.</span></span>  
  
 <span data-ttu-id="a0909-116">DEĞERLENDIR, aşağıdaki gibi bir sorgu yapabileceğiniz devralma senaryolarında kullanılır:</span><span class="sxs-lookup"><span data-stu-id="a0909-116">TREAT is used in inheritance scenarios where you can do a query like the following:</span></span>  
  
```sql  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)
```  
  
 <span data-ttu-id="a0909-117">Bu sorgu `Person` , varlıkları `Employee` türüne aktarır.</span><span class="sxs-lookup"><span data-stu-id="a0909-117">This query upcasts `Person` entities to the `Employee` type.</span></span> <span data-ttu-id="a0909-118">P değeri gerçekten tür değilse `Employee` , ifade değeri verir `null` .</span><span class="sxs-lookup"><span data-stu-id="a0909-118">If the value of p is not actually of type `Employee`, the expression yields the value `null`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a0909-119">Belirtilen ifade, `Employee` belirtilen veri türünün bir alt türü olmalıdır `Person` veya veri türü ifadenin bir alt türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a0909-119">The specified expression `Employee` must be a subtype of the specified data type `Person`, or the data type must be a subtype of the expression.</span></span> <span data-ttu-id="a0909-120">Aksi takdirde, ifade derleme zamanı hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="a0909-120">Otherwise, the expression will result in a compile-time error.</span></span>  
  
 <span data-ttu-id="a0909-121">Aşağıdaki tabloda, bazı tipik desenler ve bazı daha az ortak desenler üzerinde işleme davranışı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a0909-121">The following table shows the behavior of treat over some typical patterns and some less common patterns.</span></span> <span data-ttu-id="a0909-122">Sağlayıcı çağrılmadan önce istemci tarafında tüm özel durumlar atılır:</span><span class="sxs-lookup"><span data-stu-id="a0909-122">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="a0909-123">Desen</span><span class="sxs-lookup"><span data-stu-id="a0909-123">Pattern</span></span>|<span data-ttu-id="a0909-124">Davranış</span><span class="sxs-lookup"><span data-stu-id="a0909-124">Behavior</span></span>|  
|-------------|--------------|  
|`TREAT (null AS EntityType)`|<span data-ttu-id="a0909-125">`DbNull` döndürür.</span><span class="sxs-lookup"><span data-stu-id="a0909-125">Returns `DbNull`.</span></span>|  
|`TREAT (null AS ComplexType)`|<span data-ttu-id="a0909-126">Bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a0909-126">Throws an exception.</span></span>|  
|`TREAT (null AS RowType)`|<span data-ttu-id="a0909-127">Bir özel durum oluşturur/</span><span class="sxs-lookup"><span data-stu-id="a0909-127">Throws an exception/</span></span>|  
|`TREAT (EntityType AS EntityType)`|<span data-ttu-id="a0909-128">`EntityType`Veya döndürür `null` .</span><span class="sxs-lookup"><span data-stu-id="a0909-128">Returns `EntityType` or `null`.</span></span>|  
|`TREAT (ComplexType AS ComplexType)`|<span data-ttu-id="a0909-129">Bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a0909-129">Throws an exception.</span></span>|  
|`TREAT (RowType AS RowType)`|<span data-ttu-id="a0909-130">Bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a0909-130">Throws an exception.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a0909-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="a0909-131">Example</span></span>  
 <span data-ttu-id="a0909-132">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, bir nesne türünü Onsitekurs türünde bir nesne koleksiyonuna dönüştürmek IÇIN değerlendir işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a0909-132">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="a0909-133">Sorgu, [okul modelini](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))temel alır.</span><span class="sxs-lookup"><span data-stu-id="a0909-133">The query is based on the [School Model](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 [!code-sql[DP EntityServices Concepts#TREAT_ISOF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#treat_isof)]  
  
## <a name="see-also"></a><span data-ttu-id="a0909-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0909-134">See also</span></span>

- [<span data-ttu-id="a0909-135">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="a0909-135">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="a0909-136">Null Değer Atanabilir Yapılandırılmış Türler</span><span class="sxs-lookup"><span data-stu-id="a0909-136">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
