---
title: Gruplandırma veri (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 8f3a0871-6958-4aef-8f6f-493e189fd57d
ms.openlocfilehash: e2732c91dfff65ebb86ef45296ba369c3073a8f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644205"
---
# <a name="grouping-data-visual-basic"></a><span data-ttu-id="087d0-102">Gruplandırma veri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="087d0-102">Grouping Data (Visual Basic)</span></span>
<span data-ttu-id="087d0-103">Gruplandırma, böylece her grup içindeki öğeleri ortak bir özniteliği paylaşan gruplar halinde veri koyma işlemi için ifade eder.</span><span class="sxs-lookup"><span data-stu-id="087d0-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="087d0-104">Aşağıdaki çizimde bir karakter dizisi gruplandırma sonuçlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="087d0-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="087d0-105">Her grup için karakterin anahtarıdır.</span><span class="sxs-lookup"><span data-stu-id="087d0-105">The key for each group is the character.</span></span>  
  
 <span data-ttu-id="087d0-106">![LINQ gruplandırma işlemleri](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span><span class="sxs-lookup"><span data-stu-id="087d0-106">![LINQ Grouping Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span></span>  
  
 <span data-ttu-id="087d0-107">Veri öğeleri Grup standart sorgu işleci yöntemler aşağıdaki bölümde listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="087d0-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="087d0-108">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="087d0-108">Methods</span></span>  
  
|<span data-ttu-id="087d0-109">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="087d0-109">Method Name</span></span>|<span data-ttu-id="087d0-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="087d0-110">Description</span></span>|<span data-ttu-id="087d0-111">Visual Basic sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="087d0-111">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="087d0-112">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="087d0-112">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="087d0-113">GroupBy</span><span class="sxs-lookup"><span data-stu-id="087d0-113">GroupBy</span></span>|<span data-ttu-id="087d0-114">Ortak bir özniteliği paylaşan grupları öğeleri.</span><span class="sxs-lookup"><span data-stu-id="087d0-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="087d0-115">Her grubu tarafından temsil edilen bir <xref:System.Linq.IGrouping%602> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="087d0-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`Group … By … Into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="087d0-116">ToLookup</span><span class="sxs-lookup"><span data-stu-id="087d0-116">ToLookup</span></span>|<span data-ttu-id="087d0-117">Elemanlara ekler bir <xref:System.Linq.Lookup%602> (bir-çok sözlük) dayalı bir anahtar Seçici işlevdir.</span><span class="sxs-lookup"><span data-stu-id="087d0-117">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="087d0-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="087d0-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="087d0-119">Sorgu ifade sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="087d0-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="087d0-120">Aşağıdaki kod örneğinde `Group By` bile veya alışılmadık olup olmadıkları göre listesini Grup tamsayılar yan tümcesini.</span><span class="sxs-lookup"><span data-stu-id="087d0-120">The following code example uses the `Group By` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="087d0-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="087d0-121">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="087d0-122">Standart sorgu işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="087d0-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="087d0-123">Group By Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="087d0-123">Group By Clause</span></span>](../../../../visual-basic/language-reference/queries/group-by-clause.md)  
 [<span data-ttu-id="087d0-124">Nasıl yapılır: dosyaları uzantıya (LINQ) (Visual Basic) göre gruplama</span><span class="sxs-lookup"><span data-stu-id="087d0-124">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 [<span data-ttu-id="087d0-125">Nasıl yapılır: bir dosya grupları (LINQ) (Visual Basic) kullanarak birden çok dosyaya bölme</span><span class="sxs-lookup"><span data-stu-id="087d0-125">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
