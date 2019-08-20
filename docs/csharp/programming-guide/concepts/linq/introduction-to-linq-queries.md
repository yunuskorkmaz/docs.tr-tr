---
title: LINQ Sorgularına Giriş (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- deferred execution [LINQ]
- LINQ, queries
- LINQ, deferred execution
- queries [LINQ], about LINQ queries
ms.assetid: 37895c02-268c-41d5-be39-f7d936fa88a8
ms.openlocfilehash: a4ad928c479c971e5cf7191b95a3ed4d80bb1e57
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592211"
---
# <a name="introduction-to-linq-queries-c"></a>LINQ Sorgularına Giriş (C#)
*Sorgu* , veri kaynağından veri alan bir ifadedir. Sorgular genellikle özelleştirilmiş bir sorgu dilinde ifade edilir. Çeşitli veri kaynağı türleri için zaman içinde geliştirilmiş farklı diller, örneğin SQL ilişkisel veritabanları için SQL ve XML için XQuery. Bu nedenle, geliştiricilerin desteklemesi gereken her veri kaynağı türü veya veri biçimi için yeni bir sorgu dili öğrenmeleri gerekiyordu. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]çeşitli veri kaynakları ve biçimlerdeki verilerle çalışmaya yönelik tutarlı bir model sunarak bu durumu basitleştirir. Bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorguda, her zaman nesneleriyle birlikte çalışmanız gerekir. XML belgeleri, SQL veritabanları, ADO.NET veri kümeleri, .net koleksiyonları ve bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sağlayıcının kullanılabildiği diğer biçimdeki verileri sorgulamak ve dönüştürmek için aynı temel kodlama düzenlerini kullanırsınız.  
  
## <a name="three-parts-of-a-query-operation"></a>Bir Sorgu İşleminin Üç Bölümü  
 Tüm [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu işlemleri üç farklı eylemden oluşur:  
  
1. Veri kaynağını edinin.  
  
2. Sorguyu oluşturun.  
  
3. Sorguyu yürütün.  
  
 Aşağıdaki örnek, bir sorgu işleminin üç bölümünün kaynak kodda nasıl ifade edildiği gösterilmektedir. Örnek, bir tamsayı dizisini kolaylık sağlaması için bir veri kaynağı olarak kullanır; Ancak, aynı kavramlar diğer veri kaynakları için de geçerlidir. Bu örnek, bu konunun geri kalanı boyunca ifade edilir.  
  
 [!code-csharp[CsLINQGettingStarted#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#1)]  
  
 Aşağıdaki çizimde sorgu işleminin tamamı gösterilmektedir. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] Sorgunun yürütülmesi sorgunun kendisinden farklıdır; diğer bir deyişle, yalnızca bir sorgu değişkeni oluşturarak herhangi bir veri alınamadınız.  
  
 ![Tüm LINQ sorgu işleminin diyagramı.](./media/introduction-to-linq-queries/linq-query-complete-operation.png)  
  
## <a name="the-data-source"></a>Veri Kaynağı  
 Önceki örnekte, veri kaynağı bir dizi olduğundan, genel <xref:System.Collections.Generic.IEnumerable%601> arabirimi örtülü olarak destekler. Bu olgu, ile [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]sorgulanabilecek anlamına gelir. `foreach` Bir sorgu, bir ifadede yürütülür ve `foreach` ya da <xref:System.Collections.Generic.IEnumerable%601>gerektirir <xref:System.Collections.IEnumerable> . Destekleyen <xref:System.Collections.Generic.IEnumerable%601> türler veya genel <xref:System.Linq.IQueryable%601> gibi türetilmiş bir arabirim *sorgulanabilir türler*olarak adlandırılır.  
  
 Sorgulanabilir bir tür, veri kaynağı olarak kullanılacak değişiklik veya özel bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] işleme gerektirmez. Kaynak veriler, sorgulanabilir bir tür olarak zaten bellekte değilse, [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sağlayıcı tarafından temsil etmelidir. Örneğin, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bir XML belgesini sorgulanabilir <xref:System.Xml.Linq.XElement> bir türe yükler:  
  
 [!code-csharp[CsLINQGettingStarted#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#2)]  
  
 İle [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], ilk olarak tasarım zamanında ya da Visual Studio 'daki [Visual Studio 'daki LINQ to SQL araçlarını](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) kullanarak bir nesne ilişkisel eşleme oluşturursunuz. Sorgular nesnelere karşı yazılır ve çalışma [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] zamanında veritabanıyla iletişimi işler. Aşağıdaki örnekte, `Customers` veritabanında belirli bir tabloyu ve sorgu <xref:System.Linq.IQueryable%601>sonucunun <xref:System.Collections.Generic.IEnumerable%601>türünü temsil eder.  
  
```csharp  
Northwnd db = new Northwnd(@"c:\northwnd.mdf");  
  
// Query for customers in London.  
IQueryable<Customer> custQuery =  
    from cust in db.Customers  
    where cust.City == "London"  
    select cust;  
```  
  
 Belirli veri kaynağı türlerinin nasıl oluşturulacağı hakkında daha fazla bilgi için çeşitli [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sağlayıcılar için belgelere bakın. Ancak, temel kural çok basittir: [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] veri kaynağı, genel <xref:System.Collections.Generic.IEnumerable%601> arabirimi veya bundan devralan bir arabirimi destekleyen herhangi bir nesnedir.  
  
> [!NOTE]
>  Genel olmayan arabirimi destekleyen türler, [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] veri kaynağı olarak da kullanılabilir. <xref:System.Collections.IEnumerable> <xref:System.Collections.ArrayList> Daha fazla bilgi için [nasıl yapılır: LINQ (C#)](./how-to-query-an-arraylist-with-linq.md)ile ArrayList 'i sorgulayın.  
  
## <a name="query"></a>Sorgu  
 Sorgu, veri kaynağından veya kaynaklardan alınacak bilgileri belirtir. İsteğe bağlı olarak, bir sorgu döndürülmeden önce bu bilgilerin nasıl sıralanması, gruplandırılacağı ve şekillendirilmiş olması gerektiğini de belirtir. Sorgu bir sorgu değişkeninde depolanır ve sorgu ifadesiyle başlatılır. Sorguları C# yazmayı kolaylaştırmak için yeni sorgu söz dizimini sunmuştur.  
  
 Önceki örnekteki sorgu, tamsayı dizisindeki tüm çift sayıları döndürür. Sorgu ifadesi üç yan tümce içerir: `from` `where` ve `select`. (SQL hakkında bilginiz varsa, yan tümcelerinin sıralamasını SQL 'deki siparişten tersine çevrilmiş olduğunu fark etmiş olursunuz.) Yan tümce veri kaynağını belirtir `where` , yan tümce filtreyi uygular ve `select` yan tümce döndürülen öğelerin türünü belirtir. `from` Bunlar ve diğer sorgu yan tümceleri, [LINQ sorgu ifadeleri](../../linq-query-expressions/index.md) bölümünde ayrıntılı olarak ele alınmıştır. Şimdilik, önemli nokta içinde [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], sorgu değişkeninin kendisi hiçbir eylemde bulunmaz ve veri döndürmez. Yalnızca sorgu daha sonraki bir noktada yürütüldüğünde sonuçları üretmek için gereken bilgileri depolar. Sorguların arka planda nasıl oluşturulduğu hakkında daha fazla bilgi için bkz. [Standart sorgu Işleçlerine genel bakışC#()](./standard-query-operators-overview.md).  
  
> [!NOTE]
>  Sorgular, yöntem sözdizimi kullanılarak da ifade edilebilir. Daha fazla bilgi için bkz. [LINQ 'Te sorgu sözdizimi ve Yöntem sözdizimi](./query-syntax-and-method-syntax-in-linq.md).  
  
## <a name="query-execution"></a>Sorgu Yürütme  
  
### <a name="deferred-execution"></a>Ertelenmiş Yürütme  
 Daha önce belirtildiği gibi, sorgu değişkeni yalnızca sorgu komutlarını depolar. Sorgunun gerçek yürütmesi, bir `foreach` deyimindeki sorgu değişkeni üzerinde yineleme yapana kadar ertelenir. Bu kavram *ertelenmiş yürütme* olarak adlandırılır ve aşağıdaki örnekte gösterilmiştir:  
  
 [!code-csharp[csLinqGettingStarted#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#4)]  
  
 `foreach` İfade ayrıca sorgu sonuçlarının alındığı yerdir. Örneğin, önceki sorguda, yineleme değişkeni `num` döndürülen dizide her bir değeri (bir kerede bir kez) barındırır.  
  
 Sorgu değişkeni hiçbir zaman sorgu sonuçlarını içermediğinden, onu istediğiniz sıklıkta yürütebilirsiniz. Örneğin, ayrı bir uygulama tarafından sürekli olarak güncelleştirilmekte olan bir veritabanınız olabilir. Uygulamanızda, en son verileri alan bir sorgu oluşturabilir ve her seferinde farklı sonuçlar almak için bir aralıkta tekrar tekrar çalıştırabilirsiniz.  
  
### <a name="forcing-immediate-execution"></a>Hemen Yürütmeyi Zorlama  
 Bir kaynak öğe aralığı üzerinde toplama işlevleri gerçekleştiren sorgular önce bu öğeler üzerinde yineleme olmalıdır. Bu `Count`tür sorgulara `Max` `First`örnekler,, ve. `Average` Bu, sorgunun kendisi bir `foreach` sonuç döndürmek için kullanması `foreach` gerektiği için açık bir ifade olmadan yürütülür. Ayrıca, bu tür sorguların bir `IEnumerable` koleksiyon değil tek bir değer döndürdüğüne de not edin. Aşağıdaki sorgu, kaynak dizideki Çift sayıların sayısını döndürür:  
  
 [!code-csharp[csLinqGettingStarted#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#5)]  
  
 Herhangi bir sorgunun hemen yürütülmesini zorlamak ve sonuçlarını önbelleğe almak için, <xref:System.Linq.Enumerable.ToList%2A> veya <xref:System.Linq.Enumerable.ToArray%2A> yöntemlerini çağırabilirsiniz.  
  
 [!code-csharp[csLinqGettingStarted#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#6)]  
  
 Ayrıca, `foreach` döngüyü sorgu ifadesinden hemen sonra yerleştirerek yürütmeye zorlayabilirsiniz. Ancak, çağırarak `ToList` veya `ToArray` tek bir koleksiyon nesnesindeki tüm verileri de önbelleğe alabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#'de LINQ Kullanmaya Başlama](./getting-started-with-linq.md)
- [İzlenecek yol: Sorguları yazmaC#](./walkthrough-writing-queries-linq.md)
- [LINQ sorgu Ifadeleri](../../linq-query-expressions/index.md)
- [foreach, in](../../../language-reference/keywords/foreach-in.md)
- [Sorgu anahtar sözcükleri (LINQ)](../../../language-reference/keywords/query-keywords.md)
