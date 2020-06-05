---
title: Standart Sorgu İşleçlerine Genel Bakış
ms.date: 07/20/2015
ms.assetid: 302bd39e-2ec1-495b-94bf-37d370d6f05f
ms.openlocfilehash: 7c229a576f6695282473352d6253d2c699c76604
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406787"
---
# <a name="standard-query-operators-overview-visual-basic"></a>Standart sorgu Işleçlerine genel bakış (Visual Basic)

*Standart sorgu IŞLEÇLERI* LINQ deseninin bulunduğu yöntemlerdir. Bu yöntemlerin çoğu diziler üzerinde çalışır, burada bir sıra, türü arabirimini veya arabirimi uygulayan bir nesnedir <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Linq.IQueryable%601> . Standart sorgu işleçleri filtreleme, yansıtma, toplama, sıralama ve daha fazlasını içeren sorgu özellikleri sağlar.

Türü nesneler üzerinde çalışan diğeri türü nesneler üzerinde çalışan iki LINQ standart sorgu işleci kümesi vardır <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Linq.IQueryable%601> . Her kümeyi oluşturan Yöntemler <xref:System.Linq.Enumerable> sırasıyla ve sınıflarının statik üyeleridir <xref:System.Linq.Queryable> . Bunlar üzerinde çalıştıkları türün *Uzantı yöntemleri* olarak tanımlanmıştır. Bu, statik yöntem sözdizimi veya örnek yöntemi sözdizimi kullanılarak çağrılabilecek anlamına gelir.

Ayrıca, birkaç standart sorgu işleci yöntemi, veya tabanlı olanlar dışındaki türler üzerinde çalışır <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Linq.IQueryable%601> . <xref:System.Linq.Enumerable>Türü, her ikisi de türündeki nesneler üzerinde çalışan iki yöntemi tanımlar <xref:System.Collections.IEnumerable> . Bu yöntemler <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> ve <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29> , parametreli olmayan veya genel olmayan BIR koleksiyonun LINQ düzeninde sorgulanmasını etkinleştirmenizi sağlar. Bunu, türü kesin belirlenmiş bir nesne koleksiyonu oluşturarak yapabilirler. <xref:System.Linq.Queryable>Sınıfı, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> ve <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29> türündeki nesneler üzerinde çalışan iki benzer yöntemi tanımlar <xref:System.Linq.Queryable> .

Standart sorgu işleçleri, tek bir değer veya bir dizi değer döndürmediğine bağlı olarak yürütmesinin zamanlamalarına göre farklılık gösterir. Tek bir değer döndüren Yöntemler (örneğin, <xref:System.Linq.Enumerable.Average%2A> ve <xref:System.Linq.Enumerable.Sum%2A> ) hemen yürütülür. Bir dizi döndüren yöntemler sorgu yürütmesini erteler ve Numaralandırılabilir bir nesne döndürüyor.

Bellek içi koleksiyonlar üzerinde çalışan yöntemler söz konusu olduğunda, diğer bir deyişle, <xref:System.Collections.Generic.IEnumerable%601> döndürülen sıralanabilir nesne, metoduna geçirilen bağımsız değişkenleri yakalar. Bu nesne numaralandırıldıktan sonra, sorgu işlecinin mantığı işe alınır ve sorgu sonuçları döndürülür.

Buna karşılık, genişleyen Yöntemler <xref:System.Linq.IQueryable%601> herhangi bir sorgulama davranışı uygulamaz, ancak gerçekleştirilecek sorguyu temsil eden bir ifade ağacı oluşturur. Sorgu işleme, kaynak nesne tarafından işlenir <xref:System.Linq.IQueryable%601> .

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

Daha sık kullanılan standart sorgu işleçlerinden bazılarının, bir *sorgu* *ifadesinin*parçası olarak çağrılmasına olanak sağlayan adanmış C# ve Visual Basic Language anahtar sözcüğü vardır. Adanmış anahtar sözcüklere ve bunlara karşılık gelen sözdizimleri içeren standart sorgu işleçleri hakkında daha fazla bilgi için bkz. [Standart sorgu işleçleri Için sorgu Ifadesi sözdizimi (Visual Basic)](query-expression-syntax-for-standard-query-operators.md).

## <a name="extending-the-standard-query-operators"></a>Standart sorgu Işleçlerini genişletme

Hedef etki alanınız veya teknolojiniz için uygun olan alana özgü Yöntemler oluşturarak standart sorgu işleçleri kümesini daha da getirebilirsiniz. Standart sorgu işleçlerini, uzaktan değerlendirme, sorgu çevirisi ve iyileştirme gibi ek hizmetler sağlayan kendi uygulamalarınız ile de değiştirebilirsiniz. <xref:System.Linq.Enumerable.AsEnumerable%2A>Bir örnek için bkz..

## <a name="related-sections"></a>İlgili Bölümler

Aşağıdaki bağlantılar, işlevleri temel alan çeşitli standart sorgu işleçleri hakkında ek bilgiler sağlayan konulara götürür.

- [Verileri Sıralama](sorting-data.md)

- [Işlemleri ayarlama (Visual Basic)](set-operations.md)

- [Verileri filtreleme (Visual Basic)](filtering-data.md)

- [Nicelik belirteci Işlemleri (Visual Basic)](quantifier-operations.md)

- [Projeksiyon Işlemleri (Visual Basic)](projection-operations.md)

- [Verileri bölümlendirme (Visual Basic)](partitioning-data.md)

- [JOIN Işlemleri (Visual Basic)](join-operations.md)

- [Verileri gruplandırma (Visual Basic)](grouping-data.md)

- [Oluşturma Işlemleri (Visual Basic)](generation-operations.md)

- [Eşitlik Işlemleri (Visual Basic)](equality-operations.md)

- [Öğe Işlemleri (Visual Basic)](element-operations.md)

- [Veri türlerini dönüştürme (Visual Basic)](converting-data-types.md)

- [Birleştirme Işlemleri (Visual Basic)](concatenation-operations.md)

- [Toplama Işlemleri (Visual Basic)](aggregation-operations.md)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [LINQ 'e giriş (Visual Basic)](introduction-to-linq.md)
- [Standart sorgu Işleçleri için sorgu Ifadesi sözdizimi (Visual Basic)](query-expression-syntax-for-standard-query-operators.md)
- [Standart sorgu Işleçleri yürütme yöntemine göre sınıflandırma (Visual Basic)](classification-of-standard-query-operators-by-manner-of-execution.md)
- [Uzantı yöntemleri](../../language-features/procedures/extension-methods.md)
