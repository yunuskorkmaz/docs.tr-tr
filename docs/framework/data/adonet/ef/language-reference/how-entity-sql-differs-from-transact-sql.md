---
title: Entity SQL ile Transact-SQL Arasındaki Farklar
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: 75ce0b00962526b76ea9f4b9fdfb0d1e1e564cdc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59162743"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a>Entity SQL ile Transact-SQL Arasındaki Farklar
Bu konuda arasındaki farklar açıklanmaktadır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ve [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].  
  
## <a name="inheritance-and-relationships-support"></a>Devralma ve ilişkiler desteği  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] doğrudan kavramsal varlık şemalarıyla çalışan ve devralma ve ilişkiler gibi kavramsal model özelliklerini de destekler.  
  
 Devralma ile çalışırken, genellikle üst örnekleri koleksiyonundan bir alt örneklerini seçmek yararlıdır. [Oftype](../../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) işlecinde [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (benzer şekilde `oftype` içinde C# dizileri) bu özelliği sunar.  
  
## <a name="support-for-collections"></a>Koleksiyonlar için destek  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Koleksiyonlar, birinci sınıf varlıklar olarak değerlendirir. Örneğin:  
  
-   Koleksiyon ifadeleri geçerli bir `from` yan tümcesi.  
  
-   `in` ve `exists` alt sorgular genelleştirilmiş koleksiyonlarınız izin vermek için.  
  
     Alt sorgu koleksiyonu türüdür. `e1 in e2` ve `exists(e)` olan [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bu işlemleri gerçekleştirmek için oluşturur.  
  
-   Ayarlama işlemleri, gibi `union`, `intersect`, ve `except`, artık koleksiyonlarda çalışır.  
  
-   Birleştirmeler koleksiyonlarda çalışır.  
  
## <a name="support-for-expressions"></a>İfadeler için destek  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] alt sorgular (tablolar) ve ifadeleri (satırları ve sütunları) sahiptir.  
  
 Koleksiyonlar ve iç içe geçmiş koleksiyonlar desteklemek için [!INCLUDE[esql](../../../../../../includes/esql-md.md)] her şey bir ifade yapar. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Daha fazla birleştirilebilir olan [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]— her ifade her yerde kullanılabilir. Sorgu ifadeleri her zaman öngörülen türleri koleksiyonlarında ve neden olabilir bir toplama ifadesi izin verilen her yerde kullanılabilir. Hakkında bilgi için [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] desteklenmeyen ifadeler [!INCLUDE[esql](../../../../../../includes/esql-md.md)], bkz: [desteklenmeyen ifadeler](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md).  
  
 Aşağıdaki tüm geçerli [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgular:  
  
```  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}   
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a>Alt sorgular Tekdüzen adların kullanımı  
 Kendi Vurgu, tablolarda verilen [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] alt sorgular bağlamsal yorumunu yapar. Örneğin, bir alt sorguda `from` yan tümcesi bir çoklu küme (tablo) olarak kabul edilir. Ancak kullanılan aynı alt sorgu `select` yan tümcesi skaler bir alt sorgu olarak kabul edilir. Benzer şekilde, sol tarafında kullanılan alt sorgu bir `in` işleci, skaler bir alt sorgu sağ tarafındaki multiset alt sorgu beklenmektedir sırada olacak şekilde değerlendirilir.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Bu farklar ortadan kaldırır. Bir ifade içinde kullanıldığı bağlamda benzemez Tekdüzen bir yorumu vardır. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] multiset alt sorgular olması için tüm alt sorgulara göz önünde bulundurur. Skaler değer Alt sorgudan isteniyorsa [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sağlar `anyelement` işleci (Bu durumda, alt) bir koleksiyon üzerinde çalışır ve koleksiyondan bir singleton değeri ayıklar.  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a>Alt sorgular için örtük zorlamayı kaçınma  
 İlgili bir yan etkisi Tekdüzen değerlendirilmesi, alt sorgularda, alt sorgularda örtük dönüştürülmesi için skaler değerler ' dir. Özellikle de [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], bir çoklu küme satır (tek bir alan ile) bir skaler değerin veri türü olan alanın örtük olarak dönüştürülür.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Bu örtük zorlama desteklemez. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tekil değer bir koleksiyondan ayıklanacak ANYELEMENT işleci sağlar ve bir `select value` yan tümcesi bir sorgu ifadesinde sırasında satır sarmalayıcı oluşturmaktan kaçınmak için.  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a>Değer seçin: Örtük satır sarmalayıcı kaçınma  
 Select yan tümcesinde bir [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] alt sorgu yan tümcesinde örtük olarak bir satır funcınner çevresindeki öğeleri oluşturur. Bu, skalerler nesneleri ve koleksiyonları oluşturamıyoruz anlamına gelir. [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] bir alan bir rowtype ve aynı veri türünde bir tekil değer arasında örtük bir zorlama sağlar.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sağlar `select value` yan tümcesi örtük satır oluşturma atlanacak. Yalnızca bir öğe belirtilebilir bir `select value` yan tümcesi. Böyle bir yan tümcesi kullanıldığında, öğeler etrafında hiçbir satır sarmalayıcı oluşturulur `select` yan tümcesi ve istediğiniz şekle koleksiyonunu oluşturulur, örneğin: `select value a`.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] row oluşturucusunda rastgele satırları oluşturmak için de sağlar. `select` projeksiyon bir veya daha fazla öğeleri ve sonuçları bir veri kayıttaki alanları ile aşağıdaki gibi alır:  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a>Sol bağıntı ve diğer ad kullanımı  
 İçinde [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], belirli bir kapsamda ifadeleri (tek bir yan tümce ister `select` veya `from`) ifadeler aynı kapsam içinde daha önce tanımlanan başvuramaz. Bazı SQL larımızın (dahil olmak üzere [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]) bunların sınırlı forms desteği `from` yan tümcesi.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] içinde sol bağıntılar genelleştirir `from` yan tümcesi ve aynı şekilde davranır. İfadelerde `from` yan tümcesi aynı yan ek söz dizimi gerek kalmadan eski tanımları (sol tanımları) başvurabilir.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Ayrıca sorguları ilgili ek kısıtlamalar getirir `group by` yan tümceleri. İfadelerde `select` yan tümcesi ve `having` gibi sorguların yan tümcesi için yalnızca başvurabilir `group by` diğer adlarını aracılığıyla anahtarları. Şu yapı geçersiz [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] ancak yer almayan [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:  
  
```  
select t.x + t.y from T as t group by t.x + t.y  
```  
  
 Bunu yapmak için [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:  
  
```  
select k from T as t group by (t.x + t.y) as k  
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a>Başvuru tabloları (koleksiyonlar) sütunları (özellikleri)  
 Sütun başvurularının tümü [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tablo diğer adıyla nitelendirilmesi gerekir. Şu yapı (varsayarak `a` geçerli bir sütun tablonun `T`) geçersiz [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] fakat [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
```  
select a from T  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Formu  
  
```  
select t.a as A from T as t  
```  
  
 Tablo diğer adları isteğe bağlı olarak `from` yan tümcesi. Tablonun adını örtük diğer ad olarak kullanılır. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Aşağıdaki biçimi de sağlar:  
  
```  
select Tab.a from Tab  
```  
  
## <a name="navigation-through-objects"></a>Nesneler aracılığıyla gezinme  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] kullanır "." gösterimi sütunları (satırının) başvuru için bir tablo. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir nesnenin özelliklerini gezinmeyi desteklemek için bu gösterim (programlama dillerinden ödünç) genişletir.  
  
 Örneğin, varsa `p` olduğundan bir ifade yazın kişi, aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] adresi bu kişinin şehrini başvuran söz dizimi.  
  
```  
p.Address.City   
```  
  
## <a name="no-support-for-"></a>Desteği *  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] Nitelenmemiş destekler * sözdizimi için tüm bir satırda ve tam bir diğer ad olarak \* sözdizimi (t\*) söz konusu tablonun alanlar için bir kısayol olarak. Ayrıca, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] özel sayısını sağlar (\*) null değerler içeren bir toplama.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] desteklemediği * yapısı. [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] Formun sorguları `select * from T` ve `select T1.* from T1, T2...` ifade edilebilir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] olarak `select value t from T as t` ve `select value t1 from T1 as t1, T2 as t2...`sırasıyla. Ayrıca, bu yapıları devralma (değer substitutability) işleme sırasında `select *` çeşitleri bildirilen türü için üst düzey özelliklerini kısıtlı.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] desteklemediği `count(*)` toplama. Bunun yerine `count(0)` kullanın.  
  
## <a name="changes-to-group-by"></a>Gruplama Ölçütü değişiklikleri  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] diğer ad kullanımı, destekler `group by` anahtarları. İfadelerde `select` yan tümcesi ve `having` yan tümcesi başvurmalıdır `group by` anahtarlarında bu diğer adları. Örneğin, bu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] söz dizimi:  
  
```  
select k1, count(t.a), sum(t.a)  
from T as t  
group by t.b + t.c as k1  
```  
  
 .. belirtiminde aşağıdaki eşdeğer [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]:  
  
```  
select b + c, count(*), sum(a)   
from T  
group by b + c  
```  
  
## <a name="collection-based-aggregates"></a>Koleksiyon tabanlı toplamaları  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] iki tür toplamlar destekler.  
  
 Koleksiyon tabanlı toplamlar koleksiyonlarda çalışır ve toplanan sonucu. Bu sorguda her yerde görünebilir ve gerekli olmayan bir `group by` yan tümcesi. Örneğin:  
  
```  
select t.a as a, count({1,2,3}) as b from T as t     
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Ayrıca SQL stili toplamalar destekler. Örneğin:  
  
```  
select a, sum(t.b) from T as t group by t.a as a  
```  
  
## <a name="order-by-clause-usage"></a>ORDER BY yan tümcesi kullanımı  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] yalnızca üstteki Seç belirtilmesi ORDER BY yan tümcesi sağlar... KAYNAK.. Burada engelleyin. İçinde [!INCLUDE[esql](../../../../../../includes/esql-md.md)] iç içe geçmiş bir ORDER BY deyimi kullanabilirsiniz ve her yerde sorguda yerleştirilebilir, ancak iç içe geçmiş bir sorgusunda sıralama korunur.  
  
```  
-- The following query will order the results by the last name  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="identifiers"></a>Tanımlayıcılar  
 İçinde [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], tanımlayıcı karşılaştırmasına geçerli veritabanı harmanlaması üzerinde temel alır. İçinde [!INCLUDE[esql](../../../../../../includes/esql-md.md)], tanımlayıcılar her zaman büyük/küçük harfe duyarsızdır ve aksan duyarlı (diğer bir deyişle, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ayıran karakter vurgulanmış ve vurgulanmamış; Örneğin, 'bir' 'ấ için' eşit değildir). [!INCLUDE[esql](../../../../../../includes/esql-md.md)] aynı görünür, ancak farklı bir karakter olarak farklı kod sayfalarından olan harf sürümleri değerlendirir. Daha fazla bilgi için [giriş karakter kümesi](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md).  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a>Transact-SQL işlevleri varlık SQL kullanılamıyor  
 Aşağıdaki [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] işlevselliği kullanılabilir değil [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
 DML  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] şu anda DML deyimleri için destek sağlar (ekleme, güncelleştirme ve silme).  
  
 DDL  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] geçerli sürümünde DDL desteği sağlar.  
  
 Kesin Programlama Karşılaştırması  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] aksine kesin programlama için destek sağlar [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]. Bunun yerine bir programlama dili kullanın.  
  
 İşlevleri gruplandırma  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] henüz destek işlevleri (örneğin, CUBE, ROLLUP ve GROUPING_SET) gruplandırma için sağlamaz.  
  
 Analitik İşlevler  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] yok (henüz) analitik işlevler için destek sağlar.  
  
 Yerleşik işlevleri, işleçler  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir alt kümesini destekler [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]işlevler ve işleçler yerleşik. Bu işleç ve işlevlerini büyük depolama sağlayıcıları tarafından desteklenmesi olasılığı düşüktür. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Sağlayıcı bildiriminde belirtilen depolama özgü işlevleri kullanır. Ayrıca, [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] yerleşik bildirmek olanak tanır ve var olan kullanıcı tanımlı deposuna İşlevler, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kullanılacak.  
  
 İpuçları  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Sorgu ipuçları mekanizmalar sağlamaz.  
  
 Sorgu sonuçları toplu işleme  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Toplu işlem sorgu sonuçları desteklemez. Örneğin, aşağıdaki geçerli [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] (toplu iş olarak gönderme):  
  
```  
select * from products;  
select * from catagories;  
```  
  
 Ancak, eşdeğer [!INCLUDE[esql](../../../../../../includes/esql-md.md)] desteklenmiyor:  
  
```  
Select value p from Products as p;  
Select value c from Categories as c;  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Yalnızca komut başına bir sonuç oluşturmayı sorgu deyimini destekler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [Desteklenmeyen İfadeler](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md)
