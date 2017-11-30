---
title: "Sıralama veri (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f81065c-0c89-4bf3-a6d8-442273f8810e
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8f17c6ecad721dd3a48a01c09693b0a1cf723a5b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="sorting-data-visual-basic"></a><span data-ttu-id="2f51d-102">Sıralama veri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f51d-102">Sorting Data (Visual Basic)</span></span>
<span data-ttu-id="2f51d-103">Sıralama işlemi bir veya daha fazla özniteliklerini temel alarak bir sıradaki sıralar.</span><span class="sxs-lookup"><span data-stu-id="2f51d-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="2f51d-104">İlk sıralama ölçütü birincil sıralama öğeleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="2f51d-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="2f51d-105">İkinci bir sıralama ölçütü belirterek, her birincil sıralama grup içindeki öğeleri sıralama yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f51d-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>  
  
 <span data-ttu-id="2f51d-106">Aşağıdaki çizimde bir dizi karakterden oluşan bir alfabetik sıralama işlemi sonuçlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2f51d-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters.</span></span>  
  
 <span data-ttu-id="2f51d-107">![Sıralama işlemi LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")</span><span class="sxs-lookup"><span data-stu-id="2f51d-107">![LINQ Sorting Operation](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")</span></span>  
  
 <span data-ttu-id="2f51d-108">Verileri sıralama standart sorgu işleci yöntemler aşağıdaki bölümde listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="2f51d-108">The standard query operator methods that sort data are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2f51d-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2f51d-109">Methods</span></span>  
  
|<span data-ttu-id="2f51d-110">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="2f51d-110">Method Name</span></span>|<span data-ttu-id="2f51d-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2f51d-111">Description</span></span>|<span data-ttu-id="2f51d-112">Visual Basic sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2f51d-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="2f51d-113">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="2f51d-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="2f51d-114">OrderBy</span><span class="sxs-lookup"><span data-stu-id="2f51d-114">OrderBy</span></span>|<span data-ttu-id="2f51d-115">Artan düzende değerlerini sıralar.</span><span class="sxs-lookup"><span data-stu-id="2f51d-115">Sorts values in ascending order.</span></span>|`Order By`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="2f51d-116">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="2f51d-116">OrderByDescending</span></span>|<span data-ttu-id="2f51d-117">Azalan düzende değerlerini sıralar.</span><span class="sxs-lookup"><span data-stu-id="2f51d-117">Sorts values in descending order.</span></span>|`Order By … Descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="2f51d-118">ThenBy</span><span class="sxs-lookup"><span data-stu-id="2f51d-118">ThenBy</span></span>|<span data-ttu-id="2f51d-119">İkincil bir sıralama artan düzende gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="2f51d-119">Performs a secondary sort in ascending order.</span></span>|`Order By …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="2f51d-120">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="2f51d-120">ThenByDescending</span></span>|<span data-ttu-id="2f51d-121">İkincil bir sıralamayı azalan sırada gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="2f51d-121">Performs a secondary sort in descending order.</span></span>|`Order By …, … Descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="2f51d-122">Ters Çevir</span><span class="sxs-lookup"><span data-stu-id="2f51d-122">Reverse</span></span>|<span data-ttu-id="2f51d-123">Bir koleksiyondaki öğelerin sırasını tersine çevirir.</span><span class="sxs-lookup"><span data-stu-id="2f51d-123">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="2f51d-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="2f51d-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="2f51d-125">Sorgu ifade sözdizimi örnekleri</span><span class="sxs-lookup"><span data-stu-id="2f51d-125">Query Expression Syntax Examples</span></span>  
  
### <a name="primary-sort-examples"></a><span data-ttu-id="2f51d-126">Birincil sıralama örnekleri</span><span class="sxs-lookup"><span data-stu-id="2f51d-126">Primary Sort Examples</span></span>  
  
#### <a name="primary-ascending-sort"></a><span data-ttu-id="2f51d-127">Birincil artan sıralama</span><span class="sxs-lookup"><span data-stu-id="2f51d-127">Primary Ascending Sort</span></span>  
 <span data-ttu-id="2f51d-128">Aşağıdaki örnekte nasıl kullanılacağı ortaya `Order By` dize uzunluğu, artan bir dizi dizelerde sıralamak için bir LINQ sorgu yan tümcesinde.</span><span class="sxs-lookup"><span data-stu-id="2f51d-128">The following example demonstrates how to use the `Order By` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Length   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' the  
' fox  
' quick  
' brown  
' jumps  
```  
  
#### <a name="primary-descending-sort"></a><span data-ttu-id="2f51d-129">Birincil azalan sıralama</span><span class="sxs-lookup"><span data-stu-id="2f51d-129">Primary Descending Sort</span></span>  
 <span data-ttu-id="2f51d-130">Sonraki örnek nasıl kullanılacağı ortaya `Order By Descending` azalan sırada kendi ilk harfi dizeleri sıralamak için bir LINQ sorgu yan tümcesinde.</span><span class="sxs-lookup"><span data-stu-id="2f51d-130">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Substring(0, 1) Descending   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' the  
' quick  
' jumps  
' fox  
' brown  
```  
  
### <a name="secondary-sort-examples"></a><span data-ttu-id="2f51d-131">İkincil sıralama örnekleri</span><span class="sxs-lookup"><span data-stu-id="2f51d-131">Secondary Sort Examples</span></span>  
  
#### <a name="secondary-ascending-sort"></a><span data-ttu-id="2f51d-132">İkincil artan sıralama</span><span class="sxs-lookup"><span data-stu-id="2f51d-132">Secondary Ascending Sort</span></span>  
 <span data-ttu-id="2f51d-133">Aşağıdaki örnekte nasıl kullanılacağı ortaya `Order By` dizeleri birincil ve ikincil bir tür bir dizide gerçekleştirmek için bir LINQ sorgu yan tümcesinde.</span><span class="sxs-lookup"><span data-stu-id="2f51d-133">The following example demonstrates how to use the `Order By` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="2f51d-134">Dizeleri öncelikle uzunluğu ve ürüne ilk harfini dizesinin hem artan düzende sıralanır.</span><span class="sxs-lookup"><span data-stu-id="2f51d-134">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Length, word.Substring(0, 1)   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' fox  
' the  
' brown  
' jumps  
' quick  
```  
  
#### <a name="secondary-descending-sort"></a><span data-ttu-id="2f51d-135">İkincil azalan sıralama</span><span class="sxs-lookup"><span data-stu-id="2f51d-135">Secondary Descending Sort</span></span>  
 <span data-ttu-id="2f51d-136">Sonraki örnek nasıl kullanılacağı ortaya `Order By Descending` birincil bir sıralama düzeni ve azalan bir ikincil sıralama artan düzende gerçekleştirmek için bir LINQ sorgu yan tümcesinde.</span><span class="sxs-lookup"><span data-stu-id="2f51d-136">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="2f51d-137">Dizeleri öncelikle uzunluğu ve ürüne dizenin ilk harfini sıralanır.</span><span class="sxs-lookup"><span data-stu-id="2f51d-137">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Length, word.Substring(0, 1) Descending   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' fox  
' the  
' quick  
' jumps  
' brown  
```  
  
## <a name="see-also"></a><span data-ttu-id="2f51d-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2f51d-138">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="2f51d-139">Standart sorgu işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f51d-139">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="2f51d-140">Order By tümcesi</span><span class="sxs-lookup"><span data-stu-id="2f51d-140">Order By Clause</span></span>](../../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [<span data-ttu-id="2f51d-141">Nasıl yapılır: sorgu sonuçlarını sıralama</span><span class="sxs-lookup"><span data-stu-id="2f51d-141">How to: Sort Query Results</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-sort-query-results-by-using-linq.md)  
 [<span data-ttu-id="2f51d-142">Nasıl yapılır: sıralama veya filtre metni verilerle herhangi bir sözcük veya alana (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f51d-142">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
