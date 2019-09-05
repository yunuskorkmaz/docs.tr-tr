---
title: OFTYPE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 6d259ca7-bbf0-40f8-a154-181d25c0d67e
ms.openlocfilehash: 36701a5e75e804ea541d242aaff243de0b24cec3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249790"
---
# <a name="oftype-entity-sql"></a><span data-ttu-id="aa108-102">OFTYPE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="aa108-102">OFTYPE (Entity SQL)</span></span>
<span data-ttu-id="aa108-103">Belirli türde olan bir sorgu ifadesinden bir nesne koleksiyonu döndürür.</span><span class="sxs-lookup"><span data-stu-id="aa108-103">Returns a collection of objects from a query expression that is of a specific type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa108-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aa108-104">Syntax</span></span>  
  
```  
OFTYPE ( expression, [ONLY] test_type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="aa108-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="aa108-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="aa108-106">Bir nesne koleksiyonu döndüren geçerli bir sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="aa108-106">Any valid query expression that returns a collection of objects.</span></span>  
  
 `test_type`  
 <span data-ttu-id="aa108-107">Tarafından `expression` döndürülen her nesnenin test edilecek tür.</span><span class="sxs-lookup"><span data-stu-id="aa108-107">The type to test each object returned by `expression` against.</span></span> <span data-ttu-id="aa108-108">Tür bir ad alanı tarafından nitelenmelidir.</span><span class="sxs-lookup"><span data-stu-id="aa108-108">The type must be qualified by a namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aa108-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="aa108-109">Return Value</span></span>  
 <span data-ttu-id="aa108-110">Türünde `test_type`bir nesne koleksiyonu veya temel tür ya da türetilmiş `test_type`tür.</span><span class="sxs-lookup"><span data-stu-id="aa108-110">A collection of objects that are of type `test_type`, or a base type or derived type of `test_type`.</span></span> <span data-ttu-id="aa108-111">Yalnızca belirtilmişse, yalnızca `test_type` veya boş bir koleksiyonun örnekleri döndürülür.</span><span class="sxs-lookup"><span data-stu-id="aa108-111">If ONLY is specified, only instances of the `test_type` or an empty collection will be returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa108-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aa108-112">Remarks</span></span>  
 <span data-ttu-id="aa108-113">Bir `OFTYPE` ifade, bir koleksiyonun her öğesine karşı bir tür testi gerçekleştirmek için verilen bir tür ifadesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="aa108-113">An `OFTYPE` expression specifies a type expression that is issued to perform a type test against each element of a collection.</span></span>  <span data-ttu-id="aa108-114">İfade `OFTYPE` , yalnızca bu tür veya alt türü ile eşdeğer olan öğeleri içeren belirtilen türde yeni bir koleksiyon oluşturur.</span><span class="sxs-lookup"><span data-stu-id="aa108-114">The `OFTYPE` expression produces a new collection of the specified type containing only those elements that were either equivalent to that type or a sub-type of it.</span></span>  
  
 <span data-ttu-id="aa108-115">`OFTYPE` İfade aşağıdaki sorgu ifadesinin kısaltmasıdır:</span><span class="sxs-lookup"><span data-stu-id="aa108-115">An `OFTYPE` expression is an abbreviation of the following query expression:</span></span>  
  
```  
select value treat(t as T) from ts as t where t is of (T)  
```  
  
 <span data-ttu-id="aa108-116">Bir yöneticinin çalışan bir alt türü olduğu için, aşağıdaki ifade bir çalışan koleksiyonundan yalnızca Yöneticiler koleksiyonu oluşturur:</span><span class="sxs-lookup"><span data-stu-id="aa108-116">Given that a Manager is a subtype of Employee, the following expression produces a collection of only managers from a collection of employees:</span></span>  
  
```  
OfType(employees, NamespaceName.Manager)  
```  
  
 <span data-ttu-id="aa108-117">Tür filtresi kullanılarak bir koleksiyon atama de mümkündür:</span><span class="sxs-lookup"><span data-stu-id="aa108-117">It is also possible to up cast a collection using the type filter:</span></span>  
  
```  
OfType(executives, NamespaceName.Manager)  
```  
  
 <span data-ttu-id="aa108-118">Tüm Yöneticiler yöneticilerden dolayı, sonuçta elde edilen koleksiyon tüm özgün yöneticileri içerir, ancak koleksiyon artık bir Yöneticiler koleksiyonu olarak türdedir.</span><span class="sxs-lookup"><span data-stu-id="aa108-118">Since all executives are managers, the resulting collection still contains all the original executives, though the collection is now typed as a collection of managers.</span></span>  
  
 <span data-ttu-id="aa108-119">Aşağıdaki tablo, bazı desenlerdeki `OFTYPE` işlecin davranışını gösterir.</span><span class="sxs-lookup"><span data-stu-id="aa108-119">The following table shows the behavior of the `OFTYPE` operator over some patterns.</span></span> <span data-ttu-id="aa108-120">Sağlayıcı çağrılmadan önce istemci tarafında tüm özel durumlar atılır:</span><span class="sxs-lookup"><span data-stu-id="aa108-120">All exceptions are thrown from the client side before the provider is invoked:</span></span>  
  
|<span data-ttu-id="aa108-121">Desen</span><span class="sxs-lookup"><span data-stu-id="aa108-121">Pattern</span></span>|<span data-ttu-id="aa108-122">Davranış</span><span class="sxs-lookup"><span data-stu-id="aa108-122">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="aa108-123">OFTYPE (koleksiyon (EntityType), EntityType)</span><span class="sxs-lookup"><span data-stu-id="aa108-123">OFTYPE(Collection(EntityType), EntityType)</span></span>|<span data-ttu-id="aa108-124">Koleksiyon (EntityType)</span><span class="sxs-lookup"><span data-stu-id="aa108-124">Collection(EntityType)</span></span>|  
|<span data-ttu-id="aa108-125">OFTYPE (koleksiyon (ComplexType), ComplexType)</span><span class="sxs-lookup"><span data-stu-id="aa108-125">OFTYPE(Collection(ComplexType), ComplexType)</span></span>|<span data-ttu-id="aa108-126">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="aa108-126">Throws</span></span>|  
|<span data-ttu-id="aa108-127">OFTYPE (koleksiyon (RowType), RowType)</span><span class="sxs-lookup"><span data-stu-id="aa108-127">OFTYPE(Collection(RowType), RowType)</span></span>|<span data-ttu-id="aa108-128">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="aa108-128">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="aa108-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="aa108-129">Example</span></span>  
 <span data-ttu-id="aa108-130">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, bir kurs nesneleri koleksiyonundan onsitekurs nesnelerinin bir koleksiyonunu döndürmek için OFTYPE işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="aa108-130">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the OFTYPE operator to return a collection of OnsiteCourse objects from a collection of Course objects.</span></span> <span data-ttu-id="aa108-131">Sorgu, [okul modelini](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))temel alır.</span><span class="sxs-lookup"><span data-stu-id="aa108-131">The query is based on the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#OFTYPE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#oftype)]  
  
## <a name="see-also"></a><span data-ttu-id="aa108-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa108-132">See also</span></span>

- [<span data-ttu-id="aa108-133">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="aa108-133">Entity SQL Reference</span></span>](entity-sql-reference.md)
