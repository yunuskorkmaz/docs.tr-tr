---
title: Gruplandırma veri (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 8f3a0871-6958-4aef-8f6f-493e189fd57d
ms.openlocfilehash: c658ac5c46baec1bfa976074b78ac86d791b6515
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58842063"
---
# <a name="grouping-data-visual-basic"></a><span data-ttu-id="a0a70-102">Gruplandırma veri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0a70-102">Grouping Data (Visual Basic)</span></span>
<span data-ttu-id="a0a70-103">Gruplandırma, böylece ortak bir özniteliği her gruptaki öğe paylaştırmak gruplar halinde veri yerleştirme işlemi için ifade eder.</span><span class="sxs-lookup"><span data-stu-id="a0a70-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="a0a70-104">Aşağıdaki çizimde, bir karakter dizisi gruplandırma sonuçlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a0a70-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="a0a70-105">Her grup için anahtar karakterdir.</span><span class="sxs-lookup"><span data-stu-id="a0a70-105">The key for each group is the character.</span></span>  
  
 <span data-ttu-id="a0a70-106">![LINQ gruplandırma işlemlerinin](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span><span class="sxs-lookup"><span data-stu-id="a0a70-106">![LINQ Grouping Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span></span>  
  
 <span data-ttu-id="a0a70-107">Veri öğeleri gruplayın standart sorgu işleci yöntemleri aşağıdaki bölümünde listelenir.</span><span class="sxs-lookup"><span data-stu-id="a0a70-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a0a70-108">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a0a70-108">Methods</span></span>  
  
|<span data-ttu-id="a0a70-109">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="a0a70-109">Method Name</span></span>|<span data-ttu-id="a0a70-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0a70-110">Description</span></span>|<span data-ttu-id="a0a70-111">Visual Basic sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a0a70-111">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="a0a70-112">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="a0a70-112">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="a0a70-113">Gruplandırma ölçütü</span><span class="sxs-lookup"><span data-stu-id="a0a70-113">GroupBy</span></span>|<span data-ttu-id="a0a70-114">Sık kullanılan bir özniteliği paylaşan öğeleri gruplandırır.</span><span class="sxs-lookup"><span data-stu-id="a0a70-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="a0a70-115">Her grubu tarafından temsil edilen bir <xref:System.Linq.IGrouping%602> nesne.</span><span class="sxs-lookup"><span data-stu-id="a0a70-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`Group … By … Into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a0a70-116">ToLookup</span><span class="sxs-lookup"><span data-stu-id="a0a70-116">ToLookup</span></span>|<span data-ttu-id="a0a70-117">İçine bir öğe ekler; bir <xref:System.Linq.Lookup%602> (bire çok bir sözlük) tabanlı bir anahtar Seçici işlevdir.</span><span class="sxs-lookup"><span data-stu-id="a0a70-117">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="a0a70-118">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="a0a70-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="a0a70-119">Sorgu ifade sözdizimi örneği</span><span class="sxs-lookup"><span data-stu-id="a0a70-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="a0a70-120">Aşağıdaki kod örneğinde `Group By` yan tümcesi bir liste çift veya tek sayı olup olmadıkları göre grup dizisidir.</span><span class="sxs-lookup"><span data-stu-id="a0a70-120">The following code example uses the `Group By` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a0a70-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0a70-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="a0a70-122">Standart sorgu işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0a70-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="a0a70-123">Group By Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="a0a70-123">Group By Clause</span></span>](../../../../visual-basic/language-reference/queries/group-by-clause.md)
- [<span data-ttu-id="a0a70-124">Nasıl yapılır: Grup dosyalarını uzantısı (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0a70-124">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)
- [<span data-ttu-id="a0a70-125">Nasıl yapılır: Gruplar (LINQ) (Visual Basic) kullanarak bir dosyayı birden çok dosyaya bölme</span><span class="sxs-lookup"><span data-stu-id="a0a70-125">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
