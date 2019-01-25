---
title: Dönüştürme veri türleri (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9b0cf1ab-de48-4c6e-9f00-05b40fade46e
ms.openlocfilehash: 3845c14bc7390d486668916fe7d5d5ad840b7990
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54653742"
---
# <a name="converting-data-types-visual-basic"></a><span data-ttu-id="d981c-102">Dönüştürme veri türleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d981c-102">Converting Data Types (Visual Basic)</span></span>
<span data-ttu-id="d981c-103">Dönüştürme yöntemleri giriş nesnelerin türünü değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d981c-103">Conversion methods change the type of input objects.</span></span>  
  
 <span data-ttu-id="d981c-104">LINQ sorguları dönüştürme işlemlerinde, çeşitli uygulamalar kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="d981c-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="d981c-105">Bazı örnekler aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="d981c-105">Following are some examples:</span></span>  
  
-   <span data-ttu-id="d981c-106"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> Yöntemi, standart sorgu işleci bir türün özel uygulanışı gizlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d981c-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>  
  
-   <span data-ttu-id="d981c-107"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> Yöntemi, LINQ sorgusu için koleksiyonları forceseek etkinleştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d981c-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>  
  
-   <span data-ttu-id="d981c-108"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, Ve <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> yöntemleri ve sorgu numaralandırılana kadar bu erteleniyor yerine anlık sorgu yürütme zorlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d981c-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d981c-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d981c-109">Methods</span></span>  
 <span data-ttu-id="d981c-110">Aşağıdaki tabloda veri türü dönüşümleri gerçekleştirmek standart sorgu işleci yöntemleri listeler.</span><span class="sxs-lookup"><span data-stu-id="d981c-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>  
  
 <span data-ttu-id="d981c-111">"Statik kaynak toplama türünü değiştirebilirsiniz ancak bunu numaralandırmak değil olarak" adları ile başlayan dönüştürme yöntemleri bu tablodaki.</span><span class="sxs-lookup"><span data-stu-id="d981c-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="d981c-112">Adları ile kaynak derlemesini öğeleri ilgili koleksiyona eklediğiniz "" başlayın ve yöntemi yazın.</span><span class="sxs-lookup"><span data-stu-id="d981c-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>  
  
|<span data-ttu-id="d981c-113">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="d981c-113">Method Name</span></span>|<span data-ttu-id="d981c-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d981c-114">Description</span></span>|<span data-ttu-id="d981c-115">Visual Basic sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d981c-115">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="d981c-116">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="d981c-116">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="d981c-117">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="d981c-117">AsEnumerable</span></span>|<span data-ttu-id="d981c-118">Giriş olarak yazılan döndürür <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="d981c-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="d981c-119">Uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="d981c-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d981c-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="d981c-120">AsQueryable</span></span>|<span data-ttu-id="d981c-121">(Genel) dönüştürür <xref:System.Collections.IEnumerable> (Genel) <xref:System.Linq.IQueryable>.</span><span class="sxs-lookup"><span data-stu-id="d981c-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="d981c-122">Uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="d981c-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d981c-123">Cast</span><span class="sxs-lookup"><span data-stu-id="d981c-123">Cast</span></span>|<span data-ttu-id="d981c-124">Belirli bir koleksiyonun öğeleri çevirir.</span><span class="sxs-lookup"><span data-stu-id="d981c-124">Casts the elements of a collection to a specified type.</span></span>|`From … As …`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d981c-125">OfType</span><span class="sxs-lookup"><span data-stu-id="d981c-125">OfType</span></span>|<span data-ttu-id="d981c-126">Değerleri belirtilen bir türe yayınlanması için kendi yeteneği bağlı olarak filtreler.</span><span class="sxs-lookup"><span data-stu-id="d981c-126">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="d981c-127">Uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="d981c-127">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d981c-128">ToArray</span><span class="sxs-lookup"><span data-stu-id="d981c-128">ToArray</span></span>|<span data-ttu-id="d981c-129">Bir koleksiyonu bir diziye dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="d981c-129">Converts a collection to an array.</span></span> <span data-ttu-id="d981c-130">Bu yöntem, sorgu yürütme zorlar.</span><span class="sxs-lookup"><span data-stu-id="d981c-130">This method forces query execution.</span></span>|<span data-ttu-id="d981c-131">Uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="d981c-131">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d981c-132">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="d981c-132">ToDictionary</span></span>|<span data-ttu-id="d981c-133">Bu öğeleri eklemek koyar bir <xref:System.Collections.Generic.Dictionary%602> anahtar Seçici işleve göre.</span><span class="sxs-lookup"><span data-stu-id="d981c-133">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="d981c-134">Bu yöntem, sorgu yürütme zorlar.</span><span class="sxs-lookup"><span data-stu-id="d981c-134">This method forces query execution.</span></span>|<span data-ttu-id="d981c-135">Uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="d981c-135">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d981c-136">ToList</span><span class="sxs-lookup"><span data-stu-id="d981c-136">ToList</span></span>|<span data-ttu-id="d981c-137">Bir koleksiyona dönüştürür bir <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="d981c-137">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="d981c-138">Bu yöntem, sorgu yürütme zorlar.</span><span class="sxs-lookup"><span data-stu-id="d981c-138">This method forces query execution.</span></span>|<span data-ttu-id="d981c-139">Uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="d981c-139">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d981c-140">ToLookup</span><span class="sxs-lookup"><span data-stu-id="d981c-140">ToLookup</span></span>|<span data-ttu-id="d981c-141">Bu öğeleri eklemek koyar bir <xref:System.Linq.Lookup%602> (bire çok bir sözlük) tabanlı bir anahtar Seçici işlevdir.</span><span class="sxs-lookup"><span data-stu-id="d981c-141">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="d981c-142">Bu yöntem, sorgu yürütme zorlar.</span><span class="sxs-lookup"><span data-stu-id="d981c-142">This method forces query execution.</span></span>|<span data-ttu-id="d981c-143">Uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="d981c-143">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="d981c-144">Sorgu ifade sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="d981c-144">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="d981c-145">Aşağıdaki kod örneğinde `From As` yan tümcesini yalnızca alt türü üzerinde kullanılabilir olan bir üye erişmeden önce alt türüne dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="d981c-145">The following code example uses the `From As` clause to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d981c-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d981c-146">See also</span></span>
- <xref:System.Linq>
- [<span data-ttu-id="d981c-147">Standart sorgu işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d981c-147">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="d981c-148">From Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="d981c-148">From Clause</span></span>](../../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="d981c-149">Nasıl yapılır: (Visual Basic) LINQ ile ArrayList sorgulama</span><span class="sxs-lookup"><span data-stu-id="d981c-149">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
