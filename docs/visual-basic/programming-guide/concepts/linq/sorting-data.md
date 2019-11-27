---
title: Verileri Sıralama
ms.date: 07/20/2015
ms.assetid: 6f81065c-0c89-4bf3-a6d8-442273f8810e
ms.openlocfilehash: f1d4d8afb9b6e176a7ac048ba3270ecafdce24c9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350594"
---
# <a name="sorting-data-visual-basic"></a><span data-ttu-id="af752-102">Verileri sıralama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af752-102">Sorting Data (Visual Basic)</span></span>

<span data-ttu-id="af752-103">Sıralama işlemi bir veya daha fazla özniteliğe göre bir sıranın öğelerini sıralar.</span><span class="sxs-lookup"><span data-stu-id="af752-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="af752-104">İlk sıralama ölçütü öğeler üzerinde birincil bir sıralama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="af752-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="af752-105">İkinci bir sıralama ölçütü belirterek, her birincil sıralama grubu içindeki öğeleri sıralayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af752-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>

<span data-ttu-id="af752-106">Aşağıdaki çizimde, bir karakter dizisi üzerinde alfabetik bir sıralama işleminin sonuçları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="af752-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters.</span></span>

![Alfabetik bir sıralama işlemini gösteren grafik.](./media/sorting-data/alphabetical-sort-operation.png)

<span data-ttu-id="af752-108">Verileri sıralayan standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="af752-108">The standard query operator methods that sort data are listed in the following section.</span></span>

## <a name="methods"></a><span data-ttu-id="af752-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="af752-109">Methods</span></span>

|<span data-ttu-id="af752-110">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="af752-110">Method Name</span></span>|<span data-ttu-id="af752-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="af752-111">Description</span></span>|<span data-ttu-id="af752-112">Sorgu Ifadesi söz dizimini Visual Basic</span><span class="sxs-lookup"><span data-stu-id="af752-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="af752-113">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="af752-113">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="af752-114">OrderBy</span><span class="sxs-lookup"><span data-stu-id="af752-114">OrderBy</span></span>|<span data-ttu-id="af752-115">Değerleri artan düzende sıralar.</span><span class="sxs-lookup"><span data-stu-id="af752-115">Sorts values in ascending order.</span></span>|`Order By`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|
|<span data-ttu-id="af752-116">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="af752-116">OrderByDescending</span></span>|<span data-ttu-id="af752-117">Değerleri azalan düzende sıralar.</span><span class="sxs-lookup"><span data-stu-id="af752-117">Sorts values in descending order.</span></span>|`Order By … Descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|
|<span data-ttu-id="af752-118">ThenBy</span><span class="sxs-lookup"><span data-stu-id="af752-118">ThenBy</span></span>|<span data-ttu-id="af752-119">Artan sırada ikincil bir sıralama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="af752-119">Performs a secondary sort in ascending order.</span></span>|`Order By …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|
|<span data-ttu-id="af752-120">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="af752-120">ThenByDescending</span></span>|<span data-ttu-id="af752-121">Azalan sırada ikincil bir sıralama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="af752-121">Performs a secondary sort in descending order.</span></span>|`Order By …, … Descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|
|<span data-ttu-id="af752-122">Tersini</span><span class="sxs-lookup"><span data-stu-id="af752-122">Reverse</span></span>|<span data-ttu-id="af752-123">Bir koleksiyondaki öğelerin sırasını tersine çevirir.</span><span class="sxs-lookup"><span data-stu-id="af752-123">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="af752-124">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="af752-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-examples"></a><span data-ttu-id="af752-125">Sorgu Ifadesi söz dizimi örnekleri</span><span class="sxs-lookup"><span data-stu-id="af752-125">Query Expression Syntax Examples</span></span>

### <a name="primary-sort-examples"></a><span data-ttu-id="af752-126">Birincil sıralama örnekleri</span><span class="sxs-lookup"><span data-stu-id="af752-126">Primary Sort Examples</span></span>

#### <a name="primary-ascending-sort"></a><span data-ttu-id="af752-127">Birincil artan sıralama</span><span class="sxs-lookup"><span data-stu-id="af752-127">Primary Ascending Sort</span></span>

<span data-ttu-id="af752-128">Aşağıdaki örnek, bir dizideki dizeleri dize uzunluğuna göre artan sırada sıralamak için bir LINQ sorgusunda `Order By` yan tümcesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="af752-128">The following example demonstrates how to use the `Order By` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>

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

#### <a name="primary-descending-sort"></a><span data-ttu-id="af752-129">Birincil azalan sıralama</span><span class="sxs-lookup"><span data-stu-id="af752-129">Primary Descending Sort</span></span>

<span data-ttu-id="af752-130">Sonraki örnekte, dizeleri ilk harfine göre azalan sırada sıralamak için bir LINQ sorgusunda `Order By Descending` yan tümcesinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="af752-130">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>

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

### <a name="secondary-sort-examples"></a><span data-ttu-id="af752-131">İkincil sıralama örnekleri</span><span class="sxs-lookup"><span data-stu-id="af752-131">Secondary Sort Examples</span></span>

#### <a name="secondary-ascending-sort"></a><span data-ttu-id="af752-132">İkincil artan sıralama</span><span class="sxs-lookup"><span data-stu-id="af752-132">Secondary Ascending Sort</span></span>

<span data-ttu-id="af752-133">Aşağıdaki örnek, bir dizideki dizelerin birincil ve ikincil sıralamasını gerçekleştirmek için bir LINQ sorgusunda `Order By` yan tümcesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="af752-133">The following example demonstrates how to use the `Order By` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="af752-134">Dizeler birincil olarak length ve secondarily ile dizenin ilk harfine göre, her ikisi de artan düzende sıralanır.</span><span class="sxs-lookup"><span data-stu-id="af752-134">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>

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

#### <a name="secondary-descending-sort"></a><span data-ttu-id="af752-135">İkincil azalan sıralama</span><span class="sxs-lookup"><span data-stu-id="af752-135">Secondary Descending Sort</span></span>

<span data-ttu-id="af752-136">Sonraki örnekte, bir LINQ sorgusunda `Order By Descending` yan tümcesinin nasıl kullanılacağı gösterilmektedir ve bu bir birincil sıralama, artan düzende, ikincil bir sıralama ise azalan düzende yapılır.</span><span class="sxs-lookup"><span data-stu-id="af752-136">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="af752-137">Dizeler öncelikle dizenin ilk harfine göre uzunluğa ve secondarily göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="af752-137">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="af752-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af752-138">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="af752-139">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af752-139">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="af752-140">Order By Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="af752-140">Order By Clause</span></span>](../../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="af752-141">Nasıl yapılır: sorgu sonuçlarını sıralama</span><span class="sxs-lookup"><span data-stu-id="af752-141">How to: Sort Query Results</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-sort-query-results-by-using-linq.md)
- [<span data-ttu-id="af752-142">Nasıl yapılır: herhangi bir sözcük veya alana göre metin verilerini sıralama veya filtreleme (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af752-142">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
