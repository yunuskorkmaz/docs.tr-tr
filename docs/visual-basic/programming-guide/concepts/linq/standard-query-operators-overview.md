---
title: Standart sorgu işleçlerine genel bakış (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 302bd39e-2ec1-495b-94bf-37d370d6f05f
ms.openlocfilehash: 9bfdf2163be52d9016a800d65006bbc4fbf560a3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841478"
---
# <a name="standard-query-operators-overview-visual-basic"></a>Standart sorgu işleçlerine genel bakış (Visual Basic)
*Standart sorgu işleçleri* LINQ desen form yöntemlerdir. Bu yöntemlerin çoğu bir dizi türü uygulayan bir nesne olduğu dizileri üzerinde çalışması <xref:System.Collections.Generic.IEnumerable%601> arabirimi veya <xref:System.Linq.IQueryable%601> arabirimi. Standart sorgu işleçleri, filtreleme, projeksiyon, toplama, sıralama ve daha fazlası dahil olmak üzere sorgu işlevleri sağlayın.  
  
 LINQ standart sorgu işleçlerinin, türündeki nesneler üzerinde çalışan bir iki kümesi <xref:System.Collections.Generic.IEnumerable%601> ve türündeki nesneler üzerinde çalışan diğer <xref:System.Linq.IQueryable%601>. Her bir kümesini oluşturan yöntemleri statik üyeleridir <xref:System.Linq.Enumerable> ve <xref:System.Linq.Queryable> sınıfları, sırasıyla. Olarak tanımlanan *genişletme yöntemleri* türündeki bunlar üzerinde çalışır. Başka bir deyişle, bunlar statik yöntem sözdizimi veya örnek yöntem sözdizimi kullanılarak çağrılabilir.  
  
 Ayrıca, birçok standart sorgu işleci yöntemleri türlerine göre dışındaki çalışan <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Linq.IQueryable%601>. <xref:System.Linq.Enumerable> Türünü tanımlayan iki yöntem her ikisi de türündeki nesneler üzerinde çalışan <xref:System.Collections.IEnumerable>. Bu yöntemler <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> ve <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let LINQ desen Sorgulanacak forceseek veya genel olmayan, bir koleksiyon etkinleştirin. Bunlar nesneleri türü kesin belirlenmiş koleksiyonu oluşturmanız gerekir. <xref:System.Linq.Queryable> Sınıfı tanımlayan iki benzer yöntem <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> ve <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, türündeki nesneler üzerinde çalışan <xref:System.Linq.Queryable>.  
  
 Standart sorgu işleçleri, bunlar bir tekil değer veya değerlerini bir dizi döndürür bağlı olarak, yürütme, zamanlama içinde farklılık gösterir. Tekil değer döndüren bu yöntemler (örneğin, <xref:System.Linq.Enumerable.Average%2A> ve <xref:System.Linq.Enumerable.Sum%2A>) hemen yürütün. Bir dizi döndüren yöntemler, sorgu yürütme ertele ve bir numaralandırma nesnesi döndürür.  
  
 Bellek içi koleksiyonlarda genişleten bu yöntemler diğer bir deyişle, çalışan yöntemleri söz konusu olduğunda <xref:System.Collections.Generic.IEnumerable%601>, yönteme geçirilen bağımsız değişkenler döndürülen numaralandırılabilir nesne yakalar. Bu nesne numaralandırılana sorgu işleci mantığını işe ve sorgu sonuçları döndürülür.  
  
 Buna karşılık, yöntemleri, genişleten <xref:System.Linq.IQueryable%601> herhangi bir davranış sorgulanırken kullanılmaz, ancak gerçekleştirilmesi için sorguyu temsil eden ifade ağacında oluşturun. Sorgu işleme kaynak tarafından işlendiğini <xref:System.Linq.IQueryable%601> nesne.  
  
 Sorgu yöntemlere yapılan çağrılar, sorguları rasgele karmaşık olmasını sağlayan bir sorguda birbirine zincirlenebilir.  
  
 Aşağıdaki kod örneği, bir dizi hakkında bilgi edinmek için standart sorgu işleçleri'nın nasıl kullanılabileceğini gösterir.  
  
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
  
## <a name="query-expression-syntax"></a>Sorgu ifadesi söz dizimi  
 Bazı daha sık kullanılan standart sorgu işleçlerinin bir parçası olarak çağrılacak tanıyan C# ve Visual Basic dili anahtar sözcüğü sözdizimini adanmış bir *sorgu* *ifade*. Anahtar sözcükleri ve bunların karşılık gelen sözdizimleri adanmış standart sorgu işleçleri hakkında daha fazla bilgi için bkz. [standart sorgu işleçleri (Visual Basic) için sorgu ifade sözdizimi](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).  
  
## <a name="extending-the-standard-query-operators"></a>Standart sorgu işleçlerini genişletme  
 Hedef etki alanına veya teknoloji için uygun olan oluşturma etki alanına özgü yöntemlerle standart sorgu işleçleri kümesini genişletebilirsiniz. Uzak değerlendirme, sorgu çevirisi ve en iyi duruma getirme gibi ek hizmetler sağlayan kendi uygulamaları ile standart sorgu işleçleri de değiştirebilirsiniz. Bkz: <xref:System.Linq.Enumerable.AsEnumerable%2A> örneği.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Aşağıdaki bağlantılar işlevselliğine bağlı olarak çeşitli standart sorgu işleçleri hakkında ek bilgiler sağlayan konulara yönlendirir.  
  
 [Verileri Sıralama](../../../../visual-basic/programming-guide/concepts/linq/sorting-data.md)  
  
 [Ayarlama işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/set-operations.md)  
  
 [Filtre verileri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/filtering-data.md)  
  
 [Niceleyici işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)  
  
 [Projeksiyon işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)  
  
 [Bölümleme veri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/partitioning-data.md)  
  
 [Birleştirme işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md)  
  
 [Gruplandırma veri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/grouping-data.md)  
  
 [Oluşturma işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/generation-operations.md)  
  
 [Eşitlik işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/equality-operations.md)  
  
 [Öğe işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/element-operations.md)  
  
 [Dönüştürme veri türleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md)  
  
 [Birleştirme işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/concatenation-operations.md)  
  
 [Toplama işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [Lınq'ye giriş (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)
- [Standart sorgu işleçleri (Visual Basic) için sorgu ifade sözdizimi](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)
- [Standart sorgu işleçlerinin yöntemine göre sınıflandırılması yürütme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)
- [Genişletme Yöntemleri](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
