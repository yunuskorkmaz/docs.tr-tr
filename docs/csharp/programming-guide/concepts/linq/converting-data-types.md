---
title: Veri türlerini dönüştürme (C#)
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: 54ef612ad4e92058d9af4d96b7b3cde9732b2f9c
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45585752"
---
# <a name="converting-data-types-c"></a><span data-ttu-id="19c31-102">Veri türlerini dönüştürme (C#)</span><span class="sxs-lookup"><span data-stu-id="19c31-102">Converting Data Types (C#)</span></span>
<span data-ttu-id="19c31-103">Dönüştürme yöntemleri giriş nesnelerin türünü değiştirin.</span><span class="sxs-lookup"><span data-stu-id="19c31-103">Conversion methods change the type of input objects.</span></span>  
  
 <span data-ttu-id="19c31-104">LINQ sorguları dönüştürme işlemlerinde, çeşitli uygulamalar kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="19c31-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="19c31-105">Bazı örnekler aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="19c31-105">Following are some examples:</span></span>  
  
-   <span data-ttu-id="19c31-106"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> Yöntemi, standart sorgu işleci bir türün özel uygulanışı gizlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="19c31-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>  
  
-   <span data-ttu-id="19c31-107"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> Yöntemi, LINQ sorgusu için koleksiyonları forceseek etkinleştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="19c31-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>  
  
-   <span data-ttu-id="19c31-108"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, Ve <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> yöntemleri ve sorgu numaralandırılana kadar bu erteleniyor yerine anlık sorgu yürütme zorlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="19c31-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="19c31-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="19c31-109">Methods</span></span>  
 <span data-ttu-id="19c31-110">Aşağıdaki tabloda veri türü dönüşümleri gerçekleştirmek standart sorgu işleci yöntemleri listeler.</span><span class="sxs-lookup"><span data-stu-id="19c31-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>  
  
 <span data-ttu-id="19c31-111">"Statik kaynak toplama türünü değiştirebilirsiniz ancak bunu numaralandırmak değil olarak" adları ile başlayan dönüştürme yöntemleri bu tablodaki.</span><span class="sxs-lookup"><span data-stu-id="19c31-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="19c31-112">Adları ile kaynak derlemesini öğeleri ilgili koleksiyona eklediğiniz "" başlayın ve yöntemi yazın.</span><span class="sxs-lookup"><span data-stu-id="19c31-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>  
  
|<span data-ttu-id="19c31-113">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="19c31-113">Method Name</span></span>|<span data-ttu-id="19c31-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="19c31-114">Description</span></span>|<span data-ttu-id="19c31-115">C# sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="19c31-115">C# Query Expression Syntax</span></span>|<span data-ttu-id="19c31-116">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="19c31-116">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="19c31-117">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="19c31-117">AsEnumerable</span></span>|<span data-ttu-id="19c31-118">Giriş olarak yazılan döndürür <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="19c31-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="19c31-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="19c31-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="19c31-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="19c31-120">AsQueryable</span></span>|<span data-ttu-id="19c31-121">(Genel) dönüştürür <xref:System.Collections.IEnumerable> (Genel) <xref:System.Linq.IQueryable>.</span><span class="sxs-lookup"><span data-stu-id="19c31-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="19c31-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="19c31-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="19c31-123">Cast</span><span class="sxs-lookup"><span data-stu-id="19c31-123">Cast</span></span>|<span data-ttu-id="19c31-124">Belirli bir koleksiyonun öğeleri çevirir.</span><span class="sxs-lookup"><span data-stu-id="19c31-124">Casts the elements of a collection to a specified type.</span></span>|<span data-ttu-id="19c31-125">Açıkça yazılmış bir aralık değişkeni kullanın.</span><span class="sxs-lookup"><span data-stu-id="19c31-125">Use an explicitly typed range variable.</span></span> <span data-ttu-id="19c31-126">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="19c31-126">For example:</span></span><br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="19c31-127">OfType</span><span class="sxs-lookup"><span data-stu-id="19c31-127">OfType</span></span>|<span data-ttu-id="19c31-128">Değerleri belirtilen bir türe yayınlanması için kendi yeteneği bağlı olarak filtreler.</span><span class="sxs-lookup"><span data-stu-id="19c31-128">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="19c31-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="19c31-129">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="19c31-130">ToArray</span><span class="sxs-lookup"><span data-stu-id="19c31-130">ToArray</span></span>|<span data-ttu-id="19c31-131">Bir koleksiyonu bir diziye dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="19c31-131">Converts a collection to an array.</span></span> <span data-ttu-id="19c31-132">Bu yöntem, sorgu yürütme zorlar.</span><span class="sxs-lookup"><span data-stu-id="19c31-132">This method forces query execution.</span></span>|<span data-ttu-id="19c31-133">Yok.</span><span class="sxs-lookup"><span data-stu-id="19c31-133">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="19c31-134">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="19c31-134">ToDictionary</span></span>|<span data-ttu-id="19c31-135">Bu öğeleri eklemek koyar bir <xref:System.Collections.Generic.Dictionary%602> anahtar Seçici işleve göre.</span><span class="sxs-lookup"><span data-stu-id="19c31-135">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="19c31-136">Bu yöntem, sorgu yürütme zorlar.</span><span class="sxs-lookup"><span data-stu-id="19c31-136">This method forces query execution.</span></span>|<span data-ttu-id="19c31-137">Yok.</span><span class="sxs-lookup"><span data-stu-id="19c31-137">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="19c31-138">ToList</span><span class="sxs-lookup"><span data-stu-id="19c31-138">ToList</span></span>|<span data-ttu-id="19c31-139">Bir koleksiyona dönüştürür bir <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="19c31-139">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="19c31-140">Bu yöntem, sorgu yürütme zorlar.</span><span class="sxs-lookup"><span data-stu-id="19c31-140">This method forces query execution.</span></span>|<span data-ttu-id="19c31-141">Yok.</span><span class="sxs-lookup"><span data-stu-id="19c31-141">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="19c31-142">ToLookup</span><span class="sxs-lookup"><span data-stu-id="19c31-142">ToLookup</span></span>|<span data-ttu-id="19c31-143">Bu öğeleri eklemek koyar bir <xref:System.Linq.Lookup%602> (bire çok bir sözlük) tabanlı bir anahtar Seçici işlevdir.</span><span class="sxs-lookup"><span data-stu-id="19c31-143">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="19c31-144">Bu yöntem, sorgu yürütme zorlar.</span><span class="sxs-lookup"><span data-stu-id="19c31-144">This method forces query execution.</span></span>|<span data-ttu-id="19c31-145">Yok.</span><span class="sxs-lookup"><span data-stu-id="19c31-145">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="19c31-146">Sorgu ifade sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="19c31-146">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="19c31-147">Aşağıdaki kod örneği bir açıkça yazılmış bir aralık değişkeni bir alt yalnızca alt türü üzerinde kullanılabilir olan bir üye erişmeden önce türüne için kullanır.</span><span class="sxs-lookup"><span data-stu-id="19c31-147">The following code example uses an explicitly-typed range variable  to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="19c31-148">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="19c31-148">See Also</span></span>

- <xref:System.Linq>  
- [<span data-ttu-id="19c31-149">Standart sorgu işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="19c31-149">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
- [<span data-ttu-id="19c31-150">from yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="19c31-150">from clause</span></span>](../../../../csharp/language-reference/keywords/from-clause.md)  
- [<span data-ttu-id="19c31-151">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="19c31-151">LINQ Query Expressions</span></span>](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
- [<span data-ttu-id="19c31-152">Nasıl yapılır: LINQ (C#) ile ArrayList sorgulama</span><span class="sxs-lookup"><span data-stu-id="19c31-152">How to: Query an ArrayList with LINQ (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
