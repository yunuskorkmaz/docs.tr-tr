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
# <a name="grouping-data-visual-basic"></a>Verileri Gruplandırma (Visual Basic)
Gruplandırma, her gruptaki öğelerin ortak bir özniteliği paylaşabilmesi için verileri gruplara ayırma işlemini ifade eder.  
  
 Aşağıdaki resimde, bir karakter dizisini gruplandırmanın sonuçları gösterilmektedir. Her grup için anahtar karakterdir.  
  
 ![BIR LINQ Gruplandırma işlemini gösteren diyagram.](./media/grouping-data/linq-group-operation.png)  
  
 Veri öğelerini gruplayan standart sorgu işleci yöntemleri aşağıdaki bölümde listelenir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem Adı|Açıklama|Visual Basic Query Expression Sözdizimi|Daha Fazla Bilgi|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|GroupBy|Ortak bir özniteliği paylaşan öğeleri grupla. Her grup bir <xref:System.Linq.IGrouping%602> nesne tarafından temsil edilir.|`Group … By … Into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|Tolookup|Öğeleri anahtar seçici <xref:System.Linq.Lookup%602> işlevine dayalı bir (bir-çok sözlük) ekler.|Geçerli değildir.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Sorgu İfadesözdizimi Örneği  
 Aşağıdaki kod örneği, `Group By` tamsayıları bir listede çift veya tek olup olmadıklarına göre gruplandırmak için yan tümceyi kullanır.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart Sorgu Operatörlerine Genel Bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Maddeye Göre Gruplandırma](../../../../visual-basic/language-reference/queries/group-by-clause.md)
- [Nasıl yapılır: Uzantıya Göre Dosyaları Grupla (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)
- [Nasıl yapılır: Grupları Kullanarak Dosyayı Birçok Dosyaya Bölme (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
