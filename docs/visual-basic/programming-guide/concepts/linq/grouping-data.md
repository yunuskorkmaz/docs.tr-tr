---
title: Verileri Gruplandırma
ms.date: 07/20/2015
ms.assetid: 8f3a0871-6958-4aef-8f6f-493e189fd57d
ms.openlocfilehash: 8996eee748489c596bc5adc32f53b6b39dbfc6ac
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398389"
---
# <a name="grouping-data-visual-basic"></a><span data-ttu-id="31b1f-102">Verileri gruplandırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31b1f-102">Grouping Data (Visual Basic)</span></span>
<span data-ttu-id="31b1f-103">Gruplandırma, her bir gruptaki öğelerin ortak bir özniteliği paylaşması için verileri gruplara yerleştirme işlemini ifade eder.</span><span class="sxs-lookup"><span data-stu-id="31b1f-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="31b1f-104">Aşağıdaki çizimde, bir karakter dizisini gruplandırmanın sonuçları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="31b1f-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="31b1f-105">Her grup için anahtar karakterdir.</span><span class="sxs-lookup"><span data-stu-id="31b1f-105">The key for each group is the character.</span></span>  
  
 ![LINQ gruplama işlemini gösteren diyagram.](./media/grouping-data/linq-group-operation.png)  
  
 <span data-ttu-id="31b1f-107">Veri öğelerini gruplamak için kullanılan standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="31b1f-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="31b1f-108">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="31b1f-108">Methods</span></span>  
  
|<span data-ttu-id="31b1f-109">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="31b1f-109">Method Name</span></span>|<span data-ttu-id="31b1f-110">Description</span><span class="sxs-lookup"><span data-stu-id="31b1f-110">Description</span></span>|<span data-ttu-id="31b1f-111">Sorgu Ifadesi söz dizimini Visual Basic</span><span class="sxs-lookup"><span data-stu-id="31b1f-111">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="31b1f-112">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="31b1f-112">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="31b1f-113">GroupBy</span><span class="sxs-lookup"><span data-stu-id="31b1f-113">GroupBy</span></span>|<span data-ttu-id="31b1f-114">Ortak bir özniteliği paylaşan öğeleri gruplandırır.</span><span class="sxs-lookup"><span data-stu-id="31b1f-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="31b1f-115">Her grup bir nesne tarafından temsil edilir <xref:System.Linq.IGrouping%602> .</span><span class="sxs-lookup"><span data-stu-id="31b1f-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`Group … By … Into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="31b1f-116">ToLookup</span><span class="sxs-lookup"><span data-stu-id="31b1f-116">ToLookup</span></span>|<span data-ttu-id="31b1f-117">Bir <xref:System.Linq.Lookup%602> anahtar Seçici işlevine göre öğeleri (bire çok sözlüğüne) ekler.</span><span class="sxs-lookup"><span data-stu-id="31b1f-117">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="31b1f-118">Geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="31b1f-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="31b1f-119">Sorgu Ifadesi söz dizimi örneği</span><span class="sxs-lookup"><span data-stu-id="31b1f-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="31b1f-120">Aşağıdaki kod örneği, `Group By` bir listedeki tamsayıları, hatta veya tek olup olmadığına göre gruplamak için yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="31b1f-120">The following code example uses the `Group By` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="31b1f-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31b1f-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="31b1f-122">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31b1f-122">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="31b1f-123">Group By Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="31b1f-123">Group By Clause</span></span>](../../../language-reference/queries/group-by-clause.md)
- [<span data-ttu-id="31b1f-124">Nasıl yapılır: dosyaları uzantıya göre gruplama (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31b1f-124">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>](how-to-group-files-by-extension-linq.md)
- [<span data-ttu-id="31b1f-125">Nasıl yapılır: grupları (LINQ) kullanarak bir dosyayı birçok dosyaya bölme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31b1f-125">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
