---
title: Veri türlerini dönüştürme (C#)
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: 9e8b7726b94871a17a4be50a9b24d8b73abcf79c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594634"
---
# <a name="converting-data-types-c"></a><span data-ttu-id="8ca6f-102">Veri türlerini dönüştürme (C#)</span><span class="sxs-lookup"><span data-stu-id="8ca6f-102">Converting Data Types (C#)</span></span>
<span data-ttu-id="8ca6f-103">Dönüştürme yöntemleri giriş nesnelerinin türünü değiştirir.</span><span class="sxs-lookup"><span data-stu-id="8ca6f-103">Conversion methods change the type of input objects.</span></span>  
  
 <span data-ttu-id="8ca6f-104">LINQ sorgularındaki dönüştürme işlemleri çeşitli uygulamalarda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="8ca6f-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="8ca6f-105">Aşağıda bazı örnekler verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="8ca6f-105">Following are some examples:</span></span>  
  
- <span data-ttu-id="8ca6f-106">Yöntemi <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> , bir türün standart sorgu işlecinin özel uygulamasını gizlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8ca6f-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>  
  
- <span data-ttu-id="8ca6f-107">Yöntemi <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> , LINQ sorgulaması için parametreli olmayan koleksiyonları etkinleştirmek üzere kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8ca6f-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>  
  
- <span data-ttu-id="8ca6f-108">,, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>Ve yöntemleri,sorgunumaralandırılanakadar,sorguyürütmeyezorlamakyerinehemenbuişlemiyapmakiçinkullanılabilir.<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="8ca6f-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8ca6f-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8ca6f-109">Methods</span></span>  
 <span data-ttu-id="8ca6f-110">Aşağıdaki tabloda, veri türü dönüştürmeleri gerçekleştiren standart sorgu işleci yöntemleri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="8ca6f-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>  
  
 <span data-ttu-id="8ca6f-111">Bu tablodaki, adları "as" ile başlayan dönüştürme yöntemleri, kaynak koleksiyonun statik türünü değiştirir ancak onu numaralandırmaz.</span><span class="sxs-lookup"><span data-stu-id="8ca6f-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="8ca6f-112">Adları "to" ile başlayan Yöntemler, kaynak koleksiyonu numaralandırır ve öğeleri karşılık gelen koleksiyon türüne koyar.</span><span class="sxs-lookup"><span data-stu-id="8ca6f-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>  
  
|<span data-ttu-id="8ca6f-113">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="8ca6f-113">Method Name</span></span>|<span data-ttu-id="8ca6f-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8ca6f-114">Description</span></span>|<span data-ttu-id="8ca6f-115">C#Sorgu Ifadesi söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8ca6f-115">C# Query Expression Syntax</span></span>|<span data-ttu-id="8ca6f-116">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="8ca6f-116">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="8ca6f-117">Asılabilir</span><span class="sxs-lookup"><span data-stu-id="8ca6f-117">AsEnumerable</span></span>|<span data-ttu-id="8ca6f-118">Olarak <xref:System.Collections.Generic.IEnumerable%601>yazılan girişi döndürür.</span><span class="sxs-lookup"><span data-stu-id="8ca6f-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="8ca6f-119">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="8ca6f-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="8ca6f-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="8ca6f-120">AsQueryable</span></span>|<span data-ttu-id="8ca6f-121">Bir (genel) <xref:System.Collections.IEnumerable> bir (genel) <xref:System.Linq.IQueryable>öğesine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="8ca6f-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="8ca6f-122">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="8ca6f-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="8ca6f-123">Cast</span><span class="sxs-lookup"><span data-stu-id="8ca6f-123">Cast</span></span>|<span data-ttu-id="8ca6f-124">Bir koleksiyonun öğelerini belirtilen bir türe yayınlar.</span><span class="sxs-lookup"><span data-stu-id="8ca6f-124">Casts the elements of a collection to a specified type.</span></span>|<span data-ttu-id="8ca6f-125">Açıkça yazılmış bir Aralık değişkeni kullanın.</span><span class="sxs-lookup"><span data-stu-id="8ca6f-125">Use an explicitly typed range variable.</span></span> <span data-ttu-id="8ca6f-126">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="8ca6f-126">For example:</span></span><br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="8ca6f-127">OfType</span><span class="sxs-lookup"><span data-stu-id="8ca6f-127">OfType</span></span>|<span data-ttu-id="8ca6f-128">Değerleri, belirli bir türe atama becerisine bağlı olarak filtreler.</span><span class="sxs-lookup"><span data-stu-id="8ca6f-128">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="8ca6f-129">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="8ca6f-129">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="8ca6f-130">ToArray</span><span class="sxs-lookup"><span data-stu-id="8ca6f-130">ToArray</span></span>|<span data-ttu-id="8ca6f-131">Bir koleksiyonu bir diziye dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="8ca6f-131">Converts a collection to an array.</span></span> <span data-ttu-id="8ca6f-132">Bu yöntem sorgu yürütmeyi zorlar.</span><span class="sxs-lookup"><span data-stu-id="8ca6f-132">This method forces query execution.</span></span>|<span data-ttu-id="8ca6f-133">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="8ca6f-133">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="8ca6f-134">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="8ca6f-134">ToDictionary</span></span>|<span data-ttu-id="8ca6f-135">Öğeleri bir <xref:System.Collections.Generic.Dictionary%602> anahtar Seçici işlevine göre içine koyar.</span><span class="sxs-lookup"><span data-stu-id="8ca6f-135">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="8ca6f-136">Bu yöntem sorgu yürütmeyi zorlar.</span><span class="sxs-lookup"><span data-stu-id="8ca6f-136">This method forces query execution.</span></span>|<span data-ttu-id="8ca6f-137">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="8ca6f-137">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="8ca6f-138">ToList</span><span class="sxs-lookup"><span data-stu-id="8ca6f-138">ToList</span></span>|<span data-ttu-id="8ca6f-139">Bir koleksiyonu öğesine <xref:System.Collections.Generic.List%601>dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="8ca6f-139">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="8ca6f-140">Bu yöntem sorgu yürütmeyi zorlar.</span><span class="sxs-lookup"><span data-stu-id="8ca6f-140">This method forces query execution.</span></span>|<span data-ttu-id="8ca6f-141">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="8ca6f-141">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="8ca6f-142">ToLookup</span><span class="sxs-lookup"><span data-stu-id="8ca6f-142">ToLookup</span></span>|<span data-ttu-id="8ca6f-143">Öğeleri bir <xref:System.Linq.Lookup%602> anahtar Seçici işlevine göre (bire çok sözlüğüne) yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="8ca6f-143">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="8ca6f-144">Bu yöntem sorgu yürütmeyi zorlar.</span><span class="sxs-lookup"><span data-stu-id="8ca6f-144">This method forces query execution.</span></span>|<span data-ttu-id="8ca6f-145">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="8ca6f-145">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="8ca6f-146">Sorgu Ifadesi söz dizimi örneği</span><span class="sxs-lookup"><span data-stu-id="8ca6f-146">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="8ca6f-147">Aşağıdaki kod örneği, yalnızca alt tür üzerinde kullanılabilir olan bir üyeye erişmeden önce bir türü bir alt türe dönüştürmek için, açıkça yazılmış bir Aralık değişkeni kullanır.</span><span class="sxs-lookup"><span data-stu-id="8ca6f-147">The following code example uses an explicitly-typed range variable  to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8ca6f-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ca6f-148">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="8ca6f-149">Standart sorgu Işleçlerine genelC#bakış ()</span><span class="sxs-lookup"><span data-stu-id="8ca6f-149">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="8ca6f-150">from yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="8ca6f-150">from clause</span></span>](../../../language-reference/keywords/from-clause.md)
- [<span data-ttu-id="8ca6f-151">LINQ sorgu Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="8ca6f-151">LINQ Query Expressions</span></span>](../../linq-query-expressions/index.md)
- [<span data-ttu-id="8ca6f-152">Nasıl yapılır: LINQ (C#) ile ArrayList 'i sorgulama</span><span class="sxs-lookup"><span data-stu-id="8ca6f-152">How to: Query an ArrayList with LINQ (C#)</span></span>](./how-to-query-an-arraylist-with-linq.md)
