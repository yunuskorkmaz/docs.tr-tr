---
title: Verileri sıralama (C#)
description: C# ' de LINQ içinde sıralama işlemleri gerçekleştiren sıralama işlemleri ve standart sorgu işleci yöntemleri hakkında bilgi edinin.
ms.date: 07/20/2015
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
ms.openlocfilehash: 0665e5dec95fd2929d24d82568de66597df1c0bd
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195512"
---
# <a name="sorting-data-c"></a><span data-ttu-id="c04e3-103">Verileri sıralama (C#)</span><span class="sxs-lookup"><span data-stu-id="c04e3-103">Sorting Data (C#)</span></span>

<span data-ttu-id="c04e3-104">Sıralama işlemi bir veya daha fazla özniteliğe göre bir sıranın öğelerini sıralar.</span><span class="sxs-lookup"><span data-stu-id="c04e3-104">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="c04e3-105">İlk sıralama ölçütü öğeler üzerinde birincil bir sıralama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="c04e3-105">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="c04e3-106">İkinci bir sıralama ölçütü belirterek, her birincil sıralama grubu içindeki öğeleri sıralayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c04e3-106">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>  
  
 <span data-ttu-id="c04e3-107">Aşağıdaki çizimde, bir karakter dizisi üzerinde alfabetik bir sıralama işleminin sonuçları gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="c04e3-107">The following illustration shows the results of an alphabetical sort operation on a sequence of characters:</span></span>
  
 ![Alfabetik bir sıralama işlemini gösteren grafik.](./media/sorting-data/alphabetical-sort-operation.png)  
  
 <span data-ttu-id="c04e3-109">Verileri sıralayan standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="c04e3-109">The standard query operator methods that sort data are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c04e3-110">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c04e3-110">Methods</span></span>  
  
|<span data-ttu-id="c04e3-111">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="c04e3-111">Method Name</span></span>|<span data-ttu-id="c04e3-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c04e3-112">Description</span></span>|<span data-ttu-id="c04e3-113">C# sorgu Ifadesi sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c04e3-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="c04e3-114">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="c04e3-114">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="c04e3-115">OrderBy</span><span class="sxs-lookup"><span data-stu-id="c04e3-115">OrderBy</span></span>|<span data-ttu-id="c04e3-116">Değerleri artan düzende sıralar.</span><span class="sxs-lookup"><span data-stu-id="c04e3-116">Sorts values in ascending order.</span></span>|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c04e3-117">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="c04e3-117">OrderByDescending</span></span>|<span data-ttu-id="c04e3-118">Değerleri azalan düzende sıralar.</span><span class="sxs-lookup"><span data-stu-id="c04e3-118">Sorts values in descending order.</span></span>|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c04e3-119">ThenBy</span><span class="sxs-lookup"><span data-stu-id="c04e3-119">ThenBy</span></span>|<span data-ttu-id="c04e3-120">Artan sırada ikincil bir sıralama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="c04e3-120">Performs a secondary sort in ascending order.</span></span>|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c04e3-121">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="c04e3-121">ThenByDescending</span></span>|<span data-ttu-id="c04e3-122">Azalan sırada ikincil bir sıralama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="c04e3-122">Performs a secondary sort in descending order.</span></span>|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c04e3-123">Reverse</span><span class="sxs-lookup"><span data-stu-id="c04e3-123">Reverse</span></span>|<span data-ttu-id="c04e3-124">Bir koleksiyondaki öğelerin sırasını tersine çevirir.</span><span class="sxs-lookup"><span data-stu-id="c04e3-124">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="c04e3-125">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="c04e3-125">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="c04e3-126">Sorgu Ifadesi söz dizimi örnekleri</span><span class="sxs-lookup"><span data-stu-id="c04e3-126">Query Expression Syntax Examples</span></span>  
  
### <a name="primary-sort-examples"></a><span data-ttu-id="c04e3-127">Birincil sıralama örnekleri</span><span class="sxs-lookup"><span data-stu-id="c04e3-127">Primary Sort Examples</span></span>  
  
#### <a name="primary-ascending-sort"></a><span data-ttu-id="c04e3-128">Birincil artan sıralama</span><span class="sxs-lookup"><span data-stu-id="c04e3-128">Primary Ascending Sort</span></span>  

 <span data-ttu-id="c04e3-129">Aşağıdaki örnek, bir `orderby` dizideki dizeleri dize uzunluğuna göre artan sırada sıralamak için BIR LINQ sorgusunda yan tümcesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c04e3-129">The following example demonstrates how to use the `orderby` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>  
  
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
  
#### <a name="primary-descending-sort"></a><span data-ttu-id="c04e3-130">Birincil azalan sıralama</span><span class="sxs-lookup"><span data-stu-id="c04e3-130">Primary Descending Sort</span></span>  

 <span data-ttu-id="c04e3-131">Sonraki örnekte, `orderby descending` BIR LINQ sorgusunda, dizeyi azalan sırada ilk harfine göre sıralamak için yan tümcesinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c04e3-131">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>  
  
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
  
### <a name="secondary-sort-examples"></a><span data-ttu-id="c04e3-132">İkincil sıralama örnekleri</span><span class="sxs-lookup"><span data-stu-id="c04e3-132">Secondary Sort Examples</span></span>  
  
#### <a name="secondary-ascending-sort"></a><span data-ttu-id="c04e3-133">İkincil artan sıralama</span><span class="sxs-lookup"><span data-stu-id="c04e3-133">Secondary Ascending Sort</span></span>  

 <span data-ttu-id="c04e3-134">Aşağıdaki örnek, bir `orderby` dizideki dizelerin birincil ve ikincil sıralamasını gerçekleştirmek için BIR LINQ sorgusunda yan tümcesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c04e3-134">The following example demonstrates how to use the `orderby` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="c04e3-135">Dizeler birincil olarak length ve secondarily ile dizenin ilk harfine göre, her ikisi de artan düzende sıralanır.</span><span class="sxs-lookup"><span data-stu-id="c04e3-135">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>  
  
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
  
#### <a name="secondary-descending-sort"></a><span data-ttu-id="c04e3-136">İkincil azalan sıralama</span><span class="sxs-lookup"><span data-stu-id="c04e3-136">Secondary Descending Sort</span></span>  

 <span data-ttu-id="c04e3-137">Sonraki örnekte, `orderby descending` BIR LINQ sorgusunda yan tümcesinin nasıl kullanılacağı gösterilmektedir ve azalan düzende bir birincil sıralama, artan sırada ve ikincil bir sıralama işlemleri yapılır.</span><span class="sxs-lookup"><span data-stu-id="c04e3-137">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="c04e3-138">Dizeler öncelikle dizenin ilk harfine göre uzunluğa ve secondarily göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="c04e3-138">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c04e3-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c04e3-139">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="c04e3-140">Standart sorgu Işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="c04e3-140">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="c04e3-141">orderby tümcesi</span><span class="sxs-lookup"><span data-stu-id="c04e3-141">orderby clause</span></span>](../../../language-reference/keywords/orderby-clause.md)
- [<span data-ttu-id="c04e3-142">Join yan tümcesinin sonuçlarını sıralama</span><span class="sxs-lookup"><span data-stu-id="c04e3-142">Order the results of a join clause</span></span>](../../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="c04e3-143">Her kelime veya alana göre metin verilerini sıralama veya filtreleme (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="c04e3-143">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
