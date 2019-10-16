---
title: OFTYPE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 6d259ca7-bbf0-40f8-a154-181d25c0d67e
ms.openlocfilehash: f1dd5ba92c7b1eaf7117c9732a78e04e5d5a317a
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319450"
---
# <a name="oftype-entity-sql"></a><span data-ttu-id="8380c-102">OFTYPE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="8380c-102">OFTYPE (Entity SQL)</span></span>
<span data-ttu-id="8380c-103">Belirli türde olan bir sorgu ifadesinden bir nesne koleksiyonu döndürür.</span><span class="sxs-lookup"><span data-stu-id="8380c-103">Returns a collection of objects from a query expression that is of a specific type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8380c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8380c-104">Syntax</span></span>  
  
```sql  
OFTYPE ( expression, [ONLY] test_type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="8380c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8380c-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="8380c-106">Bir nesne koleksiyonu döndüren geçerli bir sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="8380c-106">Any valid query expression that returns a collection of objects.</span></span>  
  
 `test_type`  
 <span data-ttu-id="8380c-107">@No__t-0 tarafından döndürülen her bir nesneyi test etmek için tür.</span><span class="sxs-lookup"><span data-stu-id="8380c-107">The type to test each object returned by `expression` against.</span></span> <span data-ttu-id="8380c-108">Tür bir ad alanı tarafından nitelenmelidir.</span><span class="sxs-lookup"><span data-stu-id="8380c-108">The type must be qualified by a namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8380c-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8380c-109">Return Value</span></span>  
 <span data-ttu-id="8380c-110">@No__t-0 türünde bir nesne koleksiyonu veya bir temel tür ya da `test_type` türetilmiş türü.</span><span class="sxs-lookup"><span data-stu-id="8380c-110">A collection of objects that are of type `test_type`, or a base type or derived type of `test_type`.</span></span> <span data-ttu-id="8380c-111">YALNıZCA belirtilmişse, yalnızca `test_type` veya boş bir koleksiyonun örnekleri döndürülür.</span><span class="sxs-lookup"><span data-stu-id="8380c-111">If ONLY is specified, only instances of the `test_type` or an empty collection will be returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8380c-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8380c-112">Remarks</span></span>  
 <span data-ttu-id="8380c-113">@No__t-0 ifadesi, bir koleksiyonun her öğesine karşı bir tür testi gerçekleştirmek için verilen bir tür ifadesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8380c-113">An `OFTYPE` expression specifies a type expression that is issued to perform a type test against each element of a collection.</span></span>  <span data-ttu-id="8380c-114">@No__t-0 ifadesi, yalnızca bu tür veya alt türü ile eşdeğer olan öğeleri içeren belirtilen türde yeni bir koleksiyon oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8380c-114">The `OFTYPE` expression produces a new collection of the specified type containing only those elements that were either equivalent to that type or a sub-type of it.</span></span>  
  
 <span data-ttu-id="8380c-115">@No__t-0 ifadesi aşağıdaki sorgu ifadesinin kısaltmasıdır:</span><span class="sxs-lookup"><span data-stu-id="8380c-115">An `OFTYPE` expression is an abbreviation of the following query expression:</span></span>  
  
```sql  
select value treat(t as T) from ts as t where t is of (T)  
```  
  
 <span data-ttu-id="8380c-116">Bir yöneticinin çalışan bir alt türü olduğu için, aşağıdaki ifade bir çalışan koleksiyonundan yalnızca Yöneticiler koleksiyonu oluşturur:</span><span class="sxs-lookup"><span data-stu-id="8380c-116">Given that a Manager is a subtype of Employee, the following expression produces a collection of only managers from a collection of employees:</span></span>  
  
```sql  
OfType(employees, NamespaceName.Manager)  
```  
  
 <span data-ttu-id="8380c-117">Tür filtresi kullanılarak bir koleksiyon atama de mümkündür:</span><span class="sxs-lookup"><span data-stu-id="8380c-117">It is also possible to up cast a collection using the type filter:</span></span>  
  
```sql
OfType(executives, NamespaceName.Manager)  
```  
  
 <span data-ttu-id="8380c-118">Tüm Yöneticiler yöneticilerden dolayı, sonuçta elde edilen koleksiyon tüm özgün yöneticileri içerir, ancak koleksiyon artık bir Yöneticiler koleksiyonu olarak türdedir.</span><span class="sxs-lookup"><span data-stu-id="8380c-118">Since all executives are managers, the resulting collection still contains all the original executives, though the collection is now typed as a collection of managers.</span></span>  
  
 <span data-ttu-id="8380c-119">Aşağıdaki tabloda bazı desenler üzerinde `OFTYPE` işlecinin davranışı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8380c-119">The following table shows the behavior of the `OFTYPE` operator over some patterns.</span></span> <span data-ttu-id="8380c-120">Sağlayıcı çağrılmadan önce istemci tarafında tüm özel durumlar atılır:</span><span class="sxs-lookup"><span data-stu-id="8380c-120">All exceptions are thrown from the client side before the provider is invoked:</span></span>  
  
|<span data-ttu-id="8380c-121">Desen</span><span class="sxs-lookup"><span data-stu-id="8380c-121">Pattern</span></span>|<span data-ttu-id="8380c-122">Davranış</span><span class="sxs-lookup"><span data-stu-id="8380c-122">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="8380c-123">OFTYPE (koleksiyon (EntityType), EntityType)</span><span class="sxs-lookup"><span data-stu-id="8380c-123">OFTYPE(Collection(EntityType), EntityType)</span></span>|<span data-ttu-id="8380c-124">Koleksiyon (EntityType)</span><span class="sxs-lookup"><span data-stu-id="8380c-124">Collection(EntityType)</span></span>|  
|<span data-ttu-id="8380c-125">OFTYPE (koleksiyon (ComplexType), ComplexType)</span><span class="sxs-lookup"><span data-stu-id="8380c-125">OFTYPE(Collection(ComplexType), ComplexType)</span></span>|<span data-ttu-id="8380c-126">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="8380c-126">Throws</span></span>|  
|<span data-ttu-id="8380c-127">OFTYPE (koleksiyon (RowType), RowType)</span><span class="sxs-lookup"><span data-stu-id="8380c-127">OFTYPE(Collection(RowType), RowType)</span></span>|<span data-ttu-id="8380c-128">Oluşturur</span><span class="sxs-lookup"><span data-stu-id="8380c-128">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8380c-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="8380c-129">Example</span></span>  
 <span data-ttu-id="8380c-130">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgusu, bir kurs nesneleri koleksiyonundan Onsitekurs nesnelerinin bir koleksiyonunu döndürmek için OFTYPE işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8380c-130">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the OFTYPE operator to return a collection of OnsiteCourse objects from a collection of Course objects.</span></span> <span data-ttu-id="8380c-131">Sorgu, [okul modelini](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))temel alır.</span><span class="sxs-lookup"><span data-stu-id="8380c-131">The query is based on the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 [!code-sql[DP EntityServices Concepts#OFTYPE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#oftype)]  
  
## <a name="see-also"></a><span data-ttu-id="8380c-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8380c-132">See also</span></span>

- [<span data-ttu-id="8380c-133">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="8380c-133">Entity SQL Reference</span></span>](entity-sql-reference.md)
