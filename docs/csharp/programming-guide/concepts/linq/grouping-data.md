---
title: Verileri gruplandırma (C#)
ms.date: 07/20/2015
ms.assetid: e414e9e4-343a-4e6e-858f-4a30c5e64492
ms.openlocfilehash: 079f346435e2f21b7c46b528d68f917f5532db66
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54583226"
---
# <a name="grouping-data-c"></a><span data-ttu-id="b47e4-102">Verileri gruplandırma (C#)</span><span class="sxs-lookup"><span data-stu-id="b47e4-102">Grouping Data (C#)</span></span>
<span data-ttu-id="b47e4-103">Gruplandırma, böylece ortak bir özniteliği her gruptaki öğe paylaştırmak gruplar halinde veri yerleştirme işlemi için ifade eder.</span><span class="sxs-lookup"><span data-stu-id="b47e4-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="b47e4-104">Aşağıdaki çizimde, bir karakter dizisi gruplandırma sonuçlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b47e4-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="b47e4-105">Her grup için anahtar karakterdir.</span><span class="sxs-lookup"><span data-stu-id="b47e4-105">The key for each group is the character.</span></span>  
  
 <span data-ttu-id="b47e4-106">![LINQ gruplandırma işlemlerinin](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span><span class="sxs-lookup"><span data-stu-id="b47e4-106">![LINQ Grouping Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span></span>  
  
 <span data-ttu-id="b47e4-107">Veri öğeleri gruplayın standart sorgu işleci yöntemleri aşağıdaki bölümünde listelenir.</span><span class="sxs-lookup"><span data-stu-id="b47e4-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b47e4-108">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b47e4-108">Methods</span></span>  
  
|<span data-ttu-id="b47e4-109">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="b47e4-109">Method Name</span></span>|<span data-ttu-id="b47e4-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b47e4-110">Description</span></span>|<span data-ttu-id="b47e4-111">C# sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b47e4-111">C# Query Expression Syntax</span></span>|<span data-ttu-id="b47e4-112">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="b47e4-112">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="b47e4-113">Gruplandırma ölçütü</span><span class="sxs-lookup"><span data-stu-id="b47e4-113">GroupBy</span></span>|<span data-ttu-id="b47e4-114">Sık kullanılan bir özniteliği paylaşan öğeleri gruplandırır.</span><span class="sxs-lookup"><span data-stu-id="b47e4-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="b47e4-115">Her grubu tarafından temsil edilen bir <xref:System.Linq.IGrouping%602> nesne.</span><span class="sxs-lookup"><span data-stu-id="b47e4-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`group … by`<br /><br /> <span data-ttu-id="b47e4-116">-veya-</span><span class="sxs-lookup"><span data-stu-id="b47e4-116">-or-</span></span><br /><br /> `group … by … into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b47e4-117">ToLookup</span><span class="sxs-lookup"><span data-stu-id="b47e4-117">ToLookup</span></span>|<span data-ttu-id="b47e4-118">İçine bir öğe ekler; bir <xref:System.Linq.Lookup%602> (bire çok bir sözlük) tabanlı bir anahtar Seçici işlevdir.</span><span class="sxs-lookup"><span data-stu-id="b47e4-118">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="b47e4-119">Uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="b47e4-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="b47e4-120">Sorgu ifade sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="b47e4-120">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="b47e4-121">Aşağıdaki kod örneğinde `group by` yan tümcesi bir liste çift veya tek sayı olup olmadıkları göre grup dizisidir.</span><span class="sxs-lookup"><span data-stu-id="b47e4-121">The following code example uses the `group by` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b47e4-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b47e4-122">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="b47e4-123">Standart sorgu işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="b47e4-123">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="b47e4-124">group yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="b47e4-124">group clause</span></span>](../../../../csharp/language-reference/keywords/group-clause.md)
- [<span data-ttu-id="b47e4-125">Nasıl yapılır: İç içe geçmiş grup oluşturma</span><span class="sxs-lookup"><span data-stu-id="b47e4-125">How to: Create a Nested Group</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-create-a-nested-group.md)
- [<span data-ttu-id="b47e4-126">Nasıl yapılır: Dosyaları (LINQ) uzantıya göre gruplama (C#)</span><span class="sxs-lookup"><span data-stu-id="b47e4-126">How to: Group Files by Extension (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)
- [<span data-ttu-id="b47e4-127">Nasıl yapılır: Sorgu sonuçlarını gruplandırma</span><span class="sxs-lookup"><span data-stu-id="b47e4-127">How to: Group Query Results</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-group-query-results.md)
- [<span data-ttu-id="b47e4-128">Nasıl yapılır: Gruplandırma işleminde alt sorgu gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="b47e4-128">How to: Perform a Subquery on a Grouping Operation</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md)
- [<span data-ttu-id="b47e4-129">Nasıl yapılır: Gruplar (LINQ) kullanarak bir dosyayı birden çok dosyaya bölme (C#)</span><span class="sxs-lookup"><span data-stu-id="b47e4-129">How to: Split a File Into Many Files by Using Groups (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
