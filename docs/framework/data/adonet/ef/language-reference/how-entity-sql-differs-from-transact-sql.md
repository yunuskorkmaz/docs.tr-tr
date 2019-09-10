---
title: Entity SQL ile Transact-SQL Arasındaki Farklar
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: e809cea2f853eed51d28e55f81a411f7af2e5a33
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854478"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a>Entity SQL ile Transact-SQL Arasındaki Farklar
Bu konu, ve Transact- [!INCLUDE[esql](../../../../../../includes/esql-md.md)] SQL arasındaki farkları açıklamaktadır.  
  
## <a name="inheritance-and-relationships-support"></a>Devralma ve Ilişkiler desteği  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]doğrudan kavramsal varlık şemaları ile çalışarak devralma ve ilişkiler gibi kavramsal model özelliklerini destekler.  
  
 Devralmayla çalışırken, genellikle bir üst tür alt türünün örneklerini seçmek yararlıdır. `oftype` İçindeki [](oftype-entity-sql.md) [!INCLUDE[esql](../../../../../../includes/esql-md.md)] OfType işleci ( C# dizilerine benzer şekilde) bu yeteneği sağlar.  
  
## <a name="support-for-collections"></a>Koleksiyonlar için destek  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]koleksiyonları birinci sınıf varlıklar olarak değerlendirir. Örneğin:  
  
- Koleksiyon ifadeleri `from` yan tümcesinde geçerlidir.  
  
- `in`ve `exists` alt sorgular tüm koleksiyonlara izin verecek şekilde genelleştirilir.  
  
     Alt sorgu tek bir koleksiyon türüdür. `e1 in e2`ve `exists(e)` bu işlemleri [!INCLUDE[esql](../../../../../../includes/esql-md.md)] gerçekleştirmek için yapılardır.  
  
- ,, Ve `union` `intersect` gibi`except`işlemleri, artık koleksiyonlar üzerinde çalışır.  
  
- Birleşimler koleksiyonlar üzerinde çalışır.  
  
## <a name="support-for-expressions"></a>Ifadeler için destek  
 Transact-SQL 'de alt sorgular (tablolar) ve ifadeler (satırlar ve sütunlar) vardır.  
  
 Koleksiyonları ve iç içe koleksiyonları [!INCLUDE[esql](../../../../../../includes/esql-md.md)] desteklemek için her şeyi bir ifadeye getirir. [!INCLUDE[esql](../../../../../../includes/esql-md.md)], Transact-SQL ' den daha birleştirilebilir — her ifade her yerde kullanılabilir. Sorgu ifadeleri her zaman öngörülen türlerin koleksiyonlarına neden olur ve koleksiyon ifadesine izin verildiğinde her yerde kullanılabilir. ' De [!INCLUDE[esql](../../../../../../includes/esql-md.md)]desteklenmeyen Transact-SQL ifadeleri hakkında daha fazla bilgi için bkz. [Desteklenmeyen ifadeler](unsupported-expressions-entity-sql.md).  
  
 Tüm geçerli [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgular aşağıda verilmiştir:  
  
```  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}   
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a>Alt sorguları Tekdüzen olarak Işleme  
 Tablo üzerinde vurgusu verildiğine göre Transact-SQL, alt sorgular için bağlama yorumu uygular. Örneğin, `from` yan tümcesindeki bir alt sorgu bir çoklu küme (tablo) olarak kabul edilir. Ancak `select` yan tümcesinde kullanılan aynı alt sorgu skaler bir alt sorgu olarak kabul edilir. Benzer şekilde, bir `in` işlecin sol tarafında kullanılan bir alt sorgu skaler bir alt sorgu olarak değerlendirilir ve sağ taraftaki bir çoklu küme alt sorgusu olması beklenir.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Bu farklılıkları ortadan kaldırır. Bir ifade, kullanıldığı bağlama bağlı olmayan bir Tekdüzen yorumu içeriyor. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]tüm alt sorguları çoklu küme alt sorguları olacak şekilde değerlendirir. Alt sorgudan skaler bir değer isteniyorsa, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir koleksiyon üzerinde çalışan `anyelement` işleci (Bu durumda alt sorgu) sağlar ve koleksiyondan tek bir değer ayıklar.  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a>Alt sorgular için örtük zorlamalar önleme  
 Tek biçimli alt sorgular için ilgili bir yan etkisi, alt sorguları skaler değerlere örtülü olarak dönüştürmedir. Özellikle Transact-SQL ' de bir dizi çoklu küme (tek bir alan ile), veri türü alanın bulunduğu bir skalar değere örtülü olarak dönüştürülür.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Bu örtük zorlaması desteklemez. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]bir koleksiyondan tek bir değer ayıklamak için AnyElement işlecini ve sorgu ifadesi sırasında satır sarmalayıcı `select value` oluşturulmasını önlemek için bir yan tümceyi sağlar.  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a>Değer seçin: Örtük satır sarmalayıcısı önleme  
 Bir Transact-SQL alt sorgusunda SELECT yan tümcesi, yan tümcesindeki öğelerin etrafında örtük olarak bir satır sarmalayıcı oluşturur. Bu, yapı veya nesne koleksiyonları oluşturduğumuz anlamına gelir. Transact-SQL, tek bir alanla RowType ve aynı veri türünde tek bir değer arasında örtük bir zorlama sağlar.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]örtük satır oluşturmayı atlamak için yantümcesağlar.`select value` `select value` Yan tümcesinde yalnızca bir öğe belirtilebilir. Böyle bir yan tümce kullanıldığında, `select` yan tümcesindeki öğeler etrafında satır sarmalayıcı oluşturulmadı ve istenen şeklin bir koleksiyonu üretilmeyebilir, örneğin:. `select value a`  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Ayrıca satır oluşturucusunu rastgele satırlar oluşturmak için de sağlar. `select`projeksiyondaki bir veya daha fazla öğeyi alır ve alanları içeren bir veri kaydının aşağıdaki gibi sonuçlarını alır:  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a>Sol bağıntı ve diğer ad  
 Transact-SQL içinde, belirli bir kapsamdaki ifadeler (veya `select` `from`gibi tek bir yan tümce), aynı kapsamda daha önce tanımlanan ifadelere başvuramaz. SQL 'in bazı diatıtılarını (Transact-SQL dahil), `from` yan tümcesinde bunların sınırlı biçimlerini destekler.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]`from` yan tümce içinde sol bağıntıları genelleştirir ve bunları bir şekilde değerlendirir. `from` Yan tümcesindeki ifadeler, ek sözdizimi gerekmeden aynı yan tümce içindeki önceki tanımlara (sol ve diğer tanımlar) başvurabilir.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Ayrıca, yan tümceleri içeren `group by` sorgularda ek kısıtlamalar uygular. Bu tür sorguların `having` `group by` yan tümce ve yan tümcesindeki ifadeler yalnızca diğer adları aracılığıyla anahtarlara başvurabilir. `select` Aşağıdaki yapı Transact-SQL ' te geçerlidir ancak içinde [!INCLUDE[esql](../../../../../../includes/esql-md.md)]yoktur:  
  
```  
select t.x + t.y from T as t group by t.x + t.y  
```  
  
 Bunu yapmak [!INCLUDE[esql](../../../../../../includes/esql-md.md)]için:  
  
```  
select k from T as t group by (t.x + t.y) as k  
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a>Tabloların (koleksiyonlar) sütunlarına (Özellikler) başvurma  
 İçindeki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tüm sütun başvuruları tablo diğer adıyla nitelenmelidir. Aşağıdaki yapı (tablonun `a` `T`geçerli bir sütunu olduğunu varsayarak), Transact-SQL ' de geçerli, ancak içinde [!INCLUDE[esql](../../../../../../includes/esql-md.md)]değil.  
  
```  
select a from T  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Form  
  
```  
select t.a as A from T as t  
```  
  
 Tablo diğer adları, `from` yan tümcesinde isteğe bağlıdır. Tablonun adı örtük diğer ad olarak kullanılır. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Aşağıdaki biçime de izin verir:  
  
```  
select Tab.a from Tab  
```  
  
## <a name="navigation-through-objects"></a>Nesneler aracılığıyla gezinme  
 Transact-SQL, bir tablonun (bir satırı) sütunlarına başvurmak için "." gösterimini kullanır. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]bir nesnenin özellikleri aracılığıyla gezinmeyi desteklemek için bu gösterimi (programlama dillerinden ödünç alınan) genişletir.  
  
 Örneğin, `p` kişi türünde bir ifadesiyse, bu kişinin adresinin şehrine başvurmak için [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sözdizimi aşağıdaki gibidir.  
  
```  
p.Address.City   
```  
  
## <a name="no-support-for-"></a>\* Desteği yok  
 Transact-SQL, tüm satır için bir diğer ad olarak nitelenmemiş * sözdizimini ve bu tablonun alanları için \* bir kısayol olarak nitelenmiş\*sözdizimini (t.) destekler. Ayrıca Transact-SQL, null değerler içeren özel bir Count (\*) toplamasına izin verir.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]* yapısını desteklemez. Formunun `select * from T` Transact-SQL sorguları ve `select T1.* from T1, T2...` sırasıyla ve [!INCLUDE[esql](../../../../../../includes/esql-md.md)] `select value t from T as t` `select value t1 from T1 as t1, T2 as t2...`olarak ifade edilebilir. Ayrıca, bu yapılar devralma (değer substitutability), ancak `select *` varyantlar, belirtilen türün en üst düzey özellikleriyle sınırlandırılır.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]`count(*)` toplamasını desteklemez. Bunun yerine `count(0)` kullanın.  
  
## <a name="changes-to-group-by"></a>Gruplandırma ölçütü  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]anahtarların diğer adını `group by` destekler. Yan tümce ve `having` yan tümcesindeki ifadeler, `group by` bu diğer adlar aracılığıyla anahtarlara başvurmalıdır. `select` Örneğin, bu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] söz dizimi:  
  
```  
select k1, count(t.a), sum(t.a)  
from T as t  
group by t.b + t.c as k1  
```  
  
 ... Aşağıdaki Transact-SQL ' e eşdeğerdir:  
  
```  
select b + c, count(*), sum(a)   
from T  
group by b + c  
```  
  
## <a name="collection-based-aggregates"></a>Koleksiyon tabanlı toplamalar  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]iki tür toplamaları destekler.  
  
 Koleksiyon tabanlı toplamalar koleksiyonlar üzerinde çalışır ve toplanmış sonucu üretir. Bunlar sorgunun herhangi bir yerinde görünebilir ve `group by` yan tümce gerektirmez. Örneğin:  
  
```  
select t.a as a, count({1,2,3}) as b from T as t     
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)], SQL stili toplamlarını da destekler. Örneğin:  
  
```  
select a, sum(t.b) from T as t group by t.a as a  
```  
  
## <a name="order-by-clause-usage"></a>ORDER BY yan tümcesi kullanımı  
 Transact-SQL ORDER BY yan tümcelerinin yalnızca en üstteki SELECT içinde belirtilmesini sağlar. KAYNAK.. WHERE bloğu. İçinde [!INCLUDE[esql](../../../../../../includes/esql-md.md)] , iç içe geçmiş bir ifade kullanabilirsiniz ve sorgu içinde herhangi bir yere yerleştirilebilir, ancak iç içe bir sorgudaki sıralama korunmaz.  
  
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
 Transact-SQL ' de tanımlayıcı karşılaştırması, geçerli veritabanının harmanlanmasını temel alır. İçinde [!INCLUDE[esql](../../../../../../includes/esql-md.md)]tanımlayıcılar her zaman büyük/küçük harfe duyarlıdır ve aksan duyarlıdır (yani [!INCLUDE[esql](../../../../../../includes/esql-md.md)] , aksanlı ve aksanlı karakterler arasında ayrım yapar; örneğin, ' a ', ' ấ ' değerine eşit değildir). [!INCLUDE[esql](../../../../../../includes/esql-md.md)]aynı görünen, ancak farklı kod sayfalarından farklı karakter olan harflerin sürümlerini değerlendirir. Daha fazla bilgi için bkz. [giriş karakter kümesi](input-character-set-entity-sql.md).  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a>Transact-SQL Işlevselliği Entity SQL kullanılamıyor  
 Aşağıdaki Transact-SQL işlevselliği ' de [!INCLUDE[esql](../../../../../../includes/esql-md.md)]kullanılamaz.  
  
 DML  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Şu anda DML deyimleri (INSERT, Update, Delete) için destek sağlamaz.  
  
 DDL  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]geçerli sürümde DDL desteği sağlamaz.  
  
 Kesin Programlama Karşılaştırması  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)], Transact-SQL ' den farklı olarak, kesinlik temelli programlama için destek sağlamaz. Bunun yerine bir programlama dili kullanın.  
  
 Gruplandırma Işlevleri  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]henüz gruplandırma işlevleri için destek sağlamaz (örneğin, CUBE, ROLLUP ve GROUPING_SET).  
  
 Analitik Işlevler  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)](henüz) analitik işlevler için destek sağlamaz.  
  
 Yerleşik Işlevler, Işleçler  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Transact-SQL ' in yerleşik işlevlerinin ve işleçlerinin bir alt kümesini destekler. Bu işleçler ve işlevler büyük olasılıkla ana mağaza sağlayıcıları tarafından desteklenmektedir. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]bir sağlayıcı bildiriminde belirtilen mağazaya özgü işlevleri kullanır. Ayrıca, Entity Framework, yerleşik ve Kullanıcı tanımlı mevcut depolama işlevlerini [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kullanmak üzere bildirmenize olanak tanır.  
  
 Yapılandıracak  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]sorgu ipuçları için mekanizmalar sağlamaz.  
  
 Sorgu sonuçlarını toplu işleme  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]sorgu sonuçlarını toplu olarak oluşturmayı desteklemez. Örneğin, aşağıda geçerli Transact-SQL (Batch olarak gönderme) verilmiştir:  
  
```  
select * from products;  
select * from catagories;  
```  
  
 Ancak eşdeğer [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir değer desteklenmez:  
  
```  
Select value p from Products as p;  
Select value c from Categories as c;  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]komut başına yalnızca bir sonuç oluşturan sorgu bildirisini destekler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL’e Genel Bakış](entity-sql-overview.md)
- [Desteklenmeyen İfadeler](unsupported-expressions-entity-sql.md)
