---
title: Verileri gruplandırma (C#)
description: Gruplandırma, verileri bir özniteliği paylaşan öğe gruplarına koyar. C# ' de veri öğelerini gruplamanın standart sorgu işleci yöntemleri hakkında bilgi edinin.
ms.date: 07/20/2015
ms.assetid: e414e9e4-343a-4e6e-858f-4a30c5e64492
ms.openlocfilehash: 584d50fc15dd8b4ce1cfdf4766f3bc8b8383eb12
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202571"
---
# <a name="grouping-data-c"></a><span data-ttu-id="1908f-104">Verileri gruplandırma (C#)</span><span class="sxs-lookup"><span data-stu-id="1908f-104">Grouping Data (C#)</span></span>

<span data-ttu-id="1908f-105">Gruplandırma, her bir gruptaki öğelerin ortak bir özniteliği paylaşması için verileri gruplara yerleştirme işlemini ifade eder.</span><span class="sxs-lookup"><span data-stu-id="1908f-105">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="1908f-106">Aşağıdaki çizimde, bir karakter dizisini gruplandırmanın sonuçları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1908f-106">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="1908f-107">Her grup için anahtar karakterdir.</span><span class="sxs-lookup"><span data-stu-id="1908f-107">The key for each group is the character.</span></span>  
  
 ![LINQ gruplama işlemini gösteren diyagram.](./media/grouping-data/linq-group-operation.png)  
  
 <span data-ttu-id="1908f-109">Veri öğelerini gruplamak için kullanılan standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="1908f-109">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1908f-110">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1908f-110">Methods</span></span>  
  
|<span data-ttu-id="1908f-111">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="1908f-111">Method Name</span></span>|<span data-ttu-id="1908f-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1908f-112">Description</span></span>|<span data-ttu-id="1908f-113">C# sorgu Ifadesi sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1908f-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="1908f-114">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="1908f-114">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="1908f-115">GroupBy</span><span class="sxs-lookup"><span data-stu-id="1908f-115">GroupBy</span></span>|<span data-ttu-id="1908f-116">Ortak bir özniteliği paylaşan öğeleri gruplandırır.</span><span class="sxs-lookup"><span data-stu-id="1908f-116">Groups elements that share a common attribute.</span></span> <span data-ttu-id="1908f-117">Her grup bir nesne tarafından temsil edilir <xref:System.Linq.IGrouping%602> .</span><span class="sxs-lookup"><span data-stu-id="1908f-117">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`group … by`<br /><br /> <span data-ttu-id="1908f-118">-veya-</span><span class="sxs-lookup"><span data-stu-id="1908f-118">-or-</span></span><br /><br /> `group … by … into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="1908f-119">ToLookup</span><span class="sxs-lookup"><span data-stu-id="1908f-119">ToLookup</span></span>|<span data-ttu-id="1908f-120">Bir <xref:System.Linq.Lookup%602> anahtar Seçici işlevine göre öğeleri (bire çok sözlüğüne) ekler.</span><span class="sxs-lookup"><span data-stu-id="1908f-120">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="1908f-121">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="1908f-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="1908f-122">Sorgu Ifadesi söz dizimi örneği</span><span class="sxs-lookup"><span data-stu-id="1908f-122">Query Expression Syntax Example</span></span>  

 <span data-ttu-id="1908f-123">Aşağıdaki kod örneği, `group by` bir listedeki tamsayıları, hatta veya tek olup olmadığına göre gruplamak için yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1908f-123">The following code example uses the `group by` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
```csharp  
List<int> numbers = new List<int>() { 35, 44, 200, 84, 3987, 4, 199, 329, 446, 208 };  
  
IEnumerable<IGrouping<int, int>> query = from number in numbers  
                                         group number by number % 2;  
  
foreach (var group in query)  
{  
    Console.WriteLine(group.Key == 0 ? "\nEven numbers:" : "\nOdd numbers:");  
    foreach (int i in group)  
        Console.WriteLine(i);  
}  
  
/* This code produces the following output:  
  
    Odd numbers:  
    35  
    3987  
    199  
    329  
  
    Even numbers:  
    44  
    200  
    84  
    4  
    446  
    208  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="1908f-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1908f-124">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="1908f-125">Standart sorgu Işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="1908f-125">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="1908f-126">group tümcesi</span><span class="sxs-lookup"><span data-stu-id="1908f-126">group clause</span></span>](../../../language-reference/keywords/group-clause.md)
- [<span data-ttu-id="1908f-127">İç içe geçmiş grup oluşturma</span><span class="sxs-lookup"><span data-stu-id="1908f-127">Create a nested group</span></span>](../../../linq/create-a-nested-group.md)
- [<span data-ttu-id="1908f-128">Dosyaları uzantıya göre gruplama (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="1908f-128">How to group files by extension (LINQ) (C#)</span></span>](./how-to-group-files-by-extension-linq.md)
- [<span data-ttu-id="1908f-129">Sorgu sonuçlarını gruplandırma</span><span class="sxs-lookup"><span data-stu-id="1908f-129">Group query results</span></span>](../../../linq/group-query-results.md)
- [<span data-ttu-id="1908f-130">Gruplandırma işleminde alt sorgu gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="1908f-130">Perform a subquery on a grouping operation</span></span>](../../../linq/perform-a-subquery-on-a-grouping-operation.md)
- [<span data-ttu-id="1908f-131">Grupları (LINQ) kullanarak bir dosyayı birden çok dosyaya bölme (C#)</span><span class="sxs-lookup"><span data-stu-id="1908f-131">How to split a file into many files by using groups (LINQ) (C#)</span></span>](./how-to-split-a-file-into-many-files-by-using-groups-linq.md)
