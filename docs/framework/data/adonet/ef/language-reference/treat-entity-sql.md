---
title: "KABUL (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b77f156-55de-4cb4-8154-87f707d4c635
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: c386016eebf4571399aa55a261c1225146df8ccd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="treat-entity-sql"></a><span data-ttu-id="41ea0-102">KABUL (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="41ea0-102">TREAT (Entity SQL)</span></span>
<span data-ttu-id="41ea0-103">Belirli bir temel türdeki bir nesneyi belirtilen türetilen türde bir nesne olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="41ea0-103">Treats an object of a particular base type as an object of the specified derived type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41ea0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="41ea0-104">Syntax</span></span>  
  
```  
TREAT ( expression as type)  
```  
  
## <a name="arguments"></a><span data-ttu-id="41ea0-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="41ea0-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="41ea0-106">Bir varlık döndüren herhangi bir geçerli sorgu ifade.</span><span class="sxs-lookup"><span data-stu-id="41ea0-106">Any valid query expression that returns an entity.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="41ea0-107">Belirtilen ifade türü bir alt belirtilen veri türü olmalıdır veya veri türünün bir alt tür bir ifade olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="41ea0-107">The type of the specified expression must be a subtype of the specified data type, or the data type must be a subtype of the type of expression.</span></span>  
  
 `type`  
 <span data-ttu-id="41ea0-108">Bir varlık türü.</span><span class="sxs-lookup"><span data-stu-id="41ea0-108">An entity type.</span></span> <span data-ttu-id="41ea0-109">Türü bir ad alanı tarafından nitelenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="41ea0-109">The type must be qualified by a namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="41ea0-110">Belirtilen ifade belirtilen veri türünün bir alt olmalıdır veya alt ifade türünün veri türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="41ea0-110">The specified expression must be a subtype of the specified data type, or the data type must be a subtype of the expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="41ea0-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="41ea0-111">Return Value</span></span>  
 <span data-ttu-id="41ea0-112">Belirtilen veri türünde bir değer.</span><span class="sxs-lookup"><span data-stu-id="41ea0-112">A value of the specified data type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41ea0-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="41ea0-113">Remarks</span></span>  
 <span data-ttu-id="41ea0-114">KABUL üst türe çevirme ilgili sınıflar arasındaki gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="41ea0-114">TREAT is used to perform upcasting between related classes.</span></span> <span data-ttu-id="41ea0-115">Örneğin, varsa `Employee` türetilen `Person` ve p türü `Person`, `TREAT(p AS NamespaceName.Employee)` upcasts genel bir `Person` için örnek `Employee`; diğer bir deyişle, p davranmanız tanır `Employee`.</span><span class="sxs-lookup"><span data-stu-id="41ea0-115">For example, if `Employee` derives from `Person` and p is of type `Person`, `TREAT(p AS NamespaceName.Employee)` upcasts a generic `Person` instance to `Employee`; that is, it allows you to treat p as `Employee`.</span></span>  
  
 <span data-ttu-id="41ea0-116">KABUL aşağıdaki gibi bir sorgu burada yapabileceğiniz devralma senaryolarda kullanılır:</span><span class="sxs-lookup"><span data-stu-id="41ea0-116">TREAT is used in inheritance scenarios where you can do a query like the following:</span></span>  
  
```  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)   
```  
  
 <span data-ttu-id="41ea0-117">Bu sorgu upcasts `Person` varlıklara `Employee` türü.</span><span class="sxs-lookup"><span data-stu-id="41ea0-117">This query upcasts `Person` entities to the `Employee` type.</span></span> <span data-ttu-id="41ea0-118">P değeri değil gerçekte türü olup olmadığını `Employee`, ifade değerini verir `null`.</span><span class="sxs-lookup"><span data-stu-id="41ea0-118">If the value of p is not actually of type `Employee`, the expression yields the value `null`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="41ea0-119">Belirtilen ifade `Employee` belirtilen veri türünün bir alt olmalıdır `Person`, veya alt ifade türünün veri türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="41ea0-119">The specified expression `Employee` must be a subtype of the specified data type `Person`, or the data type must be a subtype of the expression.</span></span> <span data-ttu-id="41ea0-120">Aksi takdirde, ifade bir derleme zamanı hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="41ea0-120">Otherwise, the expression will result in a compile-time error.</span></span>  
  
 <span data-ttu-id="41ea0-121">Aşağıdaki tabloda, bazı tipik desenleri ve daha az görülen bazı desenleri kabul davranışını gösterir.</span><span class="sxs-lookup"><span data-stu-id="41ea0-121">The following table shows the behavior of treat over some typical patterns and some less common patterns.</span></span> <span data-ttu-id="41ea0-122">Sağlayıcı çağrılır önce tüm istemci tarafındaki özel durumlar:</span><span class="sxs-lookup"><span data-stu-id="41ea0-122">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="41ea0-123">Desen</span><span class="sxs-lookup"><span data-stu-id="41ea0-123">Pattern</span></span>|<span data-ttu-id="41ea0-124">Davranış</span><span class="sxs-lookup"><span data-stu-id="41ea0-124">Behavior</span></span>|  
|-------------|--------------|  
|`TREAT (null AS EntityType)`|<span data-ttu-id="41ea0-125">Döndürür `DbNull`.</span><span class="sxs-lookup"><span data-stu-id="41ea0-125">Returns `DbNull`.</span></span>|  
|`TREAT (null AS ComplexType)`|<span data-ttu-id="41ea0-126">Bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="41ea0-126">Throws an exception.</span></span>|  
|`TREAT (null AS RowType)`|<span data-ttu-id="41ea0-127">Bir özel durum oluşturur /</span><span class="sxs-lookup"><span data-stu-id="41ea0-127">Throws an exception/</span></span>|  
|`TREAT (EntityType AS EntityType)`|<span data-ttu-id="41ea0-128">Döndürür `EntityType` veya `null`.</span><span class="sxs-lookup"><span data-stu-id="41ea0-128">Returns `EntityType` or `null`.</span></span>|  
|`TREAT (ComplexType AS ComplexType)`|<span data-ttu-id="41ea0-129">Bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="41ea0-129">Throws an exception.</span></span>|  
|`TREAT (RowType AS RowType)`|<span data-ttu-id="41ea0-130">Bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="41ea0-130">Throws an exception.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="41ea0-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="41ea0-131">Example</span></span>  
 <span data-ttu-id="41ea0-132">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu indirmelere türünde bir nesne OnsiteCourse türündeki nesneler koleksiyonuna dönüştürmek için kabul işleci kullanır.</span><span class="sxs-lookup"><span data-stu-id="41ea0-132">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="41ea0-133">Sorgu dayanır [Okul modeli](http://msdn.microsoft.com/en-us/859a9587-81ea-4a45-9bc0-f8d330e1adac).</span><span class="sxs-lookup"><span data-stu-id="41ea0-133">The query is based on the [School Model](http://msdn.microsoft.com/en-us/859a9587-81ea-4a45-9bc0-f8d330e1adac).</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## <a name="see-also"></a><span data-ttu-id="41ea0-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="41ea0-134">See Also</span></span>  
 [<span data-ttu-id="41ea0-135">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="41ea0-135">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="41ea0-136">Null Değer Atanabilir Yapılandırılmış Türler</span><span class="sxs-lookup"><span data-stu-id="41ea0-136">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
