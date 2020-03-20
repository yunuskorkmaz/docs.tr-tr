---
title: TREAT (Varlık SQL)
ms.date: 03/30/2017
ms.assetid: 5b77f156-55de-4cb4-8154-87f707d4c635
ms.openlocfilehash: 06c4200434f443446e8981dcefe2baf43b1af4b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149901"
---
# <a name="treat-entity-sql"></a><span data-ttu-id="e91b8-102">TREAT (Varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="e91b8-102">TREAT (Entity SQL)</span></span>
<span data-ttu-id="e91b8-103">Belirli bir taban türünden bir nesneyi, belirtilen türemiş türdeki bir nesne olarak davranır.</span><span class="sxs-lookup"><span data-stu-id="e91b8-103">Treats an object of a particular base type as an object of the specified derived type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e91b8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e91b8-104">Syntax</span></span>  
  
```sql  
TREAT ( expression as type)  
```  
  
## <a name="arguments"></a><span data-ttu-id="e91b8-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="e91b8-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="e91b8-106">Varlığı döndüren geçerli bir sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="e91b8-106">Any valid query expression that returns an entity.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e91b8-107">Belirtilen ifadenin türü, belirtilen veri türünün bir alt türü veya veri türü ifade türünün bir alt türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e91b8-107">The type of the specified expression must be a subtype of the specified data type, or the data type must be a subtype of the type of expression.</span></span>  
  
 `type`  
 <span data-ttu-id="e91b8-108">Varlık türü.</span><span class="sxs-lookup"><span data-stu-id="e91b8-108">An entity type.</span></span> <span data-ttu-id="e91b8-109">Tür bir ad alanı tarafından nitelikli olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e91b8-109">The type must be qualified by a namespace.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e91b8-110">Belirtilen ifade, belirtilen veri türünün bir alt türü veya veri türü ifadenin bir alt türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e91b8-110">The specified expression must be a subtype of the specified data type, or the data type must be a subtype of the expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e91b8-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e91b8-111">Return Value</span></span>  
 <span data-ttu-id="e91b8-112">Belirtilen veri türünün değeri.</span><span class="sxs-lookup"><span data-stu-id="e91b8-112">A value of the specified data type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e91b8-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e91b8-113">Remarks</span></span>  
 <span data-ttu-id="e91b8-114">TREAT ilgili sınıflar arasında upcasting gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e91b8-114">TREAT is used to perform upcasting between related classes.</span></span> <span data-ttu-id="e91b8-115">Örneğin, `Employee` türetilir `Person` ve p türünde `Person` `TREAT(p AS NamespaceName.Employee)` ise, genel `Person` bir `Employee`örnek upcasts; yani, p olarak `Employee`tedavi etmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e91b8-115">For example, if `Employee` derives from `Person` and p is of type `Person`, `TREAT(p AS NamespaceName.Employee)` upcasts a generic `Person` instance to `Employee`; that is, it allows you to treat p as `Employee`.</span></span>  
  
 <span data-ttu-id="e91b8-116">TREAT, aşağıdaki gibi bir sorgu yapabileceğiniz devralma senaryolarında kullanılır:</span><span class="sxs-lookup"><span data-stu-id="e91b8-116">TREAT is used in inheritance scenarios where you can do a query like the following:</span></span>  
  
```sql  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)
```  
  
 <span data-ttu-id="e91b8-117">Bu sorgu, `Person` varlıkları `Employee` türe doğru yükselter.</span><span class="sxs-lookup"><span data-stu-id="e91b8-117">This query upcasts `Person` entities to the `Employee` type.</span></span> <span data-ttu-id="e91b8-118">p değeri aslında tür `Employee`değilse, ifade değeri `null`verir.</span><span class="sxs-lookup"><span data-stu-id="e91b8-118">If the value of p is not actually of type `Employee`, the expression yields the value `null`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e91b8-119">Belirtilen ifade, `Employee` belirtilen veri türünün `Person`bir alt türü veya veri türü ifadenin bir alt türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e91b8-119">The specified expression `Employee` must be a subtype of the specified data type `Person`, or the data type must be a subtype of the expression.</span></span> <span data-ttu-id="e91b8-120">Aksi takdirde, ifade derleme zamanı hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="e91b8-120">Otherwise, the expression will result in a compile-time error.</span></span>  
  
 <span data-ttu-id="e91b8-121">Aşağıdaki tablo, bazı tipik desenler ve bazı daha az yaygın desenler üzerinde tedavi davranışını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e91b8-121">The following table shows the behavior of treat over some typical patterns and some less common patterns.</span></span> <span data-ttu-id="e91b8-122">Sağlayıcı çağrılmadan önce tüm özel durumlar istemci tarafından atılır:</span><span class="sxs-lookup"><span data-stu-id="e91b8-122">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="e91b8-123">Desen</span><span class="sxs-lookup"><span data-stu-id="e91b8-123">Pattern</span></span>|<span data-ttu-id="e91b8-124">Davranış</span><span class="sxs-lookup"><span data-stu-id="e91b8-124">Behavior</span></span>|  
|-------------|--------------|  
|`TREAT (null AS EntityType)`|<span data-ttu-id="e91b8-125">`DbNull` döndürür.</span><span class="sxs-lookup"><span data-stu-id="e91b8-125">Returns `DbNull`.</span></span>|  
|`TREAT (null AS ComplexType)`|<span data-ttu-id="e91b8-126">Bir istisna atar.</span><span class="sxs-lookup"><span data-stu-id="e91b8-126">Throws an exception.</span></span>|  
|`TREAT (null AS RowType)`|<span data-ttu-id="e91b8-127">Bir özel durum atar/</span><span class="sxs-lookup"><span data-stu-id="e91b8-127">Throws an exception/</span></span>|  
|`TREAT (EntityType AS EntityType)`|<span data-ttu-id="e91b8-128">İade `EntityType` `null`veya .</span><span class="sxs-lookup"><span data-stu-id="e91b8-128">Returns `EntityType` or `null`.</span></span>|  
|`TREAT (ComplexType AS ComplexType)`|<span data-ttu-id="e91b8-129">Bir istisna atar.</span><span class="sxs-lookup"><span data-stu-id="e91b8-129">Throws an exception.</span></span>|  
|`TREAT (RowType AS RowType)`|<span data-ttu-id="e91b8-130">Bir istisna atar.</span><span class="sxs-lookup"><span data-stu-id="e91b8-130">Throws an exception.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e91b8-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="e91b8-131">Example</span></span>  
 <span data-ttu-id="e91b8-132">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, Kurs türündeki bir nesneyi Yerinde Kurs türündeki nesneler koleksiyonuna dönüştürmek için TREAT işleci kullanır.</span><span class="sxs-lookup"><span data-stu-id="e91b8-132">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="e91b8-133">Sorgu [Okul Modeli'ni](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))temel alın.</span><span class="sxs-lookup"><span data-stu-id="e91b8-133">The query is based on the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 [!code-sql[DP EntityServices Concepts#TREAT_ISOF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#treat_isof)]  
  
## <a name="see-also"></a><span data-ttu-id="e91b8-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e91b8-134">See also</span></span>

- [<span data-ttu-id="e91b8-135">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="e91b8-135">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="e91b8-136">Null Değer Atanabilir Yapılandırılmış Türler</span><span class="sxs-lookup"><span data-stu-id="e91b8-136">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
