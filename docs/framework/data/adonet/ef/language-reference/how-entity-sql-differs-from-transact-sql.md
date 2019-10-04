---
title: Entity SQL ile Transact-SQL Arasındaki Farklar
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: e0af0a415d812337d6abf449e9ee170526c3df0c
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833716"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a>Entity SQL ile Transact-SQL Arasındaki Farklar
Bu konuda [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ve Transact-SQL arasındaki farklar açıklanmaktadır.  
  
## <a name="inheritance-and-relationships-support"></a>Devralma ve Ilişkiler desteği  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] doğrudan kavramsal varlık şemaları ile çalışarak devralma ve ilişkiler gibi kavramsal model özelliklerini destekler.  
  
 Devralmayla çalışırken, genellikle bir üst tür alt türünün örneklerini seçmek yararlıdır. @No__t-1 ' deki [OfType](oftype-entity-sql.md) işleci (`oftype` ' de diziler C# içinde) bu yeteneği sağlar.  
  
## <a name="support-for-collections"></a>Koleksiyonlar için destek  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)], koleksiyonları birinci sınıf varlıklar olarak değerlendirir. Örneğin:  
  
- Koleksiyon ifadeleri `from` yan tümcesinde geçerlidir.  
  
- `in` ve `exists` alt sorguları tüm koleksiyonlara izin verecek şekilde genelleştirilir.  
  
     Alt sorgu tek bir koleksiyon türüdür. `e1 in e2` ve `exists(e)`, bu işlemleri gerçekleştirecek @no__t 2 yapılarıdır.  
  
- @No__t-0, `intersect` ve `except` gibi işlemleri ayarlayın, artık koleksiyonlar üzerinde çalışır.  
  
- Birleşimler koleksiyonlar üzerinde çalışır.  
  
## <a name="support-for-expressions"></a>Ifadeler için destek  
 Transact-SQL 'de alt sorgular (tablolar) ve ifadeler (satırlar ve sütunlar) vardır.  
  
 Koleksiyonları ve iç içe koleksiyonları desteklemek için [!INCLUDE[esql](../../../../../../includes/esql-md.md)] her şeyi bir ifadeye getirir. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Transact-SQL ' den daha birleştirilebilir — her ifade her yerde kullanılabilir. Sorgu ifadeleri her zaman öngörülen türlerin koleksiyonlarına neden olur ve koleksiyon ifadesine izin verildiğinde her yerde kullanılabilir. @No__t-0 ' da desteklenmeyen Transact-SQL ifadeleri hakkında daha fazla bilgi için bkz. [Desteklenmeyen ifadeler](unsupported-expressions-entity-sql.md).  
  
 Tüm geçerli [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorguları şunlardır:  
  
```sql  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}   
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a>Alt sorguları Tekdüzen olarak Işleme  
 Tablo üzerinde vurgusu verildiğine göre Transact-SQL, alt sorgular için bağlama yorumu uygular. Örneğin, `from` yan tümcesindeki bir alt sorgu bir çoklu küme (tablo) olarak kabul edilir. Ancak `select` yan tümcesinde kullanılan alt sorgu, skaler bir alt sorgu olarak kabul edilir. Benzer şekilde, bir `in` işlecinin sol tarafında kullanılan bir alt sorgu skaler bir alt sorgu olarak değerlendirilir ve sağ taraftaki bir çoklu küme alt sorgusu olması beklenir.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bu farklılıkları ortadan kaldırır. Bir ifade, kullanıldığı bağlama bağlı olmayan bir Tekdüzen yorumu içeriyor. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tüm alt sorguları çoklu küme alt sorguları olacak şekilde değerlendirir. Alt sorgudan skaler bir değer isteniyorsa, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir koleksiyon üzerinde çalışan `anyelement` işleci sağlar (Bu durumda alt sorgu) ve koleksiyondan tek bir değer ayıklar.  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a>Alt sorgular için örtük zorlamalar önleme  
 Tek biçimli alt sorgular için ilgili bir yan etkisi, alt sorguları skaler değerlere örtülü olarak dönüştürmedir. Özellikle Transact-SQL ' de bir dizi çoklu küme (tek bir alan ile), veri türü alanın bulunduğu bir skalar değere örtülü olarak dönüştürülür.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bu örtük zorlama 'yi desteklemez. [!INCLUDE[esql](../../../../../../includes/esql-md.md)], bir koleksiyondaki tek bir değeri ayıklamak için ANYELEMENT işlecini ve sorgu ifadesi sırasında satır sarmalayıcı oluşturulmasını önlemek için bir `select value` yan tümcesini sağlar.  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a>Değer seçin: örtük satır sarmalayıcısı ' ı önleme  
 Bir Transact-SQL alt sorgusunda SELECT yan tümcesi, yan tümcesindeki öğelerin etrafında örtük olarak bir satır sarmalayıcı oluşturur. Bu, yapı veya nesne koleksiyonları oluşturduğumuz anlamına gelir. Transact-SQL, tek bir alanla RowType ve aynı veri türünde tek bir değer arasında örtük bir zorlama sağlar.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)], örtük satır oluşturmayı atlamak için `select value` yan tümcesini sağlar. @No__t-0 yan tümcesinde yalnızca bir öğe belirtilebilir. Böyle bir yan tümce kullanıldığında, `select` yan tümcesindeki öğelerin çevresine satır sarmalayıcı oluşturulmadı ve istenen şeklin bir koleksiyonu üretile, örneğin: `select value a`.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Ayrıca satır oluşturucusunu rastgele satırlar oluşturmak için de sağlar. `select`, projeksiyondaki bir veya daha fazla öğeyi alır ve alanları içeren bir veri kaydına aşağıdaki şekilde neden olur:  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a>Sol bağıntı ve diğer ad  
 Transact-SQL içinde, belirli bir kapsamdaki ifadeler (`select` veya `from` gibi tek bir yan tümce), aynı kapsamda daha önce tanımlanan ifadelere başvuramaz. SQL 'in bazı diatıtılarını (Transact-SQL dahil) `from` yan tümcesinde bunlarla sınırlı biçimleri destekler.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)], `from` yan tümcesinde sol bağıntıları genelleştirir ve bunları bir şekilde değerlendirir. @No__t-0 yan tümcesindeki ifadeler, ek sözdizimi gerekmeden aynı yan tümcedeki önceki tanımlara (sol ve diğer tanımlar) başvurabilir.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)], ayrıca `group by` yan tümceleri içeren sorgularda ek kısıtlamalar uygular. @No__t-0 yan tümcesindeki ve bu tür sorguların `having` yan tümcesindeki ifadeler yalnızca diğer adları aracılığıyla `group by` anahtarlarına başvurabilir. Aşağıdaki yapı Transact-SQL ' te geçerlidir ancak [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ' da değildir:  
  
```sql  
SELECT t.x + t.y FROM T AS t group BY t.x + t.y
```  
  
 Bunu yapmak için [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:  
  
```sql  
SELET k FROM T AS t GROUP BY (t.x + t.y) AS k
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a>Tabloların (koleksiyonlar) sütunlarına (Özellikler) başvurma  
 @No__t-0 ' daki tüm sütun başvuruları tablo diğer adıyla nitelenmelidir. Aşağıdaki yapı (`a` ' ın geçerli bir tablo olduğunu varsayarsak `T`) Transact-SQL içinde geçerli ancak [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ' de değildir.  
  
```sql  
SELECT a FROM T
```  
  
 @No__t-0 formu  
  
```sql  
SELECT t.a AS A FROM T AS t
```  
  
 Tablo diğer adları `from` yan tümcesinde isteğe bağlıdır. Tablonun adı örtük diğer ad olarak kullanılır. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] aşağıdaki biçime de izin verir:  
  
```sql  
SELET Tab.a FROM Tab
```  
  
## <a name="navigation-through-objects"></a>Nesneler aracılığıyla gezinme  
 Transact-SQL, bir tablonun (bir satırı) sütunlarına başvurmak için "." gösterimini kullanır. [!INCLUDE[esql](../../../../../../includes/esql-md.md)], bir nesnenin özellikleri aracılığıyla gezinmeyi desteklemek için bu gösterimi (programlama dillerinden ödünç alınan) genişletir.  
  
 Örneğin, `p` kişi türünde bir ifadesiyse, bu kişinin adresinin şehrine başvurmak için [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sözdizimi aşağıda verilmiştir.  
  
```sql  
p.Address.City   
```  
  
## <a name="no-support-for-"></a>\* Desteği yok  
 Transact-SQL, tüm satır için bir diğer ad olarak nitelenmemiş * söz dizimini ve nitelenmiş \* sözdizimi (t. \*) tablonun alanları için bir kısayol olarak destekler. Ayrıca Transact-SQL, null değerler içeren özel bir sayı (\*) toplaması sağlar.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)], * yapısını desteklemez. @No__t-0 ve `select T1.* from T1, T2...` biçimindeki Transact-SQL sorguları, sırasıyla `select value t from T as t` ve `select value t1 from T1 as t1, T2 as t2...` @no__t ile ifade edilebilir. Ayrıca, bu yapılar devralmayı (value substitutability), ancak `select *` çeşitlemeleri, belirtilen türün en üst düzey özellikleriyle sınırlandırılır.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] `count(*)` toplamasını desteklemez. Bunun yerine `count(0)` kullanın.  
  
## <a name="changes-to-group-by"></a>Gruplandırma ölçütü  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] `group by` anahtarların diğer adını destekler. @No__t-0 yan tümcesindeki ve `having` yan tümcesindeki ifadeler, bu diğer adlar aracılığıyla `group by` anahtarlarına başvurmalıdır. Örneğin, bu @no__t 0 sözdizimi:  
  
```sql  
SELECT k1, count(t.a), sum(t.a)
FROM T AS t
GROUP BY t.b + t.c AS k1
```  
  
 ... Aşağıdaki Transact-SQL ' e eşdeğerdir:  
  
```sql  
SELECT b + c, count(*), sum(a)
FROM T
GROUP BY b + c
```  
  
## <a name="collection-based-aggregates"></a>Koleksiyon tabanlı toplamalar  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] iki tür toplamaları destekler.  
  
 Koleksiyon tabanlı toplamalar koleksiyonlar üzerinde çalışır ve toplanmış sonucu üretir. Bunlar sorgunun herhangi bir yerinde görünebilir ve `group by` yan tümcesi gerektirmez. Örneğin:  
  
```sql  
SELECT t.a AS a, count({1,2,3}) AS b FROM T AS t
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)], SQL stili toplamlarını da destekler. Örneğin:  
  
```sql  
SELECT a, sum(t.b) FROM T AS t GROUP BY t.a AS a
```  
  
## <a name="order-by-clause-usage"></a>ORDER BY yan tümcesi kullanımı  
Transact-SQL `ORDER BY` yan tümcelerinin yalnızca en üstteki `SELECT .. FROM .. WHERE` bloğunda belirtilmesini sağlar. @No__t-0 ' da, iç içe bir `ORDER BY` ifadesi kullanabilirsiniz ve sorgu içinde herhangi bir yere yerleştirilebilir, ancak iç içe bir sorgudaki sıralama korunmaz.  
  
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
 Transact-SQL ' de tanımlayıcı karşılaştırması, geçerli veritabanının harmanlanmasını temel alır. @No__t-0 ' da, tanımlayıcılar her zaman büyük/küçük harfe duyarlıdır ve aksan duyarlıdır (yani, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] aksanlı ve aksanlı karakterler arasında ayrım yapar; örneğin, ' a ', ' ấ ' değerine eşit değildir). [!INCLUDE[esql](../../../../../../includes/esql-md.md)], farklı kod sayfalarından farklı karakterler olarak görünen harflerin sürümlerini değerlendirir. Daha fazla bilgi için bkz. [giriş karakter kümesi](input-character-set-entity-sql.md).  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a>Transact-SQL Işlevselliği Entity SQL kullanılamıyor  
 Aşağıdaki Transact-SQL işlevleri [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ' da kullanılamaz.  
  
 DML  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] şu anda DML deyimleri (INSERT, Update, Delete) için destek sağlamaz.  
  
 DDL  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] geçerli sürümde DDL desteği sağlamaz.  
  
 Kesin Programlama Karşılaştırması  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)], Transact-SQL ' den farklı olarak kesinlik temelli programlama için destek sağlamaz. Bunun yerine bir programlama dili kullanın.  
  
 Gruplandırma Işlevleri  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] henüz gruplandırma işlevleri (örneğin, küp, toplama ve GROUPING_SET) için destek sağlamaz.  
  
 Analitik Işlevler  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)], analitik işlevler için destek sağlamaz (henüz).  
  
 Yerleşik Işlevler, Işleçler  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)], Transact-SQL ' in yerleşik işlevlerinin ve işleçlerinin bir alt kümesini destekler. Bu işleçler ve işlevler büyük olasılıkla ana mağaza sağlayıcıları tarafından desteklenmektedir. [!INCLUDE[esql](../../../../../../includes/esql-md.md)], bir sağlayıcı bildiriminde belirtilen mağazaya özgü işlevleri kullanır. Ayrıca Entity Framework, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ' ın kullanması için yerleşik ve Kullanıcı tanımlı depolama işlevlerini bildirmenize olanak tanır.  
  
 Yapılandıracak  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu ipuçları için mekanizmalar sağlamıyor.  
  
 Sorgu sonuçlarını toplu işleme  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu sonuçlarını toplu olarak oluşturmayı desteklemez. Örneğin, aşağıda geçerli Transact-SQL (Batch olarak gönderme) verilmiştir:  
  
```sql  
SELECT * FROM products;
SELECT * FROM catagories;
```  
  
 Ancak eşdeğer [!INCLUDE[esql](../../../../../../includes/esql-md.md)] desteklenmez:  
  
```sql  
SELECT value p FROM Products AS p;
SELECT value c FROM Categories AS c;
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)], komut başına yalnızca bir sonuç üreten sorgu bildirisini destekler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL’e Genel Bakış](entity-sql-overview.md)
- [Desteklenmeyen İfadeler](unsupported-expressions-entity-sql.md)
