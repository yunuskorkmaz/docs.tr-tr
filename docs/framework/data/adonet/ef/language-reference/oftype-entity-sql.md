---
title: OFTYPE (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 6d259ca7-bbf0-40f8-a154-181d25c0d67e
ms.openlocfilehash: 2edd3bd7802dfc418490553cd0848a4ae458ae9a
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55828117"
---
# <a name="oftype-entity-sql"></a><span data-ttu-id="cd7c3-102">OFTYPE (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="cd7c3-102">OFTYPE (Entity SQL)</span></span>
<span data-ttu-id="cd7c3-103">Belirli bir tür bir sorgu ifadesinden nesnelerinin bir koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="cd7c3-103">Returns a collection of objects from a query expression that is of a specific type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd7c3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cd7c3-104">Syntax</span></span>  
  
```  
OFTYPE ( expression, [ONLY] test_type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="cd7c3-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="cd7c3-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="cd7c3-106">Nesnelerin bir koleksiyonunu döndürür herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="cd7c3-106">Any valid query expression that returns a collection of objects.</span></span>  
  
 `test_type`  
 <span data-ttu-id="cd7c3-107">Tarafından döndürülen her nesne sınanacak tür `expression` karşı.</span><span class="sxs-lookup"><span data-stu-id="cd7c3-107">The type to test each object returned by `expression` against.</span></span> <span data-ttu-id="cd7c3-108">Türü bir ad alanı tarafından nitelendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="cd7c3-108">The type must be qualified by a namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cd7c3-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cd7c3-109">Return Value</span></span>  
 <span data-ttu-id="cd7c3-110">Türündeki nesneler koleksiyonunu `test_type`, veya bir temel tür veya türetilmiş bir tür `test_type`.</span><span class="sxs-lookup"><span data-stu-id="cd7c3-110">A collection of objects that are of type `test_type`, or a base type or derived type of `test_type`.</span></span> <span data-ttu-id="cd7c3-111">YALNIZCA belirtilen yalnızca örnekler, `test_type` ya da boş bir koleksiyon döndürülür.</span><span class="sxs-lookup"><span data-stu-id="cd7c3-111">If ONLY is specified, only instances of the `test_type` or an empty collection will be returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd7c3-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cd7c3-112">Remarks</span></span>  
 <span data-ttu-id="cd7c3-113">Bir `OFTYPE` koleksiyonun her öğesine karşı bir tür testi gerçekleştirmek için verilen bir tür ifadesi ifade belirtir.</span><span class="sxs-lookup"><span data-stu-id="cd7c3-113">An `OFTYPE` expression specifies a type expression that is issued to perform a type test against each element of a collection.</span></span>  <span data-ttu-id="cd7c3-114">`OFTYPE` İfade ya da olan öğeleri içeren belirtilen türe ait yeni bir koleksiyon oluşturur, tür veya alt türünü eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="cd7c3-114">The `OFTYPE` expression produces a new collection of the specified type containing only those elements that were either equivalent to that type or a sub-type of it.</span></span>  
  
 <span data-ttu-id="cd7c3-115">Bir `OFTYPE` aşağıdaki sorgu ifadesinin bir kısaltma ifadesidir:</span><span class="sxs-lookup"><span data-stu-id="cd7c3-115">An `OFTYPE` expression is an abbreviation of the following query expression:</span></span>  
  
```  
select value treat(t as T) from ts as t where t is of (T)  
```  
  
 <span data-ttu-id="cd7c3-116">Çalışan bir alt yöneticisidir düşünüldüğünde, aşağıdaki ifade yalnızca çalışanlar koleksiyonu yöneticileri koleksiyonu oluşturur:</span><span class="sxs-lookup"><span data-stu-id="cd7c3-116">Given that a Manager is a subtype of Employee, the following expression produces a collection of only managers from a collection of employees:</span></span>  
  
```  
OfType(employees, NamespaceName.Manager)  
```  
  
 <span data-ttu-id="cd7c3-117">En fazla türü filtresi kullanarak koleksiyon türüne mümkündür:</span><span class="sxs-lookup"><span data-stu-id="cd7c3-117">It is also possible to up cast a collection using the type filter:</span></span>  
  
```  
OfType(executives, NamespaceName.Manager)  
```  
  
 <span data-ttu-id="cd7c3-118">Tüm Yöneticiler yöneticileri olduğundan, koleksiyon artık yöneticileri koleksiyonu olarak yazılmış olsa, elde edilen koleksiyon hala tüm özgün Yöneticiler içeriyor.</span><span class="sxs-lookup"><span data-stu-id="cd7c3-118">Since all executives are managers, the resulting collection still contains all the original executives, though the collection is now typed as a collection of managers.</span></span>  
  
 <span data-ttu-id="cd7c3-119">Aşağıdaki tabloda davranışını gösteren `OFTYPE` bazı desenleri üzerinden işleci.</span><span class="sxs-lookup"><span data-stu-id="cd7c3-119">The following table shows the behavior of the `OFTYPE` operator over some patterns.</span></span> <span data-ttu-id="cd7c3-120">Sağlayıcı çağrılmadan önce tüm istemci tarafında özel durumlar:</span><span class="sxs-lookup"><span data-stu-id="cd7c3-120">All exceptions are thrown from the client side before the provider is invoked:</span></span>  
  
|<span data-ttu-id="cd7c3-121">Desen</span><span class="sxs-lookup"><span data-stu-id="cd7c3-121">Pattern</span></span>|<span data-ttu-id="cd7c3-122">Davranış</span><span class="sxs-lookup"><span data-stu-id="cd7c3-122">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="cd7c3-123">OFTYPE(Collection(EntityType), EntityType)</span><span class="sxs-lookup"><span data-stu-id="cd7c3-123">OFTYPE(Collection(EntityType), EntityType)</span></span>|<span data-ttu-id="cd7c3-124">Collection(EntityType)</span><span class="sxs-lookup"><span data-stu-id="cd7c3-124">Collection(EntityType)</span></span>|  
|<span data-ttu-id="cd7c3-125">OFTYPE(Collection(complexType), ComplexType)</span><span class="sxs-lookup"><span data-stu-id="cd7c3-125">OFTYPE(Collection(ComplexType), ComplexType)</span></span>|<span data-ttu-id="cd7c3-126">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="cd7c3-126">Throws</span></span>|  
|<span data-ttu-id="cd7c3-127">OFTYPE(Collection(RowType), RowType)</span><span class="sxs-lookup"><span data-stu-id="cd7c3-127">OFTYPE(Collection(RowType), RowType)</span></span>|<span data-ttu-id="cd7c3-128">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="cd7c3-128">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="cd7c3-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="cd7c3-129">Example</span></span>  
 <span data-ttu-id="cd7c3-130">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu OnsiteCourse nesnelerden oluşan bir koleksiyon bir koleksiyondan Elbette nesneler döndürmeye OFTYPE işleci kullanır.</span><span class="sxs-lookup"><span data-stu-id="cd7c3-130">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the OFTYPE operator to return a collection of OnsiteCourse objects from a collection of Course objects.</span></span> <span data-ttu-id="cd7c3-131">Sorgu dayanır [Okul modeli](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="cd7c3-131">The query is based on the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#OFTYPE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#oftype)]  
  
## <a name="see-also"></a><span data-ttu-id="cd7c3-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd7c3-132">See also</span></span>
- [<span data-ttu-id="cd7c3-133">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="cd7c3-133">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
