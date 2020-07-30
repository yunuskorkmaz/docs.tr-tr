---
title: Verileri sıralama (C#)
description: C# ' de LINQ içinde sıralama işlemleri gerçekleştiren sıralama işlemleri ve standart sorgu işleci yöntemleri hakkında bilgi edinin.
ms.date: 07/20/2015
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
ms.openlocfilehash: 5feeb0e2229fc370fdcb9608817f41832bffd7cc
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302340"
---
# <a name="sorting-data-c"></a><span data-ttu-id="838ce-103">Verileri sıralama (C#)</span><span class="sxs-lookup"><span data-stu-id="838ce-103">Sorting Data (C#)</span></span>
<span data-ttu-id="838ce-104">Sıralama işlemi bir veya daha fazla özniteliğe göre bir sıranın öğelerini sıralar.</span><span class="sxs-lookup"><span data-stu-id="838ce-104">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="838ce-105">İlk sıralama ölçütü öğeler üzerinde birincil bir sıralama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="838ce-105">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="838ce-106">İkinci bir sıralama ölçütü belirterek, her birincil sıralama grubu içindeki öğeleri sıralayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="838ce-106">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>  
  
 <span data-ttu-id="838ce-107">Aşağıdaki çizimde, bir karakter dizisi üzerinde alfabetik bir sıralama işleminin sonuçları gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="838ce-107">The following illustration shows the results of an alphabetical sort operation on a sequence of characters:</span></span>
  
 ![Alfabetik bir sıralama işlemini gösteren grafik.](./media/sorting-data/alphabetical-sort-operation.png)  
  
 <span data-ttu-id="838ce-109">Verileri sıralayan standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="838ce-109">The standard query operator methods that sort data are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="838ce-110">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="838ce-110">Methods</span></span>  
  
|<span data-ttu-id="838ce-111">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="838ce-111">Method Name</span></span>|<span data-ttu-id="838ce-112">Description</span><span class="sxs-lookup"><span data-stu-id="838ce-112">Description</span></span>|<span data-ttu-id="838ce-113">C# sorgu Ifadesi sözdizimi</span><span class="sxs-lookup"><span data-stu-id="838ce-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="838ce-114">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="838ce-114">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="838ce-115">OrderBy</span><span class="sxs-lookup"><span data-stu-id="838ce-115">OrderBy</span></span>|<span data-ttu-id="838ce-116">Değerleri artan düzende sıralar.</span><span class="sxs-lookup"><span data-stu-id="838ce-116">Sorts values in ascending order.</span></span>|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="838ce-117">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="838ce-117">OrderByDescending</span></span>|<span data-ttu-id="838ce-118">Değerleri azalan düzende sıralar.</span><span class="sxs-lookup"><span data-stu-id="838ce-118">Sorts values in descending order.</span></span>|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="838ce-119">ThenBy</span><span class="sxs-lookup"><span data-stu-id="838ce-119">ThenBy</span></span>|<span data-ttu-id="838ce-120">Artan sırada ikincil bir sıralama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="838ce-120">Performs a secondary sort in ascending order.</span></span>|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="838ce-121">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="838ce-121">ThenByDescending</span></span>|<span data-ttu-id="838ce-122">Azalan sırada ikincil bir sıralama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="838ce-122">Performs a secondary sort in descending order.</span></span>|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="838ce-123">Reverse</span><span class="sxs-lookup"><span data-stu-id="838ce-123">Reverse</span></span>|<span data-ttu-id="838ce-124">Bir koleksiyondaki öğelerin sırasını tersine çevirir.</span><span class="sxs-lookup"><span data-stu-id="838ce-124">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="838ce-125">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="838ce-125">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="838ce-126">Sorgu Ifadesi söz dizimi örnekleri</span><span class="sxs-lookup"><span data-stu-id="838ce-126">Query Expression Syntax Examples</span></span>  
  
### <a name="primary-sort-examples"></a><span data-ttu-id="838ce-127">Birincil sıralama örnekleri</span><span class="sxs-lookup"><span data-stu-id="838ce-127">Primary Sort Examples</span></span>  
  
#### <a name="primary-ascending-sort"></a><span data-ttu-id="838ce-128">Birincil artan sıralama</span><span class="sxs-lookup"><span data-stu-id="838ce-128">Primary Ascending Sort</span></span>  
 <span data-ttu-id="838ce-129">Aşağıdaki örnek, bir `orderby` dizideki dizeleri dize uzunluğuna göre artan sırada sıralamak için BIR LINQ sorgusunda yan tümcesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="838ce-129">The following example demonstrates how to use the `orderby` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
    quick  
    brown  
    jumps  
*/  
```  
  
#### <a name="primary-descending-sort"></a><span data-ttu-id="838ce-130">Birincil azalan sıralama</span><span class="sxs-lookup"><span data-stu-id="838ce-130">Primary Descending Sort</span></span>  
 <span data-ttu-id="838ce-131">Sonraki örnekte, `orderby descending` BIR LINQ sorgusunda, dizeyi azalan sırada ilk harfine göre sıralamak için yan tümcesinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="838ce-131">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Substring(0, 1) descending  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    quick  
    jumps  
    fox  
    brown  
*/  
```  
  
### <a name="secondary-sort-examples"></a><span data-ttu-id="838ce-132">İkincil sıralama örnekleri</span><span class="sxs-lookup"><span data-stu-id="838ce-132">Secondary Sort Examples</span></span>  
  
#### <a name="secondary-ascending-sort"></a><span data-ttu-id="838ce-133">İkincil artan sıralama</span><span class="sxs-lookup"><span data-stu-id="838ce-133">Secondary Ascending Sort</span></span>  
 <span data-ttu-id="838ce-134">Aşağıdaki örnek, bir `orderby` dizideki dizelerin birincil ve ikincil sıralamasını gerçekleştirmek için BIR LINQ sorgusunda yan tümcesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="838ce-134">The following example demonstrates how to use the `orderby` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="838ce-135">Dizeler birincil olarak length ve secondarily ile dizenin ilk harfine göre, her ikisi de artan düzende sıralanır.</span><span class="sxs-lookup"><span data-stu-id="838ce-135">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length, word.Substring(0, 1)  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    fox  
    the  
    brown  
    jumps  
    quick  
*/  
```  
  
#### <a name="secondary-descending-sort"></a><span data-ttu-id="838ce-136">İkincil azalan sıralama</span><span class="sxs-lookup"><span data-stu-id="838ce-136">Secondary Descending Sort</span></span>  
 <span data-ttu-id="838ce-137">Sonraki örnekte, `orderby descending` BIR LINQ sorgusunda yan tümcesinin nasıl kullanılacağı gösterilmektedir ve azalan düzende bir birincil sıralama, artan sırada ve ikincil bir sıralama işlemleri yapılır.</span><span class="sxs-lookup"><span data-stu-id="838ce-137">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="838ce-138">Dizeler öncelikle dizenin ilk harfine göre uzunluğa ve secondarily göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="838ce-138">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length, word.Substring(0, 1) descending  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
    quick  
    jumps  
    brown  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="838ce-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="838ce-139">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="838ce-140">Standart sorgu Işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="838ce-140">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="838ce-141">orderby tümcesi</span><span class="sxs-lookup"><span data-stu-id="838ce-141">orderby clause</span></span>](../../../language-reference/keywords/orderby-clause.md)
- [<span data-ttu-id="838ce-142">Join yan tümcesinin sonuçlarını sıralama</span><span class="sxs-lookup"><span data-stu-id="838ce-142">Order the results of a join clause</span></span>](../../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="838ce-143">Her kelime veya alana göre metin verilerini sıralama veya filtreleme (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="838ce-143">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
