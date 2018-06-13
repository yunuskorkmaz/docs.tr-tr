---
title: Varlık SQL Transact-SQL nasıl farklıdır
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: d34c6933e0f19c73b954446fdf18cea7243eae0d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766302"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a>Varlık SQL Transact-SQL nasıl farklıdır
Bu konuda arasındaki farklar açıklanmaktadır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ve [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].  
  
## <a name="inheritance-and-relationships-support"></a>Devralma ve ilişkileri desteği  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] doğrudan kavramsal varlık şemalarda çalışır ve devralma ve ilişkileri gibi kavramsal model özelliklerini destekler.  
  
 Devralma ile çalışırken, genellikle bir alt örnekleri üst örnekleri koleksiyonundan seçmek yararlıdır. [Oftype](../../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) işlecinde [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (benzer şekilde `oftype` C# serileri) bu yeteneği sağlar.  
  
## <a name="support-for-collections"></a>Koleksiyonlar için destek  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] koleksiyonları birinci sınıf varlıklar olarak değerlendirir. Örneğin:  
  
-   Koleksiyon ifadelerini geçerli bir `from` yan tümcesi.  
  
-   `in` ve `exists` alt sorgulara genelleştirilmiş herhangi bir koleksiyonu izin vermek için.  
  
     Bir alt sorgu koleksiyon türüdür. `e1 in e2` ve `exists(e)` olan [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bu işlemleri gerçekleştirmek için yapıları.  
  
-   Ayarlama işlemleri, aşağıdaki gibi `union`, `intersect`, ve `except`, şimdi koleksiyonlar üzerinde çalışır.  
  
-   Birleştirmeler koleksiyonlar üzerinde çalışır.  
  
## <a name="support-for-expressions"></a>İfadeler için destek  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] alt sorgular (tablolar) ve ifadeler (satırları ve sütunları) sahiptir.  
  
 Koleksiyonlar ve iç içe geçmiş koleksiyonları desteklemek için [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir ifade her şeyi yapar. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Daha fazla birleştirilebilir [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]— her ifade herhangi bir kullanılabilir. Sorgu ifadeleri her zaman öngörülen türleri koleksiyonlarda ve neden olabilir bir toplama ifadesi kullanılabilir, herhangi bir yerde kullanılır. Hakkında bilgi için [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] desteklenmez ifadeler [!INCLUDE[esql](../../../../../../includes/esql-md.md)], bkz: [desteklenmeyen ifadeler](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md).  
  
 Aşağıdaki tüm geçerli [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgular:  
  
```  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}   
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a>Alt sorgular Tekdüzen işlenmesi  
 Kendi Vurgu tablolarda, verilen [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] alt sorgulara bağlamsal yorumu gerçekleştirir. Örneğin, bir alt sorguda `from` yan tümcesi multiset (tablo) olarak değerlendirilir. Ancak kullanılan aynı alt sorgu `select` yan tümcesi, skaler bir alt sorgu olarak değerlendirilir. Benzer şekilde, sol tarafında kullanılan alt sorgu bir `in` işleci sağ tarafında çok kümeli bir alt sorgu beklenmektedir sırada skaler bir alt sorgu olarak değerlendirilir.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Bu farklılıklar ortadan kaldırır. Bir ifade, kullanıldığı bağlamda bağlı olmayan bir Tekdüzen yorumlama sahiptir. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] çok kümeli alt sorgulara olması için tüm alt sorgulara göz önünde bulundurur. Alt sorgudan bir skaler değere isterseniz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sağlar `anyelement` koleksiyonu (Bu durumda, alt sorgu) üzerinde çalışır ve bir tek değer koleksiyondan ayıklar işleci.  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a>Alt sorgular için örtük zorlamayı önleme  
 Alt sorgular Tekdüzen işlenmesi ilgili yan etkisi skaler değerler alt sorgulara örtük dönüştürme ' dir. Özellikle [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], multiset (ile tek bir alan) satır örtük veri türü olan alanın bir skaler değerine dönüştürülür.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Bu örtük zorlama desteklemez. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] singleton değeri bir koleksiyondan çıkarmak için ANYELEMENT işleci sağlar ve bir `select value` bir sorgu ifadesi sırasında satır sarmalayıcı oluşturmamak için yan tümcesi.  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a>Seçme değerini: örtük satır sarmalayıcı önleme  
 Select yan tümcesinde bir [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] alt sorgu yan tümcesinde örtük olarak bir satır sarmalayıcı öğelerin çevresindeki oluşturur. Bu, skalerler veya nesneler koleksiyonları oluşturamıyoruz anlamına gelir. [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] rowtype bir alan ve aynı veri türünde bir tek değer arasında örtük bir zorlama sağlar.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sağlar `select value` örtük satır yapım atlamak için yan tümcesi. Yalnızca bir öğe belirtilebilir bir `select value` yan tümcesi. Bu tür bir yan tümcesi kullanıldığında, hiçbir satır sarmalayıcı öğeleri geçici oluşturulan `select` yan tümcesi ve istediğiniz şekli koleksiyonu üretilebilir, örneğin: `select value a`.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] row Oluşturucusu rasgele satırları oluşturmak için de sağlar. `select` projeksiyon bir veya daha fazla öğe ve sonuçları bir veri kaydındaki alanları ile aşağıdaki gibi alır:  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a>Sol bağıntı ve diğer ad  
 İçinde [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], belirli bir kapsamda ifadeleri (tek bir yan tümce ister `select` veya `from`) daha önce aynı kapsamda tanımlanan ifadeleri başvuramaz. Bazı Portekizce Lehçesi SQL (de dahil olmak üzere [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]) biri ile sınırlı forms desteği `from` yan tümcesi.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] içinde sol bağıntıları genelleştirir `from` yan tümcesi ve aynı şekilde davranır. İfadelerde `from` yan tümcesi başvuru önceki tanımları (sol tanımları) ek sözdizimi gerek kalmadan aynı yan tümcesinde.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Ayrıca sorguları ilgili ek kısıtlamalar getirir `group by` yan tümceleri. İfadelerde `select` yan tümcesi ve `having` sorgularını yan tümcesi yalnızca başvurabilir `group by` benzersizse anahtarlarında. Şu yapı geçersiz [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] ancak bulunmayan [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:  
  
```  
select t.x + t.y from T as t group by t.x + t.y  
```  
  
 Bunu yapmak için [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:  
  
```  
select k from T as t group by (t.x + t.y) as k  
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a>Başvuruda bulunan sütunlar (Özellikler) tabloları (koleksiyonu)  
 Tüm sütun başvuruları [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tablo diğer ad ile nitelenmiş olmalıdır. Şu yapı (varsayılarak `a` geçerli bir sütun tablonun `T`) geçersiz [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] de [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
```  
select a from T  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Formu  
  
```  
select t.a as A from T as t  
```  
  
 Tablo diğer adları isteğe bağlı olarak `from` yan tümcesi. Tablonun adını örtük diğer ad olarak kullanılır. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Aşağıdaki form de sağlar:  
  
```  
select Tab.a from Tab  
```  
  
## <a name="navigation-through-objects"></a>Nesneleri gezinmeyi  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] kullanır "." (bir satırı) sütunlarının başvuran gösterimi bir tablo. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir nesnenin özelliklerini gezinmeyi desteklemek için bu gösterim (programlama dilleri ödünç) genişletir.  
  
 Örneğin, varsa `p` olan bir ifadenin türünü kişi, aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bu kişinin adresini Şehir başvuran söz dizimi.  
  
```  
p.Address.City   
```  
  
## <a name="no-support-for-"></a>Desteği *  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] Nitelenmemiş destekleyen * sözdizimi tüm satır ve tam bir diğer ad olarak \* sözdizimi (t.\*) bu tabloyu alanlar için bir kısayol olarak. Ayrıca, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] için özel bir sayı verir (\*) null değerler içeren toplama.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] desteklemediği * yapısı. [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] formu sorguları `select * from T` ve `select T1.* from T1, T2...` ifade edilebilir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] olarak `select value t from T as t` ve `select value t1 from T1 as t1, T2 as t2...`sırasıyla. Ek olarak, bu yapıları devralma (değer substitutability) işleme sırasında `select *` çeşitleri bildirilen en üst düzey özelliklerini kısıtlı.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] desteklemediği `count(*)` toplama. Bunun yerine `count(0)` kullanın.  
  
## <a name="changes-to-group-by"></a>Grup tarafından yapılan değişiklikler  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] diğer ad olarak destekleyen `group by` anahtarları. İfadelerde `select` yan tümcesi ve `having` yan tümcesi başvurmalıdır `group by` bu diğer adları anahtarlarında. Örneğin, bu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sözdizimi:  
  
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
  
## <a name="collection-based-aggregates"></a>Koleksiyon tabanlı toplar  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] iki tür toplamalar destekler.  
  
 Koleksiyon tabanlı toplamalar koleksiyonlar üzerinde çalışır ve toplanan sonucu. Bu sorguda herhangi bir yerde görünebilir ve gerekli olmadığı bir `group by` yan tümcesi. Örneğin:  
  
```  
select t.a as a, count({1,2,3}) as b from T as t     
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Ayrıca SQL stili toplamalar destekler. Örneğin:  
  
```  
select a, sum(t.b) from T as t group by t.a as a  
```  
  
## <a name="order-by-clause-usage"></a>ORDER BY yan tümcesi kullanımı  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] yalnızca en üstteki Seç belirtilmesini ORDER BY yan tümceleri sağlar... KAYNAK.. Burada engelleyin. İçinde [!INCLUDE[esql](../../../../../../includes/esql-md.md)] iç içe geçmiş bir ORDER BY ifadesi kullanabilirsiniz ve her yerden sorguda yerleştirilebilir, ancak iç içe bir sorgu sıralama korunur.  
  
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
 İçinde [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], tanımlayıcı karşılaştırma geçerli veritabanı harmanlamasının dayanır. İçinde [!INCLUDE[esql](../../../../../../includes/esql-md.md)], tanımlayıcıları her zaman büyük küçük harfe duyarlı ve aksan duyarlı (diğer bir deyişle, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ayırt vurgulanmış ve olarak karakter arasında; Örneğin, 'bir' 'ấ' eşit değildir). [!INCLUDE[esql](../../../../../../includes/esql-md.md)] aynı görünür, ancak farklı karakter olarak farklı kod sayfalarından olan harf sürümlerini değerlendirir. Daha fazla bilgi için bkz: [giriş karakter kümesi](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md).  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a>Transact-SQL işlevsellik varlık SQL yok  
 Aşağıdaki [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] işlevselliği kullanılabilir değil [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
 DML  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] şu anda DML deyimleri için destek sağlar (Ekle, Güncelleştir, Sil).  
  
 DDL  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Geçerli sürümde DDL desteği sağlar.  
  
 Kesinlik temelli programlama  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] aksine kesinlik temelli programlama için destek sağlar [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]. Bunun yerine bir programlama dili kullanın.  
  
 İşlevleri gruplandırma  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] henüz destek işlevleri (örneğin, CUBE, ROLLUP ve GROUPING_SET) gruplandırmak için sağlamaz.  
  
 Analitik İşlevler  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] yok (henüz) analitik işlevler için destek sağlar.  
  
 Yerleşik İşlevler, işleçler  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir alt kümesini destekler [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]yerleşik işlevler ve işleçler. Bu işleçler ve İşlevler temel depolama sağlayıcıları tarafından desteklenen olasılığı yüksektir. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Sağlayıcı bildiriminde bildirilen deposu özgü işlevlerini kullanır. Ayrıca, [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] yerleşik bildirmek sağlar ve kullanıcı tanımlı varolan depolama işlevleri için [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kullanmak için.  
  
 İpuçları  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Sorgu ipuçları için mekanizmaları sağlamaz.  
  
 Sorgu sonuçları toplu işleme  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Toplu sorgu sonuçları desteklemez. Örneğin, aşağıdaki geçerli [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] (toplu iş olarak gönderme):  
  
```  
select * from products;  
select * from catagories;  
```  
  
 Ancak, eşdeğer [!INCLUDE[esql](../../../../../../includes/esql-md.md)] desteklenmiyor:  
  
```  
Select value p from Products as p;  
Select value c from Categories as c;  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] yalnızca komutu her bir sonuç oluşturan sorgu deyimini destekler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [Desteklenmeyen İfadeler](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md)
