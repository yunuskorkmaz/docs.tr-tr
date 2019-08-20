---
title: Standart sorgu Işleçlerine genelC#bakış ()
ms.date: 07/20/2015
ms.assetid: 812fa119-5f65-4139-b4fa-55dccd8dc3ac
ms.openlocfilehash: e6419fef5c211995aa4d2bd0796a0d0336dc47a9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590981"
---
# <a name="standard-query-operators-overview-c"></a>Standart sorgu Işleçlerine genelC#bakış ()
*Standart sorgu IŞLEÇLERI* LINQ deseninin bulunduğu yöntemlerdir. Bu yöntemlerin çoğu diziler üzerinde çalışır, burada bir sıra, türü <xref:System.Collections.Generic.IEnumerable%601> arabirimini <xref:System.Linq.IQueryable%601> veya arabirimi uygulayan bir nesnedir. Standart sorgu işleçleri filtreleme, yansıtma, toplama, sıralama ve daha fazlasını içeren sorgu özellikleri sağlar.  
  
 Türü <xref:System.Collections.Generic.IEnumerable%601> nesneler üzerinde çalışan diğeri türü <xref:System.Linq.IQueryable%601>nesneler üzerinde çalışan iki LINQ standart sorgu işleci kümesi vardır. Her kümeyi oluşturan Yöntemler sırasıyla <xref:System.Linq.Enumerable> ve <xref:System.Linq.Queryable> sınıflarının statik üyeleridir. Bunlar üzerinde çalıştıkları türün *Uzantı yöntemleri* olarak tanımlanmıştır. Bu, statik yöntem sözdizimi veya örnek yöntemi sözdizimi kullanılarak çağrılabilecek anlamına gelir.  
  
 Ayrıca, birkaç standart sorgu işleci yöntemi, <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Linq.IQueryable%601>tabanlı olanlar dışındaki türler üzerinde çalışır. Türü <xref:System.Linq.Enumerable> , her ikisi de türündeki <xref:System.Collections.IEnumerable>nesneler üzerinde çalışan iki yöntemi tanımlar. Bu yöntemler <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> ve <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, parametreli olmayan veya genel olmayan bir koleksiyonun LINQ düzeninde sorgulanmasını etkinleştirmenizi sağlar. Bu, nesne türü kesin belirlenmiş bir koleksiyon oluşturarak bunu yapabilirler. Sınıfı, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> ve<xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>türündeki nesneler<xref:System.Linq.Queryable>üzerinde çalışan iki benzer yöntemi tanımlar. <xref:System.Linq.Queryable>  
  
 Standart sorgu işleçleri, tek bir değer veya bir dizi değer döndürmediğine bağlı olarak yürütmesinin zamanlamalarına göre farklılık gösterir. Tek bir değer döndüren Yöntemler (örneğin, <xref:System.Linq.Enumerable.Average%2A> ve <xref:System.Linq.Enumerable.Sum%2A>) hemen yürütülür. Bir dizi döndüren yöntemler sorgu yürütmesini erteler ve Numaralandırılabilir bir nesne döndürüyor.  
  
 Bellek içi koleksiyonlar üzerinde çalışan yöntemler söz konusu olduğunda, diğer bir deyişle <xref:System.Collections.Generic.IEnumerable%601>, döndürülen sıralanabilir nesne, metoduna geçirilen bağımsız değişkenleri yakalar. Bu nesne numaralandırıldıktan sonra, sorgu işlecinin mantığı işe alınır ve sorgu sonuçları döndürülür.  
  
 Buna karşılık, genişleyen <xref:System.Linq.IQueryable%601> Yöntemler herhangi bir sorgulama davranışı uygulamaz, ancak gerçekleştirilecek sorguyu temsil eden bir ifade ağacı oluşturur. Sorgu işleme, kaynak <xref:System.Linq.IQueryable%601> nesne tarafından işlenir.  
  
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
 Daha sık kullanılan standart sorgu işleçlerinden bazılarının, bir C# *sorgu* *ifadesinin*parçası olarak çağrılmasına olanak tanıyan adanmış ve Visual Basic Language anahtar sözcüğü sözdizimi vardır. Adanmış anahtar sözcüklere ve bunlara karşılık gelen sözdizimleri içeren standart sorgu işleçleri hakkında daha fazla bilgi için bkz. [Standart sorgu işleçleri Için sorgu IfadesiC#sözdizimi ()](./query-expression-syntax-for-standard-query-operators.md).  
  
## <a name="extending-the-standard-query-operators"></a>Standart sorgu Işleçlerini genişletme  
 Hedef etki alanınız veya teknolojiniz için uygun olan alana özgü Yöntemler oluşturarak standart sorgu işleçleri kümesini daha da getirebilirsiniz. Standart sorgu işleçlerini, uzaktan değerlendirme, sorgu çevirisi ve iyileştirme gibi ek hizmetler sağlayan kendi uygulamalarınız ile de değiştirebilirsiniz. Bir <xref:System.Linq.Enumerable.AsEnumerable%2A> örnek için bkz.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Aşağıdaki bağlantılar, işlevleri temel alan çeşitli standart sorgu işleçleri hakkında ek bilgiler sağlayan konulara götürür.  
  
 [Verileri sıralama (C#)](./sorting-data.md)  
  
 [Işlemleri ayarla (C#)](./set-operations.md)  
  
 [Verileri filtreleme (C#)](./filtering-data.md)  
  
 [Nicelik belirteci IşlemleriC#()](./quantifier-operations.md)  
  
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
- [Standart sorgu Işleçleri yürütme (C#) yöntemine göre sınıflandırması](./classification-of-standard-query-operators-by-manner-of-execution.md)
- [Genişletme Yöntemleri](../../classes-and-structs/extension-methods.md)
