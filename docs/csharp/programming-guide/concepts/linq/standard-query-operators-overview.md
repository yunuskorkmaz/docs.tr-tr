---
title: Standart sorgu işleçlerine genel bakış (C#)
ms.date: 07/20/2015
ms.assetid: 812fa119-5f65-4139-b4fa-55dccd8dc3ac
ms.openlocfilehash: 36bd5927e64ffacb97beac28b8e7790204e08c5c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33337330"
---
# <a name="standard-query-operators-overview-c"></a>Standart sorgu işleçlerine genel bakış (C#)
*Standart sorgu işleçleri* LINQ düzeni form yöntemleridir. Bu yöntemlerin çoğu bir dizi türü uygulayan bir nesne olduğu sıraları üzerinde çalışması <xref:System.Collections.Generic.IEnumerable%601> arabirimi veya <xref:System.Linq.IQueryable%601> arabirimi. Standart sorgu işleçleri filtreleme, yansıtma, toplama, sıralama ve daha fazlası dahil olmak üzere sorgu özellikleri sağlar.  
  
 LINQ standart sorgu işleçleri, bir tür nesneler üzerinde çalışan iki kümesi vardır <xref:System.Collections.Generic.IEnumerable%601> ve tür nesneler üzerinde çalışan diğer <xref:System.Linq.IQueryable%601>. Her ayarlama yapmak yöntemleri statik üyeleri olan <xref:System.Linq.Enumerable> ve <xref:System.Linq.Queryable> sınıfları, sırasıyla. Olarak tanımlanan *genişletme yöntemleri* üzerinde çalışacağı türü. Başka bir deyişle, bunlar statik yöntem sözdizimi veya örnek yöntemi sözdizimini kullanarak çağrılabilir.  
  
 Ayrıca, çeşitli standart sorgu işleci yöntemler türleri üzerinde tabanlı olanlar dışındaki çalışmayabilir <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Linq.IQueryable%601>. <xref:System.Linq.Enumerable> Türünü tanımlayan iki tür yöntem her ikisi de türündeki nesneler üzerinde çalışan <xref:System.Collections.IEnumerable>. Bu yöntemler <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> ve <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let LINQ desende Sorgulanacak parametreli olmayan veya genel olmayan, bir toplama etkinleştir. Kesin türü belirtilmiş bir nesneler koleksiyonunu oluşturarak bunu. <xref:System.Linq.Queryable> Sınıfı tanımlayan iki benzer yöntemler <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> ve <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, türündeki nesneler üzerinde çalışan <xref:System.Linq.Queryable>.  
  
 Standart sorgu işleçleri, bunlar bir singleton değeri veya değerler dizisini döndürür bağlı olarak, yürütme, zamanlama içinde farklılık gösterir. Tek değer döndürme bu yöntemleri (örneğin, <xref:System.Linq.Enumerable.Average%2A> ve <xref:System.Linq.Enumerable.Sum%2A>) hemen yürütün. Bir dizi döndüren yöntemler sorgu yürütme erteleneceği ve bir numaralandırma nesnesi döndürür.  
  
 Bellek içi koleksiyonlarında, diğer bir deyişle, genişletme bu yöntemleri çalışması yöntemleri durumunda <xref:System.Collections.Generic.IEnumerable%601>, yönteme geçirilen bağımsız değişken döndürülen numaralandırılabilir nesne yakalar. Bu nesne numaralandırılan sorgu işleci mantığı işe ve sorgusu sonuç döndürmedi.  
  
 Buna karşılık, yöntemleri, genişletme <xref:System.Linq.IQueryable%601> herhangi sorgulanırken davranışı kullanılmaz, ancak gerçekleştirilmesi için sorguyu temsil eden bir ifade ağacına derleme. Sorgu işleme kaynak tarafından işlenen <xref:System.Linq.IQueryable%601> nesnesi.  
  
 Sorgu yöntemleri çağrıları rasgele karmaşık hale gelmesine sorgularını sağlayan, tek bir sorguda birbirine zincirlenebilir.  
  
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
  
## <a name="query-expression-syntax"></a>Sorgu ifade sözdizimi  
 Bazı daha sık kullanılan standart sorgu işleçleri bunları parçası olarak çağrılacak etkinleştiren C# ve Visual Basic dil anahtar sözcüğü sözdizimini adanmış bir *sorgu* *ifade*. Anahtar sözcükler ve bunların karşılık gelen sözdizimleri ayrılmış standart sorgu işleçleri hakkında daha fazla bilgi için bkz: [standart sorgu işleçleri (C#) için sorgu ifade sözdizimi](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).  
  
## <a name="extending-the-standard-query-operators"></a>Standart sorgu işleçleri genişletme  
 Standart sorgu işleçleri kümesi hedef etki alanına veya teknoloji için uygun olan oluşturma etki alanına özgü yöntemlerle genişletebilirsiniz. Standart sorgu işleçleri, uzak değerlendirme, sorgu çeviri ve en iyi duruma getirme gibi ek hizmetleri sağlayan kendi uygulamaları ile de değiştirebilirsiniz. Bkz: <xref:System.Linq.Enumerable.AsEnumerable%2A> bir örnek.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Aşağıdaki bağlantılar işlevselliğine bağlı çeşitli standart sorgu işleçleri hakkında ek bilgiler sağlayan konulara götürür.  
  
 [Veri sıralama (C#)](../../../../csharp/programming-guide/concepts/linq/sorting-data.md)  
  
 [Ayarlama işlemleri (C#)](../../../../csharp/programming-guide/concepts/linq/set-operations.md)  
  
 [Filtre verileri (C#)](../../../../csharp/programming-guide/concepts/linq/filtering-data.md)  
  
 [Niceleyici işlemleri (C#)](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md)  
  
 [Projeksiyon işlemleri (C#)](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)  
  
 [Bölümleme verileri (C#)](../../../../csharp/programming-guide/concepts/linq/partitioning-data.md)  
  
 [Birleştirme işlemleri (C#)](../../../../csharp/programming-guide/concepts/linq/join-operations.md)  
  
 [Verileri gruplandırma (C#)](../../../../csharp/programming-guide/concepts/linq/grouping-data.md)  
  
 [Oluşturma işlemleri (C#)](../../../../csharp/programming-guide/concepts/linq/generation-operations.md)  
  
 [Eşitlik işlemleri (C#)](../../../../csharp/programming-guide/concepts/linq/equality-operations.md)  
  
 [Öğe işlemleri (C#)](../../../../csharp/programming-guide/concepts/linq/element-operations.md)  
  
 [Dönüştürme veri türleri (C#)](../../../../csharp/programming-guide/concepts/linq/converting-data-types.md)  
  
 [Birleştirme işlemleri (C#)](../../../../csharp/programming-guide/concepts/linq/concatenation-operations.md)  
  
 [Toplama işlemleri (C#)](../../../../csharp/programming-guide/concepts/linq/aggregation-operations.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Linq.Enumerable>  
 <xref:System.Linq.Queryable>  
 [Giriş LINQ sorgularını (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 [Standart sorgu işleçleri (C#) için sorgu ifade sözdizimi](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)  
 [Standart sorgu işleçleri yürütme (C#) yöntemine göre sınıflandırılması](../../../../csharp/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)  
 [Genişletme Yöntemleri](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
