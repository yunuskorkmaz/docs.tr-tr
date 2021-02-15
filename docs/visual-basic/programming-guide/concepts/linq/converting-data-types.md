---
description: 'Hakkında daha fazla bilgi edinin: veri türlerini dönüştürme (Visual Basic)'
title: Veri Türlerini Dönüştürme
ms.date: 07/20/2015
ms.assetid: 9b0cf1ab-de48-4c6e-9f00-05b40fade46e
ms.openlocfilehash: 7650f5d5d6f727b7815b9dd2de8a565e27fa18d9
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100428720"
---
# <a name="converting-data-types-visual-basic"></a><span data-ttu-id="01b16-103">Veri türlerini dönüştürme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01b16-103">Converting Data Types (Visual Basic)</span></span>

<span data-ttu-id="01b16-104">Dönüştürme yöntemleri giriş nesnelerinin türünü değiştirir.</span><span class="sxs-lookup"><span data-stu-id="01b16-104">Conversion methods change the type of input objects.</span></span>

 <span data-ttu-id="01b16-105">LINQ sorgularındaki dönüştürme işlemleri çeşitli uygulamalarda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="01b16-105">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="01b16-106">Aşağıda bazı örnekler verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="01b16-106">The following are some examples:</span></span>

- <span data-ttu-id="01b16-107">Yöntemi, bir <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> türün standart sorgu işlecinin özel uygulamasını gizlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="01b16-107">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>

- <span data-ttu-id="01b16-108"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType>Yöntemi, LINQ sorgulaması için parametreli olmayan koleksiyonları etkinleştirmek üzere kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="01b16-108">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>

- <span data-ttu-id="01b16-109"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>,, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType> <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> Ve yöntemleri, <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> sorgu numaralandırılana kadar, sorgu yürütmeye zorlamak yerine hemen bu işlemi yapmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="01b16-109">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>

## <a name="methods"></a><span data-ttu-id="01b16-110">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="01b16-110">Methods</span></span>

<span data-ttu-id="01b16-111">Aşağıdaki tabloda, veri türü dönüştürmeleri gerçekleştiren standart sorgu işleci yöntemleri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="01b16-111">The following table lists the standard query operator methods that perform data-type conversions.</span></span>

<span data-ttu-id="01b16-112">Bu tablodaki, adları "as" ile başlayan dönüştürme yöntemleri, kaynak koleksiyonun statik türünü değiştirir ancak onu numaralandırmaz.</span><span class="sxs-lookup"><span data-stu-id="01b16-112">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="01b16-113">Adları "to" ile başlayan Yöntemler, kaynak koleksiyonu numaralandırır ve öğeleri karşılık gelen koleksiyon türüne koyar.</span><span class="sxs-lookup"><span data-stu-id="01b16-113">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>

|<span data-ttu-id="01b16-114">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="01b16-114">Method Name</span></span>|<span data-ttu-id="01b16-115">Description</span><span class="sxs-lookup"><span data-stu-id="01b16-115">Description</span></span>|<span data-ttu-id="01b16-116">Sorgu Ifadesi söz dizimini Visual Basic</span><span class="sxs-lookup"><span data-stu-id="01b16-116">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="01b16-117">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="01b16-117">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="01b16-118">Asılabilir</span><span class="sxs-lookup"><span data-stu-id="01b16-118">AsEnumerable</span></span>|<span data-ttu-id="01b16-119">Olarak yazılan girişi döndürür <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="01b16-119">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="01b16-120">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="01b16-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="01b16-121">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="01b16-121">AsQueryable</span></span>|<span data-ttu-id="01b16-122">Bir (genel) bir <xref:System.Collections.IEnumerable> (genel) öğesine dönüştürür <xref:System.Linq.IQueryable> .</span><span class="sxs-lookup"><span data-stu-id="01b16-122">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="01b16-123">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="01b16-123">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="01b16-124">Cast</span><span class="sxs-lookup"><span data-stu-id="01b16-124">Cast</span></span>|<span data-ttu-id="01b16-125">Bir koleksiyonun öğelerini belirtilen bir türe yayınlar.</span><span class="sxs-lookup"><span data-stu-id="01b16-125">Casts the elements of a collection to a specified type.</span></span>|`From … As …`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|
|<span data-ttu-id="01b16-126">OfType</span><span class="sxs-lookup"><span data-stu-id="01b16-126">OfType</span></span>|<span data-ttu-id="01b16-127">Değerleri, belirli bir türe atama becerisine bağlı olarak filtreler.</span><span class="sxs-lookup"><span data-stu-id="01b16-127">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="01b16-128">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="01b16-128">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|<span data-ttu-id="01b16-129">ToArray</span><span class="sxs-lookup"><span data-stu-id="01b16-129">ToArray</span></span>|<span data-ttu-id="01b16-130">Bir koleksiyonu bir diziye dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="01b16-130">Converts a collection to an array.</span></span> <span data-ttu-id="01b16-131">Bu yöntem sorgu yürütmeyi zorlar.</span><span class="sxs-lookup"><span data-stu-id="01b16-131">This method forces query execution.</span></span>|<span data-ttu-id="01b16-132">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="01b16-132">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|
|<span data-ttu-id="01b16-133">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="01b16-133">ToDictionary</span></span>|<span data-ttu-id="01b16-134">Öğeleri bir <xref:System.Collections.Generic.Dictionary%602> anahtar Seçici işlevine göre içine koyar.</span><span class="sxs-lookup"><span data-stu-id="01b16-134">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="01b16-135">Bu yöntem sorgu yürütmeyi zorlar.</span><span class="sxs-lookup"><span data-stu-id="01b16-135">This method forces query execution.</span></span>|<span data-ttu-id="01b16-136">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="01b16-136">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|
|<span data-ttu-id="01b16-137">ToList</span><span class="sxs-lookup"><span data-stu-id="01b16-137">ToList</span></span>|<span data-ttu-id="01b16-138">Bir koleksiyonu öğesine dönüştürür <xref:System.Collections.Generic.List%601> .</span><span class="sxs-lookup"><span data-stu-id="01b16-138">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="01b16-139">Bu yöntem sorgu yürütmeyi zorlar.</span><span class="sxs-lookup"><span data-stu-id="01b16-139">This method forces query execution.</span></span>|<span data-ttu-id="01b16-140">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="01b16-140">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|
|<span data-ttu-id="01b16-141">ToLookup</span><span class="sxs-lookup"><span data-stu-id="01b16-141">ToLookup</span></span>|<span data-ttu-id="01b16-142">Öğeleri bir <xref:System.Linq.Lookup%602> anahtar Seçici işlevine göre (bire çok sözlüğüne) yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="01b16-142">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="01b16-143">Bu yöntem sorgu yürütmeyi zorlar.</span><span class="sxs-lookup"><span data-stu-id="01b16-143">This method forces query execution.</span></span>|<span data-ttu-id="01b16-144">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="01b16-144">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a><span data-ttu-id="01b16-145">Sorgu Ifadesi söz dizimi örneği</span><span class="sxs-lookup"><span data-stu-id="01b16-145">Query Expression Syntax Example</span></span>

<span data-ttu-id="01b16-146">Aşağıdaki kod örneği, `From As` yalnızca alt tür üzerinde kullanılabilir olan bir üyeye erişmeden önce bir türü bir alt türe dönüştürmek için yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="01b16-146">The following code example uses the `From As` clause to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="01b16-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01b16-147">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="01b16-148">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01b16-148">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="01b16-149">From yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="01b16-149">From Clause</span></span>](../../../language-reference/queries/from-clause.md)
- [<span data-ttu-id="01b16-150">Nasıl yapılır: LINQ ile ArrayList 'i sorgulama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01b16-150">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>](how-to-query-an-arraylist-with-linq.md)
