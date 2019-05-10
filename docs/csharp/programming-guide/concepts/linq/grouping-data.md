---
title: Verileri gruplandırma (C#)
ms.date: 07/20/2015
ms.assetid: e414e9e4-343a-4e6e-858f-4a30c5e64492
ms.openlocfilehash: a85babc43f673711fe1bdfa5cec1836a5073c785
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64753920"
---
# <a name="grouping-data-c"></a><span data-ttu-id="481c2-102">Verileri gruplandırma (C#)</span><span class="sxs-lookup"><span data-stu-id="481c2-102">Grouping Data (C#)</span></span>
<span data-ttu-id="481c2-103">Gruplandırma, böylece ortak bir özniteliği her gruptaki öğe paylaştırmak gruplar halinde veri yerleştirme işlemi için ifade eder.</span><span class="sxs-lookup"><span data-stu-id="481c2-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="481c2-104">Aşağıdaki çizimde, bir karakter dizisi gruplandırma sonuçlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="481c2-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="481c2-105">Her grup için anahtar karakterdir.</span><span class="sxs-lookup"><span data-stu-id="481c2-105">The key for each group is the character.</span></span>  
  
 ![LINQ gruplandırma işleminde gösteren diyagram.](./media/grouping-data/linq-group-operation.png)  
  
 <span data-ttu-id="481c2-107">Veri öğeleri gruplayın standart sorgu işleci yöntemleri aşağıdaki bölümünde listelenir.</span><span class="sxs-lookup"><span data-stu-id="481c2-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="481c2-108">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="481c2-108">Methods</span></span>  
  
|<span data-ttu-id="481c2-109">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="481c2-109">Method Name</span></span>|<span data-ttu-id="481c2-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="481c2-110">Description</span></span>|<span data-ttu-id="481c2-111">C# sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="481c2-111">C# Query Expression Syntax</span></span>|<span data-ttu-id="481c2-112">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="481c2-112">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="481c2-113">Gruplandırma ölçütü</span><span class="sxs-lookup"><span data-stu-id="481c2-113">GroupBy</span></span>|<span data-ttu-id="481c2-114">Sık kullanılan bir özniteliği paylaşan öğeleri gruplandırır.</span><span class="sxs-lookup"><span data-stu-id="481c2-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="481c2-115">Her grubu tarafından temsil edilen bir <xref:System.Linq.IGrouping%602> nesne.</span><span class="sxs-lookup"><span data-stu-id="481c2-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`group … by`<br /><br /> <span data-ttu-id="481c2-116">-veya-</span><span class="sxs-lookup"><span data-stu-id="481c2-116">-or-</span></span><br /><br /> `group … by … into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="481c2-117">ToLookup</span><span class="sxs-lookup"><span data-stu-id="481c2-117">ToLookup</span></span>|<span data-ttu-id="481c2-118">İçine bir öğe ekler; bir <xref:System.Linq.Lookup%602> (bire çok bir sözlük) tabanlı bir anahtar Seçici işlevdir.</span><span class="sxs-lookup"><span data-stu-id="481c2-118">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="481c2-119">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="481c2-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="481c2-120">Sorgu ifade sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="481c2-120">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="481c2-121">Aşağıdaki kod örneğinde `group by` yan tümcesi bir liste çift veya tek sayı olup olmadıkları göre grup dizisidir.</span><span class="sxs-lookup"><span data-stu-id="481c2-121">The following code example uses the `group by` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="481c2-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="481c2-122">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="481c2-123">Standart sorgu işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="481c2-123">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="481c2-124">group yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="481c2-124">group clause</span></span>](../../../../csharp/language-reference/keywords/group-clause.md)
- [<span data-ttu-id="481c2-125">Nasıl yapılır: İç içe geçmiş grup oluşturma</span><span class="sxs-lookup"><span data-stu-id="481c2-125">How to: Create a Nested Group</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-create-a-nested-group.md)
- [<span data-ttu-id="481c2-126">Nasıl yapılır: Dosyaları (LINQ) uzantıya göre gruplama (C#)</span><span class="sxs-lookup"><span data-stu-id="481c2-126">How to: Group Files by Extension (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)
- [<span data-ttu-id="481c2-127">Nasıl yapılır: Sorgu sonuçlarını gruplandırma</span><span class="sxs-lookup"><span data-stu-id="481c2-127">How to: Group Query Results</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-group-query-results.md)
- [<span data-ttu-id="481c2-128">Nasıl yapılır: Gruplandırma işleminde alt sorgu gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="481c2-128">How to: Perform a Subquery on a Grouping Operation</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md)
- [<span data-ttu-id="481c2-129">Nasıl yapılır: Gruplar (LINQ) kullanarak bir dosyayı birden çok dosyaya bölme (C#)</span><span class="sxs-lookup"><span data-stu-id="481c2-129">How to: Split a File Into Many Files by Using Groups (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
