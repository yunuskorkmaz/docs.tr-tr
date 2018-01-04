---
title: "OFTYPE (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d259ca7-bbf0-40f8-a154-181d25c0d67e
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 5b01097cdeba555fdc7435acd563f201f4d2ec8b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="oftype-entity-sql"></a><span data-ttu-id="8c327-102">OFTYPE (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="8c327-102">OFTYPE (Entity SQL)</span></span>
<span data-ttu-id="8c327-103">Belirli bir türde bir sorgu ifadesinden nesneler koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="8c327-103">Returns a collection of objects from a query expression that is of a specific type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c327-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8c327-104">Syntax</span></span>  
  
```  
OFTYPE ( expression, [ONLY] test_type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="8c327-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8c327-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="8c327-106">Nesneleri topluluğunu döndürür herhangi bir geçerli sorgu ifade.</span><span class="sxs-lookup"><span data-stu-id="8c327-106">Any valid query expression that returns a collection of objects.</span></span>  
  
 `test_type`  
 <span data-ttu-id="8c327-107">Türü tarafından döndürülen her nesne test `expression` karşı.</span><span class="sxs-lookup"><span data-stu-id="8c327-107">The type to test each object returned by `expression` against.</span></span> <span data-ttu-id="8c327-108">Türü bir ad alanı tarafından nitelenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8c327-108">The type must be qualified by a namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c327-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8c327-109">Return Value</span></span>  
 <span data-ttu-id="8c327-110">Türündeki nesneler koleksiyonunu `test_type`, veya bir taban türü veya türetilmiş türü `test_type`.</span><span class="sxs-lookup"><span data-stu-id="8c327-110">A collection of objects that are of type `test_type`, or a base type or derived type of `test_type`.</span></span> <span data-ttu-id="8c327-111">YALNIZCA belirtilen yalnızca örnekler, `test_type` ya da boş bir koleksiyon döndürülür.</span><span class="sxs-lookup"><span data-stu-id="8c327-111">If ONLY is specified, only instances of the `test_type` or an empty collection will be returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c327-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8c327-112">Remarks</span></span>  
 <span data-ttu-id="8c327-113">Bir `OFTYPE` ifadesi her bir koleksiyon öğesinin türü sınaması gerçekleştirmek için verilen bir türü ifade belirtir.</span><span class="sxs-lookup"><span data-stu-id="8c327-113">An `OFTYPE` expression specifies a type expression that is issued to perform a type test against each element of a collection.</span></span>  <span data-ttu-id="8c327-114">`OFTYPE` İfadesi belirtilen türde ya da olan öğeleri içeren yeni bir koleksiyon oluşturur türü veya alt türünü eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="8c327-114">The `OFTYPE` expression produces a new collection of the specified type containing only those elements that were either equivalent to that type or a sub-type of it.</span></span>  
  
 <span data-ttu-id="8c327-115">Bir `OFTYPE` ifadesidir aşağıdaki sorgu ifadesi için bir kısaltma:</span><span class="sxs-lookup"><span data-stu-id="8c327-115">An `OFTYPE` expression is an abbreviation of the following query expression:</span></span>  
  
```  
select value treat(t as T) from ts as t where t is of (T)  
```  
  
 <span data-ttu-id="8c327-116">Alt çalışan türünün bir yönetici olması koşuluyla, aşağıdaki deyim yalnızca yöneticileri çalışanlar koleksiyonundan koleksiyonu üretir:</span><span class="sxs-lookup"><span data-stu-id="8c327-116">Given that a Manager is a subtype of Employee, the following expression produces a collection of only managers from a collection of employees:</span></span>  
  
```  
OfType(employees, NamespaceName.Manager)  
```  
  
 <span data-ttu-id="8c327-117">En fazla türü filtresi kullanılarak bir koleksiyonu cast mümkündür:</span><span class="sxs-lookup"><span data-stu-id="8c327-117">It is also possible to up cast a collection using the type filter:</span></span>  
  
```  
OfType(executives, NamespaceName.Manager)  
```  
  
 <span data-ttu-id="8c327-118">Tüm Yöneticiler yöneticileri olduğundan, koleksiyon şimdi yöneticileri koleksiyonu olarak belirtilmiş olsa elde edilen koleksiyon hala tüm özgün Yöneticiler içeriyor.</span><span class="sxs-lookup"><span data-stu-id="8c327-118">Since all executives are managers, the resulting collection still contains all the original executives, though the collection is now typed as a collection of managers.</span></span>  
  
 <span data-ttu-id="8c327-119">Aşağıdaki tabloda davranışını gösterilmektedir `OFTYPE` bazı desenleri üzerinden işleci.</span><span class="sxs-lookup"><span data-stu-id="8c327-119">The following table shows the behavior of the `OFTYPE` operator over some patterns.</span></span> <span data-ttu-id="8c327-120">Sağlayıcı çağrılmadan önce tüm istemci tarafındaki özel durumlar:</span><span class="sxs-lookup"><span data-stu-id="8c327-120">All exceptions are thrown from the client side before the provider is invoked:</span></span>  
  
|<span data-ttu-id="8c327-121">Desen</span><span class="sxs-lookup"><span data-stu-id="8c327-121">Pattern</span></span>|<span data-ttu-id="8c327-122">Davranış</span><span class="sxs-lookup"><span data-stu-id="8c327-122">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="8c327-123">OFTYPE(Collection(EntityType), EntityType)</span><span class="sxs-lookup"><span data-stu-id="8c327-123">OFTYPE(Collection(EntityType), EntityType)</span></span>|<span data-ttu-id="8c327-124">Collection(EntityType)</span><span class="sxs-lookup"><span data-stu-id="8c327-124">Collection(EntityType)</span></span>|  
|<span data-ttu-id="8c327-125">OFTYPE(Collection(complexType), ComplexType)</span><span class="sxs-lookup"><span data-stu-id="8c327-125">OFTYPE(Collection(ComplexType), ComplexType)</span></span>|<span data-ttu-id="8c327-126">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="8c327-126">Throws</span></span>|  
|<span data-ttu-id="8c327-127">OFTYPE(Collection(RowType), RowType)</span><span class="sxs-lookup"><span data-stu-id="8c327-127">OFTYPE(Collection(RowType), RowType)</span></span>|<span data-ttu-id="8c327-128">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="8c327-128">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8c327-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="8c327-129">Example</span></span>  
 <span data-ttu-id="8c327-130">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu OnsiteCourse nesneler koleksiyonunu koleksiyondan Elbette nesneler döndürmeye OFTYPE işleci kullanır.</span><span class="sxs-lookup"><span data-stu-id="8c327-130">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the OFTYPE operator to return a collection of OnsiteCourse objects from a collection of Course objects.</span></span> <span data-ttu-id="8c327-131">Sorgu dayanır [Okul modeli](http://msdn.microsoft.com/en-us/859a9587-81ea-4a45-9bc0-f8d330e1adac).</span><span class="sxs-lookup"><span data-stu-id="8c327-131">The query is based on the [School Model](http://msdn.microsoft.com/en-us/859a9587-81ea-4a45-9bc0-f8d330e1adac).</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#OFTYPE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#oftype)]  
  
## <a name="see-also"></a><span data-ttu-id="8c327-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8c327-132">See Also</span></span>  
 [<span data-ttu-id="8c327-133">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="8c327-133">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
