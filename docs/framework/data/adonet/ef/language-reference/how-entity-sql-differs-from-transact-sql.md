---
title: Entity SQL ile Transact-SQL Arasındaki Farklar
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: 9433e7a7ffdc3a7e32900981dca95eefde32f290
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204443"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a>Entity SQL Transact-SQL ' den farklı

Bu makalede Entity SQL ve Transact-SQL arasındaki farklar açıklanmaktadır.  
  
## <a name="inheritance-and-relationships-support"></a>Devralma ve Ilişkiler desteği  

 Entity SQL doğrudan kavramsal varlık şemalarıyla çalışarak, devralma ve ilişkiler gibi kavramsal model özelliklerini destekler.  
  
 Devralmayla çalışırken, genellikle bir üst tür alt türünün örneklerini seçmek yararlıdır. Entity SQL [oftype](oftype-entity-sql.md) ( `oftype` C# dizilerinde olduğu gibi) OfType işleci bu yeteneği sağlar.  
  
## <a name="support-for-collections"></a>Koleksiyonlar için destek  

 Entity SQL, koleksiyonları birinci sınıf varlıklar olarak değerlendirir. Örneğin:  
  
- Koleksiyon ifadeleri `from` yan tümcesinde geçerlidir.  
  
- `in` ve alt `exists` sorgular tüm koleksiyonlara izin verecek şekilde genelleştirilir.  
  
     Alt sorgu tek bir koleksiyon türüdür. `e1 in e2` ve `exists(e)` Bu işlemleri gerçekleştirmek için Entity SQL yapılarıdır.  
  
- ,, Ve gibi işlemleri `union` , `intersect` `except` artık koleksiyonlar üzerinde çalışır.  
  
- Birleşimler koleksiyonlar üzerinde çalışır.  
  
## <a name="support-for-expressions"></a>Ifadeler için destek  

 Transact-SQL 'de alt sorgular (tablolar) ve ifadeler (satırlar ve sütunlar) vardır.  
  
 Koleksiyonları ve iç içe koleksiyonları desteklemek için Entity SQL her şeyi bir ifadeye getirir. Entity SQL Transact-SQL ' den daha birleştirilebilir — her ifade her yerde kullanılabilir. Sorgu ifadeleri her zaman öngörülen türlerin koleksiyonlarına neden olur ve koleksiyon ifadesine izin verildiğinde her yerde kullanılabilir. Entity SQL desteklenmeyen Transact-SQL ifadeleri hakkında daha fazla bilgi için bkz. [Desteklenmeyen ifadeler](unsupported-expressions-entity-sql.md).  
  
 Tüm geçerli Entity SQL sorguları aşağıda verilmiştir:  
  
```sql  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a>Alt sorguları Tekdüzen olarak Işleme  

 Tablo üzerinde vurgusu verildiğine göre Transact-SQL, alt sorgular için bağlama yorumu uygular. Örneğin, yan tümcesindeki bir alt sorgu `from` bir çoklu küme (tablo) olarak kabul edilir. Ancak yan tümcesinde kullanılan aynı alt sorgu `select` skaler bir alt sorgu olarak kabul edilir. Benzer şekilde, bir işlecin sol tarafında kullanılan bir alt sorgu `in` skaler bir alt sorgu olarak değerlendirilir ve sağ taraftaki bir çoklu küme alt sorgusu olması beklenir.  
  
 Entity SQL bu farklılıkları ortadan kaldırır. Bir ifade, kullanıldığı bağlama bağlı olmayan bir Tekdüzen yorumu içeriyor. Entity SQL tüm alt sorguları çoklu küme alt sorguları olacak şekilde değerlendirir. Alt sorgudan skaler bir değer isteniyorsa Entity SQL, `anyelement` bir koleksiyon üzerinde çalışan işleci (Bu durumda alt sorgu) sağlar ve koleksiyondan tek bir değer ayıklar.  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a>Alt sorgular için örtük zorlamalar önleme  

 Tek biçimli alt sorgular için ilgili bir yan etkisi, alt sorguları skaler değerlere örtülü olarak dönüştürmedir. Özellikle Transact-SQL ' de bir dizi çoklu küme (tek bir alan ile), veri türü alanın bulunduğu bir skalar değere örtülü olarak dönüştürülür.  
  
 Entity SQL, bu örtülü zorlaması desteklemez. Entity SQL `ANYELEMENT` , bir koleksiyondan tek bir değer ayıklamaya ve `select value` sorgu ifadesi sırasında satır sarmalayıcı oluşturmaktan kaçınmak için bir yan tümce sağlar.  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a>Değer seçin: örtük satır sarmalayıcısı ' ı önleme  

 Bir Transact-SQL alt sorgusunda SELECT yan tümcesi, yan tümcesindeki öğelerin etrafında örtük olarak bir satır sarmalayıcı oluşturur. Bu, yapı veya nesne koleksiyonları oluşturduğumuz anlamına gelir. Transact-SQL `rowtype` , bir alan ile aynı veri türünde tek bir değer arasında örtük bir zorlama sağlar.  
  
 Entity SQL `select value` örtük satır oluşturmayı atlamak için yan tümce sağlar. Yan tümcesinde yalnızca bir öğe belirtilebilir `select value` . Böyle bir yan tümce kullanıldığında, yan tümcesindeki öğelerin çevresine hiçbir satır sarmalayıcı oluşturulmadı `select` ve örneğin, istenen şeklin bir koleksiyonu oluşturulabilir `select value a` .  
  
 Entity SQL Ayrıca satır oluşturucusunu rastgele satırlar oluşturmak için de sağlar. `select` projeksiyde bir veya daha fazla öğe alır ve alanlarla veri kaydına neden olur:  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a>Sol bağıntı ve diğer ad  

 Transact-SQL içinde, belirli bir kapsamdaki ifadeler (veya gibi tek bir yan `select` tümce `from` ), aynı kapsamda daha önce tanımlanan ifadelere başvuramaz. SQL 'in bazı diatıtılarını (Transact-SQL dahil), yan tümcesinde bunların sınırlı biçimlerini destekler `from` .  
  
 Entity SQL yan tümcelerinde sol bağıntıları genelleştirir `from` ve bunları bir şekilde değerlendirir. `from`Yan tümcesindeki ifadeler, ek sözdizimi gerekmeden aynı yan tümce içindeki önceki tanımlara (sol ve diğer tanımlar) başvurabilir.  
  
 Entity SQL Ayrıca, yan tümceleri içeren sorgularda ek kısıtlamalar uygular `group by` . `select` `having` Bu tür sorguların yan tümce ve yan tümcesindeki ifadeler yalnızca `group by` diğer adları aracılığıyla anahtarlara başvurabilir. Aşağıdaki yapı Transact-SQL ' te geçerlidir ancak Entity SQL değildir:  
  
```sql  
SELECT t.x + t.y FROM T AS t group BY t.x + t.y
```  
  
 Bunu yapmak için Entity SQL:  
  
```sql  
SELET k FROM T AS t GROUP BY (t.x + t.y) AS k
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a>Tabloların (koleksiyonlar) sütunlarına (Özellikler) başvurma  

 Entity SQL tüm sütun başvuruları tablo diğer adıyla nitelenmelidir. Aşağıdaki yapı ( `a` tablonun geçerli bir sütunu olduğunu varsayarak `T` ) Transact-SQL ' de geçerlidir ancak Entity SQL değildir.  
  
```sql  
SELECT a FROM T
```  
  
 Entity SQL form  
  
```sql  
SELECT t.a AS A FROM T AS t
```  
  
 Tablo diğer adları, `from` yan tümcesinde isteğe bağlıdır. Tablonun adı örtük diğer ad olarak kullanılır. Entity SQL aşağıdaki biçime de izin verir:  
  
```sql  
SELET Tab.a FROM Tab
```  
  
## <a name="navigation-through-objects"></a>Nesneler aracılığıyla gezinme  

 Transact-SQL, bir tablonun (bir satırı) sütunlarına başvurmak için "." gösterimini kullanır. Entity SQL, bir nesnenin özellikleri aracılığıyla gezinmeyi desteklemek için bu gösterimi (programlama dillerinden ödünç alınan) genişletir.  
  
 Örneğin, `p` kişi türünde bir ifadesiyse, bu kişinin adresinin şehrine başvurmak için Entity SQL sözdizimi aşağıda verilmiştir.  
  
```sql  
p.Address.City
```  
  
## <a name="no-support-for-"></a>İçin destek yok \*  

 Transact-SQL, \* tüm satır için bir diğer ad olarak nitelenmemiş sözdizimini ve \* \* Bu tablonun alanları için bir kısayol olarak nitelenmiş sözdizimini (t.) destekler. Ayrıca Transact-SQL, null değerler içeren özel bir Count ( \* ) toplamasına izin verir.  
  
 Entity SQL, * yapısını desteklemez. Formunun Transact-SQL sorguları `select * from T` ve `select T1.* from T1, T2...` sırasıyla Entity SQL olarak ifade edilebilir `select value t from T as t` `select value t1 from T1 as t1, T2 as t2...` . Ayrıca, bu yapılar devralma (değer substitutability), ancak `select *` varyantlar, belirtilen türün en üst düzey özellikleriyle sınırlandırılır.  
  
 Entity SQL, `count(*)` toplamı desteklemez. Bunun yerine `count(0)` kullanın.  
  
## <a name="changes-to-group-by"></a>Gruplandırma ölçütü  

 Entity SQL anahtarların diğer adını destekler `group by` . `select`Yan tümce ve `having` yan tümcesindeki ifadeler, `group by` Bu diğer adlar aracılığıyla anahtarlara başvurmalıdır. Örneğin, bu Entity SQL söz dizimi:  
  
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

 Entity SQL iki tür toplamaları destekler.  
  
 Koleksiyon tabanlı toplamalar koleksiyonlar üzerinde çalışır ve toplanmış sonucu üretir. Bunlar sorgunun herhangi bir yerinde görünebilir ve `group by` yan tümce gerektirmez. Örneğin:  
  
```sql  
SELECT t.a AS a, count({1,2,3}) AS b FROM T AS t
```  
  
 Entity SQL Ayrıca SQL stili toplamlarını da destekler. Örneğin:  
  
```sql  
SELECT a, sum(t.b) FROM T AS t GROUP BY t.a AS a
```  
  
## <a name="order-by-clause-usage"></a>ORDER BY yan tümcesi kullanımı  

Transact-SQL `ORDER BY` yan tümcelerinin yalnızca en üstteki blokta belirtilmesini sağlar `SELECT .. FROM .. WHERE` . Entity SQL, iç içe geçmiş bir ifade kullanabilirsiniz `ORDER BY` ve sorgu içinde herhangi bir yere yerleştirilebilir, ancak iç içe bir sorgudaki sıralama korunmaz.  
  
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

 Transact-SQL ' de tanımlayıcı karşılaştırması, geçerli veritabanının harmanlanmasını temel alır. Entity SQL, tanımlayıcılar her zaman büyük/küçük harfe duyarlıdır ve aksan duyarlıdır (yani, Entity SQL aksanlı ve aksanlı karakterler arasında ayrım yapar; örneğin, ' a ', ' ấ ' değerine eşit değildir). Entity SQL, aynı olan ancak farklı kod sayfalarından farklı karakter olan harflerin sürümlerini ele alır. Daha fazla bilgi için bkz. [giriş karakter kümesi](input-character-set-entity-sql.md).  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a>Transact-SQL Işlevselliği Entity SQL kullanılamıyor  

 Aşağıdaki Transact-SQL işlevleri Entity SQL ' de kullanılamaz.  
  
 DML  
 Entity SQL Şu anda DML deyimleri (INSERT, Update, Delete) için destek sağlamaz.  
  
 DDL  
 Entity SQL geçerli sürümde DDL desteği sağlamaz.  
  
 Kesin Programlama Karşılaştırması  
 Entity SQL, Transact-SQL ' den farklı olarak, kesinlik temelli programlama için destek sağlamaz. Bunun yerine bir programlama dili kullanın.  
  
 Gruplandırma Işlevleri  
 Entity SQL, gruplandırma işlevlerini (örneğin, küp, toplama ve GROUPING_SET) için henüz destek sağlamaz.  
  
 Analitik İşlevler  
 Entity SQL, analitik işlevler için destek sağlamaz (henüz).  
  
 Yerleşik Işlevler, Işleçler  
 Entity SQL, Transact-SQL ' in yerleşik işlevlerinin ve işleçlerinin bir alt kümesini destekler. Bu işleçler ve işlevler büyük olasılıkla ana mağaza sağlayıcıları tarafından desteklenmektedir. Entity SQL, bir sağlayıcı bildiriminde belirtilen mağazaya özgü işlevleri kullanır. Ayrıca Entity Framework, Entity SQL kullanılmak üzere yerleşik ve Kullanıcı tanımlı mevcut depolama işlevlerini bildirmenize olanak tanır.  
  
 Yapılandıracak  
 Entity SQL sorgu ipuçları için mekanizmalar sağlamıyor.  
  
 Sorgu sonuçlarını toplu işleme  
 Entity SQL sorgu sonuçlarını toplu olarak oluşturmayı desteklemez. Örneğin, aşağıda geçerli Transact-SQL (Batch olarak gönderme) verilmiştir:  
  
```sql  
SELECT * FROM products;
SELECT * FROM catagories;
```  
  
 Ancak eşdeğer Entity SQL desteklenmez:  
  
```sql  
SELECT value p FROM Products AS p;
SELECT value c FROM Categories AS c;
```  
  
 Entity SQL, komut başına yalnızca bir sonucu üreten sorgu bildirisini destekler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL’e Genel Bakış](entity-sql-overview.md)
- [Desteklenmeyen İfadeler](unsupported-expressions-entity-sql.md)
