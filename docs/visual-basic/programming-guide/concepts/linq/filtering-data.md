---
title: Filtre veri (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7749519a-7edc-49fe-aef9-6a353864af6c
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 31e3a4729a98e1f4b588cd415a15fff270587234
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="filtering-data-visual-basic"></a>Filtre veri (Visual Basic)
Filtreleme, yalnızca belirtilen koşulu karşılıyor öğeleri içeren sonuç kısıtlama işlemi ifade eder. Olarak da bilinen, seçim değildir.  
  
 Aşağıdaki çizimde bir karakter dizisi filtreleme sonuçlarını gösterir. Filtreleme işlemi için koşulu karakter 'A' olması gerektiğini belirtir.  
  
 ![İşlemi filtreleme LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")  
  
 Seçim gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmektedir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|Visual Basic sorgu ifade sözdizimi|Daha Fazla Bilgi|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|OfType|Değerleri, bir belirtilen türe yeteneğini bağlı olarak seçer.|Yok.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|Where|Bir koşul işlevine dayalı değerleri seçer.|`Where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Sorgu ifade sözdizimi örneği  
 Aşağıdaki örnek kullanır `Where` dizisinden belirli bir uzunluğa sahip Bu dizelerin filtre uygulamak için.  
  
```vb  
Dim words() As String = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim query = From word In words   
            Where word.Length = 3   
            Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In query  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' the  
' fox  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Linq>  
 [Standart sorgu işleçlerine genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Burada yan tümcesi](../../../../visual-basic/language-reference/queries/where-clause.md)  
 [Nasıl yapılır: sorgu sonuçlarını filtreleme](../../../../visual-basic/programming-guide/language-features/linq/how-to-filter-query-results-by-using-linq.md)  
 [Nasıl yapılır: bir derlemenin meta verilerini yansıma (LINQ) (Visual Basic) ile sorgulama](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
 [Nasıl yapılır: belirli bir öznitelik veya ad (Visual Basic) sahip dosyaları sorgulama](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 [Nasıl yapılır: sıralama veya filtre metni verilerle herhangi bir sözcük veya alana (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
