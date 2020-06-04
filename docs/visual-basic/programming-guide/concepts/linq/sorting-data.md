---
title: Verileri Sıralama
ms.date: 07/20/2015
ms.assetid: 6f81065c-0c89-4bf3-a6d8-442273f8810e
ms.openlocfilehash: a5ccff745995ed7f41731cf98fb7c49d3247d994
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406800"
---
# <a name="sorting-data-visual-basic"></a><span data-ttu-id="1d268-102">Verileri sıralama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d268-102">Sorting Data (Visual Basic)</span></span>

<span data-ttu-id="1d268-103">Sıralama işlemi bir veya daha fazla özniteliğe göre bir sıranın öğelerini sıralar.</span><span class="sxs-lookup"><span data-stu-id="1d268-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="1d268-104">İlk sıralama ölçütü öğeler üzerinde birincil bir sıralama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="1d268-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="1d268-105">İkinci bir sıralama ölçütü belirterek, her birincil sıralama grubu içindeki öğeleri sıralayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d268-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>

<span data-ttu-id="1d268-106">Aşağıdaki çizimde, bir karakter dizisi üzerinde alfabetik bir sıralama işleminin sonuçları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1d268-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters.</span></span>

![Alfabetik bir sıralama işlemini gösteren grafik.](./media/sorting-data/alphabetical-sort-operation.png)

<span data-ttu-id="1d268-108">Verileri sıralayan standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="1d268-108">The standard query operator methods that sort data are listed in the following section.</span></span>

## <a name="methods"></a><span data-ttu-id="1d268-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1d268-109">Methods</span></span>

|<span data-ttu-id="1d268-110">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="1d268-110">Method Name</span></span>|<span data-ttu-id="1d268-111">Description</span><span class="sxs-lookup"><span data-stu-id="1d268-111">Description</span></span>|<span data-ttu-id="1d268-112">Sorgu Ifadesi söz dizimini Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1d268-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="1d268-113">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="1d268-113">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="1d268-114">OrderBy</span><span class="sxs-lookup"><span data-stu-id="1d268-114">OrderBy</span></span>|<span data-ttu-id="1d268-115">Değerleri artan düzende sıralar.</span><span class="sxs-lookup"><span data-stu-id="1d268-115">Sorts values in ascending order.</span></span>|`Order By`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|
|<span data-ttu-id="1d268-116">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="1d268-116">OrderByDescending</span></span>|<span data-ttu-id="1d268-117">Değerleri azalan düzende sıralar.</span><span class="sxs-lookup"><span data-stu-id="1d268-117">Sorts values in descending order.</span></span>|`Order By … Descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|
|<span data-ttu-id="1d268-118">ThenBy</span><span class="sxs-lookup"><span data-stu-id="1d268-118">ThenBy</span></span>|<span data-ttu-id="1d268-119">Artan sırada ikincil bir sıralama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="1d268-119">Performs a secondary sort in ascending order.</span></span>|`Order By …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|
|<span data-ttu-id="1d268-120">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="1d268-120">ThenByDescending</span></span>|<span data-ttu-id="1d268-121">Azalan sırada ikincil bir sıralama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="1d268-121">Performs a secondary sort in descending order.</span></span>|`Order By …, … Descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|
|<span data-ttu-id="1d268-122">Reverse</span><span class="sxs-lookup"><span data-stu-id="1d268-122">Reverse</span></span>|<span data-ttu-id="1d268-123">Bir koleksiyondaki öğelerin sırasını tersine çevirir.</span><span class="sxs-lookup"><span data-stu-id="1d268-123">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="1d268-124">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="1d268-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-examples"></a><span data-ttu-id="1d268-125">Sorgu Ifadesi söz dizimi örnekleri</span><span class="sxs-lookup"><span data-stu-id="1d268-125">Query Expression Syntax Examples</span></span>

### <a name="primary-sort-examples"></a><span data-ttu-id="1d268-126">Birincil sıralama örnekleri</span><span class="sxs-lookup"><span data-stu-id="1d268-126">Primary Sort Examples</span></span>

#### <a name="primary-ascending-sort"></a><span data-ttu-id="1d268-127">Birincil artan sıralama</span><span class="sxs-lookup"><span data-stu-id="1d268-127">Primary Ascending Sort</span></span>

<span data-ttu-id="1d268-128">Aşağıdaki örnek, bir `Order By` dizideki dizeleri dize uzunluğuna göre artan sırada sıralamak için BIR LINQ sorgusunda yan tümcesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d268-128">The following example demonstrates how to use the `Order By` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>

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

#### <a name="primary-descending-sort"></a><span data-ttu-id="1d268-129">Birincil azalan sıralama</span><span class="sxs-lookup"><span data-stu-id="1d268-129">Primary Descending Sort</span></span>

<span data-ttu-id="1d268-130">Sonraki örnekte, `Order By Descending` BIR LINQ sorgusunda, dizeyi azalan sırada ilk harfine göre sıralamak için yan tümcesinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1d268-130">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>

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

### <a name="secondary-sort-examples"></a><span data-ttu-id="1d268-131">İkincil sıralama örnekleri</span><span class="sxs-lookup"><span data-stu-id="1d268-131">Secondary Sort Examples</span></span>

#### <a name="secondary-ascending-sort"></a><span data-ttu-id="1d268-132">İkincil artan sıralama</span><span class="sxs-lookup"><span data-stu-id="1d268-132">Secondary Ascending Sort</span></span>

<span data-ttu-id="1d268-133">Aşağıdaki örnek, bir `Order By` dizideki dizelerin birincil ve ikincil sıralamasını gerçekleştirmek için BIR LINQ sorgusunda yan tümcesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d268-133">The following example demonstrates how to use the `Order By` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="1d268-134">Dizeler birincil olarak length ve secondarily ile dizenin ilk harfine göre, her ikisi de artan düzende sıralanır.</span><span class="sxs-lookup"><span data-stu-id="1d268-134">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>

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

#### <a name="secondary-descending-sort"></a><span data-ttu-id="1d268-135">İkincil azalan sıralama</span><span class="sxs-lookup"><span data-stu-id="1d268-135">Secondary Descending Sort</span></span>

<span data-ttu-id="1d268-136">Sonraki örnekte, `Order By Descending` BIR LINQ sorgusunda yan tümcesinin nasıl kullanılacağı gösterilmektedir ve azalan düzende bir birincil sıralama, artan sırada ve ikincil bir sıralama işlemleri yapılır.</span><span class="sxs-lookup"><span data-stu-id="1d268-136">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="1d268-137">Dizeler öncelikle dizenin ilk harfine göre uzunluğa ve secondarily göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="1d268-137">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="1d268-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d268-138">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="1d268-139">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d268-139">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="1d268-140">Order By Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="1d268-140">Order By Clause</span></span>](../../../language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="1d268-141">Nasıl yapılır: sorgu sonuçlarını sıralama</span><span class="sxs-lookup"><span data-stu-id="1d268-141">How to: Sort Query Results</span></span>](../../language-features/linq/how-to-sort-query-results-by-using-linq.md)
- [<span data-ttu-id="1d268-142">Nasıl yapılır: herhangi bir sözcük veya alana göre metin verilerini sıralama veya filtreleme (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d268-142">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
