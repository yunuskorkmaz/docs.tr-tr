---
title: Projeksiyon işlemleri (Visual Basic)
ms.date: 07/20/2015
ms.assetid: b8d38e6d-21cf-4619-8dbb-94476f4badc7
ms.openlocfilehash: e2af45f9cbbed9eb88095a30e2b77a7730740898
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58820990"
---
# <a name="projection-operations-visual-basic"></a>Projeksiyon işlemleri (Visual Basic)
Projeksiyon bir nesne, genellikle daha sonra kullanılacak olan bu özelliklerini içeren yeni bir biçime dönüştürme işlemini ifade eder. Yansıtma kullanarak her nesneden yerleşik yeni bir türünü oluşturabilirsiniz. Proje bir özelliği ve bir matematiksel işlev üzerinde gerçekleştirin. Ayrıca, değişiklik yapmadan özgün nesneye yansıtabilirsiniz.  
  
 Projeksiyon gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümünde listelenir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|Visual Basic sorgu ifade sözdizimi|Daha fazla bilgi|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Seçim|Bir dönüştürme işlevine dayalı projeler değerleri.|`Select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|  
|SelectMany|Projeleri dizileri değeri bir dönüştürme işlevi üzerinde temel alır ve ardından bunları bir dizi düzleştirir.|Birden çok kullanın `From` yan tümceleri|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Sorgu ifadesi söz dizimi örnekleri  
  
### <a name="select"></a>Seçim  
 Aşağıdaki örnekte `Select` dizelerinin listesini her bir dizenin ilk harfinden projeye yan tümcesi.  
  
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
 Aşağıdaki örnek, birden çok kullanır `From` her bir sözcüğü her bir dizenin bir dize listesi içinde proje için yan tümcesi.  
  
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
 Hem iş `Select()` ve `SelectMany()` bir sonuç değeri (veya değerler) oluşturmak için kaynak değerlerinden olduğu. `Select()` Her kaynak değeri için bir sonuç değerini veriyor. Genel sonuç, bu nedenle kaynak koleksiyonu aynı sayıda öğe içeren bir koleksiyon olur. Buna karşılık, `SelectMany()` her bir kaynak değerden birleştirilmiş alt koleksiyonlar içeren tek bir genel sonucu üretir. Bağımsız değişken olarak geçirilen dönüştürme işlevi `SelectMany()` numaralandırılabilir dizisi için her kaynak değeri değerlerinin döndürmelidir. Bu numaralandırılabilir dizileri tarafından bitiştirilir `SelectMany()` büyük bir dizi oluşturmak için.  
  
 Aşağıdaki iki çizimler eylemleri, bu iki yöntem arasındaki kavramsal farkı göstermektedir. Her durumda, seçici (dönüştürme) işlevinin her kaynak değerinden satmanın dizisi seçer varsayılır.  
  
 Bu çizimde gösterilmektedir nasıl `Select()` kaynak koleksiyonu aynı sayıda öğe içeren bir koleksiyon döndürür.  
  
 ![Seçme eylemini gösteren grafik&#40;&#41;](./media/projection-operations/select-action-graphic.png)  
  
 Bu çizimde gösterilmektedir nasıl `SelectMany()` her ara diziden her değeri içeren bir sonuç değeri diziler Ara dizisine art arda ekler.  
  
 ![SelectMany eylemini gösteren grafik&#40;&#41;.](./media/projection-operations/select-many-action-graphic.png )  
  
### <a name="code-example"></a>Kod Örneği  
 Aşağıdaki örnek davranışını karşılaştırır `Select()` ve `SelectMany()`. Bu kod, kaynak koleksiyonda çiçek adları her iki listesinden ilk iki öğeyi alarak çiçek "demeti" oluşturur. Bu örnekte, "değer tek" Bu dönüştürme işlevi <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> kullanır, kendisi değerler koleksiyonu. Bu ek gerektirir `For Each` döngü, her alt dizideki her bir dizenin numaralandırmak için.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart sorgu işleçlerine genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Select Yan Tümcesi](../../../../visual-basic/language-reference/queries/select-clause.md)
- [Nasıl yapılır: Birleştirmeleri kullanarak veri birleştirme](../../../../visual-basic/programming-guide/language-features/linq/how-to-combine-data-with-linq-by-using-joins.md)
- [Nasıl yapılır: (LINQ) (Visual Basic) birden fazla kaynaktan nesne koleksiyonları doldurma](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)
- [Nasıl yapılır: Bir LINQ Sorgu sonucunu belirli bir tür olarak döndürme](../../../../visual-basic/programming-guide/language-features/linq/how-to-return-a-linq-query-result-as-a-specific-type.md)
- [Nasıl yapılır: Gruplar (LINQ) (Visual Basic) kullanarak bir dosyayı birden çok dosyaya bölme](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
