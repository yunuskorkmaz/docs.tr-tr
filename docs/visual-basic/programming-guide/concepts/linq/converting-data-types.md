---
title: Veri Türlerini Dönüştürme
ms.date: 07/20/2015
ms.assetid: 9b0cf1ab-de48-4c6e-9f00-05b40fade46e
ms.openlocfilehash: 1394f53923ba850ae11fbc326a25c279589c3be1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410857"
---
# <a name="converting-data-types-visual-basic"></a><span data-ttu-id="4ac8f-102">Veri türlerini dönüştürme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ac8f-102">Converting Data Types (Visual Basic)</span></span>

<span data-ttu-id="4ac8f-103">Dönüştürme yöntemleri giriş nesnelerinin türünü değiştirir.</span><span class="sxs-lookup"><span data-stu-id="4ac8f-103">Conversion methods change the type of input objects.</span></span>

 <span data-ttu-id="4ac8f-104">LINQ sorgularındaki dönüştürme işlemleri çeşitli uygulamalarda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="4ac8f-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="4ac8f-105">Aşağıda bazı örnekler verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="4ac8f-105">The following are some examples:</span></span>

- <span data-ttu-id="4ac8f-106">Yöntemi, bir <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> türün standart sorgu işlecinin özel uygulamasını gizlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4ac8f-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>

- <span data-ttu-id="4ac8f-107"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType>Yöntemi, LINQ sorgulaması için parametreli olmayan koleksiyonları etkinleştirmek üzere kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4ac8f-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>

- <span data-ttu-id="4ac8f-108"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>,, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType> <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> Ve yöntemleri, <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> sorgu numaralandırılana kadar, sorgu yürütmeye zorlamak yerine hemen bu işlemi yapmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4ac8f-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>

## <a name="methods"></a><span data-ttu-id="4ac8f-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4ac8f-109">Methods</span></span>

<span data-ttu-id="4ac8f-110">Aşağıdaki tabloda, veri türü dönüştürmeleri gerçekleştiren standart sorgu işleci yöntemleri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="4ac8f-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>

<span data-ttu-id="4ac8f-111">Bu tablodaki, adları "as" ile başlayan dönüştürme yöntemleri, kaynak koleksiyonun statik türünü değiştirir ancak onu numaralandırmaz.</span><span class="sxs-lookup"><span data-stu-id="4ac8f-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="4ac8f-112">Adları "to" ile başlayan Yöntemler, kaynak koleksiyonu numaralandırır ve öğeleri karşılık gelen koleksiyon türüne koyar.</span><span class="sxs-lookup"><span data-stu-id="4ac8f-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>

|<span data-ttu-id="4ac8f-113">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="4ac8f-113">Method Name</span></span>|<span data-ttu-id="4ac8f-114">Description</span><span class="sxs-lookup"><span data-stu-id="4ac8f-114">Description</span></span>|<span data-ttu-id="4ac8f-115">Sorgu Ifadesi söz dizimini Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4ac8f-115">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="4ac8f-116">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="4ac8f-116">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="4ac8f-117">Asılabilir</span><span class="sxs-lookup"><span data-stu-id="4ac8f-117">AsEnumerable</span></span>|<span data-ttu-id="4ac8f-118">Olarak yazılan girişi döndürür <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="4ac8f-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="4ac8f-119">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="4ac8f-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="4ac8f-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="4ac8f-120">AsQueryable</span></span>|<span data-ttu-id="4ac8f-121">Bir (genel) bir <xref:System.Collections.IEnumerable> (genel) öğesine dönüştürür <xref:System.Linq.IQueryable> .</span><span class="sxs-lookup"><span data-stu-id="4ac8f-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="4ac8f-122">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="4ac8f-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="4ac8f-123">Cast</span><span class="sxs-lookup"><span data-stu-id="4ac8f-123">Cast</span></span>|<span data-ttu-id="4ac8f-124">Bir koleksiyonun öğelerini belirtilen bir türe yayınlar.</span><span class="sxs-lookup"><span data-stu-id="4ac8f-124">Casts the elements of a collection to a specified type.</span></span>|`From … As …`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|
|<span data-ttu-id="4ac8f-125">OfType</span><span class="sxs-lookup"><span data-stu-id="4ac8f-125">OfType</span></span>|<span data-ttu-id="4ac8f-126">Değerleri, belirli bir türe atama becerisine bağlı olarak filtreler.</span><span class="sxs-lookup"><span data-stu-id="4ac8f-126">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="4ac8f-127">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="4ac8f-127">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|<span data-ttu-id="4ac8f-128">ToArray</span><span class="sxs-lookup"><span data-stu-id="4ac8f-128">ToArray</span></span>|<span data-ttu-id="4ac8f-129">Bir koleksiyonu bir diziye dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="4ac8f-129">Converts a collection to an array.</span></span> <span data-ttu-id="4ac8f-130">Bu yöntem sorgu yürütmeyi zorlar.</span><span class="sxs-lookup"><span data-stu-id="4ac8f-130">This method forces query execution.</span></span>|<span data-ttu-id="4ac8f-131">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="4ac8f-131">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|
|<span data-ttu-id="4ac8f-132">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="4ac8f-132">ToDictionary</span></span>|<span data-ttu-id="4ac8f-133">Öğeleri bir <xref:System.Collections.Generic.Dictionary%602> anahtar Seçici işlevine göre içine koyar.</span><span class="sxs-lookup"><span data-stu-id="4ac8f-133">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="4ac8f-134">Bu yöntem sorgu yürütmeyi zorlar.</span><span class="sxs-lookup"><span data-stu-id="4ac8f-134">This method forces query execution.</span></span>|<span data-ttu-id="4ac8f-135">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="4ac8f-135">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|
|<span data-ttu-id="4ac8f-136">ToList</span><span class="sxs-lookup"><span data-stu-id="4ac8f-136">ToList</span></span>|<span data-ttu-id="4ac8f-137">Bir koleksiyonu öğesine dönüştürür <xref:System.Collections.Generic.List%601> .</span><span class="sxs-lookup"><span data-stu-id="4ac8f-137">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="4ac8f-138">Bu yöntem sorgu yürütmeyi zorlar.</span><span class="sxs-lookup"><span data-stu-id="4ac8f-138">This method forces query execution.</span></span>|<span data-ttu-id="4ac8f-139">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="4ac8f-139">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|
|<span data-ttu-id="4ac8f-140">ToLookup</span><span class="sxs-lookup"><span data-stu-id="4ac8f-140">ToLookup</span></span>|<span data-ttu-id="4ac8f-141">Öğeleri bir <xref:System.Linq.Lookup%602> anahtar Seçici işlevine göre (bire çok sözlüğüne) yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="4ac8f-141">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="4ac8f-142">Bu yöntem sorgu yürütmeyi zorlar.</span><span class="sxs-lookup"><span data-stu-id="4ac8f-142">This method forces query execution.</span></span>|<span data-ttu-id="4ac8f-143">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="4ac8f-143">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a><span data-ttu-id="4ac8f-144">Sorgu Ifadesi söz dizimi örneği</span><span class="sxs-lookup"><span data-stu-id="4ac8f-144">Query Expression Syntax Example</span></span>

<span data-ttu-id="4ac8f-145">Aşağıdaki kod örneği, `From As` yalnızca alt tür üzerinde kullanılabilir olan bir üyeye erişmeden önce bir türü bir alt türe dönüştürmek için yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="4ac8f-145">The following code example uses the `From As` clause to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>

```vb
Class Plant
    Public Property Name As String
End Class

Class CarnivorousPlant
    Inherits Plant
    Public Property TrapType As String
End Class

Sub Cast()

    Dim plants() As Plant = {
        New CarnivorousPlant With {.Name = "Venus Fly Trap", .TrapType = "Snap Trap"},
        New CarnivorousPlant With {.Name = "Pitcher Plant", .TrapType = "Pitfall Trap"},
        New CarnivorousPlant With {.Name = "Sundew", .TrapType = "Flypaper Trap"},
        New CarnivorousPlant With {.Name = "Waterwheel Plant", .TrapType = "Snap Trap"}}

    Dim query = From plant As CarnivorousPlant In plants
                Where plant.TrapType = "Snap Trap"
                Select plant

    Dim sb As New System.Text.StringBuilder()
    For Each plant In query
        sb.AppendLine(plant.Name)
    Next

    ' Display the results.
    MsgBox(sb.ToString())

    ' This code produces the following output:

    ' Venus Fly Trap
    ' Waterwheel Plant

End Sub
```

## <a name="see-also"></a><span data-ttu-id="4ac8f-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ac8f-146">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="4ac8f-147">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ac8f-147">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="4ac8f-148">From yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="4ac8f-148">From Clause</span></span>](../../../language-reference/queries/from-clause.md)
- [<span data-ttu-id="4ac8f-149">Nasıl yapılır: LINQ ile ArrayList 'i sorgulama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ac8f-149">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>](how-to-query-an-arraylist-with-linq.md)
