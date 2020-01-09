---
title: Verileri sıralama (C#)
ms.date: 07/20/2015
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
ms.openlocfilehash: 8db5ab2ead0e59b8d41d83704ff237d4493155c3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346464"
---
# <a name="sorting-data-c"></a><span data-ttu-id="8a8b4-102">Verileri sıralama (C#)</span><span class="sxs-lookup"><span data-stu-id="8a8b4-102">Sorting Data (C#)</span></span>
<span data-ttu-id="8a8b4-103">Sıralama işlemi bir veya daha fazla özniteliğe göre bir sıranın öğelerini sıralar.</span><span class="sxs-lookup"><span data-stu-id="8a8b4-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="8a8b4-104">İlk sıralama ölçütü öğeler üzerinde birincil bir sıralama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="8a8b4-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="8a8b4-105">İkinci bir sıralama ölçütü belirterek, her birincil sıralama grubu içindeki öğeleri sıralayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a8b4-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>  
  
 <span data-ttu-id="8a8b4-106">Aşağıdaki çizimde, bir karakter dizisi üzerinde alfabetik bir sıralama işleminin sonuçları gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="8a8b4-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters:</span></span> 
  
 ![Alfabetik bir sıralama işlemini gösteren grafik.](./media/sorting-data/alphabetical-sort-operation.png)  
  
 <span data-ttu-id="8a8b4-108">Verileri sıralayan standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="8a8b4-108">The standard query operator methods that sort data are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8a8b4-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8a8b4-109">Methods</span></span>  
  
|<span data-ttu-id="8a8b4-110">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="8a8b4-110">Method Name</span></span>|<span data-ttu-id="8a8b4-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8a8b4-111">Description</span></span>|<span data-ttu-id="8a8b4-112">C#Sorgu Ifadesi söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8a8b4-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="8a8b4-113">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="8a8b4-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="8a8b4-114">OrderBy</span><span class="sxs-lookup"><span data-stu-id="8a8b4-114">OrderBy</span></span>|<span data-ttu-id="8a8b4-115">Değerleri artan düzende sıralar.</span><span class="sxs-lookup"><span data-stu-id="8a8b4-115">Sorts values in ascending order.</span></span>|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="8a8b4-116">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="8a8b4-116">OrderByDescending</span></span>|<span data-ttu-id="8a8b4-117">Değerleri azalan düzende sıralar.</span><span class="sxs-lookup"><span data-stu-id="8a8b4-117">Sorts values in descending order.</span></span>|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="8a8b4-118">ThenBy</span><span class="sxs-lookup"><span data-stu-id="8a8b4-118">ThenBy</span></span>|<span data-ttu-id="8a8b4-119">Artan sırada ikincil bir sıralama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="8a8b4-119">Performs a secondary sort in ascending order.</span></span>|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="8a8b4-120">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="8a8b4-120">ThenByDescending</span></span>|<span data-ttu-id="8a8b4-121">Azalan sırada ikincil bir sıralama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="8a8b4-121">Performs a secondary sort in descending order.</span></span>|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="8a8b4-122">Reverse</span><span class="sxs-lookup"><span data-stu-id="8a8b4-122">Reverse</span></span>|<span data-ttu-id="8a8b4-123">Bir koleksiyondaki öğelerin sırasını tersine çevirir.</span><span class="sxs-lookup"><span data-stu-id="8a8b4-123">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="8a8b4-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="8a8b4-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="8a8b4-125">Sorgu Ifadesi söz dizimi örnekleri</span><span class="sxs-lookup"><span data-stu-id="8a8b4-125">Query Expression Syntax Examples</span></span>  
  
### <a name="primary-sort-examples"></a><span data-ttu-id="8a8b4-126">Birincil sıralama örnekleri</span><span class="sxs-lookup"><span data-stu-id="8a8b4-126">Primary Sort Examples</span></span>  
  
#### <a name="primary-ascending-sort"></a><span data-ttu-id="8a8b4-127">Birincil artan sıralama</span><span class="sxs-lookup"><span data-stu-id="8a8b4-127">Primary Ascending Sort</span></span>  
 <span data-ttu-id="8a8b4-128">Aşağıdaki örnek, bir dizideki dizeleri dize uzunluğuna göre artan sırada sıralamak için bir LINQ sorgusunda `orderby` yan tümcesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8a8b4-128">The following example demonstrates how to use the `orderby` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>  
  
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
  
#### <a name="primary-descending-sort"></a><span data-ttu-id="8a8b4-129">Birincil azalan sıralama</span><span class="sxs-lookup"><span data-stu-id="8a8b4-129">Primary Descending Sort</span></span>  
 <span data-ttu-id="8a8b4-130">Sonraki örnekte, dizeleri ilk harfine göre azalan sırada sıralamak için bir LINQ sorgusunda `orderby descending` yan tümcesinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8a8b4-130">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>  
  
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
  
### <a name="secondary-sort-examples"></a><span data-ttu-id="8a8b4-131">İkincil sıralama örnekleri</span><span class="sxs-lookup"><span data-stu-id="8a8b4-131">Secondary Sort Examples</span></span>  
  
#### <a name="secondary-ascending-sort"></a><span data-ttu-id="8a8b4-132">İkincil artan sıralama</span><span class="sxs-lookup"><span data-stu-id="8a8b4-132">Secondary Ascending Sort</span></span>  
 <span data-ttu-id="8a8b4-133">Aşağıdaki örnek, bir dizideki dizelerin birincil ve ikincil sıralamasını gerçekleştirmek için bir LINQ sorgusunda `orderby` yan tümcesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8a8b4-133">The following example demonstrates how to use the `orderby` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="8a8b4-134">Dizeler birincil olarak length ve secondarily ile dizenin ilk harfine göre, her ikisi de artan düzende sıralanır.</span><span class="sxs-lookup"><span data-stu-id="8a8b4-134">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>  
  
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
  
#### <a name="secondary-descending-sort"></a><span data-ttu-id="8a8b4-135">İkincil azalan sıralama</span><span class="sxs-lookup"><span data-stu-id="8a8b4-135">Secondary Descending Sort</span></span>  
 <span data-ttu-id="8a8b4-136">Sonraki örnekte, bir LINQ sorgusunda `orderby descending` yan tümcesinin nasıl kullanılacağı gösterilmektedir ve bu bir birincil sıralama, artan düzende, ikincil bir sıralama ise azalan düzende yapılır.</span><span class="sxs-lookup"><span data-stu-id="8a8b4-136">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="8a8b4-137">Dizeler öncelikle dizenin ilk harfine göre uzunluğa ve secondarily göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="8a8b4-137">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8a8b4-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a8b4-138">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="8a8b4-139">Standart sorgu Işleçlerine genelC#bakış ()</span><span class="sxs-lookup"><span data-stu-id="8a8b4-139">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="8a8b4-140">orderby yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="8a8b4-140">orderby clause</span></span>](../../../language-reference/keywords/orderby-clause.md)
- [<span data-ttu-id="8a8b4-141">Join yan tümcesinin sonuçlarını sıralama</span><span class="sxs-lookup"><span data-stu-id="8a8b4-141">Order the results of a join clause</span></span>](../../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="8a8b4-142">Her kelime veya alana göre metin verilerini sıralama veya filtreleme (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="8a8b4-142">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
