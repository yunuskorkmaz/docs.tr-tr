---
title: "Projeksiyon işlemleri (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8d38e6d-21cf-4619-8dbb-94476f4badc7
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4927a27795881c34b689a2054ee8697575b53026
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="projection-operations-visual-basic"></a>Projeksiyon işlemleri (Visual Basic)
Projeksiyon genellikle daha sonra kullanılacak bu özelliklerini içeren yeni bir forma bir nesne dönüştürme işlemi ifade eder. Projeksiyon kullanarak her nesneden oluşturulmuş yeni bir türü oluşturabilirsiniz. Bir özellik proje ve matematiksel işlevi gerçekleştirebilir. Özgün nesne değiştirmeden da yansıtabilirsiniz.  
  
 Projeksiyon gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmektedir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|Visual Basic sorgu ifade sözdizimi|Daha Fazla Bilgi|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Seçim|Bir dönüştürme işlevine dayalı projeleri değerleri.|`Select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|  
|SelectMany|Dönüşüm işlevi üzerinde temel alır ve bunları bir sıralı düzleştirir değerler projeleri sıralar.|Birden çok kullanmak `From` yan tümceleri|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Sorgu ifade sözdizimi örnekleri  
  
### <a name="select"></a>Seçim  
 Aşağıdaki örnek kullanır `Select` dizelerinin listesini her dizesinde ilk harfinden projeye yan tümcesi.  
  
```vb  
Dim words = New List(Of String) From {"an", "apple", "a", "day"}  
  
Dim query = From word In words   
            Select word.Substring(0, 1)  
  
Dim sb As New System.Text.StringBuilder()  
For Each letter As String In query  
    sb.AppendLine(letter)  
Next  
  
' Display the output.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' a  
' a  
' a  
' d  
```  
  
### <a name="selectmany"></a>SelectMany  
 Aşağıdaki örnek, birden çok kullanır `From` dizelerinin listesini her bir dizeden her sözcüğün projeye yan tümceleri.  
  
```vb  
Dim phrases = New List(Of String) From {"an apple a day", "the quick brown fox"}  
  
Dim query = From phrase In phrases   
            From word In phrase.Split(" "c)   
            Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In query  
    sb.AppendLine(str)  
Next  
  
' Display the output.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' an  
' apple  
' a  
' day  
' the  
' quick  
' brown  
' fox  
```  
  
## <a name="select-versus-selectmany"></a>SelectMany karşı seçin  
 Hem iş `Select()` ve `SelectMany()` sonuç değeri (veya değerler) oluşturmak için kaynak değerlerinden olduğu. `Select()`Her kaynak değeri için bir sonuç değeri oluşturur. Genel sonuç bu nedenle kaynak koleksiyonu aynı sayıda öğe içeren bir koleksiyondur. Buna karşılık, `SelectMany()` her kaynak değerinden birleştirilmiş alt koleksiyonları içeren tek bir genel sonuç üretir. Bağımsız değişken olarak geçirilen dönüştürme işlevi `SelectMany()` değerleri her bir kaynak değer için numaralandırılabilir bir dizi döndürmesi gerekir. Bu numaralandırılabilir sıralarının tarafından birleşir `SelectMany()` bir büyük sıralı oluşturmak için.  
  
 Aşağıdaki iki çizimler bu iki yöntem Eylemler kavramsal birbirinden göstermektedir. Her durumda, seçici (dönüştürme) işlevinin her kaynak değerinden çiçekler dizisi seçer varsayalım.  
  
 Bu çizimde gösterilmektedir nasıl `Select()` kaynak koleksiyonu aynı sayıda öğe içeren bir koleksiyon döndürür.  
  
 ![Kavramsal çizim eylemin seçin &#40; &#41; ] (../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")  
  
 Bu çizimde gösterilmektedir nasıl `SelectMany()` diziler ara sıra her ara dizisinden her değeri içeren bir sonuç değeri içine art arda ekler.  
  
 ![SelectMany &#40; &#41;eylemini gösteren grafik;. ] (../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "SelectMany")  
  
### <a name="code-example"></a>Kod Örneği  
 Aşağıdaki örnek davranışını karşılaştırır `Select()` ve `SelectMany()`. Kaynak koleksiyondaki her çiçek adları listesinden ilk iki öğenin gerçekleştirerek çiçek "demeti" kod oluşturur. Bu örnekte, "tek değer", dönüştürme işlevi <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> kullanımdır kendisini değerler koleksiyonu. Bu ek gerektirir `For Each` her alt dizisindeki her dize numaralandırmak için döngü.  
  
```vb  
Class Bouquet  
    Public Flowers As List(Of String)  
End Class  
  
Sub SelectVsSelectMany()  
    Dim bouquets = New List(Of Bouquet) From {   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"sunflower", "daisy", "daffodil", "larkspur"})},   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"tulip", "rose", "orchid"})},   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"gladiolis", "lily", "snapdragon", "aster", "protea"})},   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"larkspur", "lilac", "iris", "dahlia"})}}  
  
    Dim output As New System.Text.StringBuilder  
  
    ' Select()  
    Dim query1 = bouquets.Select(Function(b) b.Flowers)  
  
    output.AppendLine("Using Select():")  
    For Each flowerList In query1  
        For Each str As String In flowerList  
            output.AppendLine(str)  
        Next  
    Next  
  
    ' SelectMany()  
    Dim query2 = bouquets.SelectMany(Function(b) b.Flowers)  
  
    output.AppendLine(vbCrLf & "Using SelectMany():")  
    For Each str As String In query2  
        output.AppendLine(str)  
    Next  
  
    ' Display the output  
    MsgBox(output.ToString())  
  
    ' This code produces the following output:  
    '  
    ' Using Select():  
    ' sunflower  
    ' daisy  
    ' daffodil  
    ' larkspur  
    ' tulip  
    ' rose  
    ' orchid  
    ' gladiolis  
    ' lily  
    ' snapdragon  
    ' aster  
    ' protea  
    ' larkspur  
    ' lilac  
    ' iris  
    ' dahlia  
  
    ' Using SelectMany()  
    ' sunflower  
    ' daisy  
    ' daffodil  
    ' larkspur  
    ' tulip  
    ' rose  
    ' orchid  
    ' gladiolis  
    ' lily  
    ' snapdragon  
    ' aster  
    ' protea  
    ' larkspur  
    ' lilac  
    ' iris  
    ' dahlia  
  
End Sub  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Linq>  
 [Standart sorgu işleçlerine genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Select tümcesi](../../../../visual-basic/language-reference/queries/select-clause.md)  
 [Nasıl yapılır: birleştirmeleri kullanarak veri birleştirme](../../../../visual-basic/programming-guide/language-features/linq/how-to-combine-data-with-linq-by-using-joins.md)  
 [Nasıl yapılır: (LINQ) (Visual Basic) birden fazla kaynaktan nesne koleksiyonları doldurma](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)  
 [Nasıl yapılır: bir LINQ Sorgu sonucunu belirli bir tür olarak döndürme](../../../../visual-basic/programming-guide/language-features/linq/how-to-return-a-linq-query-result-as-a-specific-type.md)  
 [Nasıl yapılır: bir dosya grupları (LINQ) (Visual Basic) kullanarak birden çok dosyaya bölme](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
