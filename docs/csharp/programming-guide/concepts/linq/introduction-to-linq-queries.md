---
title: LINQ Sorgularına Giriş (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- deferred execution [LINQ]
- LINQ, queries
- LINQ, deferred execution
- queries [LINQ], about LINQ queries
ms.assetid: 37895c02-268c-41d5-be39-f7d936fa88a8
ms.openlocfilehash: e3439d2e0e0fb8f3126770ec7922f5ae180f781b
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418256"
---
# <a name="introduction-to-linq-queries-c"></a>LINQ Sorgularına Giriş (C#)
*Sorgu* , veri kaynağından veri alan bir ifadedir. Sorgular genellikle özelleştirilmiş bir sorgu dilinde ifade edilir. Çeşitli veri kaynağı türleri için zaman içinde geliştirilmiş farklı diller, örneğin SQL ilişkisel veritabanları için SQL ve XML için XQuery. Bu nedenle, geliştiricilerin desteklemesi gereken her veri kaynağı türü veya veri biçimi için yeni bir sorgu dili öğrenmeleri gerekiyordu. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], çeşitli veri kaynakları ve biçimlerdeki verilerle çalışmaya yönelik tutarlı bir model sunarak bu durumu basitleştirir. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgusunda, her zaman nesneleriyle birlikte çalışmanız gerekir. XML belgeleri, SQL veritabanları, ADO.NET veri kümeleri, .NET koleksiyonları ve [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sağlayıcı kullanılabilir olan diğer herhangi bir biçimde sorgulamak ve dönüştürmek için aynı temel kodlama düzenlerini kullanırsınız.  
  
## <a name="three-parts-of-a-query-operation"></a>Bir Sorgu İşleminin Üç Bölümü  
 Tüm [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu işlemleri üç farklı eylemden oluşur:  
  
1. Veri kaynağını edinin.  
  
2. Sorguyu oluşturun.  
  
3. Sorguyu yürütün.  
  
 Aşağıdaki örnek, bir sorgu işleminin üç bölümünün kaynak kodda nasıl ifade edildiği gösterilmektedir. Örnek, bir tamsayı dizisini kolaylık sağlaması için bir veri kaynağı olarak kullanır; Ancak, aynı kavramlar diğer veri kaynakları için de geçerlidir. Bu örnek, bu konunun geri kalanı boyunca ifade edilir.  
  
 [!code-csharp[CsLINQGettingStarted#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#1)]  
  
 Aşağıdaki çizimde sorgu işleminin tamamı gösterilmektedir. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], sorgunun yürütülmesi sorgunun kendisinden farklıdır; diğer bir deyişle, yalnızca bir sorgu değişkeni oluşturarak herhangi bir veri alınamadınız.  
  
 ![Tüm LINQ sorgu işleminin diyagramı.](./media/introduction-to-linq-queries/linq-query-complete-operation.png)  
  
## <a name="the-data-source"></a>Veri Kaynağı  
 Önceki örnekte, veri kaynağı bir dizi olduğundan, genel <xref:System.Collections.Generic.IEnumerable%601> arabirimini örtülü olarak destekler. Bu olgu, [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]ile sorgulanabilecek anlamına gelir. Bir sorgu `foreach` ifadesinde yürütülür ve `foreach` <xref:System.Collections.IEnumerable> veya <xref:System.Collections.Generic.IEnumerable%601>gerekir. <xref:System.Collections.Generic.IEnumerable%601> destekleyen türler veya genel <xref:System.Linq.IQueryable%601> gibi türetilmiş bir arabirim *sorgulanabilir türler*olarak adlandırılır.  
  
 Sorgulanabilir bir tür, [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] veri kaynağı olarak kullanılmak üzere değişiklik veya özel bir işleme gerektirmez. Kaynak veriler, sorgulanabilir bir tür olarak zaten bellekte değilse, [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sağlayıcı tarafından temsil etmelidir. Örneğin, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bir XML belgesini sorgulanabilir <xref:System.Xml.Linq.XElement> türüne yükler:  
  
 [!code-csharp[CsLINQGettingStarted#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#2)]  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], ilk olarak tasarım zamanında ya da Visual Studio 'daki [Visual Studio 'daki LINQ to SQL araçlarını](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) kullanarak bir nesne ilişkisel eşleme oluşturursunuz. Sorgular nesnelere karşı yazılır ve çalışma zamanında [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] veritabanıyla iletişimi işler. Aşağıdaki örnekte, `Customers` veritabanındaki belirli bir tabloyu temsil eder ve sorgu sonucunun türü <xref:System.Linq.IQueryable%601><xref:System.Collections.Generic.IEnumerable%601>türetilir.  
  
```csharp  
Northwnd db = new Northwnd(@"c:\northwnd.mdf");  
  
// Query for customers in London.  
IQueryable<Customer> custQuery =  
    from cust in db.Customers  
    where cust.City == "London"  
    select cust;  
```  
  
 Belirli veri kaynağı türlerinin nasıl oluşturulacağı hakkında daha fazla bilgi için çeşitli [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sağlayıcılarına yönelik belgelere bakın. Ancak, temel kural çok basittir: [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] veri kaynağı, genel <xref:System.Collections.Generic.IEnumerable%601> arabirimini veya bundan devralan bir arabirimi destekleyen herhangi bir nesnedir.  
  
> [!NOTE]
> Genel olmayan <xref:System.Collections.IEnumerable> arabirimini destekleyen <xref:System.Collections.ArrayList> gibi türler, [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] veri kaynağı olarak da kullanılabilir. Daha fazla bilgi için bkz. [nasıl yapılır: bir ArrayList 'ı LINQ (C#) ile sorgulama](./how-to-query-an-arraylist-with-linq.md).  
  
## <a name="query"></a>Sorgu  
 Sorgu, veri kaynağından veya kaynaklardan alınacak bilgileri belirtir. İsteğe bağlı olarak, bir sorgu döndürülmeden önce bu bilgilerin nasıl sıralanması, gruplandırılacağı ve şekillendirilmiş olması gerektiğini de belirtir. Sorgu bir sorgu değişkeninde depolanır ve sorgu ifadesiyle başlatılır. Sorguları C# yazmayı kolaylaştırmak için yeni sorgu söz dizimini sunmuştur.  
  
 Önceki örnekteki sorgu, tamsayı dizisindeki tüm çift sayıları döndürür. Sorgu ifadesi üç yan tümce içerir: `from`, `where` ve `select`. (SQL hakkında bilginiz varsa, yan tümcelerinin sıralamasını SQL 'deki siparişten tersine çevrilmiş olduğunu fark etmiş olursunuz.) `from` yan tümcesi veri kaynağını belirtir, `where` yan tümcesi filtreyi uygular ve `select` yan tümcesi döndürülen öğelerin türünü belirtir. Bunlar ve diğer sorgu yan tümceleri, [LINQ sorgu ifadeleri](../../../linq/index.md) bölümünde ayrıntılı olarak ele alınmıştır. Şimdilik, önemli nokta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], sorgu değişkeninin kendisi hiçbir eylemde bulunmaz ve veri döndürmez. Yalnızca sorgu daha sonraki bir noktada yürütüldüğünde sonuçları üretmek için gereken bilgileri depolar. Sorguların arka planda nasıl oluşturulduğu hakkında daha fazla bilgi için bkz. [Standart sorgu Işleçlerine genel bakışC#()](./standard-query-operators-overview.md).  
  
> [!NOTE]
> Sorgular, yöntem sözdizimi kullanılarak da ifade edilebilir. Daha fazla bilgi için bkz. [LINQ 'Te sorgu sözdizimi ve Yöntem sözdizimi](./query-syntax-and-method-syntax-in-linq.md).  
  
## <a name="query-execution"></a>Sorgu Yürütme  
  
### <a name="deferred-execution"></a>Ertelenmiş Yürütme  
 Daha önce belirtildiği gibi, sorgu değişkeni yalnızca sorgu komutlarını depolar. Sorgunun gerçek yürütmesi, bir `foreach` deyimindeki sorgu değişkeni üzerinde yineleme yapana kadar ertelenir. Bu kavram *ertelenmiş yürütme* olarak adlandırılır ve aşağıdaki örnekte gösterilmiştir:  
  
 [!code-csharp[csLinqGettingStarted#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#4)]  
  
 `foreach` deyimde sorgu sonuçlarının alındığı yerdir. Örneğin, önceki sorguda, yineleme `num` değişkeni, döndürülen dizideki her bir değeri (bir kez) barındırır.  
  
 Sorgu değişkeni hiçbir zaman sorgu sonuçlarını içermediğinden, onu istediğiniz sıklıkta yürütebilirsiniz. Örneğin, ayrı bir uygulama tarafından sürekli olarak güncelleştirilmekte olan bir veritabanınız olabilir. Uygulamanızda, en son verileri alan bir sorgu oluşturabilir ve her seferinde farklı sonuçlar almak için bir aralıkta tekrar tekrar çalıştırabilirsiniz.  
  
### <a name="forcing-immediate-execution"></a>Hemen Yürütmeyi Zorlama  
 Bir kaynak öğe aralığı üzerinde toplama işlevleri gerçekleştiren sorgular önce bu öğeler üzerinde yineleme olmalıdır. Bu tür sorgulara örnek olarak `Count`, `Max`, `Average`ve `First`verilebilir. Bu, sorgunun kendisi bir sonuç döndürmek için `foreach` kullanması gerektiğinden açık bir `foreach` deyimleri olmadan yürütülür. Ayrıca, bu sorgu türlerinin `IEnumerable` bir koleksiyon değil tek bir değer döndürdüğüne de göz önünde. Aşağıdaki sorgu, kaynak dizideki Çift sayıların sayısını döndürür:  
  
 [!code-csharp[csLinqGettingStarted#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#5)]  
  
 Herhangi bir sorgunun hemen yürütülmesini zorlamak ve sonuçlarını önbelleğe almak için <xref:System.Linq.Enumerable.ToList%2A> veya <xref:System.Linq.Enumerable.ToArray%2A> yöntemlerini çağırabilirsiniz.  
  
 [!code-csharp[csLinqGettingStarted#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#6)]  
  
 Ayrıca, `foreach` döngüsünü sorgu ifadesinden hemen sonra yerleştirerek yürütmeye zorlayabilirsiniz. Ancak, `ToList` veya `ToArray` çağırarak, tüm verileri tek bir koleksiyon nesnesi içinde de önbelleğe alabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#'de LINQ Kullanmaya Başlama](/dotnet/csharp/programming-guide/concepts/linq/)
- [İzlenecek yol: sorguları yazmaC#](./walkthrough-writing-queries-linq.md)
- [LINQ sorgu Ifadeleri](../../../linq/index.md)
- [foreach, in](../../../language-reference/keywords/foreach-in.md)
- [Sorgu anahtar sözcükleri (LINQ)](../../../language-reference/keywords/query-keywords.md)
