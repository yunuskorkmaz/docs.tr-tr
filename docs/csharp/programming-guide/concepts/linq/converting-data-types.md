---
title: Veri Türlerini Dönüştürme (C#)
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: 328c790a1a360907c91f69b3b6330b0b25eb414b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347198"
---
# <a name="converting-data-types-c"></a><span data-ttu-id="66d82-102">Veri Türlerini Dönüştürme (C#)</span><span class="sxs-lookup"><span data-stu-id="66d82-102">Converting Data Types (C#)</span></span>
<span data-ttu-id="66d82-103">Dönüştürme yöntemleri giriş nesnelerinin türünü değiştirir.</span><span class="sxs-lookup"><span data-stu-id="66d82-103">Conversion methods change the type of input objects.</span></span>

 <span data-ttu-id="66d82-104">LINQ sorgularında dönüşüm işlemleri çeşitli uygulamalarda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="66d82-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="66d82-105">Aşağıda bazı örnekler verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="66d82-105">Following are some examples:</span></span>

- <span data-ttu-id="66d82-106">Yöntem, <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> bir türünün standart sorgu işlecinin özel uygulamasını gizlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="66d82-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>

- <span data-ttu-id="66d82-107">Yöntem, <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> LINQ sorgusu için parametresiz koleksiyonları etkinleştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="66d82-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>

- <span data-ttu-id="66d82-108"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> ve yöntemleri sorgu numaralandırılınkadar erteleyerek yerine hemen sorgu yürütme zorlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="66d82-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>

## <a name="methods"></a><span data-ttu-id="66d82-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="66d82-109">Methods</span></span>
 <span data-ttu-id="66d82-110">Aşağıdaki tabloda, veri türü dönüştürmeleri gerçekleştiren standart sorgu işleci yöntemleri listeleilmektedir.</span><span class="sxs-lookup"><span data-stu-id="66d82-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>

 <span data-ttu-id="66d82-111">Adları "As" ile başlayan bu tablodaki dönüştürme yöntemleri kaynak koleksiyonun statik türünü değiştirir, ancak sıralamaz.</span><span class="sxs-lookup"><span data-stu-id="66d82-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="66d82-112">Adları "To" ile başlayan yöntemler kaynak koleksiyonu nisbi olarak listeler ve öğeleri ilgili koleksiyon türüne koyar.</span><span class="sxs-lookup"><span data-stu-id="66d82-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>

|<span data-ttu-id="66d82-113">Yöntem Adı</span><span class="sxs-lookup"><span data-stu-id="66d82-113">Method Name</span></span>|<span data-ttu-id="66d82-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="66d82-114">Description</span></span>|<span data-ttu-id="66d82-115">C# Sorgu İfade Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="66d82-115">C# Query Expression Syntax</span></span>|<span data-ttu-id="66d82-116">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="66d82-116">More Information</span></span>|
|-----------------|-----------------|---------------------------------|----------------------|
|<span data-ttu-id="66d82-117">Asenumerable</span><span class="sxs-lookup"><span data-stu-id="66d82-117">AsEnumerable</span></span>|<span data-ttu-id="66d82-118">' olarak <xref:System.Collections.Generic.IEnumerable%601>yazılan girişi döndürür.</span><span class="sxs-lookup"><span data-stu-id="66d82-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="66d82-119">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="66d82-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="66d82-120">Asqueryable</span><span class="sxs-lookup"><span data-stu-id="66d82-120">AsQueryable</span></span>|<span data-ttu-id="66d82-121">Bir (genel) <xref:System.Collections.IEnumerable> bir (genel) <xref:System.Linq.IQueryable>dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="66d82-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="66d82-122">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="66d82-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="66d82-123">Cast</span><span class="sxs-lookup"><span data-stu-id="66d82-123">Cast</span></span>|<span data-ttu-id="66d82-124">Bir koleksiyonun öğelerini belirli bir türe atar.</span><span class="sxs-lookup"><span data-stu-id="66d82-124">Casts the elements of a collection to a specified type.</span></span>|<span data-ttu-id="66d82-125">Açıkça yazılan bir aralık değişkeni kullanın.</span><span class="sxs-lookup"><span data-stu-id="66d82-125">Use an explicitly typed range variable.</span></span> <span data-ttu-id="66d82-126">Örnek:</span><span class="sxs-lookup"><span data-stu-id="66d82-126">For example:</span></span><br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|
|<span data-ttu-id="66d82-127">Oftype</span><span class="sxs-lookup"><span data-stu-id="66d82-127">OfType</span></span>|<span data-ttu-id="66d82-128">Belirli bir türe döküm yeteneğine bağlı olarak değerleri filtreler.</span><span class="sxs-lookup"><span data-stu-id="66d82-128">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="66d82-129">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="66d82-129">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|<span data-ttu-id="66d82-130">Toarray</span><span class="sxs-lookup"><span data-stu-id="66d82-130">ToArray</span></span>|<span data-ttu-id="66d82-131">Koleksiyonu bir diziye dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="66d82-131">Converts a collection to an array.</span></span> <span data-ttu-id="66d82-132">Bu yöntem sorgu yürütmeyi zorlar.</span><span class="sxs-lookup"><span data-stu-id="66d82-132">This method forces query execution.</span></span>|<span data-ttu-id="66d82-133">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="66d82-133">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|
|<span data-ttu-id="66d82-134">Todictionary</span><span class="sxs-lookup"><span data-stu-id="66d82-134">ToDictionary</span></span>|<span data-ttu-id="66d82-135">Öğeleri önemli <xref:System.Collections.Generic.Dictionary%602> bir seçici işlevine dayalı bir şekilde koyar.</span><span class="sxs-lookup"><span data-stu-id="66d82-135">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="66d82-136">Bu yöntem sorgu yürütmeyi zorlar.</span><span class="sxs-lookup"><span data-stu-id="66d82-136">This method forces query execution.</span></span>|<span data-ttu-id="66d82-137">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="66d82-137">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|
|<span data-ttu-id="66d82-138">Tolist</span><span class="sxs-lookup"><span data-stu-id="66d82-138">ToList</span></span>|<span data-ttu-id="66d82-139">Bir koleksiyonu bir <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="66d82-139">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="66d82-140">Bu yöntem sorgu yürütmeyi zorlar.</span><span class="sxs-lookup"><span data-stu-id="66d82-140">This method forces query execution.</span></span>|<span data-ttu-id="66d82-141">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="66d82-141">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|
|<span data-ttu-id="66d82-142">Tolookup</span><span class="sxs-lookup"><span data-stu-id="66d82-142">ToLookup</span></span>|<span data-ttu-id="66d82-143">Öğeleri anahtar <xref:System.Linq.Lookup%602> seçici işlevini temel alan bir (bir-çok sözlük) içine koyar.</span><span class="sxs-lookup"><span data-stu-id="66d82-143">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="66d82-144">Bu yöntem sorgu yürütmeyi zorlar.</span><span class="sxs-lookup"><span data-stu-id="66d82-144">This method forces query execution.</span></span>|<span data-ttu-id="66d82-145">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="66d82-145">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a><span data-ttu-id="66d82-146">Sorgu İfadesözdizimi Örneği</span><span class="sxs-lookup"><span data-stu-id="66d82-146">Query Expression Syntax Example</span></span>

<span data-ttu-id="66d82-147">Aşağıdaki kod örneği, yalnızca alt türde kullanılabilen bir üyeye erişmeden önce bir türü bir alt türe atmak için açıkça yazılan bir aralık değişkeni kullanır.</span><span class="sxs-lookup"><span data-stu-id="66d82-147">The following code example uses an explicitly typed range variable to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="66d82-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66d82-148">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="66d82-149">Standart Sorgu Operatörlerine Genel Bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="66d82-149">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="66d82-150">fıkradan</span><span class="sxs-lookup"><span data-stu-id="66d82-150">from clause</span></span>](../../../language-reference/keywords/from-clause.md)
- [<span data-ttu-id="66d82-151">LINQ Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="66d82-151">LINQ Query Expressions</span></span>](../../../linq/index.md)
- [<span data-ttu-id="66d82-152">LINQ (C#) ile ArrayList nasıl sorgulanır?</span><span class="sxs-lookup"><span data-stu-id="66d82-152">How to query an ArrayList with LINQ (C#)</span></span>](./how-to-query-an-arraylist-with-linq.md)
