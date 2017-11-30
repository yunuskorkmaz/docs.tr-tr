---
title: "Gruplandırma veri (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f3a0871-6958-4aef-8f6f-493e189fd57d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5f2e5c4c4713f1056f1eb2243f27e5acf0494542
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="grouping-data-visual-basic"></a>Gruplandırma veri (Visual Basic)
Gruplandırma, böylece her grup içindeki öğeleri ortak bir özniteliği paylaşan gruplar halinde veri koyma işlemi için ifade eder.  
  
 Aşağıdaki çizimde bir karakter dizisi gruplandırma sonuçlarını gösterir. Her grup için karakterin anahtarıdır.  
  
 ![LINQ gruplandırma işlemleri](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")  
  
 Veri öğeleri Grup standart sorgu işleci yöntemler aşağıdaki bölümde listelenmektedir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|Visual Basic sorgu ifade sözdizimi|Daha Fazla Bilgi|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|GroupBy|Ortak bir özniteliği paylaşan grupları öğeleri. Her grubu tarafından temsil edilen bir <xref:System.Linq.IGrouping%602> nesnesi.|`Group … By … Into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|ToLookup|Elemanlara ekler bir <xref:System.Linq.Lookup%602> (bir-çok sözlük) dayalı bir anahtar Seçici işlevdir.|Yok.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Sorgu ifade sözdizimi örneği  
 Aşağıdaki kod örneğinde `Group By` bile veya alışılmadık olup olmadıkları göre listesini Grup tamsayılar yan tümcesini.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Linq>  
 [Standart sorgu işleçlerine genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Group By tümcesi](../../../../visual-basic/language-reference/queries/group-by-clause.md)  
 [Nasıl yapılır: dosyaları uzantıya (LINQ) (Visual Basic) göre gruplama](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 [Nasıl yapılır: bir dosya grupları (LINQ) (Visual Basic) kullanarak birden çok dosyaya bölme](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
