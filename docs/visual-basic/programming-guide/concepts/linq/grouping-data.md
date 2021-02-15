---
description: 'Hakkında daha fazla bilgi edinin: verileri gruplandırma (Visual Basic)'
title: Verileri Gruplandırma
ms.date: 07/20/2015
ms.assetid: 8f3a0871-6958-4aef-8f6f-493e189fd57d
ms.openlocfilehash: fa6dbcc22c7d991d48775c3974cfc529840ef933
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100469805"
---
# <a name="grouping-data-visual-basic"></a><span data-ttu-id="b2921-103">Verileri gruplandırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2921-103">Grouping Data (Visual Basic)</span></span>

<span data-ttu-id="b2921-104">Gruplandırma, her bir gruptaki öğelerin ortak bir özniteliği paylaşması için verileri gruplara yerleştirme işlemini ifade eder.</span><span class="sxs-lookup"><span data-stu-id="b2921-104">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="b2921-105">Aşağıdaki çizimde, bir karakter dizisini gruplandırmanın sonuçları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b2921-105">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="b2921-106">Her grup için anahtar karakterdir.</span><span class="sxs-lookup"><span data-stu-id="b2921-106">The key for each group is the character.</span></span>  
  
 ![LINQ gruplama işlemini gösteren diyagram.](./media/grouping-data/linq-group-operation.png)  
  
 <span data-ttu-id="b2921-108">Veri öğelerini gruplamak için kullanılan standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="b2921-108">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b2921-109">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b2921-109">Methods</span></span>  
  
|<span data-ttu-id="b2921-110">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="b2921-110">Method Name</span></span>|<span data-ttu-id="b2921-111">Description</span><span class="sxs-lookup"><span data-stu-id="b2921-111">Description</span></span>|<span data-ttu-id="b2921-112">Sorgu Ifadesi söz dizimini Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b2921-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="b2921-113">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="b2921-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="b2921-114">GroupBy</span><span class="sxs-lookup"><span data-stu-id="b2921-114">GroupBy</span></span>|<span data-ttu-id="b2921-115">Ortak bir özniteliği paylaşan öğeleri gruplandırır.</span><span class="sxs-lookup"><span data-stu-id="b2921-115">Groups elements that share a common attribute.</span></span> <span data-ttu-id="b2921-116">Her grup bir nesne tarafından temsil edilir <xref:System.Linq.IGrouping%602> .</span><span class="sxs-lookup"><span data-stu-id="b2921-116">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`Group … By … Into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b2921-117">ToLookup</span><span class="sxs-lookup"><span data-stu-id="b2921-117">ToLookup</span></span>|<span data-ttu-id="b2921-118">Bir <xref:System.Linq.Lookup%602> anahtar Seçici işlevine göre öğeleri (bire çok sözlüğüne) ekler.</span><span class="sxs-lookup"><span data-stu-id="b2921-118">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="b2921-119">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="b2921-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="b2921-120">Sorgu Ifadesi söz dizimi örneği</span><span class="sxs-lookup"><span data-stu-id="b2921-120">Query Expression Syntax Example</span></span>  

 <span data-ttu-id="b2921-121">Aşağıdaki kod örneği, `Group By` bir listedeki tamsayıları, hatta veya tek olup olmadığına göre gruplamak için yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b2921-121">The following code example uses the `Group By` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
```vb  
Dim numbers As New System.Collections.Generic.List(Of Integer)(  
     New Integer() {35, 44, 200, 84, 3987, 4, 199, 329, 446, 208})  
  
Dim query = From number In numbers
            Group By Remainder = (number Mod 2) Into Group  
  
Dim sb As New System.Text.StringBuilder()  
For Each group In query  
    sb.AppendLine(If(group.Remainder = 0, vbCrLf & "Even numbers:", vbCrLf & "Odd numbers:"))  
    For Each num In group.Group  
        sb.AppendLine(num)  
    Next  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' Odd numbers:  
' 35  
' 3987  
' 199  
' 329  
  
' Even numbers:  
' 44  
' 200  
' 84  
' 4  
' 446  
' 208  
```  
  
## <a name="see-also"></a><span data-ttu-id="b2921-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2921-122">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="b2921-123">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2921-123">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="b2921-124">Group by yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="b2921-124">Group By Clause</span></span>](../../../language-reference/queries/group-by-clause.md)
- [<span data-ttu-id="b2921-125">Nasıl yapılır: dosyaları uzantıya göre gruplama (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2921-125">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>](how-to-group-files-by-extension-linq.md)
- [<span data-ttu-id="b2921-126">Nasıl yapılır: grupları (LINQ) kullanarak bir dosyayı birçok dosyaya bölme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2921-126">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
