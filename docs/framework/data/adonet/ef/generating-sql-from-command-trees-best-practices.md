---
title: Komut Ağaçlarından SQL Oluşturma - En İyi Yöntemler
ms.date: 03/30/2017
ms.assetid: 71ef6a24-4c4f-4254-af3a-ffc0d855b0a8
ms.openlocfilehash: 366e27f8c8a04c5d2507ab37459ad6d5abc255ae
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251570"
---
# <a name="generating-sql-from-command-trees---best-practices"></a>Komut Ağaçlarından SQL Oluşturma - En İyi Yöntemler

Çıktı sorgu komut ağaçları SQL 'de ifade edilecek şekilde daha yakından model sorguları. Ancak, bir çıkış komut ağacından SQL oluştururken sağlayıcı yazıcılarında ilgili bazı yaygın sorunlar vardır. Bu konuda bu sorunlar ele alınmaktadır. Bir sonraki konu başlığında, örnek sağlayıcı bu güçlükleri nasıl ele alınacağını göstermektedir.

## <a name="group-dbexpression-nodes-in-a-sql-select-statement"></a>SQL SELECT deyiminde DbExpression düğümlerini gruplandırma

Tipik bir SQL ifadesinin aşağıdaki şekle ait iç içe bir yapısı vardır:

```sql
SELECT …
FROM …
WHERE …
GROUP BY …
ORDER BY …
```

Bir veya daha fazla yan tümce boş olabilir.  İç içe bir SELECT ifadesinin herhangi bir satırda oluşması olabilir.

Bir SQL SELECT ifadesine sorgu komut ağacının olası bir çevirisi, her ilişkisel operatör için bir alt sorgu oluşturur. Bununla birlikte, okunması zor olan, gereksiz iç sorgulara yol açacaktı.  Bazı veri depolarında sorgu kötü bir şekilde çalışabilir.

Örnek olarak, aşağıdaki sorgu komut ağacını göz önünde bulundurun

```
Project (
a.x,
   a = Filter(
      b.y = 5,
      b = Scan("TableA")
   )
)
```

Verimsiz bir çeviri şunları üretir:

```sql
SELECT a.x
FROM (   SELECT *
         FROM TableA as b
         WHERE b.y = 5) as a
```

Her ilişkisel ifade düğümünün yeni bir SQL SELECT deyimi haline geldiğini unutmayın.

Bu nedenle, doğruluğu korurken çok sayıda ifade düğümünü tek bir SQL SELECT deyimine mümkün olduğunca toplamak önemlidir.

Yukarıda sunulan örnek için bu tür toplamın sonucu şöyle olacaktır:

```sql
SELECT b.x
FROM TableA as b
WHERE b.y = 5
```

## <a name="flatten-joins-in-a-sql-select-statement"></a>SQL SELECT deyimindeki birleştirmeleri düzleştirme

Birden çok düğümü tek bir SQL SELECT deyimi içinde birleştiren bir durum, birden çok JOIN ifadesini tek bir SQL SELECT deyimi içine toplayarak. DbJoinExpression iki giriş arasındaki tek bir birleştirmeyi temsil eder. Ancak, tek bir SQL SELECT ifadesinin parçası olarak birden fazla JOIN belirlenebilir. Bu durumda, birleştirmeler belirtilen sırada gerçekleştirilir.

Sol sırt birleşimleri (başka bir birleşimin sol alt öğesi olarak görünen birleşimler), tek bir SQL SELECT ifadesinde daha kolay bir şekilde düzleştirilir. Örneğin, aşağıdaki sorgu komut ağacını göz önünde bulundurun:

```
InnerJoin(
   a = LeftOuterJoin(
   b = Extent("TableA")
   c = Extent("TableB")
   ON b.y = c.x ),
   d = Extent("TableC")
   ON a.b.y = d.z
)
```

Bu, öğesine doğru şekilde çevrilebilir:

```sql
SELECT *
FROM TableA as b
LEFT OUTER JOIN TableB as c ON b.y = c.x
INNER JOIN TableC as d ON b.y = d.z
```

Ancak, sol olmayan sırtı birleştirmeleri kolayca düzleştirilmez ve bunları düzleştirmeniz gerekmez. Örneğin, aşağıdaki sorgu komut ağacındaki birleşimler:

```
InnerJoin(
   a = Extent("TableA")
   b = LeftOuterJoin(
   c = Extent("TableB")
   d = Extent("TableC")
   ON c.y = d.x),
   ON a.z = b.c.y
)
```

Alt sorgu ile bir SQL SELECT ifadesine çevrilir.

```sql
SELECT *
FROM TableA as a
INNER JOIN (SELECT *
   FROM TableB as c
   LEFT OUTER JOIN TableC as d
   ON c.y = d.x) as b
ON b.y = d.z
```

## <a name="input-alias-redirecting"></a>Giriş diğer adı yönlendirme

Girdi diğer adını yeniden yönlendirmeyi açıklamak için, DbFilterExpression, DbProjectExpression, DbCrossJoinExpression, DbJoinExpression, DbSortExpression, DbGroupByExpression, DbApplyExpression gibi ilişkisel ifadelerin yapısını göz önünde bulundurun. DbSkipExpression.

Bu türlerin her birinde, bir giriş koleksiyonu tanımlayan bir veya daha fazla giriş özelliği bulunur ve her girişe karşılık gelen bir bağlama değişkeni, bu girişin her bir öğesini bir koleksiyon çapraz geçişi sırasında temsil etmek için kullanılır. Bağlama değişkeni, giriş öğesine başvururken, örneğin bir DbFilterExpression 'ın koşul özelliğindeki veya bir DbProjectExpression 'ın Projection özelliğinin kullanıldığı durumlarda kullanılır.

Birden fazla ilişkisel ifade düğümünü tek bir SQL SELECT deyimine toplayarak ve ilişkisel bir ifadenin parçası olan bir ifadeyi değerlendirirken (örneğin, bir DbProjectExpression 'ın Projection özelliğinin bir parçası olarak), kullandığı bağlama değişkeni birden çok ifade bağlaması tek bir ölçüde yönlendirilmek zorunda olacağından, girişin diğer adıyla aynı değildir.  Bu soruna yeniden adlandırma adı verilir.

Bu konudaki ilk örneği göz önünde bulundurun. Naïve çevirisini yapar ve projeksiyonu bir. x (DbPropertyExpression (a, x)) çeviriyorsa, bağlama değişkeni ile eşleşmesi için girişin "a `a.x` " olarak başka bir ad alanı olduğu için ' a çevirmek doğru olur.  Ancak, hem düğümleri tek bir SQL SELECT deyimi içinde toplayarak, girişin "b" ile başka bir ad alanı olduğu için aynı `b.x`DbPropertyExpression ' a çevirmeniz gerekir.

## <a name="join-alias-flattening"></a>Diğer ad düzleştirmeyi Birleştir

Bir çıkış komut ağacındaki diğer tüm ilişkisel deyimlerden farklı olarak, DbJoinExpression, her biri girdilerden birine karşılık gelen iki sütundan oluşan bir satır olan sonuç türünü çıktı. Bir DbPropertyExpression, bir birleşimden kaynaklanan skaler bir özelliğe erişmek üzere yapılandırıldığında, başka bir DbPropertyExpression üzerinde bulunur.

Örnek 2 ' de "a. b. y" ve örnek 3 ' te "b. c. y" verilebilir. Bununla birlikte, bunlara karşılık gelen SQL deyimlerine "b. y" olarak başvurulur. Bu yeniden takma ad, JOIN diğer adı düzleştirme olarak adlandırılır.

## <a name="column-name-and-extent-alias-renaming"></a>Sütun adı ve uzantı diğer adı yeniden adlandırma

Bir birleşime sahip bir SQL SELECT sorgusunun projeksiyon ile tamamlanması gerekiyorsa, tüm katılan sütunları girdilerden Numaralandırırken, birden fazla girişin aynı sütun adına sahip olabileceğinden bir ad çakışması meydana gelebilir. Çarpışmadan kaçınmak için sütun için farklı bir ad kullanın.

Ayrıca, birleştirmeleri düzleştirme sırasında, katılım tabloları (veya alt sorgular), bu durumda yeniden adlandırılması gereken diğer adları çarpışmış olabilir.

## <a name="avoid-select-"></a>SELECT * kullanmaktan kaçının

Temel tablolardan seçim `SELECT *` yapmak için kullanmayın. Bir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] uygulamadaki depolama modeli yalnızca veritabanı tablosundaki sütunların bir alt kümesini içerebilir. Bu durumda, `SELECT *` yanlış sonuç verebilir. Bunun yerine, katılan ifadelerin sonuç türünden sütun adlarını kullanarak tüm katılan sütunları belirtmeniz gerekir.

## <a name="reuse-of-expressions"></a>Ifadelerin yeniden kullanılması

İfadeler tarafından [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]geçirilen sorgu komut ağacında yeniden kullanılabilir. Sorgu komut ağacında her bir ifadenin yalnızca bir kez göründüğünü varsaymayın.

## <a name="mapping-primitive-types"></a>Temel türleri eşleme

Kavramsal (EDM) türlerini sağlayıcı türlerine eşlerken, tüm olası değerlerin sığması için en geniş türe (Int32) eşleme yapmanız gerekir. Ayrıca, blob türleri gibi çok sayıda işlem için kullanılamayan türlere eşlemektan kaçının (örneğin, `ntext` SQL Server).

## <a name="see-also"></a>Ayrıca bkz.

- [SQL Üretimi](sql-generation.md)
