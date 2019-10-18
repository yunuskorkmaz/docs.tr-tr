---
title: Projeksiyon Işlemleri (Visual Basic)
ms.date: 07/20/2015
ms.assetid: b8d38e6d-21cf-4619-8dbb-94476f4badc7
ms.openlocfilehash: 9db8284d59baa764a5509b1acef0c4d315fb28a7
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524095"
---
# <a name="projection-operations-visual-basic"></a>Projeksiyon Işlemleri (Visual Basic)

Projeksiyon, bir nesneyi genellikle daha sonra kullanılacak olan özelliklerden oluşan yeni bir forma dönüştürme işlemine başvurur. Projeksiyonu kullanarak her nesneden oluşturulan yeni bir tür oluşturabilirsiniz. Bir özelliği proje üzerinde bir matematik işlevi de gerçekleştirebilirsiniz. Özgün nesneyi değiştirmeden de proje oluşturabilirsiniz.

Yansıtmayı gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.

## <a name="methods"></a>Yöntemler

|Yöntem adı|Açıklama|Sorgu Ifadesi söz dizimini Visual Basic|Daha fazla bilgi|
|-----------------|-----------------|------------------------------------------|----------------------|
|Seçim|Bir dönüşüm işlevine dayalı projeler değerleri.|`Select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|
|SelectMany|Bir dönüşüm işlevine dayalı ve sonra bunları tek bir sırayla düzleştirir.|Çoklu `From` yan tümceleri kullanma|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-examples"></a>Sorgu Ifadesi söz dizimi örnekleri

### <a name="select"></a>Seçim

Aşağıdaki örnek, bir dize listesindeki her bir dizeden ilk harfi proje için `Select` yan tümcesini kullanır.

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

Aşağıdaki örnek, dizeler listesindeki her bir dizeden her bir sözcüğü projeye eklemek için birden çok `From` yan tümcesini kullanır.

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

## <a name="select-versus-selectmany"></a>Select SelectMany

@No__t_0 ve `SelectMany()` her ikisi de, kaynak değerlerinden bir sonuç değeri (veya değerler) üretmeniz. `Select()` her kaynak değer için bir sonuç değeri üretir. Bu nedenle, genel sonuç, kaynak koleksiyonuyla aynı sayıda öğeye sahip olan bir koleksiyondur. Buna karşılık, `SelectMany()` her kaynak değerden birleştirilmiş alt koleksiyonlar içeren tek bir genel sonuç üretir. @No__t_0 bir bağımsız değişken olarak geçirilen dönüştürme işlevi, her kaynak değer için sıralanabilir bir değer dizisi döndürmelidir. Bu sıralanabilir sıralar daha sonra `SelectMany()` bir büyük sıra oluşturmak için birleştirilir.

Aşağıdaki iki çizimde, bu iki yöntemin eylemleri arasındaki kavramsal fark gösterilmektedir. Her durumda, seçici (dönüşüm) işlevinin her kaynak değerden çiçekler dizisini seçtiği varsayılır.

Bu çizimde `Select()`, kaynak koleksiyon ile aynı sayıda öğeye sahip bir koleksiyonun nasıl döndürdüğü gösterilmektedir.

![Seçme eylemini gösteren grafik&#40;&#41;](./media/projection-operations/select-action-graphic.png)

Bu çizimde, `SelectMany()` her bir ara dizideki her bir değeri içeren bir son sonuç değerindeki dizi ara diziyi nasıl birleştiren gösterilmektedir.

![SelectMany&#40;&#41;eylemini gösteren grafik.](./media/projection-operations/select-many-action-graphic.png )

### <a name="code-example"></a>Kod Örneği

Aşağıdaki örnek `Select()` ve `SelectMany()` davranışını karşılaştırır. Kod, kaynak koleksiyondaki her bir çiçek adı listesinden ilk iki öğeyi alarak çiçekler ' ın bir "Buquet" oluşturur. Bu örnekte, dönüşüm işlevinin <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> kullandığı "tek değer" bir değer koleksiyonudur. Bu, her bir alt dizideki her bir dizeyi numaralandırmak için ek `For Each` döngüsünü gerektirir.

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
- [Standart sorgu Işleçlerine genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Select Yan Tümcesi](../../../../visual-basic/language-reference/queries/select-clause.md)
- [Nasıl yapılır: birleşimlerle verileri birleştirme](../../../../visual-basic/programming-guide/language-features/linq/how-to-combine-data-with-linq-by-using-joins.md)
- [Nasıl yapılır: birden çok kaynaktan nesne koleksiyonları doldurma (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)
- [Nasıl yapılır: Bir LINQ Sorgu Sonucunu Belirli Bir Tür Olarak Döndürme](../../../../visual-basic/programming-guide/language-features/linq/how-to-return-a-linq-query-result-as-a-specific-type.md)
- [Nasıl yapılır: grupları (LINQ) kullanarak bir dosyayı birçok dosyaya bölme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
