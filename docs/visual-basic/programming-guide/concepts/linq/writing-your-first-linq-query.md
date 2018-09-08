---
title: İlk LINQ Sorgunuzu Yazma (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ queries [Visual Basic]
- LINQ [Visual Basic], writing queries
ms.assetid: 4affb732-3e9b-4479-aa31-1f9bd8183cbe
ms.openlocfilehash: 4c04c00c5392d8ba363346b06c806ec79041c439
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44184317"
---
# <a name="writing-your-first-linq-query-visual-basic"></a>İlk LINQ Sorgunuzu Yazma (Visual Basic)
A *sorgu* , verileri bir veri kaynağından alır bir ifadedir. Sorgular, bir özel sorgu dilinde ifade edilir. Zaman içinde farklı dillerde farklı türde veri kaynakları için örneğin, ilişkisel veritabanları için SQL ve XML için XQuery geliştirilmiştir. Bu, uygulama geliştiricisi, her veri kaynağı veya desteklenmeyen veri biçimi türü için yeni bir sorgu dili öğrenmek için gerekli kılar.  
  
 [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] durum, çeşitli veri kaynakları ve biçimler arasında veri ile çalışma için tutarlı bir model sunarak basitleştirir. İçinde bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu, her zaman nesnelerle. Sorgu ve veri XML belgeleri, SQL veritabanları, ADO.NET veri kümeleri ve varlıkları, .NET Framework koleksiyonları ve diğer kaynak veya biçimi için dönüştürmek için aynı temel kodlama desenlerini kullanırsınız bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sağlayıcısı kullanılabilir. Bu belge oluşturma üç aşamaya ve temel kullanımını açıklar [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgular.  
  
## <a name="three-stages-of-a-query-operation"></a>Bir Sorgu İşleminin Üç Aşaması  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu işlemleri üç eylemden oluşur:  
  
1.  Veri kaynağından veya kaynaklarından edinin.  
  
2.  Bir sorgu oluşturun.  
  
3.  Sorguyu yürütün.  
  
 İçinde [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], bir sorgunun yürütülmesi sorgunun oluşturulmasından farklıdır. Herhangi bir sorgu oluşturarak veri yok. Bu nokta, bu konunun ilerleyen bölümlerinde daha ayrıntılı ele alınmıştır.  
  
 Aşağıdaki örnek bir sorgu işleminin üç bölümü gösterilmektedir. Örnek, tamsayı dizisi tanıtım amacıyla uygun veri kaynağı olarak kullanır. Ancak aynı kavramlar diğer veri kaynakları için de geçerlidir.  
  
> [!NOTE]
>  Üzerinde [derleme sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), emin **Option Infer** ayarlanır **üzerinde**.  
  
 [!code-vb[VbLINQFirstQuery#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_1.vb)]  
  
 Çıktı:  
  
 `0 2 4 6`  
  
## <a name="the-data-source"></a>Veri Kaynağı  
 Önceki örnekte veri kaynağı bir dizi olduğundan genel örtük olarak desteklediği <xref:System.Collections.Generic.IEnumerable%601> arabirimi. Bir dizi için bir veri kaynağı olarak kullanmanızı sağlayan bu gerçeğidir bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu. Destekleyen türler <xref:System.Collections.Generic.IEnumerable%601> veya türetilmiş bir arabirim gibi genel <xref:System.Linq.IQueryable%601> adlandırılır *sorgulanabilir türler*.  
  
 Herhangi bir değişiklik veya özel olarak değerlendirilmesi olarak hizmet verecek bir örtük olarak sorgulanabilir tür olarak dizi gerektirir bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] veri kaynağı. Aynı destekleyen tüm koleksiyon türlerinde geçerlidir <xref:System.Collections.Generic.IEnumerable%601>, genel dahil olmak üzere <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.Dictionary%602>ve diğer sınıflar .NET Framework Sınıf Kitaplığı'nda.  
  
 Kaynak verileri zaten uygulamazsa <xref:System.Collections.Generic.IEnumerable%601>, [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sağlayıcı işlevselliğini uygulamak için gereken *standart sorgu işleçleri* bu veri kaynağı. Örneğin, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bir XML belgesini sorgulanabilir bir yükleme işi işler <xref:System.Xml.Linq.XElement> , aşağıdaki örnekte gösterildiği gibi yazın. Standart sorgu işleçleri hakkında daha fazla bilgi için bkz. [standart sorgu işleçlerine genel bakış (Visual Basic)](standard-query-operators-overview.md).  
  
 [!code-vb[VbLINQFirstQuery#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_2.vb)]  
  
 İle [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], önce bir nesne-ilişkisel tasarım zamanında el ile ya da kullanarak eşleme oluşturma [LINQ to SQL araçlarını Visual Studio'da](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) Visual Studio'da. Sorgularınızın karşı nesneleri ve çalışma zamanında yazma [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] veritabanı ile iletişimi gerçekleştirir. Aşağıdaki örnekte, `customers` veritabanında belirli bir tabloyu temsil eder ve <xref:System.Data.Linq.Table%601> destekleyen genel <xref:System.Linq.IQueryable%601>.  
  
```vb  
' Create a data source from a SQL table.  
Dim db As New DataContext("C:\Northwind\Northwnd.mdf")  
Dim customers As Table(Of Customer) = db.GetTable(Of Customer)  
```  
  
 Belirli türde veri kaynaklarını oluşturma hakkında daha fazla bilgi için çeşitli belgelerine bakın [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sağlayıcıları. (Bu sağlayıcıları listesi için bkz. [LINQ (dil ile tümleşik sorgu)](../../../../visual-basic/programming-guide/concepts/linq/index.md).) Temel kural basittir: bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] genel destekleyen herhangi bir nesne veri kaynağı, <xref:System.Collections.Generic.IEnumerable%601> arabirimi ya da bundan devralan bir arabirim.  
  
> [!NOTE]
>  Gibi türleri <xref:System.Collections.ArrayList> genel olmayan destekleyen <xref:System.Collections.IEnumerable> arabirimi de kullanılabilir olarak [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] veri kaynakları. Kullanan bir örnek için bir <xref:System.Collections.ArrayList>, bkz: [nasıl yapılır: (Visual Basic) LINQ ile ArrayList sorgulama](how-to-query-an-arraylist-with-linq.md).  
  
## <a name="the-query"></a>Sorgu  
 Sorgu, veri kaynağından veya kaynaklarından almak istediğiniz bilgiler belirtin. Ayrıca, nasıl bu bilgileri sıralanmış, gruplandırılmış veya döndürülmeden önce yapılandırılmış belirtme seçeneğiniz de vardır. Sorgu oluşturmayı etkinleştirmek için Visual Basic yeni sorgu sözdizimi dile yaptıysa.  
  
 Aşağıdaki örnek sorguda yürütüldüğünde, tamsayı dizisinden tüm çift sayıları döndürür `numbers`.  
  
 [!code-vb[VbLINQFirstQuery#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_1.vb)]  
  
 Sorgu ifadesi üç yan tümce içeriyor: `From`, `Where`, ve `Select`. Belirli bir işlevi ve amacı, her sorgu ifadesi yan tümcesi ele alınmıştır [temel sorgu işlemleri (Visual Basic)](basic-query-operations.md). Daha fazla bilgi için [sorguları](../../../../visual-basic/language-reference/queries/index.md). Unutmayın, [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], sorgu tanımı genellikle bir değişkende depolanır ve daha sonra yürütülür. Sorgu değişkeni gibi `evensQuery` önceki örnekte, sorgulanabilir tür olmalıdır. Türünü `evensQuery` olduğu `IEnumerable(Of Integer)`, yerel tür çıkarımı kullanarak derleyici tarafından atanmış.  
  
 Sorgu değişkeninin kendisinin hiç eylem almaması ve veri döndürmemesidir unutmamak önemlidir. Yalnızca, sorgu tanımı depolar. Önceki örnekte olduğu `For Each` Sorguyu yürüten döngü.  
  
## <a name="query-execution"></a>Sorgu Yürütme  
 Sorgu yürütme, sorgu oluşturma işleminden ayrıdır. Sorgu oluşturma sorgu tanımlar, ancak yürütme farklı bir mekanizma tarafından tetiklenir. Sorguda tanımlanan hemen sonra yürütülebilir (*hemen yürütme*), veya tanım saklanır ve sorgu daha sonra yürütülebilir (*ertelenmiş yürütme*).  
  
### <a name="deferred-execution"></a>Ertelenmiş Yürütme  
 Tipik bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu benzer bir önceki örnekte `evensQuery` tanımlanır. Sorgu oluşturur, ancak anında yürütmeye başlamaz. Bunun yerine, sorgu tanımı sorgu değişkeninde depolanır `evensQuery`. Daha sonra genellikle kullanarak sorguyu bir `For Each` değerler ya da bir standart sorgu işleci gibi uygulayarak bir dizisini döndüren döngü `Count` veya `Max`. Bu işlem olarak adlandırılır *ertelenmiş yürütme*.  
  
 [!code-vb[VbLINQFirstQuery#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_3.vb)]  
  
 Değerler dizisi için alınan yineleme değişkeni kullanarak verilere `For Each` döngü (`number` önceki örnekte). Çünkü sorgu değişkeni `evensQuery`, sorgu sonuçları yerine sorgu tanımı tutan bir sorgu, sorgu değişkeni birden fazla kez kullanarak istediğiniz sıklıkta yürütebilirsiniz. Örneğin, ayrı bir uygulama tarafından sürekli olarak güncelleştirilmekte uygulamanızda bir veritabanı olabilir. Bir sorgu, veritabanından alınan veri oluşturduktan sonra kullanabileceğiniz bir `For Each` sorguyu tekrar tekrar yürütmek için döngü her zaman en son verileri alınıyor.  
  
 Aşağıdaki örnek nasıl ertelenmiş yürütme gösterir çalışır. Sonra `evensQuery2` tanımlanır ve ile yürütülen bir `For Each` döngü, önceki örneklerde olduğu gibi bazı öğeler veri kaynağında `numbers` değiştirilir. Ardından ikinci `For Each` döngü çalıştırır `evensQuery2` yeniden. Sonuçları ikinci seferde farklı olduğu `For Each` döngü yürütür sorguyu yeniden, yeni değerleri kullanarak `numbers`.  
  
 [!code-vb[VbLINQFirstQuery#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_4.vb)]  
  
 Çıktı:  
  
 `Evens in original array:`  
  
 `0  2  4  6`  
  
 `Evens in changed array:`  
  
 `0  10  2  22  8`  
  
### <a name="immediate-execution"></a>Hemen Yürütme  
 Sorguların ertelenmiş yürütme daha sonra yürütmek için bir sorgu değişkeni sorgu tanımı depolanır. Hemen yürütme, sorgu tanımı zamanında yürütülür. Yürütme, sorgu sonucundaki öğelere erişim gerektiren bir yöntem geçerli olduğunda tetiklenir. Hemen yürütme genellikle tek bir değer standart sorgu işleçleri birini kullanarak zorlanır. Örnekler `Count`, `Max`, `Average`, ve `First`. Bu standart sorgu işleçleri hesaplamak ve tek bir sonuç döndürmek için uygulanan bir sorgu çalıştırın. Tek bir değer standart sorgu işleçleri hakkında daha fazla bilgi için bkz. [toplama işlemleri](aggregation-operations.md), [öğe işlemleri](element-operations.md), ve [Niceleyici işlemleri](quantifier-operations.md).  
  
 Aşağıdaki sorgu, tamsayı dizisi çift sayıların sayısını döndürür. Sorgu tanımı kaydedilmez, ve `numEvens` basit `Integer`.  
  
 [!code-vb[VbLINQFirstQuery#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_5.vb)]  
  
 Kullanarak aynı sonucu elde edebileceğiniz `Aggregate` yöntemi.  
  
 [!code-vb[VbLINQFirstQuery#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_6.vb)]  
  
 Çağırarak bir sorgunun zorlayabilirsiniz `ToList` veya `ToArray` sorgu (anlık) veya (Ertelenmiş), aşağıdaki kodda gösterildiği gibi sorgu değişkeni üzerinde yöntemi.  
  
 [!code-vb[VbLINQFirstQuery#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_7.vb)]  
  
 Önceki örneklerde, `evensQuery3` bir sorgu değişkeni, ancak `evensList` bir listedir ve `evensArray` bir dizidir.  
  
 Kullanarak `ToList` veya `ToArray` hemen zorlamak için yürütme hemen bir sorgu yürütmek ve sonuçları bir tek koleksiyon nesnesindeki önbelleğe almak istediğiniz senaryolarda kullanışlıdır. Bu yöntemler hakkında daha fazla bilgi için bkz. [veri türlerini dönüştürme](converting-data-types.md).  
  
 Bir sorgu kullanarak yürütülecek da neden olabilir bir `IEnumerable` yöntemi gibi <xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A> yöntemi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'te lınq'e Başlarken](getting-started-with-linq.md)  
- [Yerel Çıkarım](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
- [Standart sorgu işleçlerine genel bakış (Visual Basic)](standard-query-operators-overview.md)  
- [Visual Basic'de LINQ'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
- [Sorgular](../../../../visual-basic/language-reference/queries/index.md)
