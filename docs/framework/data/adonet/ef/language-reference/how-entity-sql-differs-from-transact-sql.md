---
title: Entity SQL ile Transact-SQL Arasındaki Farklar
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: 299cb9bbe90c72619cf809a8fc673fca456bd6fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150237"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a>Entity SQL ile Transact-SQL Arasındaki Farklar
Bu konu, Transact-SQL arasındaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] farkları açıklar.  
  
## <a name="inheritance-and-relationships-support"></a>Kalıtım ve İlişkiler Desteği  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]doğrudan kavramsal varlık şemaları ile çalışır ve kalıtım ve ilişkiler gibi kavramsal model özelliklerini destekler.  
  
 Devralma yla çalışırken, genellikle bir alt tür örneklerini bir üst tür örnekleri koleksiyonundan seçmek yararlıdır. (C# Sequences'dekine [!INCLUDE[esql](../../../../../../includes/esql-md.md)] `oftype` benzer) [oftipi](oftype-entity-sql.md) işleci bu özelliği sağlar.  
  
## <a name="support-for-collections"></a>Koleksiyonlar için Destek  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]koleksiyonları birinci sınıf varlıklar olarak ele alır. Örnek:  
  
- Koleksiyon ifadeleri bir `from` yan tümcede geçerlidir.  
  
- `in`ve `exists` alt sorgular herhangi bir koleksiyona izin verecek şekilde genelleştirilmiştir.  
  
     Alt sorgu, bir tür koleksiyondur. `e1 in e2`ve `exists(e)` bu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işlemleri gerçekleştirmek için yapılardır.  
  
- " ve `union` `intersect` `except`, şimdi koleksiyonlar üzerinde çalışır gibi işlemleri ayarlayın.  
  
- Birleştirmeler koleksiyonlarda çalışır.  
  
## <a name="support-for-expressions"></a>İfadeler için Destek  
 Transact-SQL alt sorguları (tablolar) ve ifadeler (satırlar ve sütunlar) vardır.  
  
 Koleksiyonları ve iç içe koleksiyonları [!INCLUDE[esql](../../../../../../includes/esql-md.md)] desteklemek için, her şeyi bir ifade yapar. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Transact-SQL'den daha fazla kullanılabilir— her ifade her yerde kullanılabilir. Sorgu ifadeleri her zaman yansıtılan türlerin koleksiyonlarıyla sonuçlanır ve koleksiyon ifadesine izin verilen her yerde kullanılabilir. Desteklenmeyen [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Transact-SQL ifadeleri hakkında bilgi [için](unsupported-expressions-entity-sql.md)bkz.  
  
 Geçerli [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorguların tümü şunlardır:  
  
```sql  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a>Alt Sorguların Tek Tip Tedavisi  
 Transact-SQL, tablolara verdiği önem göz önüne alındığında alt sorguların bağlamsal yorumunu gerçekleştirir. Örneğin, `from` yan tümcedeki bir alt sorgu çok ayarlı (tablo) olarak kabul edilir. Ancak `select` yan tümcede kullanılan aynı alt sorgu skaler alt sorgu olarak kabul edilir. Benzer şekilde, bir `in` işleç sol tarafında kullanılan bir alt sorgu skaler alt sorgu olarak kabul edilirken, sağ tarafında çok ayarlı bir alt sorgu olması bekleniyor.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]bu farklılıkları ortadan kaldırır. Bir ifadenin kullanıldığı içeriğe bağlı olmayan tek bir yorumu vardır. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]tüm alt sorguları çok ayarlı alt sorgular olarak kabul eder. Alt sorgudan skaler bir değer isteniyorsa, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir koleksiyon üzerinde çalışan `anyelement` işleci sağlar (bu durumda, alt sorgu) ve koleksiyondan singleton değerini ayıklar.  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a>Alt Sorgular için Örtük Zorlamalardan Kaçınma  
 Alt sorguların tek tip tedavisinin ilgili yan etkisi, alt sorguların skaler değerlere örtülü olarak dönüştürülmesidir. Özellikle, Transact-SQL'de, (tek bir alana sahip) bir satır kümesi dolaylı olarak, veri türü alanın değeri olan skaler bir değere dönüştürülür.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]bu örtük zorlamayı desteklemez. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]ANYELEMENT işlecinin bir koleksiyondan singleton değerini `select value` ayıklamasını ve sorgu ifadesi sırasında satır sarıcı oluşturmamasını önlemek için bir yan tümce sağlar.  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a>Değer Seçin: Örtük Satır Sarıcı'dan Kaçınma  
 Transact-SQL alt sorgusundaki select yan tümcesi, yan tümcedeki öğelerin etrafında dolaylı olarak bir satır sarıcı oluşturur. Bu, skaler veya nesnelerin koleksiyonlarını oluşturamayacağımız anlamına gelir. Transact-SQL, bir alana sahip bir satır türü ile aynı veri türünün singleton değeri arasında örtük bir zorlama sağlar.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]örtük `select value` satır konstrüksiyonu atlamak için yan tümce sağlar. Bir yan tümcede `select value` yalnızca bir öğe belirtilebilir. Böyle bir yan tümce kullanıldığında, `select` yan tümcedeki öğelerin etrafına satır sarıcı oluşturulmaz ve örneğin `select value a`istenen şeklin bir koleksiyonu oluşturulabilir: .  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]ayrıca satır oluşturucuya rasgele satırlar oluşturmasını sağlar. `select`projeksiyonda bir veya daha fazla öğe alır ve aşağıdaki gibi alanları içeren bir veri kaydı yla sonuçlanır:  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a>Sol Korelasyon ve Diğer Adlama  
 Transact-SQL'de, belirli bir kapsamdaki ifadeler `select` (örneğin veya `from`) aynı kapsamda daha önce tanımlanan ifadelere başvuruyapamaz. SQL'in bazı lehçeleri (Transact-SQL dahil) `from` yan tümcedeki sınırlı formları destekler.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]`from` maddedeki sol bağıntıları genelleştirir ve bunları eşit davranır. Yan tümcedeki `from` ifadeler, ek sözdizimine gerek kalmadan aynı yan tümcedeki önceki tanımlara (soldaki tanımlar) başvuru yapabilir.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]yan tümceleri içeren `group by` sorgulara ek kısıtlamalar da uygular. Bu tür `select` sorguların `having` yan tümcesindeki ve `group by` yan tümcesindeki ifadeler yalnızca diğer adlar aracılığıyla anahtarlara başvurabilir. Aşağıdaki yapı Transact-SQL'de geçerlidir [!INCLUDE[esql](../../../../../../includes/esql-md.md)]ancak aşağıdaki nde değildir:  
  
```sql  
SELECT t.x + t.y FROM T AS t group BY t.x + t.y
```  
  
 Bunu yapmak [!INCLUDE[esql](../../../../../../includes/esql-md.md)]için:  
  
```sql  
SELET k FROM T AS t GROUP BY (t.x + t.y) AS k
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a>Tabloların (Koleksiyonların Özellikleri) Başvuru Sütunları (Özellikleri)  
 Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sütun başvuruları tablo diğer adı ile nitelikli olmalıdır. Aşağıdaki yapı (tablonun `a` `T`geçerli bir sütunu olduğunu varsayarak) Transact-SQL'de [!INCLUDE[esql](../../../../../../includes/esql-md.md)]geçerlidir, ancak .  
  
```sql  
SELECT a FROM T
```  
  
 Form, [!INCLUDE[esql](../../../../../../includes/esql-md.md)]  
  
```sql  
SELECT t.a AS A FROM T AS t
```  
  
 Tablo diğer adları `from` yan tümcede isteğe bağlıdır. Tablonun adı örtük takma ad olarak kullanılır. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]aşağıdaki formu da sağlar:  
  
```sql  
SELET Tab.a FROM Tab
```  
  
## <a name="navigation-through-objects"></a>Nesneler arasında gezinme  
 Transact-SQL, bir tablonun (bir satır) sütununa başvurmak için "." notasyonunu kullanır. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]bu gösterimi (programlama dillerinden ödünç alınan) bir nesnenin özellikleri arasında gezinmeyi desteklemek için genişletir.  
  
 Örneğin, Tür `p` Kişi bir ifade ise, aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bu kişinin adresinin şehir başvurmak için sözdizimidir.  
  
```sql  
p.Address.City
```  
  
## <a name="no-support-for-"></a>Destek Yok *  
 Transact-SQL, tüm satır için bir diğer ad olarak niteliksiz \* * sözdizimini\*ve bu tablonun alanları için bir kısayol olarak nitelikli sözdizimini (t.) destekler. Buna ek olarak, Transact-SQL nulls içeren özel bir sayı ()\*toplam sağlar.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]* yapıyı desteklemez. `select * from T` Formun Transact-SQL sorguları `select T1.* from T1, T2...` ve [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sırasıyla `select value t from T as t` `select value t1 from T1 as t1, T2 as t2...`ve olarak ifade edilebilir. Ayrıca, bu yapılar devralmayı (değer ikame edilebilirliği) işlerken, `select *` varyantlar bildirilen türün üst düzey özellikleriyle sınırlıdır.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]`count(*)` toplamı desteklemez. Bunun yerine `count(0)` kullanın.  
  
## <a name="changes-to-group-by"></a>Gruplandırmadeğişiklikleri  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]anahtarların diğer `group by` adlarını destekler. Yan tümce `select` ve `having` yan tümcedeki ifadeler, bu diğer adlar aracılığıyla `group by` anahtarlara başvurulmalıdır. Örneğin, bu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sözdizimi:  
  
```sql  
SELECT k1, count(t.a), sum(t.a)
FROM T AS t
GROUP BY t.b + t.c AS k1
```  
  
 ... aşağıdaki Transact-SQL'e eşdeğerdir:  
  
```sql  
SELECT b + c, count(*), sum(a)
FROM T
GROUP BY b + c
```  
  
## <a name="collection-based-aggregates"></a>Koleksiyon Tabanlı Agregalar  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]iki tür agregayı destekler.  
  
 Koleksiyon tabanlı agregalar koleksiyonlar üzerinde çalışır ve toplanan sonucu üretir. Bunlar sorgunun herhangi bir yerinde görünebilir `group by` ve bir yan tümce gerektirmez. Örnek:  
  
```sql  
SELECT t.a AS a, count({1,2,3}) AS b FROM T AS t
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]ayrıca SQL tarzı agregaları da destekler. Örnek:  
  
```sql  
SELECT a, sum(t.b) FROM T AS t GROUP BY t.a AS a
```  
  
## <a name="order-by-clause-usage"></a>Madde Kullanımına GÖRE SİPARİş  
Transact-SQL `ORDER BY` yan tümcelerinin yalnızca en `SELECT .. FROM .. WHERE` üst blokta belirtilmesine izin verir. İç [!INCLUDE[esql](../../../../../../includes/esql-md.md)] içe bir `ORDER BY` ifade kullanabilirsiniz ve sorguda herhangi bir yere yerleştirilebilir, ancak iç içe bir sorguda sıralama korunmuyor.  
  
```sql  
-- The following query will order the results by the last name  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact AS C1
        ORDER BY C1.LastName  
```  
  
```sql  
-- In the following query ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="identifiers"></a>Tanımlayıcılar  
 Transact-SQL'de tanımlayıcı karşılaştırması geçerli veritabanının harmanlamaını temel almaktadır. In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], tanımlayıcılar her zaman duyarsız ve aksan duyarlı [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (yani, aksanlı ve aksansız karakterler arasında ayrım; örneğin, 'a' 'a' eşit değildir). [!INCLUDE[esql](../../../../../../includes/esql-md.md)]aynı görünen ancak farklı kod sayfalarından gelen harflerin sürümlerini farklı karakterler olarak ele alar. Daha fazla bilgi için [Giriş Karakter Kümesi'ne](input-character-set-entity-sql.md)bakın.  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a>Transact-SQL İşlevselliği Entity SQL'de Kullanılamıyor  
 Aşağıdaki Transact-SQL işlevi [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
 Dml  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]şu anda DML deyimleri (ekleme, güncelleme, silme) için destek sağlamaz.  
  
 Ddl  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]geçerli sürümde DDL için destek sağlamaz.  
  
 Kesin Programlama Karşılaştırması  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Transact-SQL'den farklı olarak zorunlu programlama için destek sağlamaz. Bunun yerine bir programlama dili kullanın.  
  
 İşlevleri Gruplandırma  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]henüz gruplandırma işlevleri (örneğin, CUBE, ROLLUP ve GROUPING_SET) için destek sağlamaz.  
  
 Analitik İşlevler  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)](henüz) analitik işlevler için destek sağlamaz.  
  
 Dahili Fonksiyonlar, Operatörler  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]İşlevler ve işleçler içinde yerleşik Olan Transact-SQL'in bir alt kümesini destekler. Bu işleçler ve işlevler büyük mağaza sağlayıcıları tarafından desteklenebilir. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]sağlayıcı bildiriminde beyan edilen mağazaya özgü işlevleri kullanır. Ayrıca, Varlık Çerçevesi, yerleşik ve kullanıcı tarafından tanımlanan varolan mağaza [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işlevlerini kullanmak üzere beyan etmenizi sağlar.  
  
 Ipuç -ları  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]sorgu ipuçları için mekanizmalar sağlamaz.  
  
 Toplu İşlem Sorgu Sonuçları  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]toplu sorgu sonuçlarını desteklemez. Örneğin, aşağıdaki geçerli Transact-SQL (toplu iş olarak gönderme):  
  
```sql  
SELECT * FROM products;
SELECT * FROM catagories;
```  
  
 Ancak, eşdeğeri [!INCLUDE[esql](../../../../../../includes/esql-md.md)] desteklenmez:  
  
```sql  
SELECT value p FROM Products AS p;
SELECT value c FROM Categories AS c;
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]komut başına yalnızca bir sonuç üreten sorgu deyimini destekler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL’e Genel Bakış](entity-sql-overview.md)
- [Desteklenmeyen İfadeler](unsupported-expressions-entity-sql.md)
