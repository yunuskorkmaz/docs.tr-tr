---
title: Verileri sıralama (C#)
ms.date: 07/20/2015
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
ms.openlocfilehash: 90ff7d52e6832935fe16e081e904acae3a24669a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43402035"
---
# <a name="sorting-data-c"></a><span data-ttu-id="e96c3-102">Verileri sıralama (C#)</span><span class="sxs-lookup"><span data-stu-id="e96c3-102">Sorting Data (C#)</span></span>
<span data-ttu-id="e96c3-103">Sıralama işlemi bir veya daha fazla özniteliklerine dayalı bir dizinin öğeleri sıralar.</span><span class="sxs-lookup"><span data-stu-id="e96c3-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="e96c3-104">İlk sıralama ölçütü öğelerde birincil sıralama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="e96c3-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="e96c3-105">İkinci bir sıralama ölçütünü belirterek, her birincil sıralama grup içindeki öğeleri sıralayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e96c3-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>  
  
 <span data-ttu-id="e96c3-106">Aşağıdaki çizimde, bir dizi karakter bir alfabetik sıralama işlemi sonuçlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e96c3-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters.</span></span>  
  
 <span data-ttu-id="e96c3-107">![Sıralama işlemi LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")</span><span class="sxs-lookup"><span data-stu-id="e96c3-107">![LINQ Sorting Operation](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")</span></span>  
  
 <span data-ttu-id="e96c3-108">Verileri sıralama standart sorgu işleci yöntemleri aşağıdaki bölümünde listelenir.</span><span class="sxs-lookup"><span data-stu-id="e96c3-108">The standard query operator methods that sort data are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e96c3-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e96c3-109">Methods</span></span>  
  
|<span data-ttu-id="e96c3-110">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="e96c3-110">Method Name</span></span>|<span data-ttu-id="e96c3-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e96c3-111">Description</span></span>|<span data-ttu-id="e96c3-112">C# sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e96c3-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="e96c3-113">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="e96c3-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="e96c3-114">OrderBy</span><span class="sxs-lookup"><span data-stu-id="e96c3-114">OrderBy</span></span>|<span data-ttu-id="e96c3-115">Artan değerleri sıralar.</span><span class="sxs-lookup"><span data-stu-id="e96c3-115">Sorts values in ascending order.</span></span>|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="e96c3-116">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="e96c3-116">OrderByDescending</span></span>|<span data-ttu-id="e96c3-117">Değerleri azalan düzende sıralar.</span><span class="sxs-lookup"><span data-stu-id="e96c3-117">Sorts values in descending order.</span></span>|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="e96c3-118">ThenBy</span><span class="sxs-lookup"><span data-stu-id="e96c3-118">ThenBy</span></span>|<span data-ttu-id="e96c3-119">İkincil bir sıralama, azalan sırada gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="e96c3-119">Performs a secondary sort in ascending order.</span></span>|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="e96c3-120">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="e96c3-120">ThenByDescending</span></span>|<span data-ttu-id="e96c3-121">İkincil bir sıralama, azalan sırada gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="e96c3-121">Performs a secondary sort in descending order.</span></span>|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="e96c3-122">geriye doğru</span><span class="sxs-lookup"><span data-stu-id="e96c3-122">Reverse</span></span>|<span data-ttu-id="e96c3-123">Bir koleksiyondaki öğelerin sırasını tersine çevirir.</span><span class="sxs-lookup"><span data-stu-id="e96c3-123">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="e96c3-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="e96c3-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="e96c3-125">Sorgu ifadesi söz dizimi örnekleri</span><span class="sxs-lookup"><span data-stu-id="e96c3-125">Query Expression Syntax Examples</span></span>  
  
### <a name="primary-sort-examples"></a><span data-ttu-id="e96c3-126">Birincil sıralama örnekleri</span><span class="sxs-lookup"><span data-stu-id="e96c3-126">Primary Sort Examples</span></span>  
  
#### <a name="primary-ascending-sort"></a><span data-ttu-id="e96c3-127">Birincil artan sıralama</span><span class="sxs-lookup"><span data-stu-id="e96c3-127">Primary Ascending Sort</span></span>  
 <span data-ttu-id="e96c3-128">Aşağıdaki örnek nasıl kullanılacağını gösterir `orderby` artan düzende dize uzunluğu, dizi dizeleri sıralamak için bir LINQ sorgu yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="e96c3-128">The following example demonstrates how to use the `orderby` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>  
  
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
  
#### <a name="primary-descending-sort"></a><span data-ttu-id="e96c3-129">Birincil azalan sıralama</span><span class="sxs-lookup"><span data-stu-id="e96c3-129">Primary Descending Sort</span></span>  
 <span data-ttu-id="e96c3-130">Sonraki örnek nasıl kullanılacağını gösterir `orderby descending` azalan düzende, ilk harfini dizeleri sıralamak için bir LINQ sorgu yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="e96c3-130">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>  
  
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
  
### <a name="secondary-sort-examples"></a><span data-ttu-id="e96c3-131">İkincil sıralama örnekleri</span><span class="sxs-lookup"><span data-stu-id="e96c3-131">Secondary Sort Examples</span></span>  
  
#### <a name="secondary-ascending-sort"></a><span data-ttu-id="e96c3-132">İkincil artan sıralama</span><span class="sxs-lookup"><span data-stu-id="e96c3-132">Secondary Ascending Sort</span></span>  
 <span data-ttu-id="e96c3-133">Aşağıdaki örnek nasıl kullanılacağını gösterir `orderby` bir dizide dize birincil ve ikincil bir sıralama gerçekleştirmek için bir LINQ sorgu yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="e96c3-133">The following example demonstrates how to use the `orderby` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="e96c3-134">Dizeleri öncelikle uzunluğu ve ürüne göre ilk harfini dize hem artan düzende sıralanır.</span><span class="sxs-lookup"><span data-stu-id="e96c3-134">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>  
  
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
  
#### <a name="secondary-descending-sort"></a><span data-ttu-id="e96c3-135">İkincil azalan sıralama</span><span class="sxs-lookup"><span data-stu-id="e96c3-135">Secondary Descending Sort</span></span>  
 <span data-ttu-id="e96c3-136">Sonraki örnek nasıl kullanılacağını gösterir `orderby descending` birincil bir sıralama düzeni ve ikincil bir sıralama, azalan düzende, artan düzende gerçekleştirmek için bir LINQ sorgu yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="e96c3-136">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="e96c3-137">Dizeleri öncelikle uzunluğu ve ürüne dizenin ilk harfini sıralanır.</span><span class="sxs-lookup"><span data-stu-id="e96c3-137">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e96c3-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e96c3-138">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="e96c3-139">Standart sorgu işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="e96c3-139">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="e96c3-140">orderby yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="e96c3-140">orderby clause</span></span>](../../../../csharp/language-reference/keywords/orderby-clause.md)  
 [<span data-ttu-id="e96c3-141">Nasıl yapılır: Join tümcesinin sonuçlarını sıralama</span><span class="sxs-lookup"><span data-stu-id="e96c3-141">How to: Order the Results of a Join Clause</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)  
 [<span data-ttu-id="e96c3-142">Nasıl yapılır: herhangi bir sözcük veya alana (LINQ) (C#) göre filtre metin verilerini sıralama veya</span><span class="sxs-lookup"><span data-stu-id="e96c3-142">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
