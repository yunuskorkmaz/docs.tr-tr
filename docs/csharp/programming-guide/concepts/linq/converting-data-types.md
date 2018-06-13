---
title: Dönüştürme veri türleri (C#)
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: 374ce15b8329c02c6b496a276a40fd9a60596e1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33335828"
---
# <a name="converting-data-types-c"></a><span data-ttu-id="361ba-102">Dönüştürme veri türleri (C#)</span><span class="sxs-lookup"><span data-stu-id="361ba-102">Converting Data Types (C#)</span></span>
<span data-ttu-id="361ba-103">Dönüştürme yöntemleri giriş nesnelerin türünü değiştirin.</span><span class="sxs-lookup"><span data-stu-id="361ba-103">Conversion methods change the type of input objects.</span></span>  
  
 <span data-ttu-id="361ba-104">LINQ sorgularını dönüştürme işlemlerinde çeşitli uygulamalar yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="361ba-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="361ba-105">Bazı örnekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="361ba-105">Following are some examples:</span></span>  
  
-   <span data-ttu-id="361ba-106"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> Yöntemi, bir türün özel bir standart sorgu işleci uyarlamasını gizlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="361ba-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>  
  
-   <span data-ttu-id="361ba-107"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> Yöntemi, LINQ sorgusu için koleksiyonları parametresiz etkinleştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="361ba-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>  
  
-   <span data-ttu-id="361ba-108"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, Ve <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> yöntemleri, sorgu numaralandırılan kadar yerine onu ertelemeyi hemen sorgu yürütme zorlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="361ba-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="361ba-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="361ba-109">Methods</span></span>  
 <span data-ttu-id="361ba-110">Aşağıdaki tabloda veri türü dönüşümleri gerçekleştirmek standart sorgu işleci yöntemlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="361ba-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>  
  
 <span data-ttu-id="361ba-111">Bu tabloda, adları "As" başlayın dönüştürme yöntemleri kaynak koleksiyonu statik türünü değiştirme ancak bunu numaralandırmak değil.</span><span class="sxs-lookup"><span data-stu-id="361ba-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="361ba-112">"Kaynak toplamasını ve öğeleri karşılık gelen koleksiyona koymak için" ile adları başlayan yöntemleri yazın.</span><span class="sxs-lookup"><span data-stu-id="361ba-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>  
  
|<span data-ttu-id="361ba-113">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="361ba-113">Method Name</span></span>|<span data-ttu-id="361ba-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="361ba-114">Description</span></span>|<span data-ttu-id="361ba-115">C# sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="361ba-115">C# Query Expression Syntax</span></span>|<span data-ttu-id="361ba-116">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="361ba-116">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="361ba-117">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="361ba-117">AsEnumerable</span></span>|<span data-ttu-id="361ba-118">Olarak yazılan giriş döndürür <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="361ba-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="361ba-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="361ba-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="361ba-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="361ba-120">AsQueryable</span></span>|<span data-ttu-id="361ba-121">(Genel) dönüştürür <xref:System.Collections.IEnumerable> (Genel) <xref:System.Linq.IQueryable>.</span><span class="sxs-lookup"><span data-stu-id="361ba-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="361ba-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="361ba-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="361ba-123">Cast</span><span class="sxs-lookup"><span data-stu-id="361ba-123">Cast</span></span>|<span data-ttu-id="361ba-124">Belirtilen tür için bir koleksiyonun öğelerini çevirir.</span><span class="sxs-lookup"><span data-stu-id="361ba-124">Casts the elements of a collection to a specified type.</span></span>|<span data-ttu-id="361ba-125">Açıkça belirtilmiş aralık değişkeni kullanın.</span><span class="sxs-lookup"><span data-stu-id="361ba-125">Use an explicitly typed range variable.</span></span> <span data-ttu-id="361ba-126">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="361ba-126">For example:</span></span><br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="361ba-127">OfType</span><span class="sxs-lookup"><span data-stu-id="361ba-127">OfType</span></span>|<span data-ttu-id="361ba-128">Değerleri yeteneklerini bir belirtilen türe göre filtreler.</span><span class="sxs-lookup"><span data-stu-id="361ba-128">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="361ba-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="361ba-129">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="361ba-130">ToArray</span><span class="sxs-lookup"><span data-stu-id="361ba-130">ToArray</span></span>|<span data-ttu-id="361ba-131">Bir koleksiyonu bir diziye dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="361ba-131">Converts a collection to an array.</span></span> <span data-ttu-id="361ba-132">Bu yöntem, sorgu yürütme zorlar.</span><span class="sxs-lookup"><span data-stu-id="361ba-132">This method forces query execution.</span></span>|<span data-ttu-id="361ba-133">Yok.</span><span class="sxs-lookup"><span data-stu-id="361ba-133">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="361ba-134">Todictionary öğesini</span><span class="sxs-lookup"><span data-stu-id="361ba-134">ToDictionary</span></span>|<span data-ttu-id="361ba-135">Öğeler haline getirir bir <xref:System.Collections.Generic.Dictionary%602> bir anahtar Seçici işlevine bağlı.</span><span class="sxs-lookup"><span data-stu-id="361ba-135">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="361ba-136">Bu yöntem, sorgu yürütme zorlar.</span><span class="sxs-lookup"><span data-stu-id="361ba-136">This method forces query execution.</span></span>|<span data-ttu-id="361ba-137">Yok.</span><span class="sxs-lookup"><span data-stu-id="361ba-137">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="361ba-138">ToList</span><span class="sxs-lookup"><span data-stu-id="361ba-138">ToList</span></span>|<span data-ttu-id="361ba-139">Bir koleksiyona dönüştüren bir <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="361ba-139">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="361ba-140">Bu yöntem, sorgu yürütme zorlar.</span><span class="sxs-lookup"><span data-stu-id="361ba-140">This method forces query execution.</span></span>|<span data-ttu-id="361ba-141">Yok.</span><span class="sxs-lookup"><span data-stu-id="361ba-141">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="361ba-142">ToLookup</span><span class="sxs-lookup"><span data-stu-id="361ba-142">ToLookup</span></span>|<span data-ttu-id="361ba-143">Öğeler haline getirir bir <xref:System.Linq.Lookup%602> (bir-çok sözlük) dayalı bir anahtar Seçici işlevdir.</span><span class="sxs-lookup"><span data-stu-id="361ba-143">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="361ba-144">Bu yöntem, sorgu yürütme zorlar.</span><span class="sxs-lookup"><span data-stu-id="361ba-144">This method forces query execution.</span></span>|<span data-ttu-id="361ba-145">Yok.</span><span class="sxs-lookup"><span data-stu-id="361ba-145">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="361ba-146">Sorgu ifade sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="361ba-146">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="361ba-147">Aşağıdaki kod örneğinde açıkça belirtilmiş aralık değişkeni bir alt türü yalnızca alt üzerinde kullanılabilir üyesi erişmeden önce türe için kullanır.</span><span class="sxs-lookup"><span data-stu-id="361ba-147">The following code example uses an explicitly-typed range variable  to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="361ba-148">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="361ba-148">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="361ba-149">Standart sorgu işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="361ba-149">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="361ba-150">from yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="361ba-150">from clause</span></span>](../../../../csharp/language-reference/keywords/from-clause.md)  
 [<span data-ttu-id="361ba-151">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="361ba-151">LINQ Query Expressions</span></span>](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="361ba-152">Nasıl yapılır: LINQ (C#) ile ArrayList sorgulama</span><span class="sxs-lookup"><span data-stu-id="361ba-152">How to: Query an ArrayList with LINQ (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
