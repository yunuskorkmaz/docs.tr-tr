---
title: "Dönüştürme veri türleri (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b0cf1ab-de48-4c6e-9f00-05b40fade46e
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5fb0e9dfb0f1fb882116449757ed0f0bf9029b39
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="converting-data-types-visual-basic"></a><span data-ttu-id="1528e-102">Dönüştürme veri türleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1528e-102">Converting Data Types (Visual Basic)</span></span>
<span data-ttu-id="1528e-103">Dönüştürme yöntemleri giriş nesnelerin türünü değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1528e-103">Conversion methods change the type of input objects.</span></span>  
  
 <span data-ttu-id="1528e-104">LINQ sorgularını dönüştürme işlemlerinde çeşitli uygulamalar yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="1528e-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="1528e-105">Bazı örnekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="1528e-105">Following are some examples:</span></span>  
  
-   <span data-ttu-id="1528e-106"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> Yöntemi, bir türün özel bir standart sorgu işleci uyarlamasını gizlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1528e-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>  
  
-   <span data-ttu-id="1528e-107"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> Yöntemi, LINQ sorgusu için koleksiyonları parametresiz etkinleştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1528e-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>  
  
-   <span data-ttu-id="1528e-108"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, Ve <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> yöntemleri, sorgu numaralandırılan kadar yerine onu ertelemeyi hemen sorgu yürütme zorlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1528e-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1528e-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1528e-109">Methods</span></span>  
 <span data-ttu-id="1528e-110">Aşağıdaki tabloda veri türü dönüşümleri gerçekleştirmek standart sorgu işleci yöntemlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="1528e-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>  
  
 <span data-ttu-id="1528e-111">Bu tabloda, adları "As" başlayın dönüştürme yöntemleri kaynak koleksiyonu statik türünü değiştirme ancak bunu numaralandırmak değil.</span><span class="sxs-lookup"><span data-stu-id="1528e-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="1528e-112">"Kaynak toplamasını ve öğeleri karşılık gelen koleksiyona koymak için" ile adları başlayan yöntemleri yazın.</span><span class="sxs-lookup"><span data-stu-id="1528e-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>  
  
|<span data-ttu-id="1528e-113">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="1528e-113">Method Name</span></span>|<span data-ttu-id="1528e-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1528e-114">Description</span></span>|<span data-ttu-id="1528e-115">Visual Basic sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1528e-115">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="1528e-116">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="1528e-116">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="1528e-117">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="1528e-117">AsEnumerable</span></span>|<span data-ttu-id="1528e-118">Olarak yazılan giriş döndürür <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="1528e-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="1528e-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="1528e-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="1528e-120">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="1528e-120">AsQueryable</span></span>|<span data-ttu-id="1528e-121">(Genel) dönüştürür <xref:System.Collections.IEnumerable> (Genel) <xref:System.Linq.IQueryable>.</span><span class="sxs-lookup"><span data-stu-id="1528e-121">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="1528e-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="1528e-122">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="1528e-123">Cast</span><span class="sxs-lookup"><span data-stu-id="1528e-123">Cast</span></span>|<span data-ttu-id="1528e-124">Belirtilen tür için bir koleksiyonun öğelerini çevirir.</span><span class="sxs-lookup"><span data-stu-id="1528e-124">Casts the elements of a collection to a specified type.</span></span>|`From … As …`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="1528e-125">OfType</span><span class="sxs-lookup"><span data-stu-id="1528e-125">OfType</span></span>|<span data-ttu-id="1528e-126">Değerleri yeteneklerini bir belirtilen türe göre filtreler.</span><span class="sxs-lookup"><span data-stu-id="1528e-126">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="1528e-127">Yok.</span><span class="sxs-lookup"><span data-stu-id="1528e-127">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="1528e-128">ToArray</span><span class="sxs-lookup"><span data-stu-id="1528e-128">ToArray</span></span>|<span data-ttu-id="1528e-129">Bir koleksiyonu bir diziye dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="1528e-129">Converts a collection to an array.</span></span> <span data-ttu-id="1528e-130">Bu yöntem, sorgu yürütme zorlar.</span><span class="sxs-lookup"><span data-stu-id="1528e-130">This method forces query execution.</span></span>|<span data-ttu-id="1528e-131">Yok.</span><span class="sxs-lookup"><span data-stu-id="1528e-131">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="1528e-132">Todictionary öğesini</span><span class="sxs-lookup"><span data-stu-id="1528e-132">ToDictionary</span></span>|<span data-ttu-id="1528e-133">Öğeler haline getirir bir <xref:System.Collections.Generic.Dictionary%602> bir anahtar Seçici işlevine bağlı.</span><span class="sxs-lookup"><span data-stu-id="1528e-133">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="1528e-134">Bu yöntem, sorgu yürütme zorlar.</span><span class="sxs-lookup"><span data-stu-id="1528e-134">This method forces query execution.</span></span>|<span data-ttu-id="1528e-135">Yok.</span><span class="sxs-lookup"><span data-stu-id="1528e-135">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="1528e-136">ToList</span><span class="sxs-lookup"><span data-stu-id="1528e-136">ToList</span></span>|<span data-ttu-id="1528e-137">Bir koleksiyona dönüştüren bir <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="1528e-137">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="1528e-138">Bu yöntem, sorgu yürütme zorlar.</span><span class="sxs-lookup"><span data-stu-id="1528e-138">This method forces query execution.</span></span>|<span data-ttu-id="1528e-139">Yok.</span><span class="sxs-lookup"><span data-stu-id="1528e-139">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="1528e-140">ToLookup</span><span class="sxs-lookup"><span data-stu-id="1528e-140">ToLookup</span></span>|<span data-ttu-id="1528e-141">Öğeler haline getirir bir <xref:System.Linq.Lookup%602> (bir-çok sözlük) dayalı bir anahtar Seçici işlevdir.</span><span class="sxs-lookup"><span data-stu-id="1528e-141">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="1528e-142">Bu yöntem, sorgu yürütme zorlar.</span><span class="sxs-lookup"><span data-stu-id="1528e-142">This method forces query execution.</span></span>|<span data-ttu-id="1528e-143">Yok.</span><span class="sxs-lookup"><span data-stu-id="1528e-143">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="1528e-144">Sorgu ifade sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="1528e-144">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="1528e-145">Aşağıdaki kod örneğinde `From As` yan tümcesi yalnızca alt üzerinde kullanılabilir üyesi erişmeden önce alt türüne yayınlanamıyor.</span><span class="sxs-lookup"><span data-stu-id="1528e-145">The following code example uses the `From As` clause to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1528e-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1528e-146">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="1528e-147">Standart sorgu işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1528e-147">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="1528e-148">From yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="1528e-148">From Clause</span></span>](../../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="1528e-149">Nasıl yapılır: LINQ (Visual Basic) ile ArrayList sorgulama</span><span class="sxs-lookup"><span data-stu-id="1528e-149">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
