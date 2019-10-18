---
title: Standart sorgu Işleçlerine genel bakış (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 302bd39e-2ec1-495b-94bf-37d370d6f05f
ms.openlocfilehash: 22ae1f89379deff0436177d792382c434348b2d4
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524016"
---
# <a name="standard-query-operators-overview-visual-basic"></a>Standart sorgu Işleçlerine genel bakış (Visual Basic)

*Standart sorgu IŞLEÇLERI* LINQ deseninin bulunduğu yöntemlerdir. Bu yöntemlerin çoğu diziler üzerinde çalışır, burada bir sıra, türü <xref:System.Collections.Generic.IEnumerable%601> arabirimini veya <xref:System.Linq.IQueryable%601> arabirimini uygulayan bir nesnedir. Standart sorgu işleçleri filtreleme, yansıtma, toplama, sıralama ve daha fazlasını içeren sorgu özellikleri sağlar.

@No__t_0 türünde nesneler üzerinde çalışan diğeri, <xref:System.Linq.IQueryable%601> türündeki nesneler üzerinde çalışan iki LINQ standart sorgu işleci kümesi vardır. Her kümeyi oluşturan Yöntemler sırasıyla <xref:System.Linq.Enumerable> ve <xref:System.Linq.Queryable> sınıflarının statik üyeleridir. Bunlar üzerinde çalıştıkları türün *Uzantı yöntemleri* olarak tanımlanmıştır. Bu, statik yöntem sözdizimi veya örnek yöntemi sözdizimi kullanılarak çağrılabilecek anlamına gelir.

Ayrıca, bazı standart sorgu işleci yöntemleri <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Linq.IQueryable%601> temel alan türler üzerinde çalışır. @No__t_0 türü, her ikisi de <xref:System.Collections.IEnumerable> türündeki nesneler üzerinde çalışan iki yöntemi tanımlar. Bu yöntemler, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> ve <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, parametreli olmayan veya genel olmayan bir koleksiyonun LINQ düzeninde sorgulanmasını etkinleştirmenizi sağlar. Bu, nesne türü kesin belirlenmiş bir koleksiyon oluşturarak bunu yapabilirler. @No__t_0 sınıfı, <xref:System.Linq.Queryable> türünde nesneler üzerinde çalışan <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> ve <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29> benzer iki yöntemi tanımlar.

Standart sorgu işleçleri, tek bir değer veya bir dizi değer döndürmediğine bağlı olarak yürütmesinin zamanlamalarına göre farklılık gösterir. Tek bir değer döndüren Yöntemler (örneğin, <xref:System.Linq.Enumerable.Average%2A> ve <xref:System.Linq.Enumerable.Sum%2A>) hemen yürütülür. Bir dizi döndüren yöntemler sorgu yürütmesini erteler ve Numaralandırılabilir bir nesne döndürüyor.

Bellek içi koleksiyonlar üzerinde çalışan yöntemler söz konusu olduğunda, diğer bir deyişle, <xref:System.Collections.Generic.IEnumerable%601> genişleten Yöntemler, döndürülen sıralanabilir nesne yöntemine geçirilen bağımsız değişkenleri yakalar. Bu nesne numaralandırıldıktan sonra, sorgu işlecinin mantığı işe alınır ve sorgu sonuçları döndürülür.

Buna karşılık, <xref:System.Linq.IQueryable%601> genişleyen Yöntemler herhangi bir sorgulama davranışı uygulamaz, ancak gerçekleştirilecek sorguyu temsil eden bir ifade ağacı oluşturur. Sorgu işleme, kaynak <xref:System.Linq.IQueryable%601> nesnesi tarafından işlenir.

Sorgu yöntemlerine yapılan çağrılar tek bir sorgu içinde birbirine zincirlenebilir ve bu da sorguların rastgele karmaşık olmasını sağlar.

Aşağıdaki kod örneği, bir dizi hakkında bilgi edinmek için standart sorgu işleçlerinin nasıl kullanılabileceğini gösterir.

```vb
Dim sentence = "the quick brown fox jumps over the lazy dog"
' Split the string into individual words to create a collection.
Dim words = sentence.Split(" "c)

Dim query = From word In words
            Group word.ToUpper() By word.Length Into gr = Group
            Order By Length _
            Select Length, GroupedWords = gr

Dim output As New System.Text.StringBuilder
For Each obj In query
    output.AppendLine(String.Format("Words of length {0}:", obj.Length))
    For Each word As String In obj.GroupedWords
        output.AppendLine(word)
    Next
Next

'Display the output
MsgBox(output.ToString())

' This code example produces the following output:
'
' Words of length 3:
' THE
' FOX
' THE
' DOG
' Words of length 4:
' OVER
' LAZY
' Words of length 5:
' QUICK
' BROWN
' JUMPS
```

## <a name="query-expression-syntax"></a>Sorgu Ifadesi söz dizimi

Daha sık kullanılan standart sorgu işleçlerinden bazılarının, bir C# *sorgu* *ifadesinin*parçası olarak çağrılmasına olanak tanıyan adanmış ve Visual Basic Language anahtar sözcüğü sözdizimi vardır. Adanmış anahtar sözcüklere ve bunlara karşılık gelen sözdizimleri içeren standart sorgu işleçleri hakkında daha fazla bilgi için bkz. [Standart sorgu işleçleri Için sorgu Ifadesi sözdizimi (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).

## <a name="extending-the-standard-query-operators"></a>Standart sorgu Işleçlerini genişletme

Hedef etki alanınız veya teknolojiniz için uygun olan alana özgü Yöntemler oluşturarak standart sorgu işleçleri kümesini daha da getirebilirsiniz. Standart sorgu işleçlerini, uzaktan değerlendirme, sorgu çevirisi ve iyileştirme gibi ek hizmetler sağlayan kendi uygulamalarınız ile de değiştirebilirsiniz. Bir örnek için bkz. <xref:System.Linq.Enumerable.AsEnumerable%2A>.

## <a name="related-sections"></a>İlgili Bölümler

Aşağıdaki bağlantılar, işlevleri temel alan çeşitli standart sorgu işleçleri hakkında ek bilgiler sağlayan konulara götürür.

- [Verileri Sıralama](../../../../visual-basic/programming-guide/concepts/linq/sorting-data.md)

- [Işlemleri ayarlama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/set-operations.md)

- [Verileri filtreleme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/filtering-data.md)

- [Nicelik belirteci Işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)

- [Projeksiyon Işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)

- [Verileri bölümlendirme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/partitioning-data.md)

- [JOIN Işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md)

- [Verileri gruplandırma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/grouping-data.md)

- [Oluşturma Işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/generation-operations.md)

- [Eşitlik Işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/equality-operations.md)

- [Öğe Işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/element-operations.md)

- [Veri türlerini dönüştürme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md)

- [Birleştirme Işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/concatenation-operations.md)

- [Toplama Işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [LINQ 'e giriş (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)
- [Standart sorgu Işleçleri için sorgu Ifadesi sözdizimi (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)
- [Standart sorgu Işleçleri yürütme yöntemine göre sınıflandırma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)
- [Genişletme Yöntemleri](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
