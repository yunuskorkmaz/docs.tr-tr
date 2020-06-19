---
title: Standart sorgu Işleçlerine genel bakış (C#)
ms.date: 07/20/2015
ms.assetid: 812fa119-5f65-4139-b4fa-55dccd8dc3ac
ms.openlocfilehash: 095a0b7a7a8265f235d28a4634ea82cdcd7a60c0
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990009"
---
# <a name="standard-query-operators-overview-c"></a>Standart sorgu Işleçlerine genel bakış (C#)
*Standart sorgu IŞLEÇLERI* LINQ deseninin bulunduğu yöntemlerdir. Bu yöntemlerin çoğu diziler üzerinde çalışır, burada bir sıra, türü arabirimini veya arabirimi uygulayan bir nesnedir <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Linq.IQueryable%601> . Standart sorgu işleçleri filtreleme, yansıtma, toplama, sıralama ve daha fazlasını içeren sorgu özellikleri sağlar.  
  
 LINQ standart sorgu işleçlerinin iki kümesi vardır: türü nesneler üzerinde çalışan diğeri <xref:System.Collections.Generic.IEnumerable%601> , türündeki nesneler üzerinde çalışır <xref:System.Linq.IQueryable%601> . Her kümeyi oluşturan Yöntemler <xref:System.Linq.Enumerable> sırasıyla ve sınıflarının statik üyeleridir <xref:System.Linq.Queryable> . Bunlar üzerinde çalıştıkları türün *Uzantı yöntemleri* olarak tanımlanmıştır. Uzantı yöntemleri, statik yöntem sözdizimi veya örnek yöntemi sözdizimi kullanılarak çağrılabilir.  
  
 Ayrıca, birkaç standart sorgu işleci yöntemi, veya tabanlı olanlar dışındaki türler üzerinde çalışır <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Linq.IQueryable%601> . <xref:System.Linq.Enumerable>Türü, her ikisi de türündeki nesneler üzerinde çalışan iki yöntemi tanımlar <xref:System.Collections.IEnumerable> . Bu yöntemler <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> ve <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29> , parametreli olmayan veya genel olmayan BIR koleksiyonun LINQ düzeninde sorgulanmasını etkinleştirmenizi sağlar. Bunu, türü kesin belirlenmiş bir nesne koleksiyonu oluşturarak yapabilirler. <xref:System.Linq.Queryable>Sınıfı, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> ve <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29> türündeki nesneler üzerinde çalışan iki benzer yöntemi tanımlar <xref:System.Linq.Queryable> .  
  
 Standart sorgu işleçleri, tek bir değer veya bir dizi değer döndürmediğine bağlı olarak yürütmesinin zamanlamalarına göre farklılık gösterir. Tek bir değer döndüren Yöntemler (örneğin, <xref:System.Linq.Enumerable.Average%2A> ve <xref:System.Linq.Enumerable.Sum%2A> ) hemen yürütülür. Bir dizi döndüren yöntemler sorgu yürütmesini erteler ve Numaralandırılabilir bir nesne döndürüyor.  
  
 Bellek içi koleksiyonlar üzerinde çalışan yöntemler için, diğer bir deyişle, <xref:System.Collections.Generic.IEnumerable%601> döndürülen sıralanabilir nesne, metoduna geçirilen bağımsız değişkenleri yakalar. Bu nesne numaralandırıldıktan sonra, sorgu işlecinin mantığı işe alınır ve sorgu sonuçları döndürülür.  
  
 Buna karşılık, genişleyen Yöntemler <xref:System.Linq.IQueryable%601> herhangi bir sorgulama davranışı uygulamaz. Bunlar gerçekleştirilecek sorguyu temsil eden bir ifade ağacı oluşturur. Sorgu işleme, kaynak nesne tarafından işlenir <xref:System.Linq.IQueryable%601> .  
  
 Sorgu yöntemlerine yapılan çağrılar tek bir sorgu içinde birbirine zincirlenebilir ve bu da sorguların rastgele karmaşık olmasını sağlar.  
  
 Aşağıdaki kod örneği, bir dizi hakkında bilgi edinmek için standart sorgu işleçlerinin nasıl kullanılabileceğini gösterir.  
  
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
  
## <a name="query-expression-syntax"></a>Sorgu Ifadesi söz dizimi  
 Daha sık kullanılan standart sorgu işleçlerinden bazılarının, bir *sorgu* *ifadesinin*parçası olarak çağrılmasına olanak sağlayan adanmış C# ve Visual Basic Language anahtar sözcüğü vardır. Adanmış anahtar sözcüklere ve bunlara karşılık gelen sözdizimleri içeren standart sorgu işleçleri hakkında daha fazla bilgi için bkz. [Standart sorgu işleçleri Için sorgu Ifadesi sözdizimi (C#)](./query-expression-syntax-for-standard-query-operators.md).  
  
## <a name="extending-the-standard-query-operators"></a>Standart sorgu Işleçlerini genişletme  
 Hedef etki alanınız veya teknolojiniz için uygun olan alana özgü Yöntemler oluşturarak standart sorgu işleçleri kümesini daha da getirebilirsiniz. Standart sorgu işleçlerini, uzaktan değerlendirme, sorgu çevirisi ve iyileştirme gibi ek hizmetler sağlayan kendi uygulamalarınız ile de değiştirebilirsiniz. <xref:System.Linq.Enumerable.AsEnumerable%2A>Bir örnek için bkz..  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Aşağıdaki bağlantılar, işlevleri temel alan çeşitli standart sorgu işleçleri hakkında ek bilgiler sağlayan makalelere götürür.  
  
 [Verileri sıralama (C#)](./sorting-data.md)  
  
 [Ayarlama Işlemleri (C#)](./set-operations.md)  
  
 [Verileri filtreleme (C#)](./filtering-data.md)  
  
 [Nicelik belirteci Işlemleri (C#)](./quantifier-operations.md)  
  
 [Projeksiyon Işlemleri (C#)](./projection-operations.md)  
  
 [Verileri bölümleme (C#)](./partitioning-data.md)  
  
 [JOIN Işlemleri (C#)](./join-operations.md)  
  
 [Verileri gruplandırma (C#)](./grouping-data.md)  
  
 [Oluşturma Işlemleri (C#)](./generation-operations.md)  
  
 [Eşitlik Işlemleri (C#)](./equality-operations.md)  
  
 [Öğe Işlemleri (C#)](./element-operations.md)  
  
 [Veri türlerini dönüştürme (C#)](./converting-data-types.md)  
  
 [Birleştirme Işlemleri (C#)](./concatenation-operations.md)  
  
 [Toplama Işlemleri (C#)](./aggregation-operations.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [LINQ Sorgularına Giriş (C#)](./introduction-to-linq-queries.md)
- [Standart sorgu Işleçleri için sorgu Ifadesi sözdizimi (C#)](./query-expression-syntax-for-standard-query-operators.md)
- [Standart sorgu Işleçlerinin yürütme yöntemine göre sınıflandırılması (C#)](./classification-of-standard-query-operators-by-manner-of-execution.md)
- [Uzantı Metotları](../../classes-and-structs/extension-methods.md)
