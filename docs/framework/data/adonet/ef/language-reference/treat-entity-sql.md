---
title: IŞLE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b77f156-55de-4cb4-8154-87f707d4c635
ms.openlocfilehash: 38099fa83ed78b40d46faeb5e617157f7aa7c1a1
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319256"
---
# <a name="treat-entity-sql"></a><span data-ttu-id="fb1f9-102">IŞLE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="fb1f9-102">TREAT (Entity SQL)</span></span>
<span data-ttu-id="fb1f9-103">Belirli bir temel türdeki bir nesneyi belirtilen türetilmiş türün bir nesnesi olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="fb1f9-103">Treats an object of a particular base type as an object of the specified derived type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb1f9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fb1f9-104">Syntax</span></span>  
  
```sql  
TREAT ( expression as type)  
```  
  
## <a name="arguments"></a><span data-ttu-id="fb1f9-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="fb1f9-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="fb1f9-106">Bir varlık döndüren geçerli bir sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="fb1f9-106">Any valid query expression that returns an entity.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fb1f9-107">Belirtilen ifadenin türü, belirtilen veri türünün bir alt türü olmalıdır veya veri türü, ifadenin türünün bir alt türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fb1f9-107">The type of the specified expression must be a subtype of the specified data type, or the data type must be a subtype of the type of expression.</span></span>  
  
 `type`  
 <span data-ttu-id="fb1f9-108">Bir varlık türü.</span><span class="sxs-lookup"><span data-stu-id="fb1f9-108">An entity type.</span></span> <span data-ttu-id="fb1f9-109">Tür bir ad alanı tarafından nitelenmelidir.</span><span class="sxs-lookup"><span data-stu-id="fb1f9-109">The type must be qualified by a namespace.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fb1f9-110">Belirtilen ifade, belirtilen veri türünün bir alt türü olmalıdır veya veri türü ifadenin bir alt türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fb1f9-110">The specified expression must be a subtype of the specified data type, or the data type must be a subtype of the expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fb1f9-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fb1f9-111">Return Value</span></span>  
 <span data-ttu-id="fb1f9-112">Belirtilen veri türünde bir değer.</span><span class="sxs-lookup"><span data-stu-id="fb1f9-112">A value of the specified data type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb1f9-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fb1f9-113">Remarks</span></span>  
 <span data-ttu-id="fb1f9-114">IŞLE ilgili sınıflar arasında yukarı atama gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fb1f9-114">TREAT is used to perform upcasting between related classes.</span></span> <span data-ttu-id="fb1f9-115">Örneğin, `Employee` `Person` ' den türetilse ve p `Person` türündedir, `TREAT(p AS NamespaceName.Employee)` bir genel `Person` örneğini `Employee` ' e aktarır; Yani, p 'yi `Employee` olarak değerlendirmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="fb1f9-115">For example, if `Employee` derives from `Person` and p is of type `Person`, `TREAT(p AS NamespaceName.Employee)` upcasts a generic `Person` instance to `Employee`; that is, it allows you to treat p as `Employee`.</span></span>  
  
 <span data-ttu-id="fb1f9-116">DEĞERLENDIR, aşağıdaki gibi bir sorgu yapabileceğiniz devralma senaryolarında kullanılır:</span><span class="sxs-lookup"><span data-stu-id="fb1f9-116">TREAT is used in inheritance scenarios where you can do a query like the following:</span></span>  
  
```sql  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)   
```  
  
 <span data-ttu-id="fb1f9-117">Bu sorgu `Person` varlıklarını `Employee` türüne yukarı aktarır.</span><span class="sxs-lookup"><span data-stu-id="fb1f9-117">This query upcasts `Person` entities to the `Employee` type.</span></span> <span data-ttu-id="fb1f9-118">P değeri gerçekten `Employee` türünde değilse, ifade `null` değerini verir.</span><span class="sxs-lookup"><span data-stu-id="fb1f9-118">If the value of p is not actually of type `Employee`, the expression yields the value `null`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fb1f9-119">@No__t-0 belirtilen ifadesi belirtilen veri türünün bir alt türü olmalıdır `Person` veya veri türü ifadenin bir alt türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fb1f9-119">The specified expression `Employee` must be a subtype of the specified data type `Person`, or the data type must be a subtype of the expression.</span></span> <span data-ttu-id="fb1f9-120">Aksi takdirde, ifade derleme zamanı hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="fb1f9-120">Otherwise, the expression will result in a compile-time error.</span></span>  
  
 <span data-ttu-id="fb1f9-121">Aşağıdaki tabloda, bazı tipik desenler ve bazı daha az ortak desenler üzerinde işleme davranışı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fb1f9-121">The following table shows the behavior of treat over some typical patterns and some less common patterns.</span></span> <span data-ttu-id="fb1f9-122">Sağlayıcı çağrılmadan önce istemci tarafında tüm özel durumlar atılır:</span><span class="sxs-lookup"><span data-stu-id="fb1f9-122">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="fb1f9-123">Desen</span><span class="sxs-lookup"><span data-stu-id="fb1f9-123">Pattern</span></span>|<span data-ttu-id="fb1f9-124">Davranış</span><span class="sxs-lookup"><span data-stu-id="fb1f9-124">Behavior</span></span>|  
|-------------|--------------|  
|`TREAT (null AS EntityType)`|<span data-ttu-id="fb1f9-125">@No__t-0 döndürür.</span><span class="sxs-lookup"><span data-stu-id="fb1f9-125">Returns `DbNull`.</span></span>|  
|`TREAT (null AS ComplexType)`|<span data-ttu-id="fb1f9-126">Bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fb1f9-126">Throws an exception.</span></span>|  
|`TREAT (null AS RowType)`|<span data-ttu-id="fb1f9-127">Bir özel durum oluşturur/</span><span class="sxs-lookup"><span data-stu-id="fb1f9-127">Throws an exception/</span></span>|  
|`TREAT (EntityType AS EntityType)`|<span data-ttu-id="fb1f9-128">@No__t-0 veya `null` döndürür.</span><span class="sxs-lookup"><span data-stu-id="fb1f9-128">Returns `EntityType` or `null`.</span></span>|  
|`TREAT (ComplexType AS ComplexType)`|<span data-ttu-id="fb1f9-129">Bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fb1f9-129">Throws an exception.</span></span>|  
|`TREAT (RowType AS RowType)`|<span data-ttu-id="fb1f9-130">Bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fb1f9-130">Throws an exception.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fb1f9-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="fb1f9-131">Example</span></span>  
 <span data-ttu-id="fb1f9-132">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgusu, bir nesne türünün bir nesnesini Onsitekurs türünde bir nesne koleksiyonuna dönüştürmek için DEĞERLENDIR işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="fb1f9-132">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="fb1f9-133">Sorgu, [okul modelini](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))temel alır.</span><span class="sxs-lookup"><span data-stu-id="fb1f9-133">The query is based on the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 [!code-sql[DP EntityServices Concepts#TREAT_ISOF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#treat_isof)]  
  
## <a name="see-also"></a><span data-ttu-id="fb1f9-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb1f9-134">See also</span></span>

- [<span data-ttu-id="fb1f9-135">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="fb1f9-135">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="fb1f9-136">Null Değer Atanabilir Yapılandırılmış Türler</span><span class="sxs-lookup"><span data-stu-id="fb1f9-136">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
