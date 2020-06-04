---
title: İlk LINQ Sorgunuzu Yazma
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ queries [Visual Basic]
- LINQ [Visual Basic], writing queries
ms.assetid: 4affb732-3e9b-4479-aa31-1f9bd8183cbe
ms.openlocfilehash: 9d85f9c0390a659e59e372ad949cffdd17715189
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413264"
---
# <a name="writing-your-first-linq-query-visual-basic"></a>İlk LINQ Sorgunuzu Yazma (Visual Basic)
*Sorgu* , veri kaynağından veri alan bir ifadedir. Sorgular adanmış bir sorgu dilinde ifade edilir. Zaman içinde farklı diller, örneğin, ilişkisel veritabanları için SQL ve XML için XQuery gibi farklı türlerde veri kaynakları için geliştirilmiştir. Bu, uygulama geliştiricisinin desteklenen her bir veri kaynağı türü veya veri biçimi için yeni bir sorgu dili öğrenmesini zorunlu kılar.  
  
 Dil ile tümleşik sorgu (LINQ), çeşitli veri kaynakları ve biçimlerdeki verilerle çalışmaya yönelik tutarlı bir model sunarak durumu basitleştirir. LINQ sorgusunda, her zaman nesneleriyle birlikte çalışmanız gerekir. XML belgelerinde, SQL veritabanlarında, ADO.NET veri kümelerinde ve varlıklarda, .NET Framework koleksiyonlarında ve LINQ sağlayıcısının kullanılabildiği diğer tüm kaynak veya biçimdeki verileri sorgulamak ve dönüştürmek için aynı temel kodlama düzenlerini kullanırsınız. Bu belgede temel LINQ sorgularının oluşturulması ve kullanılması için üç aşama açıklanmaktadır.  
  
## <a name="three-stages-of-a-query-operation"></a>Bir Sorgu İşleminin Üç Aşaması  
 LINQ sorgu işlemleri üç eylemden oluşur:  
  
1. Veri kaynağını veya kaynaklarını edinin.  
  
2. Sorguyu oluşturun.  
  
3. Sorguyu çalıştırın.  
  
 LINQ içinde, bir sorgunun yürütülmesi sorgunun oluşturulmasından farklıdır. Yalnızca bir sorgu oluşturarak herhangi bir veri alamazsınız. Bu nokta, bu konunun ilerleyen kısımlarında daha ayrıntılı bir şekilde ele alınmıştır.  
  
 Aşağıdaki örnekte, bir sorgu işleminin üç bölümü gösterilmektedir. Örnek, Gösterim amacıyla uygun bir veri kaynağı olarak bir tamsayılar dizisi kullanır. Ancak, aynı kavramlar diğer veri kaynakları için de geçerlidir.  
  
> [!NOTE]
> [Derleme sayfasında, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), **seçenek çıkarımı seçeneğinin** **Açık**olarak ayarlandığından emin olun.  
  
 [!code-vb[VbLINQFirstQuery#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#1)]  
  
 Çıktı:  
  
 `0 2 4 6`  
  
## <a name="the-data-source"></a>Veri Kaynağı  
 Önceki örnekteki veri kaynağı bir dizi olduğundan, genel arabirimi örtülü olarak destekler <xref:System.Collections.Generic.IEnumerable%601> . Bu aslında bir diziyi bir LINQ sorgusu için veri kaynağı olarak kullanmanıza olanak sağlar. Destekleyen türler <xref:System.Collections.Generic.IEnumerable%601> veya genel gibi türetilmiş bir arabirim <xref:System.Linq.IQueryable%601> *sorgulanabilir türler*olarak adlandırılır.  
  
 Örtük olarak sorgulanabilir bir tür olarak, dizi hiçbir değişiklik veya bir LINQ veri kaynağı olarak kullanılacak özel bir işleme gerektirmez. Aynı şekilde, <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.Generic.List%601> <xref:System.Collections.Generic.Dictionary%602> .NET Framework sınıf kitaplığındaki genel, ve diğer sınıflar da dahil olmak üzere, destekleyen tüm koleksiyon türleri için de geçerlidir.  
  
 Kaynak verileri henüz uygulamadıysanız <xref:System.Collections.Generic.IEnumerable%601> , bu veri kaynağı için *Standart sorgu işleçleri* işlevlerini uygulamak üzere bir LINQ sağlayıcısı gerekir. Örneğin, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XElement> Aşağıdaki örnekte gösterildiği gibi, bir XML belgesini bir sorgulanabilir türe yükleme işini işler. Standart sorgu işleçleri hakkında daha fazla bilgi için bkz. [Standart sorgu Işleçlerine genel bakış (Visual Basic)](standard-query-operators-overview.md).  
  
 [!code-vb[VbLINQFirstQuery#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#2)]  
  
 İle [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] , ilk olarak tasarım zamanında veya Visual Studio 'Daki [Visual studio 'Daki LINQ to SQL araçlarını](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) kullanarak bir nesne ilişkisel eşleme oluşturursunuz. Sorgular nesnelere karşı yazılır ve çalışma zamanında [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] veritabanıyla iletişimi işler. Aşağıdaki örnekte, `customers` veritabanında belirli bir tabloyu temsil eder ve genel ' i <xref:System.Data.Linq.Table%601> destekler <xref:System.Linq.IQueryable%601> .  
  
```vb  
' Create a data source from a SQL table.  
Dim db As New DataContext("C:\Northwind\Northwnd.mdf")  
Dim customers As Table(Of Customer) = db.GetTable(Of Customer)  
```  
  
 Belirli türde veri kaynakları oluşturma hakkında daha fazla bilgi için bkz. çeşitli LINQ sağlayıcıları için belgeler. (Bu sağlayıcıların listesi için bkz. [LINQ (dil Ile tümleşik sorgu)](index.md).) Temel kural basittir: LINQ veri kaynağı, genel <xref:System.Collections.Generic.IEnumerable%601> arabirimi veya bundan devralan bir arabirimi destekleyen herhangi bir nesnedir.  
  
> [!NOTE]
> <xref:System.Collections.ArrayList>Genel olmayan arabirimi destekleyen türler <xref:System.Collections.IEnumerable> , LINQ veri kaynakları olarak da kullanılabilir. Kullanan bir örnek için <xref:System.Collections.ArrayList> bkz. [nasıl yapılır: bir ARRAYLIST 'i LINQ ile sorgulama (Visual Basic)](how-to-query-an-arraylist-with-linq.md).  
  
## <a name="the-query"></a>Sorgu  
 Sorguda, veri kaynağından veya kaynaklardan hangi bilgileri almak istediğinizi belirtirsiniz. Ayrıca, bu bilgilerin döndürülmeden önce nasıl sıralanacağını, gruplanacağını veya yapılandırıldığını belirtme seçeneğiniz de vardır. Sorgu oluşturmayı etkinleştirmek için Visual Basic dilde yeni sorgu söz dizimi eklendi.  
  
 Yürütüldüğünde, aşağıdaki örnekteki sorgu bir tamsayı dizisinden gelen tüm çift sayıları döndürür `numbers` .  
  
 [!code-vb[VbLINQFirstQuery#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#1)]  
  
 Sorgu ifadesi üç yan tümce içerir: `From` , `Where` , ve `Select` . Her sorgu ifadesi yan tümcesinin belirli bir işlevi ve amacı, [temel sorgu işlemlerinde (Visual Basic)](basic-query-operations.md)ele alınmıştır. Daha fazla bilgi için bkz. [sorgular](../../../language-reference/queries/index.md). LINQ 'ta bir sorgu tanımının genellikle bir değişkende depolandığını ve daha sonra yürütüldüğünü unutmayın. Önceki örnekte olduğu gibi sorgu değişkeni, `evensQuery` sorgulanabilir bir tür olmalıdır. Türü `evensQuery` `IEnumerable(Of Integer)` , derleyici tarafından yerel tür çıkarımı kullanılarak atanır.  
  
 Sorgu değişkeninin kendisinin hiçbir eylem aldığını ve veri döndürdüğünü unutmamak önemlidir. Yalnızca sorgu tanımını depolar. Önceki örnekte, `For Each` sorguyu yürüten döngüdür.  
  
## <a name="query-execution"></a>Sorgu Yürütme  
 Sorgu yürütme sorgu oluşturulduktan farklıdır. Sorgu oluşturma sorguyu tanımlar, ancak yürütme farklı bir mekanizma tarafından tetiklenir. Sorgu, tanımlanır (*anında yürütme*), veya tanım depolanabilir ve sorgu daha sonra yürütülebilir (*ertelenmiş yürütme*).  
  
### <a name="deferred-execution"></a>Ertelenmiş Yürütme  
 Tipik bir LINQ sorgusu, içinde tanımlanan önceki örnekteki bir örneğe benzer `evensQuery` . Sorguyu oluşturur ancak hemen yürütmez. Bunun yerine sorgu tanımı sorgu değişkeninde depolanır `evensQuery` . Sorguyu daha sonra `For Each` bir değer dizisi döndüren bir döngü kullanarak ya da veya gibi standart bir sorgu işleci uygulayarak yürütün `Count` `Max` . Bu işlem *ertelenmiş yürütme*olarak adlandırılır.  
  
 [!code-vb[VbLINQFirstQuery#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#7)]  
  
 Bir değerler dizisi için, döngüdeki yineleme değişkenini kullanarak alınan verilere erişirsiniz `For Each` ( `number` Önceki örnekte). Sorgu değişkeni sorgu `evensQuery` sonuçları yerine sorgu tanımını taşıdığı için sorgu değişkenini birden çok kez kullanarak istediğiniz sıklıkta bir sorgu çalıştırabilirsiniz. Örneğin, uygulamanızda ayrı bir uygulama tarafından sürekli olarak güncelleştirilmekte olan bir veritabanınız olabilir. Bu veritabanından veri alan bir sorgu oluşturduktan sonra, `For Each` her seferinde en son verileri alarak sorguyu tekrar tekrar yürütmek için bir döngü kullanabilirsiniz.  
  
 Aşağıdaki örnek, ertelenmiş yürütmenin nasıl çalıştığını gösterir. `evensQuery2`Bir döngüyle tanımlandıktan ve yürütüldükten sonra, `For Each` Önceki örneklerde olduğu gibi, veri kaynağındaki bazı öğeler `numbers` değiştirilir. Sonra ikinci bir `For Each` döngü `evensQuery2` yeniden çalışır. Sonuçlar ikinci kez farklı olur, çünkü `For Each` döngü sorguyu tekrar yürüterek içindeki yeni değerleri kullanarak yeniden yürütür `numbers` .  
  
 [!code-vb[VbLINQFirstQuery#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#3)]  
  
 Çıktı:  
  
 `Evens in original array:`  
  
 `0  2  4  6`  
  
 `Evens in changed array:`  
  
 `0  10  2  22  8`  
  
### <a name="immediate-execution"></a>Hemen Yürütme  
 Sorguları ertelenmiş olarak yürütmek için sorgu tanımı daha sonra yürütülmek üzere bir sorgu değişkeninde depolanır. Anında yürütme sırasında sorgu, tanımı sırasında yürütülür. Sorgu sonucunun ayrı öğelerine erişim gerektiren bir yöntemi uyguladığınızda yürütme tetiklenir. Hemen yürütme genellikle tek değer döndüren standart sorgu işleçlerinden biri kullanılarak zorlanır. Örnekler,,, `Count` `Max` `Average` ve `First` . Bu standart sorgu işleçleri, tek bir sonucu hesaplamak ve döndürmek için uygulandıktan hemen sonra sorguyu yürütür. Tek değerler döndüren standart sorgu işleçleri hakkında daha fazla bilgi için bkz. [toplama işlemleri](aggregation-operations.md), [öğe Işlemleri](element-operations.md)ve [nicelik toplamı işlemleri](quantifier-operations.md).  
  
 Aşağıdaki sorgu, bir tamsayılar dizisindeki Çift sayıların sayımını döndürür. Sorgu tanımı kaydedilmez ve `numEvens` basit bir işlemdir `Integer` .  
  
 [!code-vb[VbLINQFirstQuery#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#4)]  
  
 Yöntemini kullanarak aynı sonucu elde edebilirsiniz `Aggregate` .  
  
 [!code-vb[VbLINQFirstQuery#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#5)]  
  
 Ayrıca, `ToList` `ToArray` aşağıdaki kodda gösterildiği gibi bir sorgu (anında) veya sorgu değişkeni (ertelenmiş) üzerinde veya yöntemini çağırarak bir sorgunun yürütülmesini zorlayabilirsiniz.  
  
 [!code-vb[VbLINQFirstQuery#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#6)]  
  
 Önceki örneklerde `evensQuery3` bir sorgu değişkenidir, ancak bir `evensList` listesidir ve bir `evensArray` dizidir.  
  
 `ToList` `ToArray` Hemen yürütmeye zorlamak için veya kullanmak, sorguyu hemen yürütmek ve sonuçları tek bir koleksiyon nesnesi içinde önbelleğe almak istediğiniz senaryolarda özellikle yararlıdır. Bu yöntemler hakkında daha fazla bilgi için bkz. [veri türlerini dönüştürme](converting-data-types.md).  
  
 Ayrıca, yöntemi gibi bir yöntemi kullanarak bir sorgunun yürütülmesine neden olabilirsiniz `IEnumerable` <xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'te LINQ'e Başlarken](getting-started-with-linq.md)
- [Yerel Tür Arabirimi](../../language-features/variables/local-type-inference.md)
- [Standart sorgu Işleçlerine genel bakış (Visual Basic)](standard-query-operators-overview.md)
- [Visual Basic'de LINQ'e Giriş](../../language-features/linq/introduction-to-linq.md)
- [LINQ](../../language-features/linq/index.md)
- [Sorgular](../../../language-reference/queries/index.md)
