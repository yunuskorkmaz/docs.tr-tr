---
title: Verileri Gruplandırma
ms.date: 07/20/2015
ms.assetid: 8f3a0871-6958-4aef-8f6f-493e189fd57d
ms.openlocfilehash: 9a4011b77f91ff241d23f7aeca95925a1e170483
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266826"
---
# <a name="grouping-data-visual-basic"></a><span data-ttu-id="b127b-102">Verileri Gruplandırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b127b-102">Grouping Data (Visual Basic)</span></span>
<span data-ttu-id="b127b-103">Gruplandırma, her gruptaki öğelerin ortak bir özniteliği paylaşabilmesi için verileri gruplara ayırma işlemini ifade eder.</span><span class="sxs-lookup"><span data-stu-id="b127b-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="b127b-104">Aşağıdaki resimde, bir karakter dizisini gruplandırmanın sonuçları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b127b-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="b127b-105">Her grup için anahtar karakterdir.</span><span class="sxs-lookup"><span data-stu-id="b127b-105">The key for each group is the character.</span></span>  
  
 ![BIR LINQ Gruplandırma işlemini gösteren diyagram.](./media/grouping-data/linq-group-operation.png)  
  
 <span data-ttu-id="b127b-107">Veri öğelerini gruplayan standart sorgu işleci yöntemleri aşağıdaki bölümde listelenir.</span><span class="sxs-lookup"><span data-stu-id="b127b-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b127b-108">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b127b-108">Methods</span></span>  
  
|<span data-ttu-id="b127b-109">Yöntem Adı</span><span class="sxs-lookup"><span data-stu-id="b127b-109">Method Name</span></span>|<span data-ttu-id="b127b-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b127b-110">Description</span></span>|<span data-ttu-id="b127b-111">Visual Basic Query Expression Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b127b-111">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="b127b-112">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="b127b-112">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="b127b-113">GroupBy</span><span class="sxs-lookup"><span data-stu-id="b127b-113">GroupBy</span></span>|<span data-ttu-id="b127b-114">Ortak bir özniteliği paylaşan öğeleri grupla.</span><span class="sxs-lookup"><span data-stu-id="b127b-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="b127b-115">Her grup bir <xref:System.Linq.IGrouping%602> nesne tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="b127b-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`Group … By … Into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b127b-116">Tolookup</span><span class="sxs-lookup"><span data-stu-id="b127b-116">ToLookup</span></span>|<span data-ttu-id="b127b-117">Öğeleri anahtar seçici <xref:System.Linq.Lookup%602> işlevine dayalı bir (bir-çok sözlük) ekler.</span><span class="sxs-lookup"><span data-stu-id="b127b-117">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="b127b-118">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="b127b-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="b127b-119">Sorgu İfadesözdizimi Örneği</span><span class="sxs-lookup"><span data-stu-id="b127b-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="b127b-120">Aşağıdaki kod örneği, `Group By` tamsayıları bir listede çift veya tek olup olmadıklarına göre gruplandırmak için yan tümceyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="b127b-120">The following code example uses the `Group By` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b127b-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b127b-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="b127b-122">Standart Sorgu Operatörlerine Genel Bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b127b-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="b127b-123">Maddeye Göre Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="b127b-123">Group By Clause</span></span>](../../../../visual-basic/language-reference/queries/group-by-clause.md)
- [<span data-ttu-id="b127b-124">Nasıl yapılır: Uzantıya Göre Dosyaları Grupla (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b127b-124">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)
- [<span data-ttu-id="b127b-125">Nasıl yapılır: Grupları Kullanarak Dosyayı Birçok Dosyaya Bölme (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b127b-125">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
