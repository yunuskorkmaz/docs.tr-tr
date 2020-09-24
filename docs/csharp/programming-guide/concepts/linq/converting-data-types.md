---
title: Veri türlerini dönüştürme (C#)
description: Dönüştürme yöntemleri giriş nesnelerinin türünü değiştirir. Bkz. C# ' de, sıralanabilir. Assıralanabilir ve Numaralandırılabilir. OfType gibi LINQ sorgularında dönüştürme işlemleri.
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: f9e3b354fd6eeba6564067550ea3821e4946d92f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91159143"
---
# <a name="converting-data-types-c"></a><span data-ttu-id="5592a-104">Veri türlerini dönüştürme (C#)</span><span class="sxs-lookup"><span data-stu-id="5592a-104">Converting Data Types (C#)</span></span>

<span data-ttu-id="5592a-105">Dönüştürme yöntemleri giriş nesnelerinin türünü değiştirir.</span><span class="sxs-lookup"><span data-stu-id="5592a-105">Conversion methods change the type of input objects.</span></span>

 <span data-ttu-id="5592a-106">LINQ sorgularındaki dönüştürme işlemleri çeşitli uygulamalarda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="5592a-106">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="5592a-107">Aşağıda bazı örnekler verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5592a-107">Following are some examples:</span></span>

- <span data-ttu-id="5592a-108">Yöntemi, bir <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> türün standart sorgu işlecinin özel uygulamasını gizlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5592a-108">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>

- <span data-ttu-id="5592a-109"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType>Yöntemi, LINQ sorgulaması için parametreli olmayan koleksiyonları etkinleştirmek üzere kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5592a-109">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>

- <span data-ttu-id="5592a-110"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>,, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType> <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> Ve yöntemleri, <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> sorgu numaralandırılana kadar, sorgu yürütmeye zorlamak yerine hemen bu işlemi yapmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5592a-110">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>

## <a name="methods"></a><span data-ttu-id="5592a-111">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5592a-111">Methods</span></span>

 <span data-ttu-id="5592a-112">Aşağıdaki tabloda, veri türü dönüştürmeleri gerçekleştiren standart sorgu işleci yöntemleri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="5592a-112">The following table lists the standard query operator methods that perform data-type conversions.</span></span>

 <span data-ttu-id="5592a-113">Bu tablodaki, adları "as" ile başlayan dönüştürme yöntemleri, kaynak koleksiyonun statik türünü değiştirir ancak onu numaralandırmaz.</span><span class="sxs-lookup"><span data-stu-id="5592a-113">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="5592a-114">Adları "to" ile başlayan Yöntemler, kaynak koleksiyonu numaralandırır ve öğeleri karşılık gelen koleksiyon türüne koyar.</span><span class="sxs-lookup"><span data-stu-id="5592a-114">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>

|<span data-ttu-id="5592a-115">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="5592a-115">Method Name</span></span>|<span data-ttu-id="5592a-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5592a-116">Description</span></span>|<span data-ttu-id="5592a-117">C# sorgu Ifadesi sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5592a-117">C# Query Expression Syntax</span></span>|<span data-ttu-id="5592a-118">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="5592a-118">More Information</span></span>|
|-----------------|-----------------|---------------------------------|----------------------|
|<span data-ttu-id="5592a-119">Asılabilir</span><span class="sxs-lookup"><span data-stu-id="5592a-119">AsEnumerable</span></span>|<span data-ttu-id="5592a-120">Olarak yazılan girişi döndürür <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="5592a-120">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="5592a-121">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="5592a-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="5592a-122">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="5592a-122">AsQueryable</span></span>|<span data-ttu-id="5592a-123">Bir (genel) bir <xref:System.Collections.IEnumerable> (genel) öğesine dönüştürür <xref:System.Linq.IQueryable> .</span><span class="sxs-lookup"><span data-stu-id="5592a-123">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="5592a-124">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="5592a-124">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="5592a-125">Cast</span><span class="sxs-lookup"><span data-stu-id="5592a-125">Cast</span></span>|<span data-ttu-id="5592a-126">Bir koleksiyonun öğelerini belirtilen bir türe yayınlar.</span><span class="sxs-lookup"><span data-stu-id="5592a-126">Casts the elements of a collection to a specified type.</span></span>|<span data-ttu-id="5592a-127">Açıkça yazılmış bir Aralık değişkeni kullanın.</span><span class="sxs-lookup"><span data-stu-id="5592a-127">Use an explicitly typed range variable.</span></span> <span data-ttu-id="5592a-128">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="5592a-128">For example:</span></span><br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|
|<span data-ttu-id="5592a-129">OfType</span><span class="sxs-lookup"><span data-stu-id="5592a-129">OfType</span></span>|<span data-ttu-id="5592a-130">Değerleri, belirli bir türe atama becerisine bağlı olarak filtreler.</span><span class="sxs-lookup"><span data-stu-id="5592a-130">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="5592a-131">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="5592a-131">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|<span data-ttu-id="5592a-132">ToArray</span><span class="sxs-lookup"><span data-stu-id="5592a-132">ToArray</span></span>|<span data-ttu-id="5592a-133">Bir koleksiyonu bir diziye dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="5592a-133">Converts a collection to an array.</span></span> <span data-ttu-id="5592a-134">Bu yöntem sorgu yürütmeyi zorlar.</span><span class="sxs-lookup"><span data-stu-id="5592a-134">This method forces query execution.</span></span>|<span data-ttu-id="5592a-135">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="5592a-135">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|
|<span data-ttu-id="5592a-136">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="5592a-136">ToDictionary</span></span>|<span data-ttu-id="5592a-137">Öğeleri bir <xref:System.Collections.Generic.Dictionary%602> anahtar Seçici işlevine göre içine koyar.</span><span class="sxs-lookup"><span data-stu-id="5592a-137">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="5592a-138">Bu yöntem sorgu yürütmeyi zorlar.</span><span class="sxs-lookup"><span data-stu-id="5592a-138">This method forces query execution.</span></span>|<span data-ttu-id="5592a-139">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="5592a-139">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|
|<span data-ttu-id="5592a-140">ToList</span><span class="sxs-lookup"><span data-stu-id="5592a-140">ToList</span></span>|<span data-ttu-id="5592a-141">Bir koleksiyonu öğesine dönüştürür <xref:System.Collections.Generic.List%601> .</span><span class="sxs-lookup"><span data-stu-id="5592a-141">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="5592a-142">Bu yöntem sorgu yürütmeyi zorlar.</span><span class="sxs-lookup"><span data-stu-id="5592a-142">This method forces query execution.</span></span>|<span data-ttu-id="5592a-143">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="5592a-143">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|
|<span data-ttu-id="5592a-144">ToLookup</span><span class="sxs-lookup"><span data-stu-id="5592a-144">ToLookup</span></span>|<span data-ttu-id="5592a-145">Öğeleri bir <xref:System.Linq.Lookup%602> anahtar Seçici işlevine göre (bire çok sözlüğüne) yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="5592a-145">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="5592a-146">Bu yöntem sorgu yürütmeyi zorlar.</span><span class="sxs-lookup"><span data-stu-id="5592a-146">This method forces query execution.</span></span>|<span data-ttu-id="5592a-147">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="5592a-147">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a><span data-ttu-id="5592a-148">Sorgu Ifadesi söz dizimi örneği</span><span class="sxs-lookup"><span data-stu-id="5592a-148">Query Expression Syntax Example</span></span>

<span data-ttu-id="5592a-149">Aşağıdaki kod örneği, yalnızca alt tür üzerinde kullanılabilir olan bir üyeye erişmeden önce bir türü bir alt türe dönüştürmek için açıkça yazılmış bir Aralık değişkeni kullanır.</span><span class="sxs-lookup"><span data-stu-id="5592a-149">The following code example uses an explicitly typed range variable to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5592a-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5592a-150">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="5592a-151">Standart sorgu Işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="5592a-151">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="5592a-152">from yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="5592a-152">from clause</span></span>](../../../language-reference/keywords/from-clause.md)
- [<span data-ttu-id="5592a-153">LINQ sorgu Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="5592a-153">LINQ Query Expressions</span></span>](../../../linq/index.md)
- [<span data-ttu-id="5592a-154">LINQ ile ArrayList 'i sorgulama (C#)</span><span class="sxs-lookup"><span data-stu-id="5592a-154">How to query an ArrayList with LINQ (C#)</span></span>](./how-to-query-an-arraylist-with-linq.md)
