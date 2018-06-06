---
title: Visual Basic'de LINQ'e Giriş
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], about LINQ in Visual Basic queries
- query execution [LINQ in Visual Basic]
- range variables [Visual Basic]
- LINQ [Visual Basic]
- LINQ [Visual Basic], about LINQ in Visual Basic
- query expressions [LINQ in Visual Basic]
- LINQ
- deferred execution
- iteration variables [Visual Basic]
ms.assetid: 3047d86e-0d49-40e2-928b-dc02e46c7984
ms.openlocfilehash: 7e6d299bafff2a5a34a8f0942ba6dc9c25fcdd83
ms.sourcegitcommit: fc70fcb9c789b6a4aefcdace46f3643fd076450f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2018
ms.locfileid: "34805743"
---
# <a name="introduction-to-linq-in-visual-basic"></a>Visual Basic'de LINQ'e Giriş
Dil ile tümleşik sorgu (LINQ) Visual Basic'e sorgu özellikleri ekler ve her türlü verileri çalıştığınızda basit ve güçlü özellikler sağlar. İşlenmek üzere bir veritabanına bir sorgu gönderme veya her aradığınız veri türü için farklı sorgu sözdizimi ile çalışma yerine LINQ sorgularını Visual Basic dilinin bir parçası olarak tanıtır. Veri türü ne olursa olsun birleşik bir sözdizimi kullanır.  
  
 LINQ sağlar, sorgu verileri bir SQL Server veritabanı, XML, bellek içi diziler ve koleksiyonlar, [!INCLUDE[vstecado](~/includes/vstecado-md.md)] veri kümeleri veya diğer uzak veya yerel veri kaynağı LINQ destekleyen. Tüm ortak Visual Basic Dil öğeleri ile bunu yapabilirsiniz. Sorgularınızın Visual Basic dilinde yazılır olduğundan, sorgu sonuçları kesin türü belirtilmiş nesneler olarak döndürülür. Bu nesneler, kodu daha hızlı yazmanıza ve derleme zamanında yerine çalışma zamanında sorgularınızda hatalarını yakalama sağlar IntelliSense destekler. LINQ sorgularını sonuçları daraltmak için ek sorgu kaynağı olarak kullanılabilir. Böylece kullanıcılar, kolayca görüntüleyebilir ve sorgu sonuçlarınızı değiştirmek için denetimleri de bağlanabilir.  
  
 Örneğin, aşağıdaki kod örneğinde, müşterilerin listesini koleksiyondan döndüren bir LINQ Sorgu ve konumlarını göre grupları gösterir.  
  
 [!code-vb[VbVbalrIntroToLINQ#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_1.vb)]  
  
 Bu konuda, aşağıdaki alanlarda hakkında bilgiler bulacaksınız:  
  
-   [Örnekleri çalıştırma](#RunningtheExamples)  
  
-   [LINQ sağlayıcıları](#LINQProviders)  
  
-   [LINQ Sorgu yapısı](#StructureOfALINQQuery)  
  
-   [Visual Basic LINQ Sorgu işleçleri](#VisualBasicLINQQueryOperators)  
  
-   [LINQ-SQL kullanarak bir veritabanına bağlanma](#ConnectingToADatabase)  
  
-   [LINQ'i Destekleyen Visual Basic Özellikleri](#VisualBasicFeaturesThatSupportLINQ)  
  
-   [Ertelenmiş ve hemen sorgu yürütme](#QueryExecution)  
  
-   [Visual Basic'te XML](#XMLInVisualBasic)  
  
-   [İlgili kaynaklar](#RelatedResources)  
  
-   [Nasıl yapılır ve gözden geçirme konuları](#HowToAndWalkthroughTopics)  
  
##  <a name="RunningtheExamples"></a> Örnekleri çalıştırma  
 Giriş ve "Yapısı, bir LINQ Sorgu" bölümünde örnekleri çalıştırmak için müşteriler ve siparişler listesini döndürür aşağıdaki kodu ekleyin.  
  
 [!code-vb[VbVbalrIntroToLINQ#31](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_2.vb)]  
  
##  <a name="LINQProviders"></a> LINQ sağlayıcıları  
 A *LINQ sağlayıcısı* sorgulanan veri kaynağı, Visual Basic LINQ sorgularını eşler. LINQ Sorgu yazdığınızda, sağlayıcı bu sorguyu alır ve veri kaynağı yürütme yapabileceği komutlara çevirir. Sağlayıcı ayrıca veri kaynağından Sorgu sonucunuz nesnelerini dönüştürür. Veri kaynağına güncelleştirmeleri gönderdiğinizde, son olarak, bu nesneleri verilere dönüştürür.  
  
 Visual Basic aşağıdaki LINQ sağlayıcıları içerir.  
  
|Sağlayıcı|Açıklama|  
|---|---|  
|Nesnelere LINQ|Nesneleri sağlayıcısına LINQ Sorgu bellek içi koleksiyonları ve diziler sağlar. Bir nesne ya da destekliyorsa <xref:System.Collections.IEnumerable> veya <xref:System.Collections.Generic.IEnumerable%601> arabirimi, LINQ to nesneleri sağlayıcısı, sorgu olanak sağlar.<br /><br /> İçeri aktararak nesneleri sağlayıcısına LINQ etkinleştirebilirsiniz <xref:System.Linq> tüm Visual Basic projeleri için varsayılan olarak içeri aktarılan ad alanı.<br /><br /> Nesneleri sağlayıcısına LINQ hakkında daha fazla bilgi için bkz: [nesnelere LINQ](http://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9).|  
|LINQ - SQL|LINQ-SQL sağlayıcısı, sorgu ve SQL Server veritabanındaki verileri değiştirme olanak sağlar. Bu, tablolar ve bir veritabanındaki nesneler için bir uygulama için nesne modeli eşlemek kolaylaştırır.<br /><br /> Visual Basic nesne ilişkisel Tasarımcısı (O/R Tasarımcısı) dahil ederek LINQ-SQL çalışmak daha kolay hale getirir. Bu tasarımcı nesne modeli bir veritabanındaki nesneler için eşleşen bir uygulama oluşturmak için kullanılır. O/R Tasarımcısı ayrıca saklı yordamlar eşlemek için işlevsellik sağlar ve verecek işlevler <xref:System.Data.Linq.DataContext> veritabanı ile iletişim yönetir ve depolar iyimser eşzamanlılık denetimleri için Durum nesnesidir.<br /><br /> LINQ-SQL sağlayıcısı hakkında daha fazla bilgi için bkz: [LINQ-SQL](../../../../framework/data/adonet/sql/linq/index.md). Nesne İlişkisel Tasarımcısı hakkında daha fazla bilgi için bkz: [LINQ-SQL Visual Studio Araçları](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).|  
|LINQ - XML|LINQ-XML sağlayıcısı, sorgu ve XML değiştirmenize olanak sağlar. Bellek içi XML'yi değiştirebilir, veya XML gelen ve XML kaydetme bir dosyaya yükleyebilirsiniz.<br /><br /> Ayrıca, XML sağlayıcısına LINQ XML değişmez değerleri ve XML doğrudan Visual Basic kodunda yazmak etkinleştirmeniz XML eksen özellikleri sağlar. Daha fazla bilgi için bkz: [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md).|  
|LINQ - DataSet|Veri kümesi sağlayıcısına LINQ Sorgu ve güncelleştirme verilerde sağlayan bir [!INCLUDE[vstecado](~/includes/vstecado-md.md)] veri kümesi. LINQ gücünü basitleştirmek ve yeteneklerinizi sorgulama, toplama ve Veri kümenizi verileri güncelleştirmek için genişletmek için veri kümeleri kullanan uygulamalar ekleyebilirsiniz.<br /><br /> Daha fazla bilgi için bkz: [LINQ-DataSet](../../../../framework/data/adonet/linq-to-dataset.md).|  
  
##  <a name="StructureOfALINQQuery"></a> LINQ Sorgu yapısı  
 LINQ Sorgu genellikle olarak bilinir bir *sorgu ifadesi*, veri kaynakları ve sorgu için yineleme değişkenleri tanımlamak sorgu yan tümceleri bileşimini oluşur. Bir sorgu ifadesi kaynak verilere uygulanacak sıralama, filtreleme, gruplama ve katılma veya hesaplamalar için yönergeleri de içerir. Sorgu ifade sözdizimi SQL söz dizimi benzer; Bu nedenle, sözdizimi çoğunu hakkında bilgi bulabilirsiniz.  
  
 Bir sorgu ifadesi ile başlayan bir `From` yan tümcesi. Bu yan tümcesi bir sorgu ve veri kaynağını her öğe için ayrı ayrı başvurmak için kullanılan değişkenler için kaynak verilerini tanımlar. Bu değişkenler adlı *aralık değişkenleri* veya *yineleme değişkenleri*. `From` Yan tümcesi dışında bir sorgu için gereklidir `Aggregate` sorguları yeri `From` yan tümcesi isteğe bağlı. Kapsamını ve sorgunun kaynağı olarak tanımlanan sonra `From` veya `Aggregate` yan tümceleri, sorguyu daraltmak için sorgu yan tümceleri herhangi bir birleşimini içerebilir. Sorgu yan tümceleri hakkında daha fazla ayrıntı için Visual Basic LINQ Sorgu işleçleri bu konunun ilerleyen bölümlerinde bkz. Örneğin, aşağıdaki sorguyu kaynak koleksiyonu Müşteri verilerinin tanımlayan `customers` değişkeni ve adlı bir yineleme değişkeni `cust`.  
  
 [!code-vb[VbVbalrIntroToLINQ#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_3.vb)]  
  
 Bu örnekte, geçerli bir sorgu tek başına, Ancak, sonuç iyileştirmek için daha fazla sorgu yan tümceleri eklediğinizde, sorguyu daha güçlü olur. Örneğin, ekleyebileceğiniz bir `Where` sonucu bir veya daha fazla değerlerine göre filtre uygulamak için yan tümcesi. Sorgu ifadeleri tek satırlık bir kod; yine de uygun istiyor musunuz? Ek sorgu yan tümceleri yalnızca sorgu sonuna ekleyebilirsiniz. Birden çok alt çizgi (_) satır devamlılığı karakteri kullanarak okunabilirliğini artırmak için metin satırı arasında bir sorgu bölün. Aşağıdaki kod örneği içeren bir sorgu örneği gösterilmektedir bir `Where` yan tümcesi.  
  
 [!code-vb[VbVbalrIntroToLINQ#3](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_4.vb)]  
  
 Başka bir güçlü sorgu yan tümcesi `Select` yan tümcesi, yalnızca seçili alanları veri kaynağından döndürülecek sağlar. LINQ sorguları güçlü şekilde yazılan nesnelerin numaralandırılabilir koleksiyonları döndürür. Bir sorgu anonim türler veya adlandırılmış türler koleksiyonu döndürebilir. Kullanabileceğiniz `Select` yalnızca tek bir alanı veri kaynağından döndürülecek yan tümcesi. Bunu yaptığınızda, döndürülen koleksiyon türü, tek bir alan türüdür. Aynı zamanda `Select` birden çok alan veri kaynağından döndürülecek yan tümcesi. Bunu yaptığınızda, döndürülen koleksiyonu yeni bir anonim tür türüdür. Belirtilen bir adlandırılmış tür alanları için sorgu tarafından döndürülen alanları eşleştirir. Aşağıdaki kod örneği, bir veri kaynağından seçilen alanlarından verilerle doldurulur üyelere sahip anonim türler koleksiyonu döndüren bir sorgu ifadesi gösterilir.  
  
 [!code-vb[VbVbalrIntroToLINQ#4](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_5.vb)]  
  
 LINQ sorgularını, birden çok veri kaynağı birleştirmek ve tek bir sonuç için de kullanılabilir. Bu bir veya daha fazla ile yapılabilir `From` yan tümceleri, veya kullanarak `Join` veya `Group Join` sorgu yan tümceleri. Aşağıdaki kod örneğinde, müşteri ve sipariş verileri birleştirir ve anonim türler müşteri ve sipariş verilerini içeren koleksiyonu döndüren bir sorgu ifadesi gösterilir.  
  
 [!code-vb[VbVbalrIntroToLINQ#5](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_6.vb)]  
  
 Kullanabileceğiniz `Group Join` müşteri nesneler koleksiyonunu içeren bir hiyerarşik sorgu sonucu oluşturmak için yan tümcesi. Her müşteri nesnesi, o müşteri için tüm siparişleri koleksiyonunu içeren bir özelliğe sahiptir. Aşağıdaki kod örneğinde, müşteri ve sipariş verileri hiyerarşik bir sonucu olarak birleştirir ve anonim türler koleksiyonu döndüren bir sorgu ifadesi gösterilir. Sorgu içeren bir tür döndüren bir `CustomerOrders` müşteri siparişi verilerinin bir koleksiyonunu içeren özelliği. Ayrıca içeren bir `OrderTotal` o müşteri için tüm siparişler için toplamları toplamını içeren özelliği. (Bu sorguyu bir LEFT OUTER JOIN için eşdeğerdir.)  
  
 [!code-vb[VbVbalrIntroToLINQ#6](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_7.vb)]  
  
 Güçlü sorgu ifadeleri oluşturmak için kullanabileceğiniz birkaç ek LINQ Sorgu işleçleri vardır. Bu konunun sonraki bölümlerinde sorgu ifadesinde dahil çeşitli sorgu yan tümceleri açıklanır. Visual Basic sorgu yan tümceleri hakkında daha fazla ayrıntı için bkz: [sorguları](../../../../visual-basic/language-reference/queries/queries.md).  
  
##  <a name="VisualBasicLINQQueryOperators"></a> Visual Basic LINQ Sorgu işleçleri  
 Sınıflarda <xref:System.Linq> ad alanı ve LINQ sorgularını destekler diğer ad alanları oluşturmak ve uygulamanızın gereksinimlerine göre sorgular daraltmak için arama yöntemleri içerir. Visual Basic tarafından aşağıdaki tabloda açıklandığı gibi en yaygın sorgu yan tümceleri için anahtar sözcükleri içerir.  
  
|Terim|Tanım|  
|---|---|  
|[From Yan Tümcesi](../../../../visual-basic/language-reference/queries/from-clause.md)|Ya da bir `From` yan tümcesinin veya bir `Aggregate` yan tümcesi, bir sorgu başlamak için gereklidir. A `From` yan tümcesi, bir kaynak koleksiyonu ve bir sorgu için bir yineleme değişkeni belirtir. Örneğin:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#7](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_8.vb)]|  
|[Select Yan Tümcesi](../../../../visual-basic/language-reference/queries/select-clause.md)|İsteğe bağlı. Yineleme değişkenleri bir sorgu için bir dizi bildirir. Örneğin:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#8](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_9.vb)]<br /><br /> Varsa bir `Select` yan tümcesi belirtilmezse, sorgu için yineleme değişkenleri tarafından belirtilen yineleme değişkenleri oluşur `From` veya `Aggregate` yan tümcesi.|  
|[Where Yan Tümcesi](../../../../visual-basic/language-reference/queries/where-clause.md)|İsteğe bağlı. Bir sorgu için bir filtre koşulu belirtir. Örneğin:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#9](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_10.vb)]|  
|[Order By Yan Tümcesi](../../../../visual-basic/language-reference/queries/order-by-clause.md)|İsteğe bağlı. Sütunlar için sıralama düzenini sorguda belirtir. Örneğin:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#10](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_11.vb)]|  
|[Join Yan Tümcesi](../../../../visual-basic/language-reference/queries/join-clause.md)|İsteğe bağlı. Tek bir koleksiyon iki koleksiyonlara birleştirir. Örneğin:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#11](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_12.vb)]|  
|[Group By Yan Tümcesi](../../../../visual-basic/language-reference/queries/group-by-clause.md)|İsteğe bağlı. Sorgu sonucu öğelerini gruplandırır. Her gruba toplama işlevleri uygulamak için kullanılabilir. Örneğin:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#12](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_13.vb)]|  
|[Group Join Yan Tümcesi](../../../../visual-basic/language-reference/queries/group-join-clause.md)|İsteğe bağlı. Tek bir hiyerarşik koleksiyon iki koleksiyonlara birleştirir. Örneğin:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#13](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_14.vb)]|  
|[Aggregate Yan Tümcesi](../../../../visual-basic/language-reference/queries/aggregate-clause.md)|Ya da bir `From` yan tümcesinin veya bir `Aggregate` yan tümcesi, bir sorgu başlamak için gereklidir. Bir `Aggregate` yan tümcesi bir veya daha fazla toplama işlevleri bir koleksiyona uygulanır. Örneğin, kullanabileceğiniz `Aggregate` bir sorgu tarafından döndürülen tüm öğelerin toplamı hesaplamak için yan tümcesi.<br /><br /> [!code-vb[VbVbalrIntroToLINQ#14](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_15.vb)]<br /><br /> Aynı zamanda `Aggregate` yan tümcesini bir sorguyu değiştirin. Örneğin, kullanabileceğiniz `Aggregate` ilişkili sorgu koleksiyon üzerinde bir hesaplama gerçekleştirmek için yan tümcesi.<br /><br /> [!code-vb[VbVbalrIntroToLINQ#15](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_16.vb)]|  
|[Let Yan Tümcesi](../../../../visual-basic/language-reference/queries/let-clause.md)|İsteğe bağlı. Bir değeri hesaplar ve sorgu yeni bir değişkene atar. Örneğin:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#16](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_17.vb)]|  
|[Distinct Yan Tümcesi](../../../../visual-basic/language-reference/queries/distinct-clause.md)|İsteğe bağlı. Sorgu sonuçları yinelenen değerler ortadan kaldırmak için geçerli yineleme değişkeni değerlerini kısıtlar. Örneğin:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#17](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_18.vb)]|  
|[Skip Yan Tümcesi](../../../../visual-basic/language-reference/queries/skip-clause.md)|İsteğe bağlı. Belirtilen bir koleksiyondaki öğelerin sayısı atlar ve kalan öğeleri döndürür. Örneğin:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#18](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_19.vb)]|  
|[Skip While Yan Tümcesi](../../../../visual-basic/language-reference/queries/skip-while-clause.md)|İsteğe bağlı. Belirtilen bir koşul olduğu sürece bir koleksiyondaki öğelerin atlar `true` ve kalan öğeleri döndürür. Örneğin:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#19](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_20.vb)]|  
|[Take Yan Tümcesi](../../../../visual-basic/language-reference/queries/take-clause.md)|İsteğe bağlı. Belirtilen sayıda bitişik öğeyi koleksiyonu başından döndürür. Örneğin:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#20](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_21.vb)]|  
|[Take While Yan Tümcesi](../../../../visual-basic/language-reference/queries/take-while-clause.md)|İsteğe bağlı. Belirtilen bir koşul olduğu sürece bir koleksiyondaki öğeleri içeren `true` ve kalan öğeleri atlar. Örneğin:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#21](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_22.vb)]|  
  
 Visual Basic sorgu yan tümceleri hakkında daha fazla ayrıntı için bkz: [sorguları](../../../../visual-basic/language-reference/queries/queries.md).  
  
 LINQ tarafından sağlanan numaralandırılabilir ve sorgulanabilir türleri arama üyeleri tarafından ek LINQ Sorgu özellikleri kullanabilirsiniz. Bir sorgu ifadesi sonucu üzerinde belirli bir sorgu işleci çağırarak bu ek özellikler kullanabilirsiniz. Örneğin, aşağıdaki örnek kullanımları kod <xref:System.Linq.Enumerable.Union%2A> iki sorguların sonuçlarını bir sorgu sonucu birleştirmek için yöntem. Kullandığı <xref:System.Linq.Enumerable.ToList%2A> yöntemi sorgu sonucu genel bir liste olarak döndürür.  
  
 [!code-vb[VbVbalrIntroToLINQ#22](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_23.vb)]  
  
 Ek LINQ özellikleri hakkında daha fazla bilgi için bkz [standart sorgu işleçlerine genel bakış](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).  
  
##  <a name="ConnectingToADatabase"></a> LINQ-SQL kullanarak bir veritabanına bağlanma  
 Visual Basic'te, SQL Server veritabanı nesneleri tabloları, görünümleri ve saklı yordamlar SQL dosyası için bir LINQ kullanarak erişim sağlamak istediğiniz gibi tanımlayın. Bir LINQ to SQL dosyası .dbml uzantısına sahip.  
  
 Bir SQL Server veritabanı için geçerli bir bağlantı varsa, ekleyebileceğiniz bir **LINQ'ten SQL'e sınıflarını** projenize öğe şablonu. Bu nesne ilişkisel Tasarımcısı (O/R Tasarımcısı) görüntüler. O/R Tasarımcısı kodunuzdan erişmek için istediğiniz öğeleri sürükleyin sağlar **Sunucu Gezgini**/**Database Explorer** Tasarımcı yüzeyine. LINQ-SQL dosya ekler bir <xref:System.Data.Linq.DataContext> projenize nesnesi. Bu nesnenin özellikleri ve tabloları ve görünümleri, aramak istediğiniz saklı yordamlar için yöntemleri ve erişimi istediğiniz koleksiyonları içerir. LINQ-SQL (.dbml) dosyası için yaptığınız değişiklikleri kaydettikten sonra bu nesnelerin kodunuzda başvurarak erişebilirsiniz <xref:System.Data.Linq.DataContext> O/R tasarımcısı tarafından tanımlanan nesnesi. <xref:System.Data.Linq.DataContext> Projenizi adlı nesne temel alarak, LINQ to SQL dosya adı. Örneğin, bir LINQ to Northwind.dbml adlı SQL dosyası oluşturacak bir <xref:System.Data.Linq.DataContext> adlı nesne `NorthwindDataContext`.  
  
 Adım adım yönergeleri ile ilgili örnekler için bkz: [nasıl yapılır: veritabanını sorgulama](../../../../visual-basic/programming-guide/language-features/linq/how-to-query-a-database-by-using-linq.md) ve [nasıl yapılır: bir saklı yordam çağrısı](../../../../visual-basic/programming-guide/language-features/linq/how-to-call-a-stored-procedure-by-using-linq.md).  
  
##  <a name="VisualBasicFeaturesThatSupportLINQ"></a> Lınq'i destekleyen Visual Basic özellikleri  
 Visual Basic, LINQ kullanımını basitleştirir ve LINQ sorgularını gerçekleştirmek için yazmanız gereken kod miktarını azaltmak diğer önemli özellikler içerir. Bunlar aşağıdakileri içerir:  
  
-   **Anonim türler**, bir sorgu sonucuna göre yeni bir türü oluşturmak etkinleştirin.  
  
-   **Değişken türü örtük olarak belirlenmiş**, bir tür belirleme erteleneceği etkinleştirmek ve let derleyici Infer sorgu sonucuna türü.  
  
-   **Genişletme yöntemleri**, mevcut bir türle türü değiştirmeden kendi yöntemleriyle genişletmek etkinleştirin.  
  
 Ayrıntılar için bkz [Visual Basic özellikleri, destek LINQ](../../../../visual-basic/programming-guide/concepts/linq/features-that-support-linq.md).  
  
##  <a name="QueryExecution"></a> Ertelenmiş ve hemen sorgu yürütme  
 Sorgu yürütme sorgu oluşturma ayrıdır. Bir sorgu oluşturulduktan sonra yürütülmesinin ayrı bir mekanizma tarafından tetiklenir. Sorguda tanımlanan hemen yürütülebilir (*hemen yürütme*), veya tanımı depolanabilir ve sorgu daha sonra çalıştırılabilir (*yürütme ertelenmiş*).  
  
 Bir sorgu oluşturduğunuzda varsayılan olarak, sorgu hemen çalıştırma. Bunun yerine, sorgu tanımı sorgu sonucu başvurmak için kullanılan değişkende depolanır. Sorgu sonucu değişkeni eriştiği kodu, daha sonra gibi bir `For…Next` döngü, sorgu gerçekleştirilir. Bu işlem olarak adlandırılır *yürütme ertelenmiş*.  
  
 Sorguları da yürütülebilir bunlar, hangi olarak adlandırılır tanımlandığında *hemen yürütme*. Sorgu sonucunun tek tek öğelere erişim gerektiren bir yöntemi uygulayarak hemen yürütme tetikleyebilir. Bu gibi bir toplama işlevi dahil olmak üzere sonucu olabilir `Count`, `Sum`, `Average`, `Min`, veya `Max`. Toplama işlevleri hakkında daha fazla bilgi için bkz: [Aggregate tümcesi](../../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Kullanarak `ToList` veya `ToArray` yöntemleri de hemen yürütme zorla. Sorguyu hemen çalıştırmak ve sonuçları önbelleğe istediğinizde bu yararlı olabilir. Bu yöntemler hakkında daha fazla bilgi için bkz: [veri türlerini dönüştürme](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md).  
  
 Sorgu yürütme hakkında daha fazla bilgi için bkz: [yazma bilgisayarınızı ilk LINQ sorgusu](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
##  <a name="XMLInVisualBasic"></a> Visual Basic'de XML  
 XML değişmez değerleri Visual Basic'te XML özellikleri içerir ve kolayca oluşturmanıza olanak tanır, XML eksen özellikleri erişim, sorgu ve XML kodunuzu değiştirmek. XML değişmez değerleri kodunuzda doğrudan XML yazmanızı sağlar. Visual Basic derleyici XML birinci sınıf veri nesnesi olarak değerlendirir.  
  
 Aşağıdaki kod örneği, bir XML öğesi oluşturmak, kendi alt öğeleri ve özniteliklerinin erişmek ve öğenin içeriğini LINQ kullanarak sorgulama gösterilmektedir.  
  
 [!code-vb[VbXmlSamples#8](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/introduction-to-linq_24.vb)]  
  
 Daha fazla bilgi için bkz: [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md).  
  
##  <a name="RelatedResources"></a> İlgili kaynaklar  
  
|Konu|Açıklama|  
|---|---|  
|[XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)|Visual Basic'te, sorgulanabilir ve birinci sınıf veri nesneleri, Visual Basic kodundaki olarak XML eklemenizi sağlamak XML özellikleri açıklar.|  
|[Sorgular](../../../../visual-basic/language-reference/queries/queries.md)|Visual Basic'te kullanılabilir sorgu yan tümceleri hakkında başvuru bilgileri sağlar.|  
|[LINQ (dil ile tümleşik sorgu)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)|Genel bilgiler, programlama kılavuzu ve örnekleri için LINQ içerir.|  
|[LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)|LINQ-SQL genel bilgiler, programlama yönergeler ve örnekleri içerir.|  
|[LINQ to Objects](http://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9)|Nesnelere LINQ genel bilgiler, programlama yönergeler ve örnekleri içerir.|  
|[LINQ to ADO.NET (Portal Sayfası)](http://msdn.microsoft.com/library/dd7d3c6a-ff98-47e9-a1a7-2d4cfc42d150)|LINQ to için genel bilgileri, programlama kılavuzu ve örnek bağlantılarını içerir [!INCLUDE[vstecado](~/includes/vstecado-md.md)].|  
|[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13)|LINQ-XML için genel bilgileri, programlama kılavuzu ve örnekleri içerir.|  
  
##  <a name="HowToAndWalkthroughTopics"></a> Nasıl yapılır ve gözden geçirme konuları  
 [Nasıl yapılır: veritabanını sorgulama](how-to-query-a-database-by-using-linq.md)  
  
 [Nasıl yapılır: bir saklı yordamı çağırma](how-to-call-a-stored-procedure-by-using-linq.md)  
  
 [Nasıl yapılır: veritabanındaki verileri değiştirme](how-to-modify-data-in-a-database-by-using-linq.md)  
  
 [Nasıl yapılır: birleştirmeleri kullanarak veri birleştirme](how-to-combine-data-with-linq-by-using-joins.md)  
  
 [Nasıl yapılır: sorgu sonuçlarını sıralama](how-to-sort-query-results-by-using-linq.md)  
  
 [Nasıl yapılır: sorgu sonuçlarını filtreleme](how-to-filter-query-results-by-using-linq.md)  
  
 [Nasıl yapılır: Count, Sum veya Average verisi](how-to-count-sum-or-average-data-by-using-linq.md)  
  
 [Nasıl yapılır: bir sorgu sonucunda en düşük ve en büyük değeri Bul](how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)  
  
 [Nasıl yapılır: güncelleştirme, ekleme ve silme (O/R Tasarımcısı) gerçekleştirmek için saklı yordamlar atayın](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)  
  
## <a name="featured-book-chapters"></a>Özel Kitap Bölümleri  
 [Bölüm 17: LINQ](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652502(v=orm.10)) içinde [Visual Basic 2008 programlama](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652504(v=orm.10))  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ (dil ile tümleşik sorgu)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [LINQ-XML Visual Basic'de genel bakış](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 [LINQ to DataSet Genel Bakış](../../../../framework/data/adonet/linq-to-dataset-overview.md)  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
 [LINQ-SQL Visual Studio Araçları](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)  
 [DataContext yöntemleri (O/R Tasarımcısı)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
