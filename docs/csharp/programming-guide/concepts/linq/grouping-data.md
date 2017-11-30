---
title: "Verileri gruplandırma (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: e414e9e4-343a-4e6e-858f-4a30c5e64492
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4aef8d10eaffb384fe919ffa6a1e742cb837f540
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="grouping-data-c"></a><span data-ttu-id="d7949-102">Verileri gruplandırma (C#)</span><span class="sxs-lookup"><span data-stu-id="d7949-102">Grouping Data (C#)</span></span>
<span data-ttu-id="d7949-103">Gruplandırma, böylece her grup içindeki öğeleri ortak bir özniteliği paylaşan gruplar halinde veri koyma işlemi için ifade eder.</span><span class="sxs-lookup"><span data-stu-id="d7949-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="d7949-104">Aşağıdaki çizimde bir karakter dizisi gruplandırma sonuçlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d7949-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="d7949-105">Her grup için karakterin anahtarıdır.</span><span class="sxs-lookup"><span data-stu-id="d7949-105">The key for each group is the character.</span></span>  
  
 <span data-ttu-id="d7949-106">![LINQ gruplandırma işlemleri](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span><span class="sxs-lookup"><span data-stu-id="d7949-106">![LINQ Grouping Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span></span>  
  
 <span data-ttu-id="d7949-107">Veri öğeleri Grup standart sorgu işleci yöntemler aşağıdaki bölümde listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="d7949-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d7949-108">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d7949-108">Methods</span></span>  
  
|<span data-ttu-id="d7949-109">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="d7949-109">Method Name</span></span>|<span data-ttu-id="d7949-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d7949-110">Description</span></span>|<span data-ttu-id="d7949-111">C# sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d7949-111">C# Query Expression Syntax</span></span>|<span data-ttu-id="d7949-112">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="d7949-112">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="d7949-113">GroupBy</span><span class="sxs-lookup"><span data-stu-id="d7949-113">GroupBy</span></span>|<span data-ttu-id="d7949-114">Ortak bir özniteliği paylaşan grupları öğeleri.</span><span class="sxs-lookup"><span data-stu-id="d7949-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="d7949-115">Her grubu tarafından temsil edilen bir <xref:System.Linq.IGrouping%602> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="d7949-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`group … by`<br /><br /> <span data-ttu-id="d7949-116">veya</span><span class="sxs-lookup"><span data-stu-id="d7949-116">-or-</span></span><br /><br /> `group … by … into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d7949-117">ToLookup</span><span class="sxs-lookup"><span data-stu-id="d7949-117">ToLookup</span></span>|<span data-ttu-id="d7949-118">Elemanlara ekler bir <xref:System.Linq.Lookup%602> (bir-çok sözlük) dayalı bir anahtar Seçici işlevdir.</span><span class="sxs-lookup"><span data-stu-id="d7949-118">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="d7949-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="d7949-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="d7949-120">Sorgu ifade sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="d7949-120">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="d7949-121">Aşağıdaki kod örneğinde `group by` bile veya alışılmadık olup olmadıkları göre listesini Grup tamsayılar yan tümcesini.</span><span class="sxs-lookup"><span data-stu-id="d7949-121">The following code example uses the `group by` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d7949-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d7949-122">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="d7949-123">Standart sorgu işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="d7949-123">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="d7949-124">Group tümcesi</span><span class="sxs-lookup"><span data-stu-id="d7949-124">group clause</span></span>](../../../../csharp/language-reference/keywords/group-clause.md)  
 [<span data-ttu-id="d7949-125">Nasıl yapılır: iç içe geçmiş grup oluşturma</span><span class="sxs-lookup"><span data-stu-id="d7949-125">How to: Create a Nested Group</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-create-a-nested-group.md)  
 [<span data-ttu-id="d7949-126">Nasıl yapılır: dosyaları uzantıya (LINQ) (C#) göre gruplama</span><span class="sxs-lookup"><span data-stu-id="d7949-126">How to: Group Files by Extension (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 [<span data-ttu-id="d7949-127">Nasıl yapılır: sorgu sonuçlarını gruplandırma</span><span class="sxs-lookup"><span data-stu-id="d7949-127">How to: Group Query Results</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-group-query-results.md)  
 [<span data-ttu-id="d7949-128">Nasıl yapılır: gruplandırma işleminde alt sorgu gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="d7949-128">How to: Perform a Subquery on a Grouping Operation</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md)  
 [<span data-ttu-id="d7949-129">Nasıl yapılır: bir dosya grupları (LINQ) (C#) kullanarak birden çok dosyaya bölme</span><span class="sxs-lookup"><span data-stu-id="d7949-129">How to: Split a File Into Many Files by Using Groups (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
