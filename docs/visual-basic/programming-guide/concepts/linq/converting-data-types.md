---
title: Veri Türlerini Dönüştürme
ms.date: 07/20/2015
ms.assetid: 9b0cf1ab-de48-4c6e-9f00-05b40fade46e
ms.openlocfilehash: 25d21954f0bb7555f1f5666f83fb37f4f73e2a60
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354254"
---
# <a name="converting-data-types-visual-basic"></a><span data-ttu-id="eaaca-102">Veri türlerini dönüştürme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eaaca-102">Converting Data Types (Visual Basic)</span></span>

<span data-ttu-id="eaaca-103">Dönüştürme yöntemleri giriş nesnelerinin türünü değiştirir.</span><span class="sxs-lookup"><span data-stu-id="eaaca-103">Conversion methods change the type of input objects.</span></span>

 <span data-ttu-id="eaaca-104">LINQ sorgularındaki dönüştürme işlemleri çeşitli uygulamalarda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="eaaca-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="eaaca-105">Aşağıda bazı örnekler verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="eaaca-105">The following are some examples:</span></span>

- <span data-ttu-id="eaaca-106"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> yöntemi, bir türün standart sorgu işlecinin özel uygulamasını gizlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eaaca-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>

- <span data-ttu-id="eaaca-107"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> yöntemi, LINQ sorgulaması için parametreli olmayan koleksiyonları etkinleştirmek üzere kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eaaca-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>

- <span data-ttu-id="eaaca-108"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>ve <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> yöntemleri, sorgu numaralandırılana kadar, sorgu yürütmeye zorlamak yerine hemen bu işlemi yapmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eaaca-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>

## <a name="methods"></a><span data-ttu-id="eaaca-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="eaaca-109">Methods</span></span>

<span data-ttu-id="eaaca-110">Aşağıdaki tabloda, veri türü dönüştürmeleri gerçekleştiren standart sorgu işleci yöntemleri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="eaaca-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>

<span data-ttu-id="eaaca-111">Bu tablodaki, adları "as" ile başlayan dönüştürme yöntemleri, kaynak koleksiyonun statik türünü değiştirir ancak onu numaralandırmaz.</span><span class="sxs-lookup"><span data-stu-id="eaaca-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="eaaca-112">Adları "to" ile başlayan Yöntemler, kaynak koleksiyonu numaralandırır ve öğeleri karşılık gelen koleksiyon türüne koyar.</span><span class="sxs-lookup"><span data-stu-id="eaaca-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>

|<span data-ttu-id="eaaca-113">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="eaaca-113">Method Name</span></span>|<span data-ttu-id="eaaca-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eaaca-114">Description</span></span>|<span data-ttu-id="eaaca-115">Sorgu Ifadesi söz dizimini Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eaaca-115">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="eaaca-116">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="eaaca-116">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="eaaca-117">Asılabilir</span><span class="sxs-lookup"><span data-stu-id="eaaca-117">AsEnumerable</span></span>|<span data-ttu-id="eaaca-118"><xref:System.Collections.Generic.IEnumerable%601>olarak yazılan girişi döndürür.</span><span class="sxs-lookup"><span data-stu-id="eaaca-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="eaaca-119">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="eaaca-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="eaaca-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="eaaca-120">AsQueryable</span></span>|<span data-ttu-id="eaaca-121">Bir (genel) <xref:System.Collections.IEnumerable> bir (genel) <xref:System.Linq.IQueryable>dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="eaaca-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="eaaca-122">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="eaaca-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="eaaca-123">Cast</span><span class="sxs-lookup"><span data-stu-id="eaaca-123">Cast</span></span>|<span data-ttu-id="eaaca-124">Bir koleksiyonun öğelerini belirtilen bir türe yayınlar.</span><span class="sxs-lookup"><span data-stu-id="eaaca-124">Casts the elements of a collection to a specified type.</span></span>|`From … As …`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|
|<span data-ttu-id="eaaca-125">OfType</span><span class="sxs-lookup"><span data-stu-id="eaaca-125">OfType</span></span>|<span data-ttu-id="eaaca-126">Değerleri, belirli bir türe atama becerisine bağlı olarak filtreler.</span><span class="sxs-lookup"><span data-stu-id="eaaca-126">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="eaaca-127">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="eaaca-127">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|<span data-ttu-id="eaaca-128">ToArray</span><span class="sxs-lookup"><span data-stu-id="eaaca-128">ToArray</span></span>|<span data-ttu-id="eaaca-129">Bir koleksiyonu bir diziye dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="eaaca-129">Converts a collection to an array.</span></span> <span data-ttu-id="eaaca-130">Bu yöntem sorgu yürütmeyi zorlar.</span><span class="sxs-lookup"><span data-stu-id="eaaca-130">This method forces query execution.</span></span>|<span data-ttu-id="eaaca-131">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="eaaca-131">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|
|<span data-ttu-id="eaaca-132">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="eaaca-132">ToDictionary</span></span>|<span data-ttu-id="eaaca-133">Öğeleri bir anahtar Seçici işlevine göre <xref:System.Collections.Generic.Dictionary%602> koyar.</span><span class="sxs-lookup"><span data-stu-id="eaaca-133">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="eaaca-134">Bu yöntem sorgu yürütmeyi zorlar.</span><span class="sxs-lookup"><span data-stu-id="eaaca-134">This method forces query execution.</span></span>|<span data-ttu-id="eaaca-135">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="eaaca-135">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|
|<span data-ttu-id="eaaca-136">ToList</span><span class="sxs-lookup"><span data-stu-id="eaaca-136">ToList</span></span>|<span data-ttu-id="eaaca-137">Bir koleksiyonu bir <xref:System.Collections.Generic.List%601>dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="eaaca-137">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="eaaca-138">Bu yöntem sorgu yürütmeyi zorlar.</span><span class="sxs-lookup"><span data-stu-id="eaaca-138">This method forces query execution.</span></span>|<span data-ttu-id="eaaca-139">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="eaaca-139">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|
|<span data-ttu-id="eaaca-140">ToLookup</span><span class="sxs-lookup"><span data-stu-id="eaaca-140">ToLookup</span></span>|<span data-ttu-id="eaaca-141">Öğeleri bir anahtar Seçici işlevine göre bir <xref:System.Linq.Lookup%602> (bire çok sözlüğüne) koyar.</span><span class="sxs-lookup"><span data-stu-id="eaaca-141">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="eaaca-142">Bu yöntem sorgu yürütmeyi zorlar.</span><span class="sxs-lookup"><span data-stu-id="eaaca-142">This method forces query execution.</span></span>|<span data-ttu-id="eaaca-143">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="eaaca-143">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a><span data-ttu-id="eaaca-144">Sorgu Ifadesi söz dizimi örneği</span><span class="sxs-lookup"><span data-stu-id="eaaca-144">Query Expression Syntax Example</span></span>

<span data-ttu-id="eaaca-145">Aşağıdaki kod örneği, yalnızca alt tür üzerinde kullanılabilir olan bir üyeye erişmeden önce bir türü bir alt türe dönüştürmek için `From As` yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="eaaca-145">The following code example uses the `From As` clause to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="eaaca-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eaaca-146">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="eaaca-147">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eaaca-147">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="eaaca-148">From Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="eaaca-148">From Clause</span></span>](../../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="eaaca-149">Nasıl yapılır: LINQ ile ArrayList 'i sorgulama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eaaca-149">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
