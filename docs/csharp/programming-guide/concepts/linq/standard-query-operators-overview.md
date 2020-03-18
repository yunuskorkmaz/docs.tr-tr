---
title: Standart Sorgu Operatörlerine Genel Bakış (C#)
ms.date: 07/20/2015
ms.assetid: 812fa119-5f65-4139-b4fa-55dccd8dc3ac
ms.openlocfilehash: 76c2c4684f33c3fb30748b5f08efd215548661ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167861"
---
# <a name="standard-query-operators-overview-c"></a>Standart Sorgu Operatörlerine Genel Bakış (C#)
*Standart sorgu işleçleri* LINQ deseni oluşturan yöntemlerdir. Bu yöntemlerin çoğu, bir dizinin <xref:System.Collections.Generic.IEnumerable%601> arabirimi veya <xref:System.Linq.IQueryable%601> arabirimi uygulayan bir nesne olduğu diziler üzerinde çalışır. Standart sorgu işleçleri filtreleme, projeksiyon, toplama, sıralama ve daha fazlası dahil olmak üzere sorgu yetenekleri sağlar.  
  
 LinQ standart sorgu işleçleri, bir tür <xref:System.Collections.Generic.IEnumerable%601> nesneleri üzerinde çalışan ve diğer tür <xref:System.Linq.IQueryable%601>nesneleri üzerinde çalışan iki küme vardır. Her kümeyi oluşturan yöntemler sırasıyla <xref:System.Linq.Enumerable> sınıfların <xref:System.Linq.Queryable> statik üyeleridir. Bunlar, çalıştıkları türün *uzantı yöntemleri* olarak tanımlanırlar. Bu, statik yöntem sözdizimi veya örnek yöntemi sözdizimi kullanılarak çağrılabileceği anlamına gelir.  
  
 Buna ek olarak, çeşitli standart sorgu işleci <xref:System.Collections.Generic.IEnumerable%601> yöntemleri, temel veya . <xref:System.Linq.IQueryable%601> Tür, <xref:System.Linq.Enumerable> her ikisi de tür <xref:System.Collections.IEnumerable>nesneleri üzerinde çalışan bu tür iki yöntem tanımlar. Bu yöntemler <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>ve , linq deseninde sorgulanmak için parametreli olmayan veya genel olmayan bir koleksiyon etkinleştirmenize olanak sağlar. Bunu, güçlü bir şekilde yazılan nesneler koleksiyonu oluşturarak yaparlar. Sınıf <xref:System.Linq.Queryable> iki benzer yöntem <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> tanımlar <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>ve , türü <xref:System.Linq.Queryable>nesneleri üzerinde çalışır.  
  
 Standart sorgu işleçleri, tek ton değeri veya bir değer dizisi döndürüp döndürmediklerine bağlı olarak yürütme zamanlaması açısından farklılık gösterir. Singleton değerini döndüren bu yöntemler <xref:System.Linq.Enumerable.Average%2A> <xref:System.Linq.Enumerable.Sum%2A>(örneğin, ve) hemen çalıştırın. Sırayı döndüren yöntemler sorgu yürütmesini erteler ve sayısal bir nesne döndürür.  
  
 Bellek içi koleksiyonları nda çalışan yöntemler söz konusu olduğunda, yani uzabilen <xref:System.Collections.Generic.IEnumerable%601>bu yöntemlerde, döndürülen sayısal nesne yönteme geçirilen bağımsız değişkenleri yakalar. Bu nesne numaralandırıldığında, sorgu işlecinin mantığı kullanılır ve sorgu sonuçları döndürülür.  
  
 Buna karşılık, genişleten <xref:System.Linq.IQueryable%601> yöntemler herhangi bir sorgu davranışı uygulamaz, ancak gerçekleştirilecek sorguyu temsil eden bir ifade ağacı oluşturur. Sorgu işleme kaynak <xref:System.Linq.IQueryable%601> nesne tarafından işlenir.  
  
 Sorgu yöntemlerine yapılan çağrılar, sorguların rasgele karmaşık hale gelmesine olanak tanıyan tek bir sorguda birbirine zincirlenebilir.  
  
 Aşağıdaki kod örneği, standart sorgu işleçlerinin bir dizi hakkında bilgi edinmek için nasıl kullanılabileceğini gösterir.  
  
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
  
## <a name="query-expression-syntax"></a>Sorgu İfade Sözdizimi  
 Daha sık kullanılan standart sorgu işleçlerinden bazıları, *sorgu* *ifadesinin*bir parçası olarak çağrılmasını sağlayan C# ve Visual Basic dil sözdizimini adadı. Özel anahtar kelimeleri ve bunların karşılık gelen sözdizimi leri olan standart sorgu işleçleri hakkında daha fazla bilgi [için, Standart Sorgu Operatörleri (C#) için Sorgu İfadesözdizimi'ne](./query-expression-syntax-for-standard-query-operators.md)bakın.  
  
## <a name="extending-the-standard-query-operators"></a>Standart Sorgu Operatörlerini Genişletme  
 Hedef etki alanınız veya teknolojiniz için uygun etki alanına özgü yöntemler oluşturarak standart sorgu işleçleri kümesini artırabilirsiniz. Ayrıca, standart sorgu işleçlerini uzaktan değerlendirme, sorgu çevirisi ve optimizasyon gibi ek hizmetler sağlayan kendi uygulamalarınızla da değiştirebilirsiniz. Bir <xref:System.Linq.Enumerable.AsEnumerable%2A> örnek için bkz.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Aşağıdaki bağlantılar, işlevsellik dayalı çeşitli standart sorgu operatörleri hakkında ek bilgi sağlayan konulara götürür.  
  
 [Verileri Sıralama (C#)](./sorting-data.md)  
  
 [İşlemleri Ayarla (C#)](./set-operations.md)  
  
 [Veri Filtreleme (C#)](./filtering-data.md)  
  
 [Niceleyici İşlemleri (C#)](./quantifier-operations.md)  
  
 [Projeksiyon İşlemleri (C#)](./projection-operations.md)  
  
 [Veri Bölümleme (C#)](./partitioning-data.md)  
  
 [İşleme Katılma (C#)](./join-operations.md)  
  
 [Verileri Gruplandırma (C#)](./grouping-data.md)  
  
 [Üretim İşlemleri (C#)](./generation-operations.md)  
  
 [Eşitlik İşlemleri (C#)](./equality-operations.md)  
  
 [Eleman İşlemleri (C#)](./element-operations.md)  
  
 [Veri Türlerini Dönüştürme (C#)](./converting-data-types.md)  
  
 [Concatenation İşlemleri (C#)](./concatenation-operations.md)  
  
 [Toplama İşlemleri (C#)](./aggregation-operations.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [LINQ Sorgularına Giriş (C#)](./introduction-to-linq-queries.md)
- [Standart Sorgu Operatörleri için Sorgu İfade Sözdizimi (C#)](./query-expression-syntax-for-standard-query-operators.md)
- [Standart Sorgu Operatörlerinin Yürütme Şekline Göre Sınıflandırılması (C#)](./classification-of-standard-query-operators-by-manner-of-execution.md)
- [Genişletme Yöntemleri](../../classes-and-structs/extension-methods.md)
