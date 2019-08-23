---
title: İlk LINQ Sorgunuzu Yazma (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ queries [Visual Basic]
- LINQ [Visual Basic], writing queries
ms.assetid: 4affb732-3e9b-4479-aa31-1f9bd8183cbe
ms.openlocfilehash: 5c83d888f65ce5c216327e94c5d4d1267fb93c29
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952007"
---
# <a name="writing-your-first-linq-query-visual-basic"></a>İlk LINQ Sorgunuzu Yazma (Visual Basic)
*Sorgu* , veri kaynağından veri alan bir ifadedir. Sorgular adanmış bir sorgu dilinde ifade edilir. Zaman içinde farklı diller, örneğin, ilişkisel veritabanları için SQL ve XML için XQuery gibi farklı türlerde veri kaynakları için geliştirilmiştir. Bu, uygulama geliştiricisinin desteklenen her bir veri kaynağı türü veya veri biçimi için yeni bir sorgu dili öğrenmesini zorunlu kılar.  
  
 [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]çeşitli veri kaynakları ve biçimlerdeki verilerle çalışmaya yönelik tutarlı bir model sunarak durumu basitleştirir. Bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorguda, her zaman nesneleriyle birlikte çalışmanız gerekir. XML belgelerinde, SQL veritabanlarında, ADO.NET veri kümelerinde ve varlıklarda, .NET Framework koleksiyonlarında ve bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sağlayıcının kullanılabildiği diğer tüm kaynak veya biçimdeki verileri sorgulamak ve dönüştürmek için aynı temel kodlama düzenlerini kullanırsınız. Bu belgede temel [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorguların oluşturulması ve kullanılması için üç aşama açıklanmaktadır.  
  
## <a name="three-stages-of-a-query-operation"></a>Bir Sorgu İşleminin Üç Aşaması  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]sorgu işlemleri üç eylemden oluşur:  
  
1. Veri kaynağını veya kaynaklarını edinin.  
  
2. Sorguyu oluşturun.  
  
3. Sorguyu yürütün.  
  
 ' [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]De, bir sorgunun yürütülmesi sorgu oluşturulduktan farklıdır. Yalnızca bir sorgu oluşturarak herhangi bir veri alamazsınız. Bu nokta, bu konunun ilerleyen kısımlarında daha ayrıntılı bir şekilde ele alınmıştır.  
  
 Aşağıdaki örnekte, bir sorgu işleminin üç bölümü gösterilmektedir. Örnek, Gösterim amacıyla uygun bir veri kaynağı olarak bir tamsayılar dizisi kullanır. Ancak, aynı kavramlar diğer veri kaynakları için de geçerlidir.  
  
> [!NOTE]
> [Derleme sayfasında, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), **seçenek çıkarımı seçeneğinin** **Açık**olarak ayarlandığından emin olun.  
  
 [!code-vb[VbLINQFirstQuery#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#1)]  
  
 Çıktı:  
  
 `0 2 4 6`  
  
## <a name="the-data-source"></a>Veri Kaynağı  
 Önceki örnekteki veri kaynağı bir dizi olduğundan, genel <xref:System.Collections.Generic.IEnumerable%601> arabirimi örtülü olarak destekler. Bu aslında bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu için veri kaynağı olarak bir dizi kullanmanıza olanak sağlar. Destekleyen <xref:System.Collections.Generic.IEnumerable%601> türler veya genel <xref:System.Linq.IQueryable%601> gibi türetilmiş bir arabirim *sorgulanabilir türler*olarak adlandırılır.  
  
 Örtük olarak sorgulanabilir bir tür olarak, dizi hiçbir değişiklik veya bir veri kaynağı olarak kullanılacak özel bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] işleme gerektirmez. Aynı şekilde, .NET Framework sınıf kitaplığındaki genel <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.Dictionary%602>ve diğer sınıflar da dahil olmak üzere, destekleyen tüm koleksiyon türleri için de geçerlidir.  
  
 Kaynak verileri henüz uygulamadıysanız <xref:System.Collections.Generic.IEnumerable%601>, bu veri kaynağı için [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] *Standart sorgu işleçleri* işlevlerini uygulamak üzere bir sağlayıcı gerekir. Örneğin, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] aşağıdaki örnekte gösterildiği gibi, bir XML belgesini bir sorgulanabilir <xref:System.Xml.Linq.XElement> türe yükleme işini işler. Standart sorgu işleçleri hakkında daha fazla bilgi için bkz. [Standart sorgu Işleçlerine genel bakış (Visual Basic)](standard-query-operators-overview.md).  
  
 [!code-vb[VbLINQFirstQuery#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#2)]  
  
 İle [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], ilk olarak tasarım zamanında veya Visual Studio 'daki [Visual Studio 'daki LINQ to SQL araçlarını](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) kullanarak bir nesne ilişkisel eşleme oluşturursunuz. Sorgular nesnelere karşı yazılır ve çalışma [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] zamanında veritabanıyla iletişimi işler. Aşağıdaki örnekte, `customers` veritabanında belirli bir tabloyu temsil eder ve <xref:System.Data.Linq.Table%601> genel <xref:System.Linq.IQueryable%601>' i destekler.  
  
```vb  
' Create a data source from a SQL table.  
Dim db As New DataContext("C:\Northwind\Northwnd.mdf")  
Dim customers As Table(Of Customer) = db.GetTable(Of Customer)  
```  
  
 Belirli veri kaynağı türlerinin nasıl oluşturulacağı hakkında daha fazla bilgi için çeşitli [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sağlayıcılar için belgelere bakın. (Bu sağlayıcıların listesi için bkz. [LINQ (dil Ile tümleşik sorgu)](../../../../visual-basic/programming-guide/concepts/linq/index.md).) Temel kural basittir: [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] veri kaynağı, genel <xref:System.Collections.Generic.IEnumerable%601> arabirimi veya bundan devralan bir arabirimi destekleyen herhangi bir nesnedir.  
  
> [!NOTE]
> Genel olmayan arabirimi destekleyen türler, veri kaynakları olarak [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] da kullanılabilir. <xref:System.Collections.IEnumerable> <xref:System.Collections.ArrayList> Kullanan <xref:System.Collections.ArrayList>bir örnek için bkz [. nasıl yapılır: LINQ (Visual Basic)](how-to-query-an-arraylist-with-linq.md)ile bir ArrayList 'i sorgulayın.  
  
## <a name="the-query"></a>Sorgu  
 Sorguda, veri kaynağından veya kaynaklardan hangi bilgileri almak istediğinizi belirtirsiniz. Ayrıca, bu bilgilerin döndürülmeden önce nasıl sıralanacağını, gruplanacağını veya yapılandırıldığını belirtme seçeneğiniz de vardır. Sorgu oluşturmayı etkinleştirmek için Visual Basic dilde yeni sorgu söz dizimi eklendi.  
  
 Yürütüldüğünde, aşağıdaki örnekteki sorgu bir tamsayı dizisinden `numbers`gelen tüm çift sayıları döndürür.  
  
 [!code-vb[VbLINQFirstQuery#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#1)]  
  
 Sorgu ifadesi üç yan tümce içerir: `From`, `Where`, ve `Select`. Her sorgu ifadesi yan tümcesinin belirli bir işlevi ve amacı, [temel sorgu işlemlerinde (Visual Basic)](basic-query-operations.md)ele alınmıştır. Daha fazla bilgi için bkz. [sorgular](../../../../visual-basic/language-reference/queries/index.md). ' De [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], bir sorgu tanımının genellikle bir değişkende depolandığını ve daha sonra yürütüldüğünü unutmayın. Önceki örnekte olduğu `evensQuery` gibi sorgu değişkeni, sorgulanabilir bir tür olmalıdır. `evensQuery` Türü`IEnumerable(Of Integer)`, derleyici tarafından yerel tür çıkarımı kullanılarak atanır.  
  
 Sorgu değişkeninin kendisinin hiçbir eylem aldığını ve veri döndürdüğünü unutmamak önemlidir. Yalnızca sorgu tanımını depolar. Önceki örnekte, sorguyu yürüten `For Each` döngüdür.  
  
## <a name="query-execution"></a>Sorgu Yürütme  
 Sorgu yürütme sorgu oluşturulduktan farklıdır. Sorgu oluşturma sorguyu tanımlar, ancak yürütme farklı bir mekanizma tarafından tetiklenir. Sorgu, tanımlanır (*anında yürütme*), veya tanım depolanabilir ve sorgu daha sonra yürütülebilir (*ertelenmiş yürütme*).  
  
### <a name="deferred-execution"></a>Ertelenmiş Yürütme  
 Tipik [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] bir sorgu, `evensQuery` içinde tanımlanan önceki örnekteki bir örneğe benzer. Sorguyu oluşturur ancak hemen yürütmez. Bunun yerine sorgu tanımı sorgu değişkeninde `evensQuery`depolanır. Sorguyu daha sonra bir değer dizisi döndüren bir `For Each` döngü kullanarak ya da `Count` veya `Max`gibi standart bir sorgu işleci uygulayarak yürütün. Bu işlem *ertelenmiş yürütme*olarak adlandırılır.  
  
 [!code-vb[VbLINQFirstQuery#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#7)]  
  
 Bir değerler dizisi için, `For Each` döngüdeki yineleme değişkenini kullanarak alınan verilere erişirsiniz (`number` önceki örnekte). Sorgu değişkeni `evensQuery`sorgu sonuçları yerine sorgu tanımını taşıdığı için sorgu değişkenini birden çok kez kullanarak istediğiniz sıklıkta bir sorgu çalıştırabilirsiniz. Örneğin, uygulamanızda ayrı bir uygulama tarafından sürekli olarak güncelleştirilmekte olan bir veritabanınız olabilir. Bu veritabanından veri alan bir sorgu oluşturduktan sonra, her seferinde en son verileri alarak sorguyu tekrar `For Each` tekrar yürütmek için bir döngü kullanabilirsiniz.  
  
 Aşağıdaki örnek, ertelenmiş yürütmenin nasıl çalıştığını gösterir. `numbers` Bir `evensQuery2` döngüyletanımlandıktanveyürütüldüktensonra,öncekiörneklerdeolduğugibi,verikaynağındakibazıöğelerdeğiştirilir.`For Each` Sonra ikinci `For Each` bir döngü yeniden `evensQuery2` çalışır. Sonuçlar ikinci kez farklı olur, çünkü `For Each` döngü sorguyu tekrar yürüterek içindeki `numbers`yeni değerleri kullanarak yeniden yürütür.  
  
 [!code-vb[VbLINQFirstQuery#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#3)]  
  
 Çıktı:  
  
 `Evens in original array:`  
  
 `0  2  4  6`  
  
 `Evens in changed array:`  
  
 `0  10  2  22  8`  
  
### <a name="immediate-execution"></a>Hemen Yürütme  
 Sorguları ertelenmiş olarak yürütmek için sorgu tanımı daha sonra yürütülmek üzere bir sorgu değişkeninde depolanır. Anında yürütme sırasında sorgu, tanımı sırasında yürütülür. Sorgu sonucunun ayrı öğelerine erişim gerektiren bir yöntemi uyguladığınızda yürütme tetiklenir. Hemen yürütme genellikle tek değer döndüren standart sorgu işleçlerinden biri kullanılarak zorlanır. Örnekler,,, ve`First`. `Count` `Max` `Average` Bu standart sorgu işleçleri, tek bir sonucu hesaplamak ve döndürmek için uygulandıktan hemen sonra sorguyu yürütür. Tek değerler döndüren standart sorgu işleçleri hakkında daha fazla bilgi için bkz. [toplama işlemleri](aggregation-operations.md), [öğe Işlemleri](element-operations.md)ve [nicelik toplamı işlemleri](quantifier-operations.md).  
  
 Aşağıdaki sorgu, bir tamsayılar dizisindeki Çift sayıların sayımını döndürür. Sorgu tanımı kaydedilmez ve `numEvens` basit `Integer`bir işlemdir.  
  
 [!code-vb[VbLINQFirstQuery#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#4)]  
  
 `Aggregate` Yöntemini kullanarak aynı sonucu elde edebilirsiniz.  
  
 [!code-vb[VbLINQFirstQuery#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#5)]  
  
 Ayrıca, aşağıdaki kodda gösterildiği gibi bir sorgu (anında) `ToList` veya `ToArray` sorgu değişkeni (ertelenmiş) üzerinde veya yöntemini çağırarak bir sorgunun yürütülmesini zorlayabilirsiniz.  
  
 [!code-vb[VbLINQFirstQuery#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#6)]  
  
 Önceki örneklerde `evensQuery3` bir sorgu değişkenidir, ancak `evensList` bir listesidir ve `evensArray` bir dizidir.  
  
 Hemen `ToList` yürütmeye `ToArray` zorlamak için veya kullanmak, sorguyu hemen yürütmek ve sonuçları tek bir koleksiyon nesnesi içinde önbelleğe almak istediğiniz senaryolarda özellikle yararlıdır. Bu yöntemler hakkında daha fazla bilgi için bkz. [veri türlerini dönüştürme](converting-data-types.md).  
  
 Ayrıca, `IEnumerable` <xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A> yöntemi gibi bir yöntemi kullanarak bir sorgunun yürütülmesine neden olabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic LINQ ile çalışmaya başlama](getting-started-with-linq.md)
- [Yerel Çıkarım](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Standart sorgu Işleçlerine genel bakış (Visual Basic)](standard-query-operators-overview.md)
- [Visual Basic LINQ 'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Sorgular](../../../../visual-basic/language-reference/queries/index.md)
