---
title: Sıralama veri (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 6f81065c-0c89-4bf3-a6d8-442273f8810e
ms.openlocfilehash: f52000d37df45c97754463de1e81cd523806e9c4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646870"
---
# <a name="sorting-data-visual-basic"></a><span data-ttu-id="f79c5-102">Sıralama veri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f79c5-102">Sorting Data (Visual Basic)</span></span>
<span data-ttu-id="f79c5-103">Sıralama işlemi bir veya daha fazla özniteliklerini temel alarak bir sıradaki sıralar.</span><span class="sxs-lookup"><span data-stu-id="f79c5-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="f79c5-104">İlk sıralama ölçütü birincil sıralama öğeleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="f79c5-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="f79c5-105">İkinci bir sıralama ölçütü belirterek, her birincil sıralama grup içindeki öğeleri sıralama yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f79c5-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>  
  
 <span data-ttu-id="f79c5-106">Aşağıdaki çizimde bir dizi karakterden oluşan bir alfabetik sıralama işlemi sonuçlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f79c5-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters.</span></span>  
  
 <span data-ttu-id="f79c5-107">![Sıralama işlemi LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")</span><span class="sxs-lookup"><span data-stu-id="f79c5-107">![LINQ Sorting Operation](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")</span></span>  
  
 <span data-ttu-id="f79c5-108">Verileri sıralama standart sorgu işleci yöntemler aşağıdaki bölümde listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="f79c5-108">The standard query operator methods that sort data are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f79c5-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f79c5-109">Methods</span></span>  
  
|<span data-ttu-id="f79c5-110">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="f79c5-110">Method Name</span></span>|<span data-ttu-id="f79c5-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f79c5-111">Description</span></span>|<span data-ttu-id="f79c5-112">Visual Basic sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f79c5-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="f79c5-113">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="f79c5-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="f79c5-114">OrderBy</span><span class="sxs-lookup"><span data-stu-id="f79c5-114">OrderBy</span></span>|<span data-ttu-id="f79c5-115">Artan düzende değerlerini sıralar.</span><span class="sxs-lookup"><span data-stu-id="f79c5-115">Sorts values in ascending order.</span></span>|`Order By`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f79c5-116">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="f79c5-116">OrderByDescending</span></span>|<span data-ttu-id="f79c5-117">Azalan düzende değerlerini sıralar.</span><span class="sxs-lookup"><span data-stu-id="f79c5-117">Sorts values in descending order.</span></span>|`Order By … Descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f79c5-118">ThenBy</span><span class="sxs-lookup"><span data-stu-id="f79c5-118">ThenBy</span></span>|<span data-ttu-id="f79c5-119">İkincil bir sıralama artan düzende gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="f79c5-119">Performs a secondary sort in ascending order.</span></span>|`Order By …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f79c5-120">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="f79c5-120">ThenByDescending</span></span>|<span data-ttu-id="f79c5-121">İkincil bir sıralamayı azalan sırada gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="f79c5-121">Performs a secondary sort in descending order.</span></span>|`Order By …, … Descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f79c5-122">Ters Çevir</span><span class="sxs-lookup"><span data-stu-id="f79c5-122">Reverse</span></span>|<span data-ttu-id="f79c5-123">Bir koleksiyondaki öğelerin sırasını tersine çevirir.</span><span class="sxs-lookup"><span data-stu-id="f79c5-123">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="f79c5-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="f79c5-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="f79c5-125">Sorgu ifade sözdizimi örnekleri</span><span class="sxs-lookup"><span data-stu-id="f79c5-125">Query Expression Syntax Examples</span></span>  
  
### <a name="primary-sort-examples"></a><span data-ttu-id="f79c5-126">Birincil sıralama örnekleri</span><span class="sxs-lookup"><span data-stu-id="f79c5-126">Primary Sort Examples</span></span>  
  
#### <a name="primary-ascending-sort"></a><span data-ttu-id="f79c5-127">Birincil artan sıralama</span><span class="sxs-lookup"><span data-stu-id="f79c5-127">Primary Ascending Sort</span></span>  
 <span data-ttu-id="f79c5-128">Aşağıdaki örnekte nasıl kullanılacağı ortaya `Order By` dize uzunluğu, artan bir dizi dizelerde sıralamak için bir LINQ sorgu yan tümcesinde.</span><span class="sxs-lookup"><span data-stu-id="f79c5-128">The following example demonstrates how to use the `Order By` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>  
  
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
  
#### <a name="primary-descending-sort"></a><span data-ttu-id="f79c5-129">Birincil azalan sıralama</span><span class="sxs-lookup"><span data-stu-id="f79c5-129">Primary Descending Sort</span></span>  
 <span data-ttu-id="f79c5-130">Sonraki örnek nasıl kullanılacağı ortaya `Order By Descending` azalan sırada kendi ilk harfi dizeleri sıralamak için bir LINQ sorgu yan tümcesinde.</span><span class="sxs-lookup"><span data-stu-id="f79c5-130">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>  
  
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
  
### <a name="secondary-sort-examples"></a><span data-ttu-id="f79c5-131">İkincil sıralama örnekleri</span><span class="sxs-lookup"><span data-stu-id="f79c5-131">Secondary Sort Examples</span></span>  
  
#### <a name="secondary-ascending-sort"></a><span data-ttu-id="f79c5-132">İkincil artan sıralama</span><span class="sxs-lookup"><span data-stu-id="f79c5-132">Secondary Ascending Sort</span></span>  
 <span data-ttu-id="f79c5-133">Aşağıdaki örnekte nasıl kullanılacağı ortaya `Order By` dizeleri birincil ve ikincil bir tür bir dizide gerçekleştirmek için bir LINQ sorgu yan tümcesinde.</span><span class="sxs-lookup"><span data-stu-id="f79c5-133">The following example demonstrates how to use the `Order By` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="f79c5-134">Dizeleri öncelikle uzunluğu ve ürüne ilk harfini dizesinin hem artan düzende sıralanır.</span><span class="sxs-lookup"><span data-stu-id="f79c5-134">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>  
  
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
  
#### <a name="secondary-descending-sort"></a><span data-ttu-id="f79c5-135">İkincil azalan sıralama</span><span class="sxs-lookup"><span data-stu-id="f79c5-135">Secondary Descending Sort</span></span>  
 <span data-ttu-id="f79c5-136">Sonraki örnek nasıl kullanılacağı ortaya `Order By Descending` birincil bir sıralama düzeni ve azalan bir ikincil sıralama artan düzende gerçekleştirmek için bir LINQ sorgu yan tümcesinde.</span><span class="sxs-lookup"><span data-stu-id="f79c5-136">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="f79c5-137">Dizeleri öncelikle uzunluğu ve ürüne dizenin ilk harfini sıralanır.</span><span class="sxs-lookup"><span data-stu-id="f79c5-137">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f79c5-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f79c5-138">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="f79c5-139">Standart sorgu işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f79c5-139">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="f79c5-140">Order By Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="f79c5-140">Order By Clause</span></span>](../../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [<span data-ttu-id="f79c5-141">Nasıl yapılır: sorgu sonuçlarını sıralama</span><span class="sxs-lookup"><span data-stu-id="f79c5-141">How to: Sort Query Results</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-sort-query-results-by-using-linq.md)  
 [<span data-ttu-id="f79c5-142">Nasıl yapılır: sıralama veya filtre metni verilerle herhangi bir sözcük veya alana (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f79c5-142">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
