---
title: KABUL (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 5b77f156-55de-4cb4-8154-87f707d4c635
ms.openlocfilehash: e1382c4daa513477011a1d1c2132840dfae84de0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879573"
---
# <a name="treat-entity-sql"></a><span data-ttu-id="17bd5-102">KABUL (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="17bd5-102">TREAT (Entity SQL)</span></span>
<span data-ttu-id="17bd5-103">Belirli bir temel türü bir nesneyi belirtilen türetilmiş bir türde bir nesne olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="17bd5-103">Treats an object of a particular base type as an object of the specified derived type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17bd5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="17bd5-104">Syntax</span></span>  
  
```  
TREAT ( expression as type)  
```  
  
## <a name="arguments"></a><span data-ttu-id="17bd5-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="17bd5-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="17bd5-106">Bir varlık döndürür herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="17bd5-106">Any valid query expression that returns an entity.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="17bd5-107">Belirtilen ifadenin belirtilen veri türünün bir alt türünde olmalıdır veya veri türü bir alt ifadenin türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="17bd5-107">The type of the specified expression must be a subtype of the specified data type, or the data type must be a subtype of the type of expression.</span></span>  
  
 `type`  
 <span data-ttu-id="17bd5-108">Bir varlık türü.</span><span class="sxs-lookup"><span data-stu-id="17bd5-108">An entity type.</span></span> <span data-ttu-id="17bd5-109">Türü bir ad alanı tarafından nitelendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="17bd5-109">The type must be qualified by a namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="17bd5-110">Belirtilen ifade belirtilen veri türünün bir alt türü olmalıdır veya bir alt ifadenin veri türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="17bd5-110">The specified expression must be a subtype of the specified data type, or the data type must be a subtype of the expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="17bd5-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="17bd5-111">Return Value</span></span>  
 <span data-ttu-id="17bd5-112">Belirtilen veri türünde bir değer.</span><span class="sxs-lookup"><span data-stu-id="17bd5-112">A value of the specified data type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17bd5-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="17bd5-113">Remarks</span></span>  
 <span data-ttu-id="17bd5-114">KABUL ilgili sınıflar arasında yukarı çevrim gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="17bd5-114">TREAT is used to perform upcasting between related classes.</span></span> <span data-ttu-id="17bd5-115">Örneğin, varsa `Employee` türetildiği `Person` ve p türünü `Person`, `TREAT(p AS NamespaceName.Employee)` upcasts genel bir `Person` için örnek `Employee`; diğer bir deyişle, p değerlendirilecek tanır `Employee`.</span><span class="sxs-lookup"><span data-stu-id="17bd5-115">For example, if `Employee` derives from `Person` and p is of type `Person`, `TREAT(p AS NamespaceName.Employee)` upcasts a generic `Person` instance to `Employee`; that is, it allows you to treat p as `Employee`.</span></span>  
  
 <span data-ttu-id="17bd5-116">KABUL burada aşağıdaki gibi bir sorguda yapabileceğiniz devralma senaryolarda kullanılır:</span><span class="sxs-lookup"><span data-stu-id="17bd5-116">TREAT is used in inheritance scenarios where you can do a query like the following:</span></span>  
  
```  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)   
```  
  
 <span data-ttu-id="17bd5-117">Bu sorgu upcasts `Person` varlıklara `Employee` türü.</span><span class="sxs-lookup"><span data-stu-id="17bd5-117">This query upcasts `Person` entities to the `Employee` type.</span></span> <span data-ttu-id="17bd5-118">P değerini değil gerçekten türde ise `Employee`, ifade değerini verir `null`.</span><span class="sxs-lookup"><span data-stu-id="17bd5-118">If the value of p is not actually of type `Employee`, the expression yields the value `null`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="17bd5-119">Belirtilen ifade `Employee` belirtilen veri türünün bir alt türü olmalıdır `Person`, veya bir alt ifadenin veri türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="17bd5-119">The specified expression `Employee` must be a subtype of the specified data type `Person`, or the data type must be a subtype of the expression.</span></span> <span data-ttu-id="17bd5-120">Aksi takdirde, ifadeyi bir derleme zamanı hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="17bd5-120">Otherwise, the expression will result in a compile-time error.</span></span>  
  
 <span data-ttu-id="17bd5-121">Aşağıdaki tabloda, bazı tipik desenleri ve daha az yaygın olan bazı desenleri üzerinden kabul davranışını gösterir.</span><span class="sxs-lookup"><span data-stu-id="17bd5-121">The following table shows the behavior of treat over some typical patterns and some less common patterns.</span></span> <span data-ttu-id="17bd5-122">Sağlayıcı çağrılır önce tüm istemci tarafında özel durumlar:</span><span class="sxs-lookup"><span data-stu-id="17bd5-122">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="17bd5-123">Desen</span><span class="sxs-lookup"><span data-stu-id="17bd5-123">Pattern</span></span>|<span data-ttu-id="17bd5-124">Davranış</span><span class="sxs-lookup"><span data-stu-id="17bd5-124">Behavior</span></span>|  
|-------------|--------------|  
|`TREAT (null AS EntityType)`|<span data-ttu-id="17bd5-125">Döndürür `DbNull`.</span><span class="sxs-lookup"><span data-stu-id="17bd5-125">Returns `DbNull`.</span></span>|  
|`TREAT (null AS ComplexType)`|<span data-ttu-id="17bd5-126">Özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="17bd5-126">Throws an exception.</span></span>|  
|`TREAT (null AS RowType)`|<span data-ttu-id="17bd5-127">Bir özel durum oluşturur /</span><span class="sxs-lookup"><span data-stu-id="17bd5-127">Throws an exception/</span></span>|  
|`TREAT (EntityType AS EntityType)`|<span data-ttu-id="17bd5-128">Döndürür `EntityType` veya `null`.</span><span class="sxs-lookup"><span data-stu-id="17bd5-128">Returns `EntityType` or `null`.</span></span>|  
|`TREAT (ComplexType AS ComplexType)`|<span data-ttu-id="17bd5-129">Özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="17bd5-129">Throws an exception.</span></span>|  
|`TREAT (RowType AS RowType)`|<span data-ttu-id="17bd5-130">Özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="17bd5-130">Throws an exception.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="17bd5-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="17bd5-131">Example</span></span>  
 <span data-ttu-id="17bd5-132">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu OnsiteCourse türünden nesnelerin bir koleksiyonunu kurs türdeki bir nesneyi dönüştürmek için kabul işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="17bd5-132">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="17bd5-133">Sorgu dayanır [Okul modeli](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="17bd5-133">The query is based on the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## <a name="see-also"></a><span data-ttu-id="17bd5-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17bd5-134">See also</span></span>

- [<span data-ttu-id="17bd5-135">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="17bd5-135">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="17bd5-136">Null Değer Atanabilir Yapılandırılmış Türler</span><span class="sxs-lookup"><span data-stu-id="17bd5-136">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
