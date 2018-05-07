---
title: İlk LINQ Sorgunuzu Yazma (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ queries [Visual Basic]
- LINQ [Visual Basic], writing queries
ms.assetid: 4affb732-3e9b-4479-aa31-1f9bd8183cbe
ms.openlocfilehash: f426aac5358837563081d2bf9783f6d4fe04d853
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="writing-your-first-linq-query-visual-basic"></a>İlk LINQ Sorgunuzu Yazma (Visual Basic)
A *sorgu* bir veri kaynağından veri alır bir ifadedir. Sorguları bir adanmış sorgu dili ifade edilir. Zamanla, farklı diller farklı türlerde veri kaynakları için örneğin, ilişkisel veritabanları için SQL ve XQuery XML için geliştirilmiştir. Bu, her veri kaynağı veya desteklenen veri biçimi türü için yeni bir sorgu dili öğrenmek uygulama geliştiricisi için gerekli kılar.  
  
 [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] durum, çeşitli veri kaynakları ve biçimleri arasında verilerle çalışmak için tutarlı bir model sunarak basitleştirir. İçinde bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu nesneler her zaman çalıştığınız. Sorgu ve veri XML belgelerindeki, SQL veritabanları, ADO.NET veri kümeleri ve varlıklar, .NET Framework koleksiyonları ve herhangi diğer kaynak veya biçimi için dönüştürmek için aynı temel kodlama modelleri kullanmanıza bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sağlayıcısı kullanılabilir. Bu belge oluşturma üç aşamaya ve temel kullanımını açıklar [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgular.  
  
## <a name="three-stages-of-a-query-operation"></a>Bir Sorgu İşleminin Üç Aşaması  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu işlemleri üç eylemlerini oluşur:  
  
1.  Veri kaynağı veya kaynakları edinin.  
  
2.  Sorgu oluşturun.  
  
3.  Sorgu yürütün.  
  
 İçinde [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], bir sorgu yürütme sorgu oluşturulmasından farklıdır. Herhangi bir sorgu oluşturarak yalnızca verileri değil. Bu nokta, bu konunun ilerleyen bölümlerinde daha ayrıntılı ele alınmıştır.  
  
 Aşağıdaki örnek bir sorgu işlemi üç bölümden gösterilmektedir. Örnek dizisi, Tanıtım amaçlı uygun veri kaynağı olarak kullanır. Ancak, aynı kavramlar, diğer veri kaynakları için de geçerlidir.  
  
> [!NOTE]
>  Üzerinde [derleme sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), emin **Option Infer** ayarlanır **üzerinde**.  
  
 [!code-vb[VbLINQFirstQuery#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_1.vb)]  
  
 Çıktı:  
  
 `0 2 4 6`  
  
## <a name="the-data-source"></a>Veri Kaynağı  
 Önceki örnekte veri kaynağı bir dizi olduğundan genel örtük olarak desteklediği <xref:System.Collections.Generic.IEnumerable%601> arabirimi. İçin bir veri kaynağı olarak bir dizi kullanmanızı sağlayan bu gerçeğidir bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu. Türlerini destekleyen <xref:System.Collections.Generic.IEnumerable%601> veya türetilmiş bir arabirim genel gibi <xref:System.Linq.IQueryable%601> denir *sorgulanabilir türleri*.  
  
 Örtük olarak sorgulanabilir bir tür olarak dizi hiçbir değişiklik ya da olarak hizmet verecek özel işleme gerektiren bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] veri kaynağı. Aynı destekleyen herhangi bir koleksiyon türü için geçerlidir <xref:System.Collections.Generic.IEnumerable%601>, genel dahil olmak üzere <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.Dictionary%602>ve .NET Framework Sınıf Kitaplığı'nda diğer sınıflar.  
  
 Veri kaynağını zaten uygulamazsa <xref:System.Collections.Generic.IEnumerable%601>, [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sağlayıcı işlevselliğini uygulamak için gereken *standart sorgu işleçleri* bu veri kaynağı için. Örneğin, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgulanabilir bir XML belgesi yüklenirken iş işleme <xref:System.Xml.Linq.XElement> , aşağıdaki örnekte gösterildiği gibi yazın. Standart sorgu işleçleri hakkında daha fazla bilgi için bkz: [standart sorgu işleçlerine genel bakış (Visual Basic)](standard-query-operators-overview.md).  
  
 [!code-vb[VbLINQFirstQuery#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_2.vb)]  
  
 İle [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], bir nesne ilişkisel tasarım zamanında el ile veya kullanarak eşleme oluşturduğunuz ilk [LINQ-SQL Visual Studio Araçları](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) Visual Studio. Sorgularınızın nesneleri karşı ve çalışma zamanında yazma [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] veritabanı ile iletişim işler. Aşağıdaki örnekte, `customers` veritabanında belirli bir tablo temsil eder ve <xref:System.Data.Linq.Table%601> destekler genel <xref:System.Linq.IQueryable%601>.  
  
```vb  
' Create a data source from a SQL table.  
Dim db As New DataContext("C:\Northwind\Northwnd.mdf")  
Dim customers As Table(Of Customer) = db.GetTable(Of Customer)  
```  
  
 Belirli veri kaynağı türleri oluşturma hakkında daha fazla bilgi için çeşitli belgelerine bakın [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sağlayıcıları. (Bu sağlayıcılar listesi için bkz: [LINQ (dil ile tümleşik sorgu)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).) Temel kural basittir: bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] veri kaynağıdır genel destekleyen herhangi bir nesne <xref:System.Collections.Generic.IEnumerable%601> arabirimi veya devralan bir arabirim.  
  
> [!NOTE]
>  Gibi türleri <xref:System.Collections.ArrayList> genel olmayan destekleyen <xref:System.Collections.IEnumerable> arabirimi de kullanılabilir olarak [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] veri kaynakları. Kullanan bir örneğin bir <xref:System.Collections.ArrayList>, bkz: [nasıl yapılır: LINQ (Visual Basic) ile ArrayList sorgulama](how-to-query-an-arraylist-with-linq.md).  
  
## <a name="the-query"></a>Sorgu  
 Sorgu, veri kaynağı veya kaynakları almak istediğiniz bilgileri belirtin. Ayrıca, nasıl bu bilgileri sıralanmış, gruplandırılmış veya, döndürülmeden önce yapılandırılmış belirtme seçeneğiniz de vardır. Sorgu oluşturma etkinleştirmek için Visual Basic diline yeni sorgu söz dizimi birleştirilmiş.  
  
 Yürütüldüğünde, aşağıdaki örnek sorguda tüm çift sayıları tamsayı dizisinden döndürür. `numbers`.  
  
 [!code-vb[VbLINQFirstQuery#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_1.vb)]  
  
 Sorgu ifadesi üç yan tümcesi içeren: `From`, `Where`, ve `Select`. Belirli işlevi ve amacı her sorgu ifadesi yan tümcesinin ele alınmıştır [temel sorgu işlemleri (Visual Basic)](basic-query-operations.md). Daha fazla bilgi için bkz: [sorguları](../../../../visual-basic/language-reference/queries/queries.md). İçinde unutmayın [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], sorgu tanımı genellikle bir değişkende depolanır ve daha sonra yürütülür. Sorgu gibi değişken `evensQuery` önceki örnekte, sorgulanabilir bir türü olmalıdır. Türü `evensQuery` olan `IEnumerable(Of Integer)`, yerel türü çıkarımı kullanarak derleyici tarafından atanmış.  
  
 Sorgu değişkeni hiçbir eylemde bulunmaz ve hiçbir veri döndürür unutmamak önemlidir. Yalnızca sorgu tanımı da depolar. Önceki örnekte olmasından `For Each` Sorguyu yürüten döngü.  
  
## <a name="query-execution"></a>Sorgu Yürütme  
 Sorgu yürütme sorgu oluşturma ' ayrıdır. Sorgu oluşturma sorgusu tanımlar, ancak yürütme farklı mekanizması tarafından tetiklenir. Sorguda tanımlanan hemen yürütülebilir (*hemen yürütme*), veya tanımı depolanabilir ve sorgu daha sonra çalıştırılabilir (*yürütme ertelenmiş*).  
  
### <a name="deferred-execution"></a>Ertelenmiş Yürütme  
 Tipik bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu benzer bir önceki örnekte `evensQuery` tanımlanır. Sorgu oluşturur ama hemen çalıştırma. Bunun yerine, sorgu tanımı sorgu değişkende depolanır `evensQuery`. Sorguyu daha sonra genellikle kullanarak yürütmek bir `For Each` değerlerin ya da bir standart sorgu işleci gibi uygulayarak bir dizi döndürür döngü `Count` veya `Max`. Bu işlem olarak adlandırılır *yürütme ertelenmiş*.  
  
 [!code-vb[VbLINQFirstQuery#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_3.vb)]  
  
 Değerleri dizisi için size alınan veriler içinde yineleme değişkeni kullanarak erişim `For Each` döngü (`number` önceki örnekte). Çünkü sorgu değişkeni `evensQuery`, sorgu sonuçları yerine sorgu tanımı tutan birden fazla kez sorgu değişkeni kullanarak istediğiniz sıklıkta bir sorgu yürütebilir. Örneğin, ayrı bir uygulama tarafından sürekli olarak güncelleştiriliyor, uygulamanızdaki bir veritabanı sahip olabilir. Verileri, veritabanından alınan bir sorgu oluşturduktan sonra kullanabileceğiniz bir `For Each` sorguyu tekrar tekrar yürütmek için döngü her zaman en son veriler alınıyor.  
  
 Aşağıdaki örnekte nasıl ertelenmiş yürütme gösteren çalışır. Sonra `evensQuery2` tanımlanan ve ile yürütülebilir bir `For Each` , bazı öğeler veri kaynağındaki önceki örneklerde olduğu gibi döngü `numbers` değiştirilir. İkinci bir sonra `For Each` döngü çalıştırır `evensQuery2` yeniden. Sonuçları ikincisinde ise, çünkü farklı `For Each` döngü yürütür sorguyu yeniden yeni değerleri kullanarak `numbers`.  
  
 [!code-vb[VbLINQFirstQuery#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_4.vb)]  
  
 Çıktı:  
  
 `Evens in original array:`  
  
 `0  2  4  6`  
  
 `Evens in changed array:`  
  
 `0  10  2  22  8`  
  
### <a name="immediate-execution"></a>Hemen Yürütme  
 Sorguları ertelenmiş yürütülmesi sorgu tanımı daha sonra çalıştırılmak için bir sorgu değişkeni depolanır. Hemen bir yürütme sorgu tanımına aynı anda çalıştırılır. Sorgu sonucunun tek tek öğelere erişim gerektiren bir yöntemi uyguladığınızda yürütme tetiklenir. Hemen çalıştırılmak genellikle tek bir değer standart sorgu işleçleri birini kullanarak zorlanır. Örnekler `Count`, `Max`, `Average`, ve `First`. Bu standart sorgu işleçleri hesaplamak ve bir singleton sonuca dönmek için uygulanan sorgu çalıştırın. Tek değer döndürmek standart sorgu işleçleri hakkında daha fazla bilgi için bkz: [toplama işlemleri](aggregation-operations.md), [öğesi işlemleri](element-operations.md), ve [Niceleyici işlemleri](quantifier-operations.md).  
  
 Aşağıdaki sorgu dizisi içinde çift sayıları sayısını döndürür. Sorgu tanımı kaydedilmemişse, ve `numEvens` basit olan `Integer`.  
  
 [!code-vb[VbLINQFirstQuery#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_5.vb)]  
  
 Kullanarak aynı sonucu elde edebilirsiniz `Aggregate` yöntemi.  
  
 [!code-vb[VbLINQFirstQuery#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_6.vb)]  
  
 Ayrıca, çağırarak bir sorgu yürütme zorlayabilirsiniz `ToList` veya `ToArray` bir sorgu (hemen) veya (Ertelenmiş), sorgu değişkeni aşağıdaki kodda gösterildiği gibi yöntemi.  
  
 [!code-vb[VbLINQFirstQuery#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_7.vb)]  
  
 Önceki örneklerde, `evensQuery3` bir sorgu değişken, ancak `evensList` listesidir ve `evensArray` bir dizidir.  
  
 Kullanarak `ToList` veya `ToArray` hemen zorlamak için yürütme istediğiniz sorguyu hemen yürütmek ve tek koleksiyon nesnesi sonuçlarında önbelleğe almasını senaryolarda kullanışlıdır. Bu yöntemler hakkında daha fazla bilgi için bkz: [veri türlerini dönüştürme](converting-data-types.md).  
  
 Bir sorgu kullanarak çalıştırılmasına neden olabilir bir `IEnumerable` yöntemi gibi <xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A> yöntemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'te Lınq'e Başlarken](getting-started-with-linq.md)  
 [Yerel Çıkarım](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Standart sorgu işleçlerine genel bakış (Visual Basic)](standard-query-operators-overview.md)  
 [Visual Basic'de LINQ'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Sorgular](../../../../visual-basic/language-reference/queries/queries.md)
