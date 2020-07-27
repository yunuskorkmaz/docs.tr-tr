---
title: LINQ Sorgularına Giriş (C#)
description: LINQ çeşitli veri kaynakları ve biçimlerdeki veriler üzerinde sorgular için tutarlı bir model sunar. LINQ sorgusunda, her zaman nesneleriyle birlikte çalışmanız gerekir.
ms.date: 07/20/2015
helpviewer_keywords:
- deferred execution [LINQ]
- LINQ, queries
- LINQ, deferred execution
- queries [LINQ], about LINQ queries
ms.assetid: 37895c02-268c-41d5-be39-f7d936fa88a8
ms.openlocfilehash: ce878dc255d2502f0594626b294393c399c932e5
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165830"
---
# <a name="introduction-to-linq-queries-c"></a>LINQ Sorgularına Giriş (C#)
*Sorgu* , veri kaynağından veri alan bir ifadedir. Sorgular genellikle özelleştirilmiş bir sorgu dilinde ifade edilir. Çeşitli veri kaynağı türleri için zaman içinde geliştirilmiş farklı diller, örneğin SQL ilişkisel veritabanları için SQL ve XML için XQuery. Bu nedenle, geliştiricilerin desteklemesi gereken her veri kaynağı türü veya veri biçimi için yeni bir sorgu dili öğrenmeleri gerekiyordu. LINQ, çeşitli veri kaynakları ve biçimlerdeki verilerle çalışmaya yönelik tutarlı bir model sunarak bu durumu basitleştirir. LINQ sorgusunda, her zaman nesneleriyle birlikte çalışmanız gerekir. XML belgeleri, SQL veritabanları, ADO.NET veri kümeleri, .NET koleksiyonları ve bir LINQ sağlayıcısının kullanılabildiği diğer biçimdeki verileri sorgulamak ve dönüştürmek için aynı temel kodlama düzenlerini kullanırsınız.  
  
## <a name="three-parts-of-a-query-operation"></a>Bir Sorgu İşleminin Üç Bölümü  
 Tüm LINQ sorgu işlemleri üç farklı eylemden oluşur:  
  
1. Veri kaynağını edinin.  
  
2. Sorguyu oluşturun.  
  
3. Sorguyu çalıştırın.  
  
 Aşağıdaki örnek, bir sorgu işleminin üç bölümünün kaynak kodda nasıl ifade edildiği gösterilmektedir. Örnek, bir tamsayı dizisini kolaylık sağlaması için bir veri kaynağı olarak kullanır; Ancak, aynı kavramlar diğer veri kaynakları için de geçerlidir. Bu örnek, bu konunun geri kalanı boyunca ifade edilir.  
  
 [!code-csharp[CsLINQGettingStarted#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#1)]  
  
 Aşağıdaki çizimde sorgu işleminin tamamı gösterilmektedir. LINQ 'da sorgunun yürütülmesi sorgunun kendisinden farklıdır. Diğer bir deyişle, yalnızca bir sorgu değişkeni oluşturarak herhangi bir veri alınmadı.  
  
 ![Tüm LINQ sorgu işleminin diyagramı.](./media/introduction-to-linq-queries/linq-query-complete-operation.png)  
  
## <a name="the-data-source"></a>Veri Kaynağı  
 Önceki örnekte, veri kaynağı bir dizi olduğundan, genel arabirimi örtülü olarak destekler <xref:System.Collections.Generic.IEnumerable%601> . Bu olgu, LINQ ile sorgulanabilecek anlamına gelir. Bir sorgu, bir ifadede yürütülür `foreach` ve `foreach` <xref:System.Collections.IEnumerable> ya da gerektirir <xref:System.Collections.Generic.IEnumerable%601> . Destekleyen türler <xref:System.Collections.Generic.IEnumerable%601> veya genel gibi türetilmiş bir arabirim <xref:System.Linq.IQueryable%601> *sorgulanabilir türler*olarak adlandırılır.  
  
 Sorgulanabilir bir tür, LINQ veri kaynağı olarak kullanılacak değişiklik veya özel bir işleme gerektirmez. Kaynak veriler, sorgulanabilir bir tür olarak zaten bellekte değilse, LINQ sağlayıcısı bunu temsil etmelidir. Örneğin, bir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML belgesini sorgulanabilir bir <xref:System.Xml.Linq.XElement> türe yükler:  
  
 [!code-csharp[CsLINQGettingStarted#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#2)]  
  
 İle [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] , önce tasarım zamanında ya da [Visual Studio 'Daki LINQ to SQL araçlarını](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)kullanarak bir nesne ilişkisel eşleme oluşturursunuz. Sorgular nesnelere karşı yazılır ve çalışma zamanında [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] veritabanıyla iletişimi işler. Aşağıdaki örnekte, `Customers` veritabanında belirli bir tabloyu ve sorgu sonucunun türünü temsil eder <xref:System.Linq.IQueryable%601> <xref:System.Collections.Generic.IEnumerable%601> .  
  
```csharp  
Northwnd db = new Northwnd(@"c:\northwnd.mdf");  
  
// Query for customers in London.  
IQueryable<Customer> custQuery =  
    from cust in db.Customers  
    where cust.City == "London"  
    select cust;  
```  
  
 Belirli türde veri kaynakları oluşturma hakkında daha fazla bilgi için bkz. çeşitli LINQ sağlayıcıları için belgeler. Ancak, temel kural çok basittir: LINQ veri kaynağı, genel <xref:System.Collections.Generic.IEnumerable%601> arabirimi veya bundan devralan bir arabirimi destekleyen herhangi bir nesnedir.  
  
> [!NOTE]
> <xref:System.Collections.ArrayList>Genel olmayan arabirimi destekleyen türler <xref:System.Collections.IEnumerable> , LINQ veri kaynağı olarak da kullanılabilir. Daha fazla bilgi için bkz. [LINQ Ile ArrayList 'i sorgulama (C#)](./how-to-query-an-arraylist-with-linq.md).  
  
## <a name="the-query"></a><a name="query"></a>Sorgu  
 Sorgu, veri kaynağından veya kaynaklardan alınacak bilgileri belirtir. İsteğe bağlı olarak, bir sorgu döndürülmeden önce bu bilgilerin nasıl sıralanması, gruplandırılacağı ve şekillendirilmiş olması gerektiğini de belirtir. Sorgu bir sorgu değişkeninde depolanır ve sorgu ifadesiyle başlatılır. Sorgu yazmanın daha kolay olması için C# yeni sorgu söz dizimini sunmuştur.  
  
 Önceki örnekteki sorgu, tamsayı dizisindeki tüm çift sayıları döndürür. Sorgu ifadesi üç yan tümce içerir: `from` `where` ve `select` . (SQL hakkında bilginiz varsa, yan tümcelerinin sıralamasını SQL 'deki siparişten tersine çevrilmiş olduğunu fark etmiş olursunuz.) `from`Yan tümce veri kaynağını belirtir, `where` yan tümce filtreyi uygular ve `select` yan tümce döndürülen öğelerin türünü belirtir. Bunlar ve diğer sorgu yan tümceleri, [Dil tümleşik sorgu (LINQ)](../../../linq/index.md) bölümünde ayrıntılı olarak ele alınmıştır. Şimdilik, önemli nokta LINQ içinde, sorgu değişkeninin kendisi hiçbir eylemde bulunmaz ve veri döndürmez. Yalnızca sorgu daha sonraki bir noktada yürütüldüğünde sonuçları üretmek için gereken bilgileri depolar. Sorguların arka planda nasıl oluşturulduğu hakkında daha fazla bilgi için bkz. [Standart sorgu Işleçlerine genel bakış (C#)](./standard-query-operators-overview.md).  
  
> [!NOTE]
> Sorgular, yöntem sözdizimi kullanılarak da ifade edilebilir. Daha fazla bilgi için bkz. [LINQ 'Te sorgu sözdizimi ve Yöntem sözdizimi](./query-syntax-and-method-syntax-in-linq.md).  
  
## <a name="query-execution"></a>Sorgu Yürütme  
  
### <a name="deferred-execution"></a>Ertelenmiş Yürütme  
 Daha önce belirtildiği gibi, sorgu değişkeni yalnızca sorgu komutlarını depolar. Sorgunun gerçek yürütmesi, bir deyimindeki sorgu değişkeni üzerinde yineleme yapana kadar ertelenir `foreach` . Bu kavram *ertelenmiş yürütme* olarak adlandırılır ve aşağıdaki örnekte gösterilmiştir:  
  
 [!code-csharp[csLinqGettingStarted#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#4)]  
  
 `foreach`İfade ayrıca sorgu sonuçlarının alındığı yerdir. Örneğin, önceki sorguda, yineleme değişkeni `num` döndürülen dizide her bir değeri (bir kerede bir kez) barındırır.  
  
 Sorgu değişkeni hiçbir zaman sorgu sonuçlarını içermediğinden, onu istediğiniz sıklıkta yürütebilirsiniz. Örneğin, ayrı bir uygulama tarafından sürekli olarak güncelleştirilmekte olan bir veritabanınız olabilir. Uygulamanızda, en son verileri alan bir sorgu oluşturabilir ve her seferinde farklı sonuçlar almak için bir aralıkta tekrar tekrar çalıştırabilirsiniz.  
  
### <a name="forcing-immediate-execution"></a>Hemen Yürütmeyi Zorlama  
 Bir kaynak öğe aralığı üzerinde toplama işlevleri gerçekleştiren sorgular önce bu öğeler üzerinde yineleme olmalıdır. Bu tür sorgulara örnekler, `Count` , `Max` `Average` ve `First` . Bu `foreach` , sorgunun kendisi `foreach` bir sonuç döndürmek için kullanması gerektiği için açık bir ifade olmadan yürütülür. Ayrıca, bu tür sorguların bir koleksiyon değil tek bir değer döndürdüğüne de not edin `IEnumerable` . Aşağıdaki sorgu, kaynak dizideki Çift sayıların sayısını döndürür:  
  
 [!code-csharp[csLinqGettingStarted#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#5)]  
  
 Herhangi bir sorgunun hemen yürütülmesini zorlamak ve sonuçlarını önbelleğe almak için, <xref:System.Linq.Enumerable.ToList%2A> veya <xref:System.Linq.Enumerable.ToArray%2A> yöntemlerini çağırabilirsiniz.  
  
 [!code-csharp[csLinqGettingStarted#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#6)]  
  
 Ayrıca, `foreach` döngüyü sorgu ifadesinden hemen sonra yerleştirerek yürütmeye zorlayabilirsiniz. Ancak, çağırarak `ToList` veya `ToArray` tek bir koleksiyon nesnesindeki tüm verileri de önbelleğe alabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#'de LINQ'e Başlarken](index.md)
- [İzlenecek yol: C 'de sorgu yazma #](./walkthrough-writing-queries-linq.md)
- [Dil ile Tümleşik Sorgu (LINQ)](../../../linq/index.md)
- [foreach, in](../../../language-reference/keywords/foreach-in.md)
- [Sorgu anahtar sözcükleri (LINQ)](../../../language-reference/keywords/query-keywords.md)
