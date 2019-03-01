---
title: LINQ Sorgularına Giriş (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- deferred execution [LINQ]
- LINQ, queries
- LINQ, deferred execution
- queries [LINQ], about LINQ queries
ms.assetid: 37895c02-268c-41d5-be39-f7d936fa88a8
ms.openlocfilehash: 73b7f8b8460e4cdfad5e1dbc669447ec6fe01b8f
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969511"
---
# <a name="introduction-to-linq-queries-c"></a>LINQ Sorgularına Giriş (C#)
A *sorgu* , verileri bir veri kaynağından alır bir ifadedir. Sorgular genellikle bir özel sorgu dilinde ifade edilir. Farklı diller zamanla çeşitli veri kaynakları, örneğin ilişkisel veritabanları için SQL ve XML için XQuery geliştirilmiştir. Bu nedenle, geliştiriciler, her veri kaynağı veya desteklemeleri gereken veri biçimi türü için yeni bir sorgu dili öğrenmek zorunda kalmışlardır. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] Bu durum, çeşitli veri kaynakları ve biçimler arasında veri ile çalışma için tutarlı bir model sunarak basitleştirir. İçinde bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu, her zaman nesnelerle. XML belgelerinde, SQL veritabanları, veri sorgulamak ve dönüştürmek için aynı temel kodlama desenlerini kullanırsınız [!INCLUDE[vstecado](~/includes/vstecado-md.md)] veri kümeleri, .NET koleksiyonlarında ve başka bir biçimi olan bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sağlayıcısı kullanılabilir.  
  
## <a name="three-parts-of-a-query-operation"></a>Bir Sorgu İşleminin Üç Bölümü  
 Tüm [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu işlemleri üç farlı eylemden oluşur oluşur:  
  
1.  Veri kaynağını edinin.  
  
2.  Bir sorgu oluşturun.  
  
3.  Sorguyu yürütün.  
  
 Aşağıdaki örnek, bir sorgu işleminin üç bölümü kaynak kodunda nasıl ifade edildiğini gösterir. Örnek bir tamsayı dizisi kolaylık sağlamak için veri kaynağı olarak kullanır; Ancak, aynı kavramlar diğer veri kaynakları için de geçerlidir. Bu örnekte, bu konunun geri kalan aşamalarında adlandırılır.  
  
 [!code-csharp[CsLINQGettingStarted#1](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/introduction-to-linq-queries_1.cs)]  
  
 Aşağıda tam bir sorgu işlemi gösterilmektedir. İçinde [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgunun yürütülmesi sorgunun kendisinden farklıdır, diğer bir deyişle, veriler yalnızca bir sorgu değişkeni oluşturarak almış olmazsınız.  
  
 ![LINQ Sorgu işlemi](../../../../csharp/programming-guide/concepts/linq/media/linq_query.png "LINQ_Query")  
  
## <a name="the-data-source"></a>Veri Kaynağı  
 Veri kaynağı bir dizi olduğundan önceki örnekte, örtük olarak genel destekliyorsa <xref:System.Collections.Generic.IEnumerable%601> arabirimi. Bu, ile sorgulanabileceği anlamına gelir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]. Bir sorgu içinde yürütülen bir `foreach` deyimi ve `foreach` gerektirir <xref:System.Collections.IEnumerable> veya <xref:System.Collections.Generic.IEnumerable%601>. Destekleyen türler <xref:System.Collections.Generic.IEnumerable%601> veya türetilmiş bir arabirim gibi genel <xref:System.Linq.IQueryable%601> adlandırılır *sorgulanabilir türler*.  
  
 Sorgulanabilir tür herhangi bir değişiklik veya olarak hizmet vermek için özel olarak değerlendirilmesi gerekir. bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] veri kaynağı. Kaynak verileri bellekte bir sorgulanabilir tür olarak yoksa [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sağlayıcısı temsil etmesi gerekir, bu nedenle. Örneğin, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bir XML belgesini sorgulanabilir bir yükleyen <xref:System.Xml.Linq.XElement> türü:  
  
 [!code-csharp[CsLINQGettingStarted#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#2)]  
  
 İle [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], önce bir nesne-ilişkisel tasarım zamanında el ile ya da kullanarak eşleme oluşturma [LINQ to SQL araçlarını Visual Studio'da](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) Visual Studio'da. Sorgularınızın karşı nesneleri ve çalışma zamanında yazma [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] veritabanı ile iletişimi gerçekleştirir. Aşağıdaki örnekte, `Customers` belirli bir tablo veritabanının yanı sıra, sorgu sonuç türünü temsil eden <xref:System.Linq.IQueryable%601>, türetilen <xref:System.Collections.Generic.IEnumerable%601>.  
  
```csharp  
Northwnd db = new Northwnd(@"c:\northwnd.mdf");  
  
// Query for customers in London.  
IQueryable<Customer> custQuery =  
    from cust in db.Customers  
    where cust.City == "London"  
    select cust;  
```  
  
 Belirli türde veri kaynaklarını oluşturma hakkında daha fazla bilgi için çeşitli belgelerine bakın [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sağlayıcıları. Ancak, temel kural çok basittir: bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] genel destekleyen herhangi bir nesne veri kaynağı, <xref:System.Collections.Generic.IEnumerable%601> arabirimi ya da bundan devralan bir arabirim.  
  
> [!NOTE]
>  Gibi türleri <xref:System.Collections.ArrayList> genel olmayan destekleyen <xref:System.Collections.IEnumerable> arabirimi de kullanılabilir olarak bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] veri kaynağı. Daha fazla bilgi için [nasıl yapılır: LINQ ile ArrayList sorgulama (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md).  
  
##  <a name="query"></a> Sorgu  
 Sorgu, hangi bilgilerin veri kaynağından veya kaynaklarından alınacağını belirtir. İsteğe bağlı olarak, bir sorgunun nasıl bu bilgileri sıralanmış, gruplandırılmış ve döndürülmeden önce şeklinde belirtir. Bir sorguyu sorgu değişkeninde depolanır ve sorgu ifadesiyle başlatılır. Sorguları yazmayı kolaylaştırmak için C# yeni sorgu sözdizimi tanıttı.  
  
 Önceki örnekte sorgu tamsayı dizisinden tüm çift sayıları döndürür. Sorgu ifadesi üç yan tümce içeriyor: `from`, `where` ve `select`. (SQL ile bilginiz varsa, yan tümcelerini sıralama sırasının SQL'deki gelen ters olduğunu fark etmiş.) `from` Yan tümcesi veri kaynağını belirtir `where` yan tümcesi filtreyi uygular ve `select` yan tümcesi ise döndürülen öğelerin türünü belirtir. Bunlar ve diğer sorgu yan tümceleri içinde ayrıntılı olarak ele alınmıştır [LINQ Sorgu ifadeleri](../../../../csharp/programming-guide/linq-query-expressions/index.md) bölümü. Şimdilik önemli nokta, olan [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], sorgu değişkeninin kendisinin hiç eylem almaması ve veri döndürmemesidir. Yalnızca, sonraki noktada sorgu çalıştırıldığında sonuçları üretmek için gerekli olan bilgileri depolar. Sorguları Sahne arkasında nasıl oluşturulduğu hakkında daha fazla bilgi için bkz. [standart sorgu işleçlerine genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
> [!NOTE]
>  Sorgular ayrıca yöntem sözdizimini kullanarak ifade edilebilir. Daha fazla bilgi için [sorgu sözdizimi ve yöntem sözdizimi LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
## <a name="query-execution"></a>Sorgu Yürütme  
  
### <a name="deferred-execution"></a>Ertelenmiş Yürütme  
 Daha önce bahsedildiği gibi sorgu değişkeni sorgu komutlarını yalnızca depolar. Sorgunun gerçek yürütmesi içindeki sorgu değişkeni üzerinde yineleme kadar ertelenmiştir bir `foreach` deyimi. Bu kavram olarak adlandırılır *ertelenmiş yürütme* ve aşağıdaki örnekte gösterilmiştir:  
  
 [!code-csharp[csLinqGettingStarted#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#4)]  
  
 `foreach` Burada sorgu sonuçlarının alındığı deyimi aynı zamanda. Örneğin, önceki sorguya, yineleme değişkeni de `num` her değeri (teker teker) döndürülen sırada tutar.  
  
 Sorgu değişkeninin kendisi asla sorgu sonuçlarını tutmadığından istediğiniz sıklıkta yürütebilirsiniz. Örneğin, ayrı bir uygulama tarafından sürekli olarak güncelleştirilmekte olan bir veritabanı olabilir. Uygulamanızın en son verileri alan bir sorgu oluşturabilir ve her seferinde farklı sonuçlar almak için bazı aralıklarla sürekli olarak yürütebilirsiniz.  
  
### <a name="forcing-immediate-execution"></a>Hemen Yürütmeyi Zorlama  
 Çeşitli kaynak öğeler üzerinde toplama işlevleri gerçekleştiren sorgular önce bu öğeler üzerinde yinelenmelidir. Gibi sorguların örnekleri `Count`, `Max`, `Average`, ve `First`. Bunlar açık bir yürütme `foreach` deyimi sorgu kullanması gerektiğinden `foreach` bir sonuç döndürmek için. Ayrıca sorguların bu türlerinin tek bir değer döndürmediğine dikkat edin bir `IEnumerable` koleksiyonu. Aşağıdaki sorgu kaynak dizideki çift sayıların sayısını döndürür:  
  
 [!code-csharp[csLinqGettingStarted#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#5)]  
  
 Herhangi bir sorgunun hemen yürütülmesini zorlamak ve sonuçlarını önbelleğe kaydetmek için çağırabilirsiniz <xref:System.Linq.Enumerable.ToList%2A> veya <xref:System.Linq.Enumerable.ToArray%2A> yöntemleri.  
  
 [!code-csharp[csLinqGettingStarted#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#6)]  
  
 Koyarak da yürütmeyi zorlayabilirsiniz `foreach` sorgu ifadesinin hemen sonra döngü. Çağırarak ancak `ToList` veya `ToArray` ayrıca tüm veriyi tek koleksiyon nesnesindeki önbelleğe alın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#'de LINQ Kullanmaya Başlama](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
- [İzlenecek yol: Sorguları yazmaC#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)
- [İzlenecek yol: Sorguları yazmaC#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)
- [LINQ Sorgu ifadeleri](../../../../csharp/programming-guide/linq-query-expressions/index.md)
- [foreach, in](../../../../csharp/language-reference/keywords/foreach-in.md)
- [Query Keywords (LINQ)](../../../../csharp/language-reference/keywords/query-keywords.md)
