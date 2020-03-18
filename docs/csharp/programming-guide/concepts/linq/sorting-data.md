---
title: Verileri Sıralama (C#)
ms.date: 07/20/2015
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
ms.openlocfilehash: 29a5e3e685bdc73536961b7783f4986796b46bdf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167913"
---
# <a name="sorting-data-c"></a><span data-ttu-id="eb8a9-102">Verileri Sıralama (C#)</span><span class="sxs-lookup"><span data-stu-id="eb8a9-102">Sorting Data (C#)</span></span>
<span data-ttu-id="eb8a9-103">Sıralama işlemi, bir veya daha fazla özöğeyi temel alan bir dizinin öğelerini sıralar.</span><span class="sxs-lookup"><span data-stu-id="eb8a9-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="eb8a9-104">İlk sıralama ölçütü öğeler üzerinde birincil sıralama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="eb8a9-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="eb8a9-105">İkinci bir sıralama ölçütü belirterek, her birincil sıralama grubundaki öğeleri sıralayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb8a9-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>  
  
 <span data-ttu-id="eb8a9-106">Aşağıdaki resimde, bir karakter dizisi üzerinde alfabetik sıralama işleminin sonuçları gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="eb8a9-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters:</span></span>
  
 ![Alfabetik sıralama işlemi gösteren grafik.](./media/sorting-data/alphabetical-sort-operation.png)  
  
 <span data-ttu-id="eb8a9-108">Verileri sıralayan standart sorgu işleci yöntemleri aşağıdaki bölümde listelenir.</span><span class="sxs-lookup"><span data-stu-id="eb8a9-108">The standard query operator methods that sort data are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eb8a9-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="eb8a9-109">Methods</span></span>  
  
|<span data-ttu-id="eb8a9-110">Yöntem Adı</span><span class="sxs-lookup"><span data-stu-id="eb8a9-110">Method Name</span></span>|<span data-ttu-id="eb8a9-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eb8a9-111">Description</span></span>|<span data-ttu-id="eb8a9-112">C# Sorgu İfade Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eb8a9-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="eb8a9-113">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="eb8a9-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="eb8a9-114">Orderby</span><span class="sxs-lookup"><span data-stu-id="eb8a9-114">OrderBy</span></span>|<span data-ttu-id="eb8a9-115">Değerleri artan sırada sıralar.</span><span class="sxs-lookup"><span data-stu-id="eb8a9-115">Sorts values in ascending order.</span></span>|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="eb8a9-116">Orderbydescending</span><span class="sxs-lookup"><span data-stu-id="eb8a9-116">OrderByDescending</span></span>|<span data-ttu-id="eb8a9-117">Değerleri azalan sırada sıralar.</span><span class="sxs-lookup"><span data-stu-id="eb8a9-117">Sorts values in descending order.</span></span>|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="eb8a9-118">Thenby</span><span class="sxs-lookup"><span data-stu-id="eb8a9-118">ThenBy</span></span>|<span data-ttu-id="eb8a9-119">Artan sırada ikincil bir sıralama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="eb8a9-119">Performs a secondary sort in ascending order.</span></span>|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="eb8a9-120">Thenbydescending</span><span class="sxs-lookup"><span data-stu-id="eb8a9-120">ThenByDescending</span></span>|<span data-ttu-id="eb8a9-121">Azalan sırada ikincil bir sıralama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="eb8a9-121">Performs a secondary sort in descending order.</span></span>|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="eb8a9-122">Reverse</span><span class="sxs-lookup"><span data-stu-id="eb8a9-122">Reverse</span></span>|<span data-ttu-id="eb8a9-123">Koleksiyondaki öğelerin sırasını tersine çevirir.</span><span class="sxs-lookup"><span data-stu-id="eb8a9-123">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="eb8a9-124">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="eb8a9-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="eb8a9-125">Sorgu İfadesözdizimi Örnekleri</span><span class="sxs-lookup"><span data-stu-id="eb8a9-125">Query Expression Syntax Examples</span></span>  
  
### <a name="primary-sort-examples"></a><span data-ttu-id="eb8a9-126">Birincil Sıralama Örnekleri</span><span class="sxs-lookup"><span data-stu-id="eb8a9-126">Primary Sort Examples</span></span>  
  
#### <a name="primary-ascending-sort"></a><span data-ttu-id="eb8a9-127">Birincil Artan Sıralama</span><span class="sxs-lookup"><span data-stu-id="eb8a9-127">Primary Ascending Sort</span></span>  
 <span data-ttu-id="eb8a9-128">Aşağıdaki örnek, bir dizideki `orderby` dizeleri artan sırada dize uzunluğuna göre sıralamak için BIR LINQ sorgusunda yan tümcenin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="eb8a9-128">The following example demonstrates how to use the `orderby` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>  
  
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
  
#### <a name="primary-descending-sort"></a><span data-ttu-id="eb8a9-129">Birincil Azalan Sıralama</span><span class="sxs-lookup"><span data-stu-id="eb8a9-129">Primary Descending Sort</span></span>  
 <span data-ttu-id="eb8a9-130">Sonraki örnek, dizeleri azalan `orderby descending` sırada ilk harflerine göre sıralamak için bir LINQ sorgusunda yan tümcenin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="eb8a9-130">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>  
  
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
  
### <a name="secondary-sort-examples"></a><span data-ttu-id="eb8a9-131">İkincil Sıralama Örnekleri</span><span class="sxs-lookup"><span data-stu-id="eb8a9-131">Secondary Sort Examples</span></span>  
  
#### <a name="secondary-ascending-sort"></a><span data-ttu-id="eb8a9-132">İkincil Artan Sıralama</span><span class="sxs-lookup"><span data-stu-id="eb8a9-132">Secondary Ascending Sort</span></span>  
 <span data-ttu-id="eb8a9-133">Aşağıdaki örnek, bir dizideki `orderby` dizeleri birincil ve ikincil bir tür gerçekleştirmek için bir LINQ sorgusunda yan tümceyi nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="eb8a9-133">The following example demonstrates how to use the `orderby` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="eb8a9-134">Dizeleri öncelikle uzunluk ve ikinci olarak dize ilk harfi, her ikisi de artan sırada sıralanır.</span><span class="sxs-lookup"><span data-stu-id="eb8a9-134">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>  
  
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
  
#### <a name="secondary-descending-sort"></a><span data-ttu-id="eb8a9-135">İkincil Azalan Sıralama</span><span class="sxs-lookup"><span data-stu-id="eb8a9-135">Secondary Descending Sort</span></span>  
 <span data-ttu-id="eb8a9-136">Sonraki örnek, bir birincil `orderby descending` sıralama gerçekleştirmek için bir LINQ sorgusunda yan tümcesinin nasıl kullanılacağını, artan sırada ve ikincil sıralamayı azalan sırada gösterir.</span><span class="sxs-lookup"><span data-stu-id="eb8a9-136">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="eb8a9-137">Dizeleri öncelikle uzunluk ve ikinci olarak dize ilk harfi tarafından sıralanır.</span><span class="sxs-lookup"><span data-stu-id="eb8a9-137">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="eb8a9-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb8a9-138">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="eb8a9-139">Standart Sorgu Operatörlerine Genel Bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="eb8a9-139">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="eb8a9-140">orderby yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="eb8a9-140">orderby clause</span></span>](../../../language-reference/keywords/orderby-clause.md)
- [<span data-ttu-id="eb8a9-141">Join yan tümcesinin sonuçlarını sıralama</span><span class="sxs-lookup"><span data-stu-id="eb8a9-141">Order the results of a join clause</span></span>](../../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="eb8a9-142">Metin verilerini herhangi bir sözcüğe veya alana göre sıralama veya filtreleme (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="eb8a9-142">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
