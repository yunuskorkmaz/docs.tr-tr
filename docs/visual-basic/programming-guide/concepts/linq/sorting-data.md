---
title: (Visual Basic) verileri sıralama
ms.date: 07/20/2015
ms.assetid: 6f81065c-0c89-4bf3-a6d8-442273f8810e
ms.openlocfilehash: ad39aca6a53221f077a6b8313262d508744ff5ea
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819092"
---
# <a name="sorting-data-visual-basic"></a><span data-ttu-id="66d35-102">(Visual Basic) verileri sıralama</span><span class="sxs-lookup"><span data-stu-id="66d35-102">Sorting Data (Visual Basic)</span></span>
<span data-ttu-id="66d35-103">Sıralama işlemi bir veya daha fazla özniteliklerine dayalı bir dizinin öğeleri sıralar.</span><span class="sxs-lookup"><span data-stu-id="66d35-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="66d35-104">İlk sıralama ölçütü öğelerde birincil sıralama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="66d35-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="66d35-105">İkinci bir sıralama ölçütünü belirterek, her birincil sıralama grup içindeki öğeleri sıralayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66d35-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>  
  
 <span data-ttu-id="66d35-106">Aşağıdaki çizimde, bir dizi karakter bir alfabetik sıralama işlemi sonuçlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="66d35-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters.</span></span>  
  
 ![Bir alfabetik sıralama işlemini gösteren grafik.](./media/sorting-data/alphabetical-sort-operation.png)  
  
 <span data-ttu-id="66d35-108">Verileri sıralama standart sorgu işleci yöntemleri aşağıdaki bölümünde listelenir.</span><span class="sxs-lookup"><span data-stu-id="66d35-108">The standard query operator methods that sort data are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="66d35-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="66d35-109">Methods</span></span>  
  
|<span data-ttu-id="66d35-110">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="66d35-110">Method Name</span></span>|<span data-ttu-id="66d35-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="66d35-111">Description</span></span>|<span data-ttu-id="66d35-112">Visual Basic sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="66d35-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="66d35-113">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="66d35-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="66d35-114">OrderBy</span><span class="sxs-lookup"><span data-stu-id="66d35-114">OrderBy</span></span>|<span data-ttu-id="66d35-115">Artan değerleri sıralar.</span><span class="sxs-lookup"><span data-stu-id="66d35-115">Sorts values in ascending order.</span></span>|`Order By`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="66d35-116">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="66d35-116">OrderByDescending</span></span>|<span data-ttu-id="66d35-117">Değerleri azalan düzende sıralar.</span><span class="sxs-lookup"><span data-stu-id="66d35-117">Sorts values in descending order.</span></span>|`Order By … Descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="66d35-118">ThenBy</span><span class="sxs-lookup"><span data-stu-id="66d35-118">ThenBy</span></span>|<span data-ttu-id="66d35-119">İkincil bir sıralama, azalan sırada gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="66d35-119">Performs a secondary sort in ascending order.</span></span>|`Order By …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="66d35-120">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="66d35-120">ThenByDescending</span></span>|<span data-ttu-id="66d35-121">İkincil bir sıralama, azalan sırada gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="66d35-121">Performs a secondary sort in descending order.</span></span>|`Order By …, … Descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="66d35-122">geriye doğru</span><span class="sxs-lookup"><span data-stu-id="66d35-122">Reverse</span></span>|<span data-ttu-id="66d35-123">Bir koleksiyondaki öğelerin sırasını tersine çevirir.</span><span class="sxs-lookup"><span data-stu-id="66d35-123">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="66d35-124">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="66d35-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="66d35-125">Sorgu ifadesi söz dizimi örnekleri</span><span class="sxs-lookup"><span data-stu-id="66d35-125">Query Expression Syntax Examples</span></span>  
  
### <a name="primary-sort-examples"></a><span data-ttu-id="66d35-126">Birincil sıralama örnekleri</span><span class="sxs-lookup"><span data-stu-id="66d35-126">Primary Sort Examples</span></span>  
  
#### <a name="primary-ascending-sort"></a><span data-ttu-id="66d35-127">Birincil artan sıralama</span><span class="sxs-lookup"><span data-stu-id="66d35-127">Primary Ascending Sort</span></span>  
 <span data-ttu-id="66d35-128">Aşağıdaki örnek nasıl kullanılacağını gösterir `Order By` artan düzende dize uzunluğu, dizi dizeleri sıralamak için bir LINQ sorgu yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="66d35-128">The following example demonstrates how to use the `Order By` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>  
  
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
  
#### <a name="primary-descending-sort"></a><span data-ttu-id="66d35-129">Birincil azalan sıralama</span><span class="sxs-lookup"><span data-stu-id="66d35-129">Primary Descending Sort</span></span>  
 <span data-ttu-id="66d35-130">Sonraki örnek nasıl kullanılacağını gösterir `Order By Descending` azalan düzende, ilk harfini dizeleri sıralamak için bir LINQ sorgu yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="66d35-130">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>  
  
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
  
### <a name="secondary-sort-examples"></a><span data-ttu-id="66d35-131">İkincil sıralama örnekleri</span><span class="sxs-lookup"><span data-stu-id="66d35-131">Secondary Sort Examples</span></span>  
  
#### <a name="secondary-ascending-sort"></a><span data-ttu-id="66d35-132">İkincil artan sıralama</span><span class="sxs-lookup"><span data-stu-id="66d35-132">Secondary Ascending Sort</span></span>  
 <span data-ttu-id="66d35-133">Aşağıdaki örnek nasıl kullanılacağını gösterir `Order By` bir dizide dize birincil ve ikincil bir sıralama gerçekleştirmek için bir LINQ sorgu yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="66d35-133">The following example demonstrates how to use the `Order By` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="66d35-134">Dizeleri öncelikle uzunluğu ve ürüne göre ilk harfini dize hem artan düzende sıralanır.</span><span class="sxs-lookup"><span data-stu-id="66d35-134">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>  
  
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
  
#### <a name="secondary-descending-sort"></a><span data-ttu-id="66d35-135">İkincil azalan sıralama</span><span class="sxs-lookup"><span data-stu-id="66d35-135">Secondary Descending Sort</span></span>  
 <span data-ttu-id="66d35-136">Sonraki örnek nasıl kullanılacağını gösterir `Order By Descending` birincil bir sıralama düzeni ve ikincil bir sıralama, azalan düzende, artan düzende gerçekleştirmek için bir LINQ sorgu yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="66d35-136">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="66d35-137">Dizeleri öncelikle uzunluğu ve ürüne dizenin ilk harfini sıralanır.</span><span class="sxs-lookup"><span data-stu-id="66d35-137">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="66d35-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66d35-138">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="66d35-139">Standart sorgu işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="66d35-139">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="66d35-140">Order By Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="66d35-140">Order By Clause</span></span>](../../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="66d35-141">Nasıl yapılır: Sorgu sonuçlarını sıralama</span><span class="sxs-lookup"><span data-stu-id="66d35-141">How to: Sort Query Results</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-sort-query-results-by-using-linq.md)
- [<span data-ttu-id="66d35-142">Nasıl yapılır: Herhangi bir sözcük veya alana (LINQ) (Visual Basic) göre filtre metin verilerini sıralama veya</span><span class="sxs-lookup"><span data-stu-id="66d35-142">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
