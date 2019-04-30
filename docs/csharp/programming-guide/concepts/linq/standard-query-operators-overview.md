---
title: Standart sorgu işleçlerine genel bakış (C#)
ms.date: 07/20/2015
ms.assetid: 812fa119-5f65-4139-b4fa-55dccd8dc3ac
ms.openlocfilehash: 7ce3a13c98bf08eae79906f1806427741568155e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61680512"
---
# <a name="standard-query-operators-overview-c"></a>Standart sorgu işleçlerine genel bakış (C#)
*Standart sorgu işleçleri* LINQ desen form yöntemlerdir. Bu yöntemlerin çoğu bir dizi türü uygulayan bir nesne olduğu dizileri üzerinde çalışması <xref:System.Collections.Generic.IEnumerable%601> arabirimi veya <xref:System.Linq.IQueryable%601> arabirimi. Standart sorgu işleçleri, filtreleme, projeksiyon, toplama, sıralama ve daha fazlası dahil olmak üzere sorgu işlevleri sağlayın.  
  
 LINQ standart sorgu işleçlerinin, türündeki nesneler üzerinde çalışan bir iki kümesi <xref:System.Collections.Generic.IEnumerable%601> ve türündeki nesneler üzerinde çalışan diğer <xref:System.Linq.IQueryable%601>. Her bir kümesini oluşturan yöntemleri statik üyeleridir <xref:System.Linq.Enumerable> ve <xref:System.Linq.Queryable> sınıfları, sırasıyla. Olarak tanımlanan *genişletme yöntemleri* türündeki bunlar üzerinde çalışır. Başka bir deyişle, bunlar statik yöntem sözdizimi veya örnek yöntem sözdizimi kullanılarak çağrılabilir.  
  
 Ayrıca, birçok standart sorgu işleci yöntemleri türlerine göre dışındaki çalışan <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Linq.IQueryable%601>. <xref:System.Linq.Enumerable> Türünü tanımlayan iki yöntem her ikisi de türündeki nesneler üzerinde çalışan <xref:System.Collections.IEnumerable>. Bu yöntemler <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> ve <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let LINQ desen Sorgulanacak forceseek veya genel olmayan, bir koleksiyon etkinleştirin. Bunlar nesneleri türü kesin belirlenmiş koleksiyonu oluşturmanız gerekir. <xref:System.Linq.Queryable> Sınıfı tanımlayan iki benzer yöntem <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> ve <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, türündeki nesneler üzerinde çalışan <xref:System.Linq.Queryable>.  
  
 Standart sorgu işleçleri, bunlar bir tekil değer veya değerlerini bir dizi döndürür bağlı olarak, yürütme, zamanlama içinde farklılık gösterir. Tekil değer döndüren bu yöntemler (örneğin, <xref:System.Linq.Enumerable.Average%2A> ve <xref:System.Linq.Enumerable.Sum%2A>) hemen yürütün. Bir dizi döndüren yöntemler, sorgu yürütme ertele ve bir numaralandırma nesnesi döndürür.  
  
 Bellek içi koleksiyonlarda genişleten bu yöntemler diğer bir deyişle, çalışan yöntemleri söz konusu olduğunda <xref:System.Collections.Generic.IEnumerable%601>, yönteme geçirilen bağımsız değişkenler döndürülen numaralandırılabilir nesne yakalar. Bu nesne numaralandırılana sorgu işleci mantığını işe ve sorgu sonuçları döndürülür.  
  
 Buna karşılık, yöntemleri, genişleten <xref:System.Linq.IQueryable%601> herhangi bir davranış sorgulanırken kullanılmaz, ancak gerçekleştirilmesi için sorguyu temsil eden ifade ağacında oluşturun. Sorgu işleme kaynak tarafından işlendiğini <xref:System.Linq.IQueryable%601> nesne.  
  
 Sorgu yöntemlere yapılan çağrılar, sorguları rasgele karmaşık olmasını sağlayan bir sorguda birbirine zincirlenebilir.  
  
 Aşağıdaki kod örneği, bir dizi hakkında bilgi edinmek için standart sorgu işleçleri'nın nasıl kullanılabileceğini gösterir.  
  
```csharp  
string sentence = "the quick brown fox jumps over the lazy dog";  
// Split the string into individual words to create a collection.  
string[] words = sentence.Split(' ');  
  
// Using query expression syntax.  
var query = from word in words  
            group word.ToUpper() by word.Length into gr  
            orderby gr.Key  
            select new { Length = gr.Key, Words = gr };  
  
// Using method-based query syntax.  
var query2 = words.  
    GroupBy(w => w.Length, w => w.ToUpper()).  
    Select(g => new { Length = g.Key, Words = g }).  
    OrderBy(o => o.Length);  
  
foreach (var obj in query)  
{  
    Console.WriteLine("Words of length {0}:", obj.Length);  
    foreach (string word in obj.Words)  
        Console.WriteLine(word);  
}  
  
// This code example produces the following output:  
//  
// Words of length 3:  
// THE  
// FOX  
// THE  
// DOG  
// Words of length 4:  
// OVER  
// LAZY  
// Words of length 5:  
// QUICK  
// BROWN  
// JUMPS   
```  
  
## <a name="query-expression-syntax"></a>Sorgu ifadesi söz dizimi  
 Bazı daha sık kullanılan standart sorgu işleçlerinin bir parçası olarak çağrılacak tanıyan C# ve Visual Basic dili anahtar sözcüğü sözdizimini adanmış bir *sorgu* *ifade*. Anahtar sözcükleri ve bunların karşılık gelen sözdizimleri adanmış standart sorgu işleçleri hakkında daha fazla bilgi için bkz. [standart sorgu işleçleri (C#) için sorgu ifade sözdizimi](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).  
  
## <a name="extending-the-standard-query-operators"></a>Standart sorgu işleçlerini genişletme  
 Hedef etki alanına veya teknoloji için uygun olan oluşturma etki alanına özgü yöntemlerle standart sorgu işleçleri kümesini genişletebilirsiniz. Uzak değerlendirme, sorgu çevirisi ve en iyi duruma getirme gibi ek hizmetler sağlayan kendi uygulamaları ile standart sorgu işleçleri de değiştirebilirsiniz. Bkz: <xref:System.Linq.Enumerable.AsEnumerable%2A> örneği.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Aşağıdaki bağlantılar işlevselliğine bağlı olarak çeşitli standart sorgu işleçleri hakkında ek bilgiler sağlayan konulara yönlendirir.  
  
 [Verileri sıralama (C#)](../../../../csharp/programming-guide/concepts/linq/sorting-data.md)  
  
 [Ayarlama işlemleri (C#)](../../../../csharp/programming-guide/concepts/linq/set-operations.md)  
  
 [Verileri filtreleme (C#)](../../../../csharp/programming-guide/concepts/linq/filtering-data.md)  
  
 [Niceleyici işlemleri (C#)](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md)  
  
 [Projeksiyon işlemleri (C#)](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)  
  
 [Veri bölümleme (C#)](../../../../csharp/programming-guide/concepts/linq/partitioning-data.md)  
  
 [Birleştirme işlemleri (C#)](../../../../csharp/programming-guide/concepts/linq/join-operations.md)  
  
 [Verileri gruplandırma (C#)](../../../../csharp/programming-guide/concepts/linq/grouping-data.md)  
  
 [Oluşturma işlemleri (C#)](../../../../csharp/programming-guide/concepts/linq/generation-operations.md)  
  
 [Eşitlik işlemleri (C#)](../../../../csharp/programming-guide/concepts/linq/equality-operations.md)  
  
 [Öğe işlemleri (C#)](../../../../csharp/programming-guide/concepts/linq/element-operations.md)  
  
 [Veri türlerini dönüştürme (C#)](../../../../csharp/programming-guide/concepts/linq/converting-data-types.md)  
  
 [Birleştirme işlemleri (C#)](../../../../csharp/programming-guide/concepts/linq/concatenation-operations.md)  
  
 [Toplama işlemleri (C#)](../../../../csharp/programming-guide/concepts/linq/aggregation-operations.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [LINQ sorguları (C#) giriş](../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)
- [Standart sorgu işleçleri (C#) için sorgu ifade sözdizimi](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)
- [Standart sorgu işleçlerinin yöntemine göre sınıflandırılması yürütme (C#)](../../../../csharp/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)
- [Genişletme Yöntemleri](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
