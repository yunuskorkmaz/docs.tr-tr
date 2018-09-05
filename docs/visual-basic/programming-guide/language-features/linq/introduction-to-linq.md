---
title: Visual Basic'de LINQ'e Giriş
ms.date: 08/28/2018
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
ms.openlocfilehash: 0b163ac4af4e487ccab4c18b7907eba5a31e5779
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43509058"
---
# <a name="introduction-to-linq-in-visual-basic"></a>Visual Basic'de LINQ'e Giriş
Dil ile tümleşik sorgu (LINQ), Visual Basic sorgu özellikleri ekler ve her tür veri ile çalışırken, basit ve güçlü özellikler sağlar. Bir sorguyu işlenmek üzere bir veritabanına göndermek veya her arama yaptığınız veri türü için farklı sorgu sözdizimiyle çalışmak yerine LINQ sorguları Visual Basic dilinin bir parçası olarak tanıtır. Veri türünden bağımsız olarak birleştirilmiş sözdizimi kullanır.  
  
 LINQ, bir SQL Server veritabanı, XML, bellek içi diziler ve koleksiyonlar, ADO.NET veri kümeleri veya LINQ destekleyen herhangi bir uzak veya yerel veri kaynağı sorgu verileri olanak tanır. Tüm ortak Visual Basic Dil öğeleri ile bunu yapabilirsiniz. Sorgularınızı Visual Basic dilinde yazıldığından, sorgu sonuçlarınız türü kesin olarak belirtilmiş nesneler olarak döndürülür. Bu nesneler, daha hızlı kod yazmanızı ve derleme zamanında yerine çalışma zamanında sorgularınızdaki hataları yakalamasına olanak sağlayan IntelliSense desteği sunar. LINQ sorguları Sonuçları iyileştirmek için ek sorgu kaynakları kullanılabilir. Kullanıcıların, kolayca görüntüleyin ve sorgu sonuçlarınız değiştirme denetimlere de bağlanabilir.  
  
 Örneğin, aşağıdaki kod örneği, bir koleksiyondan Müşteri listesini döndüren bir LINQ Sorgu ve bunları kendi konuma göre gruplandıran gösterir.  
  
 [!code-vb[VbVbalrIntroToLINQ#1](codesnippet/VisualBasic/introduction-to-linq_1.vb)]  
  
## <a name="running-the-examples"></a>Örnekleri çalıştırma  
 Giriş ve örnekleri çalıştırmak için [LINQ sorgusunun yapısı](#structure-of-a-linq-query) bölümünde, müşteriler ve siparişler listesi döndüren aşağıdaki kodu ekleyin.  
  
 [!code-vb[VbVbalrIntroToLINQ#31](codesnippet/VisualBasic/introduction-to-linq_2.vb)]  
  
## <a name="linq-providers"></a>LINQ sağlayıcıları  
 A *LINQ sağlayıcısı* Visual Basic LINQ sorgularınızı sorgulanan veri kaynağına eşler. LINQ sorgusu yazdığınızda, sağlayıcı sorguyu alır ve yürütmek veri kaynağı doğrulayabilecek komutlara çevirir. Sağlayıcı kaynaktan verileri sorgu sonucunuzu oluşturan nesnelere de dönüştürür. Güncelleştirmeleri veri kaynağına gönderdiğinizde, son olarak, bu nesneleri verilere dönüştürür.  
  
 Visual Basic aşağıdaki LINQ sağlayıcıları içerir.  
  
|Sağlayıcı|Açıklama|  
|---|---|  
|Nesnelere LINQ|LINQ to Objects sağlayıcısı, bellek içi koleksiyonlarda ve dizilerde sorgu olanak tanır. Bir nesne destekliyorsa <xref:System.Collections.IEnumerable> veya <xref:System.Collections.Generic.IEnumerable%601> arabirimi, LINQ to Objects sağlayıcısı sorgulamanız için bunu etkinleştirir.<br /><br /> LINQ to Objects sağlayıcısı içeri aktararak etkinleştirebilirsiniz <xref:System.Linq> tüm Visual Basic projeleri için varsayılan olarak içeri aktarılan ad alanı.<br /><br /> LINQ to Objects sağlayıcısı hakkında daha fazla bilgi için bkz: [LINQ to Objects'in](../../concepts/linq/linq-to-objects.md).|  
|LINQ - SQL|SQL sağlayıcı için LINQ sorgusu ve SQL Server veritabanındaki verileri değiştirmenize olanak sağlar. Bu, bir uygulama tablolar ve bir veritabanındaki nesneler için nesne modeli eşlemek kolaylaştırır.<br /><br /> Visual Basic Object Relational Designer (O/R Tasarımcısı) dahil ederek LINQ to SQL ile çalışmak daha kolay hale getirir. Bu tasarımcı, bir uygulamada veritabanındaki nesnelerle eşleşen bir nesne modeli oluşturmak için kullanılır. O/R Tasarımcısı ayrıca depolanan yordamları eşlemek üzere işlevsellik sağlar ve yaramaz <xref:System.Data.Linq.DataContext> veritabanı ile iletişimi yönetir ve iyimser eşzamanlılık denetimlerinin durumunu depolar nesnesidir.<br /><br /> LINQ to SQL sağlayıcısı hakkında daha fazla bilgi için bkz: [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md). Nesne İlişkisel Tasarımcısı hakkında daha fazla bilgi için bkz. [LINQ to SQL araçlarını Visual Studio'da](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).|  
|LINQ - XML|XML sağlayıcı için LINQ, XML sorgulamanıza ve değiştirmenize olanak sağlar. Bellek içi XML değiştirebilir veya, XML gelen ve XML kaydetmek için bir dosya yükleyebilirsiniz.<br /><br /> Ayrıca, XML sağlayıcı için LINQ, XML değişmez değerleri ve Visual Basic kodunuzda doğrudan XML yazmanıza olanak tanıyan XML eksen özellikleri sağlar. Daha fazla bilgi için [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md).|  
|LINQ - DataSet|DataSet sağlayıcı için LINQ Sorgu ve güncelleştirme verilerde sağlayan bir [!INCLUDE[vstecado](~/includes/vstecado-md.md)] veri kümesi. LINQ basitleştirin ve sorgulama, toplama ve veri kümenizde verileri güncelleştirme, özelliklerini genişletmek için veri kümelerini kullanan uygulamaları ekleyebilirsiniz.<br /><br /> Daha fazla bilgi için [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).|  
  
## <a name="structure-of-a-linq-query"></a>LINQ sorgusunun yapısı  
 Bir LINQ sorgusu sık olarak adlandırılan bir *sorgu ifadesi*, veri kaynaklarını ve sorgu için yineleme değişkenlerini tanımlayan sorgu yan tümcelerinin bileşiminden oluşur. Bir sorgu ifadesinde, kaynak verilere uygulanacak sıralama, filtreleme, gruplama ve katılma veya hesaplamalar için yönergeleri de içerebilir. Sorgu ifadesi sözdizimi SQL sözdizimine benzer ancak; Bu nedenle, söz dizimi çoğunu tanıdık gelebilir.  
  
 Sorgu ifadesi ile başlayan bir `From` yan tümcesi. Bu yan tümce sorgu ve kaynak verilerin her bir öğesine başvurmak için kullanılan değişkenleri için kaynak verilerini tanımlar. Bu değişkenler adlı *aralık değişkenleri* veya *yineleme değişkenleri*. `From` Dışında bir sorgu için yan tümcesi gereklidir `Aggregate` sorguları, burada `From` yan tümcesi, isteğe bağlıdır. Kapsamı ve kaynağı sorgunun tümcelerinde tanımlandıktan sonra `From` veya `Aggregate` yan tümceleri, sorguyu daraltmak için sorgu yan tümcelerinin birleşimini dahil edebilirsiniz. Sorgu yan tümceleri hakkında daha fazla ayrıntı için Visual Basic LINQ Sorgu işleçleri, bu konunun ilerleyen bölümlerinde bkz. Örneğin, aşağıdaki sorguyu Müşteri verilerinin kaynak koleksiyonunu tanımlar `customers` değişkeni ve adında bir yineleme değişkeni `cust`.  
  
 [!code-vb[VbVbalrIntroToLINQ#2](codesnippet/VisualBasic/introduction-to-linq_3.vb)]  
  
 Bu geçerli bir sorgu tarafından kendisine örnektir; ancak sonucu iyileştirmek için daha fazla sorgu yan tümcesi eklediğinizde sorgu daha güçlü hale gelir. Örneğin, ekleyebileceğiniz bir `Where` sonucu bir veya daha fazla değere göre filtrelemek için yan tümcesi. Sorgu ifadeleri tek satırlık bir kod işlevleridir. yalnızca, ek sorgu yan tümcelerini sorgunun sonuna ekleyebilirsiniz. Bir sorguyu metin alt çizgi kullanarak okunabilirliği artırmak için birden fazla satıra bölebilir (\_) satır devamlılığı karakteri. Aşağıdaki kod örneği içeren bir sorgu örneğini gösterir. bir `Where` yan tümcesi.  
  
 [!code-vb[VbVbalrIntroToLINQ#3](codesnippet/VisualBasic/introduction-to-linq_4.vb)]  
  
 Başka bir güçlü sorgu yan tümcesi `Select` yan tümcesi veri kaynağından yalnızca seçili alanları döndürmenizi sağlar. LINQ sorguları, numaralandırılabilir türü kesin belirlenmiş nesne koleksiyonları döndürür. Bir sorgu, anonim türlerin veya adlandırılmış türlerin koleksiyonunu döndürebilir. Kullanabileceğiniz `Select` veri kaynağından tek bir alan döndürülecek yan tümcesi. Bunu yaptığınızda, döndürülen koleksiyon türü o tek alanın türüdür. Ayrıca `Select` yan tümcesi veri kaynağından birden fazla alan döndürmek için. Bunu yaptığınızda, döndürülen koleksiyon türü yeni bir anonim tür ' dir. İçin belirtilen adlandırılmış tür alanlarını sorgu tarafından döndürülen alanları da eşleştirebilirsiniz. Aşağıdaki kod örneği, bir veri kaynağından seçilen alanlarından alınan verilerle doldurulmuş üyeleri olan anonim türlerin koleksiyonunu döndüren bir sorgu ifadesini gösterir.  
  
 [!code-vb[VbVbalrIntroToLINQ#4](codesnippet/VisualBasic/introduction-to-linq_5.vb)]  
  
 LINQ sorguları ayrıca birden fazla veri kaynağını birleştirmek ve tek bir sonuç döndürmek için kullanılabilir. Bu bir veya daha fazla yapılabilir `From` yan tümcesi veya kullanarak `Join` veya `Group Join` sorgu yan tümceleri. Aşağıdaki kod örneği, müşteri ile sipariş verilerini birleştiren ve müşteri ile sipariş verilerini içeren anonim türlerin koleksiyonunu döndüren bir sorgu ifadesini gösterir.  
  
 [!code-vb[VbVbalrIntroToLINQ#5](codesnippet/VisualBasic/introduction-to-linq_6.vb)]  
  
 Kullanabileceğiniz `Group Join` müşteri nesnesi koleksiyonu içeren hiyerarşik sorgu sonucunu oluşturmak için yan tümcesi. Her müşteri nesnesi, o müşteriye ait tüm siparişleri koleksiyonu içeren bir özelliğe sahiptir. Aşağıdaki kod örneği, müşteri ile sipariş verilerini bir hiyerarşi sonucu olarak birleştiren ve anonim türlerin koleksiyonunu döndüren bir sorgu ifadesini gösterir. Sorgu içeren bir tür döndüren bir `CustomerOrders` müşterinin sipariş verilerinin bir koleksiyonunu içeren özellik. Ayrıca bir `OrderTotal` siparişlerine bu müşterinin tüm siparişlerine ilişkin toplamı içeren özelliği. (Bu sorgu bir LEFT OUTER JOIN ile eşdeğerdir.)  
  
 [!code-vb[VbVbalrIntroToLINQ#6](codesnippet/VisualBasic/introduction-to-linq_7.vb)]  
  
 Güçlü sorgu ifadeleri oluşturmak için kullanabileceğiniz birçok ek LINQ sorgu işleci vardır. Bu konunun sonraki bölümünde, bir sorgu ifadesine dahil edebileceğiniz çeşitli sorgu yan tümceleri açıklanır. Visual Basic sorgu yan tümceleri hakkında daha fazla ayrıntı için bkz: [sorguları](../../../../visual-basic/language-reference/queries/index.md).  
  
## <a name="visual-basic-linq-query-operators"></a>Visual Basic LINQ Sorgu işleçleri  

Sınıflarda <xref:System.Linq> ad alanı ve LINQ sorgularını destekleyen diğer ad oluşturmak ve sorgular, uygulamanızın ihtiyaçlarına göre daraltmak için çağırabileceğiniz yöntemler içerir. Visual Basic aşağıdaki ortak sorgu yan tümcesi için anahtar sözcükler içerir. Visual Basic sorgu yan tümceleri hakkında daha fazla ayrıntı için bkz: [sorguları](../../../language-reference/queries/index.md).

### <a name="from-clause"></a>From yan tümcesi

Ya da bir [ `From` yan tümcesi](../../../../visual-basic/language-reference/queries/from-clause.md) veya `Aggregate` yan tümcesi, bir sorguya başlamak için gereklidir. A `From` yan tümcesi, bir kaynak koleksiyonu ve bir sorgu için yineleme değişkeni belirtir. Örneğin:

[!code-vb[VbVbalrIntroToLINQ#7](codesnippet/VisualBasic/introduction-to-linq_8.vb)]

### <a name="select-clause"></a>Select tümcesi

İsteğe bağlı. A [ `Select` yan tümcesi](../../../../visual-basic/language-reference/queries/select-clause.md) bir sorgu için yineleme değişkenleri kümesi bildirir. Örneğin:

[!code-vb[VbVbalrIntroToLINQ#8](codesnippet/VisualBasic/introduction-to-linq_9.vb)]

Varsa bir `Select` yan tümcesi belirtilmediyse, sorgu için yineleme değişkenleri tarafından belirtilen yineleme değişkenlerinden oluşur `From` veya `Aggregate` yan tümcesi.

### <a name="where-clause"></a>Where yan tümcesi

İsteğe bağlı. A [ `Where` yan tümcesi](../../../../visual-basic/language-reference/queries/where-clause.md) bir sorgu için filtreleme koşulunu belirtir. Örneğin:

[!code-vb[VbVbalrIntroToLINQ#9](codesnippet/VisualBasic/introduction-to-linq_10.vb)]

### <a name="order-by-clause"></a>Order By yan tümcesi]

| İsteğe bağlı. Bir [ `Order By` yan tümcesi](../../../../visual-basic/language-reference/queries/order-by-clause.md) sorguda sütunlar için sıralama düzenini belirtir. Örneğin:

[!code-vb[VbVbalrIntroToLINQ#10](codesnippet/VisualBasic/introduction-to-linq_11.vb)]

### <a name="join-clause"></a>Join tümcesi

İsteğe bağlı. A [ `Join` yan tümcesi](../../../../visual-basic/language-reference/queries/join-clause.md) iki koleksiyonu tek bir koleksiyon halinde birleştirir. Örneğin:

[!code-vb[VbVbalrIntroToLINQ#11](codesnippet/VisualBasic/introduction-to-linq_12.vb)]

### <a name="group-by-clause"></a>Group By tümcesi

İsteğe bağlı. A [ `Group By` yan tümcesi](../../../../visual-basic/language-reference/queries/group-by-clause.md) bir sorgu sonucunun öğelerini gruplandırır. Her grup için toplama işlevleri uygulamak için kullanılabilir. Örneğin:

[!code-vb[VbVbalrIntroToLINQ#12](codesnippet/VisualBasic/introduction-to-linq_13.vb)]

### <a name="group-join-clause"></a>Group Join tümcesi

İsteğe bağlı. A [ `Group Join` yan tümcesi](../../../../visual-basic/language-reference/queries/group-join-clause.md) iki koleksiyonu tek bir hiyerarşik koleksiyon halinde birleştirir. Örneğin:

[!code-vb[VbVbalrIntroToLINQ#13](codesnippet/VisualBasic/introduction-to-linq_14.vb)]

### <a name="aggregate-clause"></a>Aggregate tümcesi

Ya da bir [ `Aggregate` yan tümcesi](../../../../visual-basic/language-reference/queries/aggregate-clause.md) veya `From` yan tümcesi, bir sorguya başlamak için gereklidir. Bir `Aggregate` yan tümcesi bir koleksiyona bir veya daha fazla toplama işlevi uygular. Örneğin, kullanabileceğiniz `Aggregate` aşağıdaki örnekte olduğu gibi bir sorgu tarafından döndürülen tüm öğelerin toplamını hesaplamak için yan tümcesi.

[!code-vb[VbVbalrIntroToLINQ#14](codesnippet/VisualBasic/introduction-to-linq_15.vb)]

Ayrıca `Aggregate` yan tümcesi bir sorguyu değiştirmek için. Örneğin, kullanabileceğiniz `Aggregate` ilişkili sorgu koleksiyonu üzerinde bir hesaplama gerçekleştirmek için yan tümcesi. Örneğin:

[!code-vb[VbVbalrIntroToLINQ#15](codesnippet/VisualBasic/introduction-to-linq_16.vb)]

### <a name="let-clause"></a>Let tümcesi

İsteğe bağlı. A [ `Let` yan tümcesi](../../../../visual-basic/language-reference/queries/let-clause.md) bir değeri hesaplar ve sorguda yeni bir değişkene atar. Örneğin:

[!code-vb[VbVbalrIntroToLINQ#16](codesnippet/VisualBasic/introduction-to-linq_17.vb)]

### <a name="distinct-clause"></a>Distinct tümcesi

İsteğe bağlı. A `Distinct` yan tümce sorgu sonuçlarındaki yinelenen değerleri ortadan kaldırmak için geçerli yineleme değişkeni değerlerini sınırlandırır. Örneğin:

[!code-vb[VbVbalrIntroToLINQ#17](codesnippet/VisualBasic/introduction-to-linq_18.vb)]

### <a name="skip-clause"></a>Skip tümcesi

İsteğe bağlı. A [ `Skip` yan tümcesi](../../../../visual-basic/language-reference/queries/skip-clause.md) belirtilen sayıda bir koleksiyondaki öğeleri atlar ve kalan öğeleri döndürür. Örneğin:

[!code-vb[VbVbalrIntroToLINQ#18](codesnippet/VisualBasic/introduction-to-linq_19.vb)]

### <a name="skip-while-clause"></a>Skip While tümcesi

İsteğe bağlı. A [ `Skip While` yan tümcesi](../../../../visual-basic/language-reference/queries/skip-while-clause.md) belirtilen bir koşulu olduğu sürece bir koleksiyondaki öğeleri atlar `true` ve kalan öğeleri döndürür. Örneğin:

[!code-vb[VbVbalrIntroToLINQ#19](codesnippet/VisualBasic/introduction-to-linq_20.vb)]

### <a name="take-clause"></a>Take tümcesi

İsteğe bağlı. A [ `Take` yan tümcesi](../../../../visual-basic/language-reference/queries/take-clause.md) bir koleksiyon başlangıcından belirtilen bir bitişik öğelerin sayısını döndürür. Örneğin:

[!code-vb[VbVbalrIntroToLINQ#20](codesnippet/VisualBasic/introduction-to-linq_21.vb)]

### <a name="take-while-clause"></a>Take While tümcesi

İsteğe bağlı. A [ `Take While` yan tümcesi](../../../../visual-basic/language-reference/queries/take-while-clause.md) belirtilen bir koşulu olduğu sürece öğeleri bir koleksiyona dahil `true` ve kalan öğeleri atlar. Örneğin:

[!code-vb[VbVbalrIntroToLINQ#21](codesnippet/VisualBasic/introduction-to-linq_22.vb)]
  
## <a name="use-additional-linq-query-features"></a>Ek LINQ Sorgu özelliklerini kullanın  
  
LINQ tarafından sağlanan numaralandırılabilir ve sorgulanabilir türleri üyelerini çağırarak ek LINQ Sorgu özelliklerini kullanabilirsiniz. Bir sorgu ifadesinin sonucu üzerinde belirli bir sorgu işlecini çağırarak bu ek özellikleri kullanabilirsiniz. Örneğin, aşağıdaki örnekte <xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType> iki sorgunun sonuçlarını tek bir sorgu sonucunda birleştirmek için yöntemi. Kullandığı <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> sorgu sonucunu genel listeye döndürmek için yöntemi.
  
 [!code-vb[VbVbalrIntroToLINQ#22](codesnippet/VisualBasic/introduction-to-linq_23.vb)]  
  
 Ek LINQ özellikleri hakkında daha fazla ayrıntı için bkz: [standart sorgu işleçlerine genel bakış](../../concepts/linq/standard-query-operators-overview.md).  
  
## <a name="connect-to-a-database-by-using-linq-to-sql"></a>LINQ to SQL kullanarak bir veritabanına bağlanma  
 Visual Basic'te, LINQ to SQL dosyasını kullanarak erişmek istediğiniz saklı yordamlar, tablolar ve görünümler gibi SQL Server veritabanı nesneleri tanımlar. LINQ to SQL dosyası, .dbml uzantısına sahiptir.  
  
 Geçerli bir SQL Server veritabanı bağlantınız olduğunda ekleyebileceğiniz bir **LINQ to SQL sınıfları** projenize öğe şablonu. Bu, Object Relational Designer (O/R Tasarımcısı) görüntülenir. O/R Tasarımcısı kodunuzda erişmek istediğiniz öğeleri sürükleyin sağlar **Sunucu Gezgini**/**veritabanı Gezgini** Tasarımcı yüzeyine. LINQ to SQL dosyası ekler bir <xref:System.Data.Linq.DataContext> projenize nesne. Bu nesne için tablolar ve görünümler, erişim ve yöntemleri çağırmak istediğiniz saklı yordamları için istediğiniz özellikler ve Koleksiyonlar içerir. LINQ to SQL (.dbml) dosyası için yaptığınız değişiklikleri kaydettikten sonra bu nesneler, kodunuzda başvurarak erişebilirsiniz <xref:System.Data.Linq.DataContext> O/R tasarımcısı tarafından tanımlanan nesne. <xref:System.Data.Linq.DataContext> Nesne projeniz temel alınarak, LINQ to SQL dosyası adı. Örneğin, Northwind.dbml olarak adlandırılan SQL dosyası için bir LINQ oluşturacak bir <xref:System.Data.Linq.DataContext> adlı nesne `NorthwindDataContext`.  
  
 Adım adım yönergeleri içeren örnekler için bkz [nasıl yapılır: veritabanını sorgulama](how-to-query-a-database-by-using-linq.md) ve [nasıl yapılır: bir saklı yordam çağırma](how-to-call-a-stored-procedure-by-using-linq.md).  
  
## <a name="visual-basic-features-that-support-linq"></a>LINQ'i destekleyen Visual Basic özellikleri  
 Visual Basic LINQ kullanımını kolaylaştırır ve LINQ sorguları gerçekleştirmek için yazmanız gereken kod miktarını azaltmak başka önemli özellikler içerir. Bunlar aşağıdakileri içerir:  
  
-   **Anonim türler**, yeni bir sorgu sonucuna göre türü oluşturun etkinleştirin.  
  
-   **Örtülü türdeki değişkenler**, bir tür belirterek erteleme etkinleştirmek ve Infer sorgu sonucuna göre türü olanak sağlar.  
  
-   **Genişletme yöntemleri**, türün kendisini değiştirmeden, kendi yöntemlerinizle mevcut türü genişletmek etkinleştirin.  
  
 Ayrıntılar için bkz [Visual Basic özellikleri, destek LINQ](../../concepts/linq/features-that-support-linq.md).  
  
## <a name="deferred-and-immediate-query-execution"></a>Ertelenmiş ve anlık sorgu yürütme

 Sorgu yürütme, sorgu oluşturmadan farklıdır. Sorgu oluşturulduktan sonra yürütmesi ayrı bir mekanizma tarafından tetiklenir. Sorguda tanımlanan hemen sonra yürütülebilir (*hemen yürütme*), veya tanım saklanır ve sorgu daha sonra yürütülebilir (*ertelenmiş yürütme*).  
  
 Bir sorgu oluşturduğunuzda varsayılan olarak, sorgunun kendisi anında yürütmeye başlamaz. Bunun yerine, sorgu tanımı sorgu sonucuna başvuru için kullanılan bir değişkende depolanır. Ne zaman sorgu sonucu değişkenine erişilen kodda daha sonra olduğu gibi bir `For…Next` döngü, sorgu yürütülür. Bu işlem olarak adlandırılır *ertelenmiş yürütme*.  
  
 Sorgular, ayrıca bunlar, olarak adlandırılan tanımlandığında çalıştırılabilir *hemen yürütme*. Sorgu sonucundaki öğelere erişim gerektiren bir yöntem uygulayarak anında yürütme tetikleyebilirsiniz. Bu gibi bir toplama işlevinin dahil olmak üzere sonucu olabilir `Count`, `Sum`, `Average`, `Min`, veya `Max`. Toplama işlevleri hakkında daha fazla bilgi için bkz: [Aggregate tümcesi](../../../language-reference/queries/aggregate-clause.md).  
  
 Kullanarak `ToList` veya `ToArray` yöntemleri de anında yürütmeyi zorunlu. Hemen bir sorgu yürütmek ve sonuçları önbelleğe istediğinizde bu yararlı olabilir. Bu yöntemler hakkında daha fazla bilgi için bkz. [veri türlerini dönüştürme](../../concepts/linq/converting-data-types.md).  
  
 Sorgu yürütme hakkında daha fazla bilgi için bkz: [bilgisayarınızı ilk LINQ sorgusu yazma](../../concepts/linq/writing-your-first-linq-query.md).  
  
## <a name="xml-in-visual-basic"></a>Visual Basic'de XML  
 XML değişmez değerleri Visual Basic'te XML özelliklerini içerir ve kolayca oluşturmanıza olanak sağlar, XML eksen özellikleri erişmek, sorgu ve XML kodunuzu değiştirin. XML değişmez değerleri, kodunuzda doğrudan XML yazmanıza olanak sağlar. Visual Basic Derleyicisi, XML bir birinci sınıf veri nesnesi gibi davranır.  
  
 Aşağıdaki kod örneği, bir XML öğesi oluşturun, onun alt öğelerine ve özniteliklerine erişmek ve öğe içeriklerinin LINQ kullanarak sorgulama gösterilmektedir.  
  
 [!code-vb[VbXmlSamples#8](../../../language-reference/operators/codesnippet/VisualBasic/introduction-to-linq_24.vb)]  
  
 Daha fazla bilgi için [XML](../xml/index.md).  
  
## <a name="related-resources"></a>İlgili kaynaklar  
  
|Konu|Açıklama|  
|---|---|  
|[XML](../../language-features/xml/index.md)|Visual Basic'te, sorgulanabilir ve XML Visual Basic kodunuzda birinci sınıf veri nesneleri olarak eklemenizi sağlayan XML özelliklerini açıklar.|  
|[Sorgular](../../../language-reference/queries/index.md)|Visual Basic'te kullanılabilir sorgu yan tümceleri hakkında başvuru bilgileri sağlar.|  
|[LINQ (dil ile tümleşik sorgu)](../../concepts/linq/index.md)|LINQ için genel bilgileri, programlama yönergelerini ve örnekleri içerir.|  
|[LINQ to SQL](~/docs/framework/data/adonet/sql/linq/index.md)|LINQ to SQL için genel bilgileri, programlama yönergelerini ve örnekleri içerir.|  
|[LINQ to Objects](../../concepts/linq/linq-to-objects.md)|LINQ to Objects için genel bilgileri, programlama yönergelerini ve örnekleri içerir.|  
|[LINQ to ADO.NET (Portal Sayfası)](../../concepts/linq/linq-to-adonet-portal-page.md)|ADO.NET'e LINQ için genel bilgileri, programlama yönergelerini ve örnekleri bağlantılarını içerir.|  
|[LINQ to XML](../../concepts/linq/linq-to-xml.md)|LINQ to XML için genel bilgileri, programlama yönergelerini ve örnekleri içerir.|  
  
## <a name="how-to-and-walkthrough-topics"></a>Nasıl yapılır ve izlenecek yol konuları
 [Nasıl yapılır: veritabanını sorgulama](how-to-query-a-database-by-using-linq.md)  
  
 [Nasıl yapılır: bir saklı yordamı çağırma](how-to-call-a-stored-procedure-by-using-linq.md)  
  
 [Nasıl yapılır: bir veritabanındaki verileri değiştirme](how-to-modify-data-in-a-database-by-using-linq.md)  
  
 [Nasıl yapılır: birleştirmeleri kullanarak veri birleştirme](how-to-combine-data-with-linq-by-using-joins.md)  
  
 [Nasıl yapılır: sorgu sonuçlarını sıralama](how-to-sort-query-results-by-using-linq.md)  
  
 [Nasıl yapılır: sorgu sonuçlarını filtreleme](how-to-filter-query-results-by-using-linq.md)  
  
 [Nasıl yapılır: Count, Sum veya Average verisi](how-to-count-sum-or-average-data-by-using-linq.md)  
  
 [Nasıl yapılır: bir sorgu sonucunda en düşük ve en fazla değeri bulma](how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)  
  
 [Nasıl yapılır: Güncelleştirme, ekleme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama (O/R Tasarımcısı)](https://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)  
  
## <a name="featured-book-chapters"></a>Özel Kitap bölümleri  
 [Bölüm 17: LINQ](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652502(v=orm.10)) içinde [Visual Basic 2008 programlama](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652504(v=orm.10))  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ (dil ile tümleşik sorgu)](../../concepts/linq/index.md)  
- [LINQ to XML Visual Basic'de genel bakış](../../language-features/xml/overview-of-linq-to-xml.md)  
- [LINQ to DataSet Genel Bakış](~/docs/framework/data/adonet/linq-to-dataset-overview.md)  
- [LINQ to SQL](~/docs/framework/data/adonet/sql/linq/index.md)  
- [Visual Studio'daki LINQ to SQL Araçları](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)  
- [DataContext Metotları (O/R Tasarımcısı)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
