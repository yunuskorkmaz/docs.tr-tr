---
title: Verileri gruplandırma (C#)
ms.date: 07/20/2015
ms.assetid: e414e9e4-343a-4e6e-858f-4a30c5e64492
ms.openlocfilehash: 15dafdb144ee9fd4184d4c8281d041e03161a16b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594195"
---
# <a name="grouping-data-c"></a><span data-ttu-id="79ff0-102">Verileri gruplandırma (C#)</span><span class="sxs-lookup"><span data-stu-id="79ff0-102">Grouping Data (C#)</span></span>
<span data-ttu-id="79ff0-103">Gruplandırma, her bir gruptaki öğelerin ortak bir özniteliği paylaşması için verileri gruplara yerleştirme işlemini ifade eder.</span><span class="sxs-lookup"><span data-stu-id="79ff0-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="79ff0-104">Aşağıdaki çizimde, bir karakter dizisini gruplandırmanın sonuçları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="79ff0-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="79ff0-105">Her grup için anahtar karakterdir.</span><span class="sxs-lookup"><span data-stu-id="79ff0-105">The key for each group is the character.</span></span>  
  
 ![LINQ gruplama işlemini gösteren diyagram.](./media/grouping-data/linq-group-operation.png)  
  
 <span data-ttu-id="79ff0-107">Veri öğelerini gruplamak için kullanılan standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="79ff0-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="79ff0-108">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="79ff0-108">Methods</span></span>  
  
|<span data-ttu-id="79ff0-109">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="79ff0-109">Method Name</span></span>|<span data-ttu-id="79ff0-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79ff0-110">Description</span></span>|<span data-ttu-id="79ff0-111">C#Sorgu Ifadesi söz dizimi</span><span class="sxs-lookup"><span data-stu-id="79ff0-111">C# Query Expression Syntax</span></span>|<span data-ttu-id="79ff0-112">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="79ff0-112">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="79ff0-113">Ölçütü</span><span class="sxs-lookup"><span data-stu-id="79ff0-113">GroupBy</span></span>|<span data-ttu-id="79ff0-114">Ortak bir özniteliği paylaşan öğeleri gruplandırır.</span><span class="sxs-lookup"><span data-stu-id="79ff0-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="79ff0-115">Her grup bir <xref:System.Linq.IGrouping%602> nesne tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="79ff0-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`group … by`<br /><br /> <span data-ttu-id="79ff0-116">-veya-</span><span class="sxs-lookup"><span data-stu-id="79ff0-116">-or-</span></span><br /><br /> `group … by … into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="79ff0-117">ToLookup</span><span class="sxs-lookup"><span data-stu-id="79ff0-117">ToLookup</span></span>|<span data-ttu-id="79ff0-118">Bir <xref:System.Linq.Lookup%602> anahtar Seçici işlevine göre öğeleri (bire çok sözlüğüne) ekler.</span><span class="sxs-lookup"><span data-stu-id="79ff0-118">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="79ff0-119">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="79ff0-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="79ff0-120">Sorgu Ifadesi söz dizimi örneği</span><span class="sxs-lookup"><span data-stu-id="79ff0-120">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="79ff0-121">Aşağıdaki kod örneği, bir listedeki `group by` tamsayıları, hatta veya tek olup olmadığına göre gruplamak için yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="79ff0-121">The following code example uses the `group by` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="79ff0-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79ff0-122">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="79ff0-123">Standart sorgu Işleçlerine genelC#bakış ()</span><span class="sxs-lookup"><span data-stu-id="79ff0-123">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="79ff0-124">group yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="79ff0-124">group clause</span></span>](../../../language-reference/keywords/group-clause.md)
- [<span data-ttu-id="79ff0-125">Nasıl yapılır: Iç Içe geçmiş grup oluşturma</span><span class="sxs-lookup"><span data-stu-id="79ff0-125">How to: Create a Nested Group</span></span>](../../linq-query-expressions/how-to-create-a-nested-group.md)
- [<span data-ttu-id="79ff0-126">Nasıl yapılır: Dosyaları uzantıya göre Gruplandır (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="79ff0-126">How to: Group Files by Extension (LINQ) (C#)</span></span>](./how-to-group-files-by-extension-linq.md)
- [<span data-ttu-id="79ff0-127">Nasıl yapılır: Sorgu sonuçlarını gruplandırma</span><span class="sxs-lookup"><span data-stu-id="79ff0-127">How to: Group Query Results</span></span>](../../linq-query-expressions/how-to-group-query-results.md)
- [<span data-ttu-id="79ff0-128">Nasıl yapılır: Gruplandırma Işleminde alt sorgu gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="79ff0-128">How to: Perform a Subquery on a Grouping Operation</span></span>](../../linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md)
- [<span data-ttu-id="79ff0-129">Nasıl yapılır: Grupları (LINQ) kullanarak bir dosyayı çok sayıda dosyaya bölme (LINQC#) ()</span><span class="sxs-lookup"><span data-stu-id="79ff0-129">How to: Split a File Into Many Files by Using Groups (LINQ) (C#)</span></span>](./how-to-split-a-file-into-many-files-by-using-groups-linq.md)
