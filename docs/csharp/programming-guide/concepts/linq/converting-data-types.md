---
title: Veri türlerini dönüştürme (C#)
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: 328c790a1a360907c91f69b3b6330b0b25eb414b
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347198"
---
# <a name="converting-data-types-c"></a><span data-ttu-id="81fdb-102">Veri türlerini dönüştürme (C#)</span><span class="sxs-lookup"><span data-stu-id="81fdb-102">Converting Data Types (C#)</span></span>
<span data-ttu-id="81fdb-103">Dönüştürme yöntemleri giriş nesnelerinin türünü değiştirir.</span><span class="sxs-lookup"><span data-stu-id="81fdb-103">Conversion methods change the type of input objects.</span></span>

 <span data-ttu-id="81fdb-104">LINQ sorgularındaki dönüştürme işlemleri çeşitli uygulamalarda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="81fdb-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="81fdb-105">Aşağıda bazı örnekler verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="81fdb-105">Following are some examples:</span></span>

- <span data-ttu-id="81fdb-106"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> yöntemi, bir türün standart sorgu işlecinin özel uygulamasını gizlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="81fdb-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>

- <span data-ttu-id="81fdb-107"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> yöntemi, LINQ sorgulaması için parametreli olmayan koleksiyonları etkinleştirmek üzere kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="81fdb-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>

- <span data-ttu-id="81fdb-108"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>ve <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> yöntemleri, sorgu numaralandırılana kadar, sorgu yürütmeye zorlamak yerine hemen bu işlemi yapmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="81fdb-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>

## <a name="methods"></a><span data-ttu-id="81fdb-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="81fdb-109">Methods</span></span>
 <span data-ttu-id="81fdb-110">Aşağıdaki tabloda, veri türü dönüştürmeleri gerçekleştiren standart sorgu işleci yöntemleri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="81fdb-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>

 <span data-ttu-id="81fdb-111">Bu tablodaki, adları "as" ile başlayan dönüştürme yöntemleri, kaynak koleksiyonun statik türünü değiştirir ancak onu numaralandırmaz.</span><span class="sxs-lookup"><span data-stu-id="81fdb-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="81fdb-112">Adları "to" ile başlayan Yöntemler, kaynak koleksiyonu numaralandırır ve öğeleri karşılık gelen koleksiyon türüne koyar.</span><span class="sxs-lookup"><span data-stu-id="81fdb-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>

|<span data-ttu-id="81fdb-113">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="81fdb-113">Method Name</span></span>|<span data-ttu-id="81fdb-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81fdb-114">Description</span></span>|<span data-ttu-id="81fdb-115">C#Sorgu Ifadesi söz dizimi</span><span class="sxs-lookup"><span data-stu-id="81fdb-115">C# Query Expression Syntax</span></span>|<span data-ttu-id="81fdb-116">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="81fdb-116">More Information</span></span>|
|-----------------|-----------------|---------------------------------|----------------------|
|<span data-ttu-id="81fdb-117">Asılabilir</span><span class="sxs-lookup"><span data-stu-id="81fdb-117">AsEnumerable</span></span>|<span data-ttu-id="81fdb-118"><xref:System.Collections.Generic.IEnumerable%601>olarak yazılan girişi döndürür.</span><span class="sxs-lookup"><span data-stu-id="81fdb-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="81fdb-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="81fdb-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="81fdb-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="81fdb-120">AsQueryable</span></span>|<span data-ttu-id="81fdb-121">Bir (genel) <xref:System.Collections.IEnumerable> bir (genel) <xref:System.Linq.IQueryable>dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="81fdb-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="81fdb-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="81fdb-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="81fdb-123">Cast</span><span class="sxs-lookup"><span data-stu-id="81fdb-123">Cast</span></span>|<span data-ttu-id="81fdb-124">Bir koleksiyonun öğelerini belirtilen bir türe yayınlar.</span><span class="sxs-lookup"><span data-stu-id="81fdb-124">Casts the elements of a collection to a specified type.</span></span>|<span data-ttu-id="81fdb-125">Açıkça yazılmış bir Aralık değişkeni kullanın.</span><span class="sxs-lookup"><span data-stu-id="81fdb-125">Use an explicitly typed range variable.</span></span> <span data-ttu-id="81fdb-126">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="81fdb-126">For example:</span></span><br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|
|<span data-ttu-id="81fdb-127">OfType</span><span class="sxs-lookup"><span data-stu-id="81fdb-127">OfType</span></span>|<span data-ttu-id="81fdb-128">Değerleri, belirli bir türe atama becerisine bağlı olarak filtreler.</span><span class="sxs-lookup"><span data-stu-id="81fdb-128">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="81fdb-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="81fdb-129">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|<span data-ttu-id="81fdb-130">toArray</span><span class="sxs-lookup"><span data-stu-id="81fdb-130">ToArray</span></span>|<span data-ttu-id="81fdb-131">Bir koleksiyonu bir diziye dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="81fdb-131">Converts a collection to an array.</span></span> <span data-ttu-id="81fdb-132">Bu yöntem sorgu yürütmeyi zorlar.</span><span class="sxs-lookup"><span data-stu-id="81fdb-132">This method forces query execution.</span></span>|<span data-ttu-id="81fdb-133">Yok.</span><span class="sxs-lookup"><span data-stu-id="81fdb-133">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|
|<span data-ttu-id="81fdb-134">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="81fdb-134">ToDictionary</span></span>|<span data-ttu-id="81fdb-135">Öğeleri bir anahtar Seçici işlevine göre <xref:System.Collections.Generic.Dictionary%602> koyar.</span><span class="sxs-lookup"><span data-stu-id="81fdb-135">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="81fdb-136">Bu yöntem sorgu yürütmeyi zorlar.</span><span class="sxs-lookup"><span data-stu-id="81fdb-136">This method forces query execution.</span></span>|<span data-ttu-id="81fdb-137">Yok.</span><span class="sxs-lookup"><span data-stu-id="81fdb-137">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|
|<span data-ttu-id="81fdb-138">toList</span><span class="sxs-lookup"><span data-stu-id="81fdb-138">ToList</span></span>|<span data-ttu-id="81fdb-139">Bir koleksiyonu bir <xref:System.Collections.Generic.List%601>dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="81fdb-139">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="81fdb-140">Bu yöntem sorgu yürütmeyi zorlar.</span><span class="sxs-lookup"><span data-stu-id="81fdb-140">This method forces query execution.</span></span>|<span data-ttu-id="81fdb-141">Yok.</span><span class="sxs-lookup"><span data-stu-id="81fdb-141">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|
|<span data-ttu-id="81fdb-142">ToLookup</span><span class="sxs-lookup"><span data-stu-id="81fdb-142">ToLookup</span></span>|<span data-ttu-id="81fdb-143">Öğeleri bir anahtar Seçici işlevine göre bir <xref:System.Linq.Lookup%602> (bire çok sözlüğüne) koyar.</span><span class="sxs-lookup"><span data-stu-id="81fdb-143">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="81fdb-144">Bu yöntem sorgu yürütmeyi zorlar.</span><span class="sxs-lookup"><span data-stu-id="81fdb-144">This method forces query execution.</span></span>|<span data-ttu-id="81fdb-145">Yok.</span><span class="sxs-lookup"><span data-stu-id="81fdb-145">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a><span data-ttu-id="81fdb-146">Sorgu Ifadesi söz dizimi örneği</span><span class="sxs-lookup"><span data-stu-id="81fdb-146">Query Expression Syntax Example</span></span>

<span data-ttu-id="81fdb-147">Aşağıdaki kod örneği, yalnızca alt tür üzerinde kullanılabilir olan bir üyeye erişmeden önce bir türü bir alt türe dönüştürmek için açıkça yazılmış bir Aralık değişkeni kullanır.</span><span class="sxs-lookup"><span data-stu-id="81fdb-147">The following code example uses an explicitly typed range variable to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>

```csharp
class Plant
{
    public string Name { get; set; }
}

class CarnivorousPlant : Plant
{
    public string TrapType { get; set; }
}

static void Cast()
{
    Plant[] plants = new Plant[] {
        new CarnivorousPlant { Name = "Venus Fly Trap", TrapType = "Snap Trap" },
        new CarnivorousPlant { Name = "Pitcher Plant", TrapType = "Pitfall Trap" },
        new CarnivorousPlant { Name = "Sundew", TrapType = "Flypaper Trap" },
        new CarnivorousPlant { Name = "Waterwheel Plant", TrapType = "Snap Trap" }
    };

    var query = from CarnivorousPlant cPlant in plants
                where cPlant.TrapType == "Snap Trap"
                select cPlant;

    foreach (Plant plant in query)
        Console.WriteLine(plant.Name);

    /* This code produces the following output:

        Venus Fly Trap
        Waterwheel Plant
    */
}
```

## <a name="see-also"></a><span data-ttu-id="81fdb-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="81fdb-148">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="81fdb-149">Standart sorgu Işleçlerine genelC#bakış ()</span><span class="sxs-lookup"><span data-stu-id="81fdb-149">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="81fdb-150">from yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="81fdb-150">from clause</span></span>](../../../language-reference/keywords/from-clause.md)
- [<span data-ttu-id="81fdb-151">LINQ sorgu Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="81fdb-151">LINQ Query Expressions</span></span>](../../../linq/index.md)
- [<span data-ttu-id="81fdb-152">LINQ (C#) ile ArrayList 'i sorgulama</span><span class="sxs-lookup"><span data-stu-id="81fdb-152">How to query an ArrayList with LINQ (C#)</span></span>](./how-to-query-an-arraylist-with-linq.md)
