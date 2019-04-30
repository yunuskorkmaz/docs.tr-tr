---
title: Veri türlerini dönüştürme (C#)
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: ea1f204ab59ecdd3e3e7e65d12c1be37e9b09f01
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61702392"
---
# <a name="converting-data-types-c"></a><span data-ttu-id="d0002-102">Veri türlerini dönüştürme (C#)</span><span class="sxs-lookup"><span data-stu-id="d0002-102">Converting Data Types (C#)</span></span>
<span data-ttu-id="d0002-103">Dönüştürme yöntemleri giriş nesnelerin türünü değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d0002-103">Conversion methods change the type of input objects.</span></span>  
  
 <span data-ttu-id="d0002-104">LINQ sorguları dönüştürme işlemlerinde, çeşitli uygulamalar kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="d0002-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="d0002-105">Bazı örnekler aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="d0002-105">Following are some examples:</span></span>  
  
- <span data-ttu-id="d0002-106"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> Yöntemi, standart sorgu işleci bir türün özel uygulanışı gizlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d0002-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>  
  
- <span data-ttu-id="d0002-107"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> Yöntemi, LINQ sorgusu için koleksiyonları forceseek etkinleştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d0002-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>  
  
- <span data-ttu-id="d0002-108"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, Ve <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> yöntemleri ve sorgu numaralandırılana kadar bu erteleniyor yerine anlık sorgu yürütme zorlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d0002-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d0002-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d0002-109">Methods</span></span>  
 <span data-ttu-id="d0002-110">Aşağıdaki tabloda veri türü dönüşümleri gerçekleştirmek standart sorgu işleci yöntemleri listeler.</span><span class="sxs-lookup"><span data-stu-id="d0002-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>  
  
 <span data-ttu-id="d0002-111">"Statik kaynak toplama türünü değiştirebilirsiniz ancak bunu numaralandırmak değil olarak" adları ile başlayan dönüştürme yöntemleri bu tablodaki.</span><span class="sxs-lookup"><span data-stu-id="d0002-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="d0002-112">Adları ile kaynak derlemesini öğeleri ilgili koleksiyona eklediğiniz "" başlayın ve yöntemi yazın.</span><span class="sxs-lookup"><span data-stu-id="d0002-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>  
  
|<span data-ttu-id="d0002-113">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="d0002-113">Method Name</span></span>|<span data-ttu-id="d0002-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0002-114">Description</span></span>|<span data-ttu-id="d0002-115">C# sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0002-115">C# Query Expression Syntax</span></span>|<span data-ttu-id="d0002-116">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="d0002-116">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="d0002-117">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="d0002-117">AsEnumerable</span></span>|<span data-ttu-id="d0002-118">Giriş olarak yazılan döndürür <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="d0002-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="d0002-119">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="d0002-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d0002-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="d0002-120">AsQueryable</span></span>|<span data-ttu-id="d0002-121">(Genel) dönüştürür <xref:System.Collections.IEnumerable> (Genel) <xref:System.Linq.IQueryable>.</span><span class="sxs-lookup"><span data-stu-id="d0002-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="d0002-122">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="d0002-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d0002-123">Cast</span><span class="sxs-lookup"><span data-stu-id="d0002-123">Cast</span></span>|<span data-ttu-id="d0002-124">Belirli bir koleksiyonun öğeleri çevirir.</span><span class="sxs-lookup"><span data-stu-id="d0002-124">Casts the elements of a collection to a specified type.</span></span>|<span data-ttu-id="d0002-125">Açıkça yazılmış bir aralık değişkeni kullanın.</span><span class="sxs-lookup"><span data-stu-id="d0002-125">Use an explicitly typed range variable.</span></span> <span data-ttu-id="d0002-126">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="d0002-126">For example:</span></span><br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d0002-127">OfType</span><span class="sxs-lookup"><span data-stu-id="d0002-127">OfType</span></span>|<span data-ttu-id="d0002-128">Değerleri belirtilen bir türe yayınlanması için kendi yeteneği bağlı olarak filtreler.</span><span class="sxs-lookup"><span data-stu-id="d0002-128">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="d0002-129">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="d0002-129">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d0002-130">ToArray</span><span class="sxs-lookup"><span data-stu-id="d0002-130">ToArray</span></span>|<span data-ttu-id="d0002-131">Bir koleksiyonu bir diziye dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="d0002-131">Converts a collection to an array.</span></span> <span data-ttu-id="d0002-132">Bu yöntem, sorgu yürütme zorlar.</span><span class="sxs-lookup"><span data-stu-id="d0002-132">This method forces query execution.</span></span>|<span data-ttu-id="d0002-133">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="d0002-133">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d0002-134">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="d0002-134">ToDictionary</span></span>|<span data-ttu-id="d0002-135">Bu öğeleri eklemek koyar bir <xref:System.Collections.Generic.Dictionary%602> anahtar Seçici işleve göre.</span><span class="sxs-lookup"><span data-stu-id="d0002-135">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="d0002-136">Bu yöntem, sorgu yürütme zorlar.</span><span class="sxs-lookup"><span data-stu-id="d0002-136">This method forces query execution.</span></span>|<span data-ttu-id="d0002-137">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="d0002-137">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d0002-138">ToList</span><span class="sxs-lookup"><span data-stu-id="d0002-138">ToList</span></span>|<span data-ttu-id="d0002-139">Bir koleksiyona dönüştürür bir <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="d0002-139">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="d0002-140">Bu yöntem, sorgu yürütme zorlar.</span><span class="sxs-lookup"><span data-stu-id="d0002-140">This method forces query execution.</span></span>|<span data-ttu-id="d0002-141">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="d0002-141">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d0002-142">ToLookup</span><span class="sxs-lookup"><span data-stu-id="d0002-142">ToLookup</span></span>|<span data-ttu-id="d0002-143">Bu öğeleri eklemek koyar bir <xref:System.Linq.Lookup%602> (bire çok bir sözlük) tabanlı bir anahtar Seçici işlevdir.</span><span class="sxs-lookup"><span data-stu-id="d0002-143">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="d0002-144">Bu yöntem, sorgu yürütme zorlar.</span><span class="sxs-lookup"><span data-stu-id="d0002-144">This method forces query execution.</span></span>|<span data-ttu-id="d0002-145">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="d0002-145">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="d0002-146">Sorgu ifade sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="d0002-146">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="d0002-147">Aşağıdaki kod örneği bir açıkça yazılmış bir aralık değişkeni bir alt yalnızca alt türü üzerinde kullanılabilir olan bir üye erişmeden önce türüne için kullanır.</span><span class="sxs-lookup"><span data-stu-id="d0002-147">The following code example uses an explicitly-typed range variable  to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d0002-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0002-148">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="d0002-149">Standart sorgu işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="d0002-149">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="d0002-150">from yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="d0002-150">from clause</span></span>](../../../../csharp/language-reference/keywords/from-clause.md)
- [<span data-ttu-id="d0002-151">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="d0002-151">LINQ Query Expressions</span></span>](../../../../csharp/programming-guide/linq-query-expressions/index.md)
- [<span data-ttu-id="d0002-152">Nasıl yapılır: LINQ ile ArrayList sorgulama (C#)</span><span class="sxs-lookup"><span data-stu-id="d0002-152">How to: Query an ArrayList with LINQ (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
