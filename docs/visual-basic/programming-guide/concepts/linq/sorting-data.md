---
title: "Sıralama veri (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f81065c-0c89-4bf3-a6d8-442273f8810e
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8f17c6ecad721dd3a48a01c09693b0a1cf723a5b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="sorting-data-visual-basic"></a>Sıralama veri (Visual Basic)
Sıralama işlemi bir veya daha fazla özniteliklerini temel alarak bir sıradaki sıralar. İlk sıralama ölçütü birincil sıralama öğeleri gerçekleştirir. İkinci bir sıralama ölçütü belirterek, her birincil sıralama grup içindeki öğeleri sıralama yapabilirsiniz.  
  
 Aşağıdaki çizimde bir dizi karakterden oluşan bir alfabetik sıralama işlemi sonuçlarını gösterir.  
  
 ![Sıralama işlemi LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")  
  
 Verileri sıralama standart sorgu işleci yöntemler aşağıdaki bölümde listelenmektedir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|Visual Basic sorgu ifade sözdizimi|Daha Fazla Bilgi|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|OrderBy|Artan düzende değerlerini sıralar.|`Order By`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|OrderByDescending|Azalan düzende değerlerini sıralar.|`Order By … Descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|ThenBy|İkincil bir sıralama artan düzende gerçekleştirir.|`Order By …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|ThenByDescending|İkincil bir sıralamayı azalan sırada gerçekleştirir.|`Order By …, … Descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|Ters Çevir|Bir koleksiyondaki öğelerin sırasını tersine çevirir.|Yok.|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Sorgu ifade sözdizimi örnekleri  
  
### <a name="primary-sort-examples"></a>Birincil sıralama örnekleri  
  
#### <a name="primary-ascending-sort"></a>Birincil artan sıralama  
 Aşağıdaki örnekte nasıl kullanılacağı ortaya `Order By` dize uzunluğu, artan bir dizi dizelerde sıralamak için bir LINQ sorgu yan tümcesinde.  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Length   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' the  
' fox  
' quick  
' brown  
' jumps  
```  
  
#### <a name="primary-descending-sort"></a>Birincil azalan sıralama  
 Sonraki örnek nasıl kullanılacağı ortaya `Order By Descending` azalan sırada kendi ilk harfi dizeleri sıralamak için bir LINQ sorgu yan tümcesinde.  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Substring(0, 1) Descending   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' the  
' quick  
' jumps  
' fox  
' brown  
```  
  
### <a name="secondary-sort-examples"></a>İkincil sıralama örnekleri  
  
#### <a name="secondary-ascending-sort"></a>İkincil artan sıralama  
 Aşağıdaki örnekte nasıl kullanılacağı ortaya `Order By` dizeleri birincil ve ikincil bir tür bir dizide gerçekleştirmek için bir LINQ sorgu yan tümcesinde. Dizeleri öncelikle uzunluğu ve ürüne ilk harfini dizesinin hem artan düzende sıralanır.  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Length, word.Substring(0, 1)   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' fox  
' the  
' brown  
' jumps  
' quick  
```  
  
#### <a name="secondary-descending-sort"></a>İkincil azalan sıralama  
 Sonraki örnek nasıl kullanılacağı ortaya `Order By Descending` birincil bir sıralama düzeni ve azalan bir ikincil sıralama artan düzende gerçekleştirmek için bir LINQ sorgu yan tümcesinde. Dizeleri öncelikle uzunluğu ve ürüne dizenin ilk harfini sıralanır.  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Length, word.Substring(0, 1) Descending   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' fox  
' the  
' quick  
' jumps  
' brown  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Linq>  
 [Standart sorgu işleçlerine genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Order By tümcesi](../../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [Nasıl yapılır: sorgu sonuçlarını sıralama](../../../../visual-basic/programming-guide/language-features/linq/how-to-sort-query-results-by-using-linq.md)  
 [Nasıl yapılır: sıralama veya filtre metni verilerle herhangi bir sözcük veya alana (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
