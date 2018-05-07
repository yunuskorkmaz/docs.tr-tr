---
title: LINQ Sorgularına Giriş (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- deferred execution [LINQ]
- LINQ, queries
- LINQ, deferred execution
- queries [LINQ], about LINQ queries
ms.assetid: 37895c02-268c-41d5-be39-f7d936fa88a8
ms.openlocfilehash: f74b762532f0fb2795625185e59360cdfb76b124
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="introduction-to-linq-queries-c"></a>LINQ Sorgularına Giriş (C#)
A *sorgu* bir veri kaynağından veri alır bir ifadedir. Sorguları genellikle bir özel sorgu dili ifade edilir. Farklı diller, zaman içinde çeşitli veri kaynakları, örneğin ilişkisel veritabanları için SQL ve XQuery XML için geliştirilmiştir. Bu nedenle, geliştiricilerin her veri kaynağı veya desteklemesi gerekir veri biçimi türü için yeni bir sorgu dili öğrenin gerekirdi. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] Bu durum, çeşitli veri kaynakları ve biçimleri arasında verilerle çalışmak için tutarlı bir model sunarak basitleştirir. İçinde bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu nesneler her zaman çalıştığınız. XML belgeleri, SQL veritabanları, verileri sorgulamak veya dönüştürme aynı temel kodlama modelleri kullanmanıza [!INCLUDE[vstecado](~/includes/vstecado-md.md)] veri kümeleri, .NET koleksiyonları ve başka bir biçime kendisi için bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sağlayıcısı kullanılabilir.  
  
## <a name="three-parts-of-a-query-operation"></a>Bir Sorgu İşleminin Üç Bölümü  
 Tüm [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu işlemleri üç ayrı eylemi oluşur:  
  
1.  Veri kaynağı edinin.  
  
2.  Sorgu oluşturun.  
  
3.  Sorgu yürütün.  
  
 Aşağıdaki örnek, bir sorgu işlemi üç bölümden kaynak kodunda nasıl belirtilmiştir gösterir. Örnek bir tamsayı dizisi kolaylık sağlamak için bir veri kaynağı olarak kullanır; Ancak, aynı kavramlar diğer veri kaynakları için de geçerlidir. Bu örnek için bu konunun geri kalanında geçer.  
  
 [!code-csharp[CsLINQGettingStarted#1](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/introduction-to-linq-queries_1.cs)]  
  
 Aşağıdaki resimde, tam bir sorgu işlemi gösterilmektedir. İçinde [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgunun yürütülmesi, sorgudan farklıdır; diğer bir deyişle, herhangi bir veri yalnızca bir sorgu değişkeni oluşturarak alınan değil.  
  
 ![LINQ Sorgu işlemini tamamlama](../../../../csharp/programming-guide/concepts/linq/media/linq_query.png "LINQ_Query")  
  
## <a name="the-data-source"></a>Veri Kaynağı  
 Veri kaynağı bir dizi olduğundan önceki örnekte örtük olarak genel destekliyorsa <xref:System.Collections.Generic.IEnumerable%601> arabirimi. Bunu sorgulanan ile bu olgu anlamına gelir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]. Bir sorgu yürütülür bir `foreach` deyimi, ve `foreach` gerektirir <xref:System.Collections.IEnumerable> veya <xref:System.Collections.Generic.IEnumerable%601>. Türlerini destekleyen <xref:System.Collections.Generic.IEnumerable%601> veya türetilmiş bir arabirim genel gibi <xref:System.Linq.IQueryable%601> denir *sorgulanabilir türleri*.  
  
 Sorgulanabilir bir tür hiçbir değişiklik ya da olarak hizmet verecek özel işleme gerektiren bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] veri kaynağı. Veri kaynağını sorgulanabilir bir tür olarak bellekte değilse [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sağlayıcı temsil etmesi gerekir, bu nedenle. Örneğin, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bir XML belgesi sorgulanabilir yükler <xref:System.Xml.Linq.XElement> türü:  
  
 [!code-csharp[CsLINQGettingStarted#2](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/introduction-to-linq-queries_2.cs)]  
  
 İle [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], bir nesne ilişkisel tasarım zamanında el ile veya kullanarak eşleme oluşturduğunuz ilk [LINQ-SQL Visual Studio Araçları](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) Visual Studio. Sorgularınızın nesneleri karşı ve çalışma zamanında yazma [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] veritabanı ile iletişim işler. Aşağıdaki örnekte, `Customers` veritabanı ve sorgunun sonuç türü belirli bir tabloda temsil eden <xref:System.Linq.IQueryable%601>, türetilen <xref:System.Collections.Generic.IEnumerable%601>.  
  
```csharp  
Northwnd db = new Northwnd(@"c:\northwnd.mdf");  
  
// Query for customers in London.  
IQueryable<Customer> custQuery =  
    from cust in db.Customers  
    where cust.City == "London"  
    select cust;  
```  
  
 Belirli veri kaynağı türleri oluşturma hakkında daha fazla bilgi için çeşitli belgelerine bakın [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sağlayıcıları. Ancak, temel kural çok basittir: bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] veri kaynağıdır genel destekleyen herhangi bir nesne <xref:System.Collections.Generic.IEnumerable%601> arabirimi veya devralan bir arabirim.  
  
> [!NOTE]
>  Gibi türleri <xref:System.Collections.ArrayList> genel olmayan destekleyen <xref:System.Collections.IEnumerable> arabirimi de kullanılabilir olarak bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] veri kaynağı. Daha fazla bilgi için bkz: [nasıl yapılır: LINQ (C#) ile ArrayList sorgulama](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md).  
  
##  <a name="query"></a> Sorgu  
 Sorgu veri kaynağı veya kaynakları almak için hangi bilgilerin belirtir. İsteğe bağlı olarak, bir sorgu nasıl bu bilgileri sıralanmış, gruplandırılmış ve, döndürülmeden önce şeklinde belirtir. Bir sorgu bir sorgu değişkende depolanır ve bir sorgu ifadesi ile başlatıldı. Sorguları yazmayı kolaylaştırmak için C# yeni sorgu söz dizimi anlatılmıştır.  
  
 Önceki örnekte sorgu, tamsayı dizisinden tüm çift sayıları döndürür. Sorgu ifadesi üç yan tümcesi içeren: `from`, `where` ve `select`. (SQL ile bilginiz varsa, yan tümcelerini sıralama SQL sipariş tersine olduğunu fark etmiş.) `from` Yan tümcesi veri kaynağını belirtir `where` yan tümcesi filtre uygular ve `select` yan tümcesi döndürülen öğeler türünü belirtir. Bunlar ve diğer sorgu yan tümceleri içinde ayrıntılı olarak ele alınmıştır [LINQ Sorgu ifadeleri](../../../../csharp/programming-guide/linq-query-expressions/index.md) bölümü. Şimdilik, önemli giriş noktasıdır [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], sorgu değişkeni hiçbir eylemde bulunmaz ve hiçbir veri döndürür. Yalnızca, daha sonraki bir noktada sorgu çalıştırıldığında sonuçları üretmek için gerekli olan bilgileri depolar. Sorguları arka planda nasıl oluşturulur hakkında daha fazla bilgi için bkz: [standart sorgu işleçlerine genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
> [!NOTE]
>  Sorguları yöntem sözdizimi kullanılarak da belirtilebilir. Daha fazla bilgi için bkz: [sorgu sözdizimi ve yöntem sözdizimi LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
## <a name="query-execution"></a>Sorgu Yürütme  
  
### <a name="deferred-execution"></a>Ertelenmiş Yürütme  
 Daha önce belirtildiği gibi sorgu değişkeni sorgu komutları yalnızca depolar. Gerçek sorgunun yürütülmesi, sorgu değişkeninde üzerinden yineleme kadar ertelenir bir `foreach` deyimi. Bu kavram olarak adlandırılır *yürütme ertelenmiş* ve aşağıdaki örnekte gösterilmiştir:  
  
 [!code-csharp[csLinqGettingStarted#4](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/introduction-to-linq-queries_3.cs)]  
  
 `foreach` Açıklamadır de sorgu sonuçları burada alınır. Örneğin, sorguda önceki yineleme değişkeni `num` döndürülen dizideki her değeri (birer birer) tutar.  
  
 Sorgu değişkeni hiçbir zaman sorgu sonuçlarını tutan çünkü istediğiniz sıklıkta yürütebilir. Örneğin, ayrı bir uygulama tarafından sürekli güncelleştirilen bir veritabanı olabilir. Uygulamanızın, en son verileri alan bir sorgu oluşturabilirsiniz ve her zaman farklı sonuçlar almak için bazı aralıkla art arda yürütebilir.  
  
### <a name="forcing-immediate-execution"></a>Hemen Yürütmeyi Zorlama  
 Kaynak öğelerin aralığında toplama işlevleri gerçekleştiren sorguları önce bu öğeleri yineleme gerekir. Bu tür sorgular örnekleri `Count`, `Max`, `Average`, ve `First`. Bunlar açık bir yürütün `foreach` deyimi sorgu kullanmanız gerekir çünkü `foreach` bir sonuç dönebilmek için. Ayrıca bu sorgu türleri tek bir değer döndürme değil olduğunu unutmayın bir `IEnumerable` koleksiyonu. Aşağıdaki sorguyu kaynak dizisinde çift sayıları sayımını döndürür:  
  
 [!code-csharp[csLinqGettingStarted#5](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/introduction-to-linq-queries_4.cs)]  
  
 Herhangi bir sorgu hemen yürütülmesi zorlamak ve sonuçlarını önbelleğe almasını çağırabilirsiniz <xref:System.Linq.Enumerable.ToList%2A> veya <xref:System.Linq.Enumerable.ToArray%2A> yöntemleri.  
  
 [!code-csharp[csLinqGettingStarted#6](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/introduction-to-linq-queries_5.cs)]  
  
 Ayrıca, koyarak yürütme zorlayabilirsiniz `foreach` döngü sorgu ifadesi hemen sonra. Ancak, çağıran tarafından `ToList` veya `ToArray` ayrıca bir tek koleksiyon nesnesinde tüm verileri önbelleğe alma.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C#'de LINQ Kullanmaya Başlama](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [İzlenecek yol: Sorguları C# ile yazma](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)  
 [İzlenecek yol: Sorguları C# ile yazma](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)  
 [LINQ Sorgu ifadeleri](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [foreach, in](../../../../csharp/language-reference/keywords/foreach-in.md)  
 [Sorgu anahtar sözcükleri (LINQ)](../../../../csharp/language-reference/keywords/query-keywords.md)
