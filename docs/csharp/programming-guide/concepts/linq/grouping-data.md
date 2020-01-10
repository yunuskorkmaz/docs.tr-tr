---
title: Verileri gruplandırma (C#)
ms.date: 07/20/2015
ms.assetid: e414e9e4-343a-4e6e-858f-4a30c5e64492
ms.openlocfilehash: 7ef3d3c9097d7a9478605565518ac8975feb9fe2
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635749"
---
# <a name="grouping-data-c"></a><span data-ttu-id="066f9-102">Verileri gruplandırma (C#)</span><span class="sxs-lookup"><span data-stu-id="066f9-102">Grouping Data (C#)</span></span>
<span data-ttu-id="066f9-103">Gruplandırma, her bir gruptaki öğelerin ortak bir özniteliği paylaşması için verileri gruplara yerleştirme işlemini ifade eder.</span><span class="sxs-lookup"><span data-stu-id="066f9-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="066f9-104">Aşağıdaki çizimde, bir karakter dizisini gruplandırmanın sonuçları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="066f9-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="066f9-105">Her grup için anahtar karakterdir.</span><span class="sxs-lookup"><span data-stu-id="066f9-105">The key for each group is the character.</span></span>  
  
 ![LINQ gruplama işlemini gösteren diyagram.](./media/grouping-data/linq-group-operation.png)  
  
 <span data-ttu-id="066f9-107">Veri öğelerini gruplamak için kullanılan standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="066f9-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="066f9-108">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="066f9-108">Methods</span></span>  
  
|<span data-ttu-id="066f9-109">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="066f9-109">Method Name</span></span>|<span data-ttu-id="066f9-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="066f9-110">Description</span></span>|<span data-ttu-id="066f9-111">C#Sorgu Ifadesi söz dizimi</span><span class="sxs-lookup"><span data-stu-id="066f9-111">C# Query Expression Syntax</span></span>|<span data-ttu-id="066f9-112">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="066f9-112">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="066f9-113">GroupBy</span><span class="sxs-lookup"><span data-stu-id="066f9-113">GroupBy</span></span>|<span data-ttu-id="066f9-114">Ortak bir özniteliği paylaşan öğeleri gruplandırır.</span><span class="sxs-lookup"><span data-stu-id="066f9-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="066f9-115">Her grup <xref:System.Linq.IGrouping%602> nesne tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="066f9-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`group … by`<br /><br /> <span data-ttu-id="066f9-116">veya</span><span class="sxs-lookup"><span data-stu-id="066f9-116">-or-</span></span><br /><br /> `group … by … into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="066f9-117">ToLookup</span><span class="sxs-lookup"><span data-stu-id="066f9-117">ToLookup</span></span>|<span data-ttu-id="066f9-118">Bir anahtar Seçici işlevine dayalı olarak bir <xref:System.Linq.Lookup%602> (bire çok sözlüğüne) öğe ekler.</span><span class="sxs-lookup"><span data-stu-id="066f9-118">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="066f9-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="066f9-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="066f9-120">Sorgu Ifadesi söz dizimi örneği</span><span class="sxs-lookup"><span data-stu-id="066f9-120">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="066f9-121">Aşağıdaki kod örneği, bir listedeki tamsayıları, hatta veya tek olup olmadığına göre gruplamak için `group by` yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="066f9-121">The following code example uses the `group by` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="066f9-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="066f9-122">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="066f9-123">Standart sorgu Işleçlerine genelC#bakış ()</span><span class="sxs-lookup"><span data-stu-id="066f9-123">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="066f9-124">group yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="066f9-124">group clause</span></span>](../../../language-reference/keywords/group-clause.md)
- [<span data-ttu-id="066f9-125">İç içe geçmiş grup oluşturma</span><span class="sxs-lookup"><span data-stu-id="066f9-125">Create a nested group</span></span>](../../../linq/create-a-nested-group.md)
- [<span data-ttu-id="066f9-126">Dosyaları uzantıya göre gruplama (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="066f9-126">How to group files by extension (LINQ) (C#)</span></span>](./how-to-group-files-by-extension-linq.md)
- [<span data-ttu-id="066f9-127">Sorgu sonuçlarını gruplandırma</span><span class="sxs-lookup"><span data-stu-id="066f9-127">Group query results</span></span>](../../../linq/group-query-results.md)
- [<span data-ttu-id="066f9-128">Gruplandırma işleminde alt sorgu gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="066f9-128">Perform a subquery on a grouping operation</span></span>](../../../linq/perform-a-subquery-on-a-grouping-operation.md)
- [<span data-ttu-id="066f9-129">Grupları (LINQ) kullanarak bir dosyayı birden çok dosyaya bölme (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="066f9-129">How to split a file into many files by using groups (LINQ) (C#)</span></span>](./how-to-split-a-file-into-many-files-by-using-groups-linq.md)
