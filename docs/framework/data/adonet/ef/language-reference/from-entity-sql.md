---
title: (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ff3e3048-0d5d-4502-ae5c-9187fcbd0514
ms.openlocfilehash: 993e71e6fee2e18806da789bdb10a488337d030f
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250947"
---
# <a name="from-entity-sql"></a>(Entity SQL)
[Select](select-entity-sql.md) deyimlerinde kullanılan koleksiyonu belirtir.

## <a name="syntax"></a>Sözdizimi

```
FROM expression [ ,...n ] as C
```

## <a name="arguments"></a>Arguments

`expression` \
Bir `SELECT` deyimde kaynak olarak kullanılacak bir koleksiyon veren geçerli bir sorgu ifadesi.

## <a name="remarks"></a>Açıklamalar

Yan tümce bir veya daha fazla `FROM` yan tümce öğesinin virgülle ayrılmış listesidir. `FROM` Yan `FROM` tümce, bir `SELECT` deyimin bir veya daha fazla kaynağını belirtmek için kullanılabilir. `FROM` Yan tümcesinin en basit biçimi, aşağıdaki örnekte gösterildiği gibi bir koleksiyonu ve bir `SELECT` deyimde kaynak olarak kullanılan diğer adı tanımlayan tek bir sorgu deyimidir:

`FROM C as c`

## <a name="from-clause-items"></a>FROM yan tümce öğeleri

Her `FROM` yan tümce öğesi [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgudaki bir kaynak koleksiyonu ifade eder. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Aşağıdaki `FROM` yan tümce öğelerini destekler: basit `FROM` yan tümce öğeleri, `JOIN FROM` yan tümce öğeleri ve `APPLY FROM` yan tümce öğeleri. Bu `FROM` yan tümce öğelerinin her biri, aşağıdaki bölümlerde daha ayrıntılı olarak açıklanmıştır.

### <a name="simple-from-clause-item"></a>Basit FROM yan tümce öğesi

En basit `FROM` yan tümce öğesi, bir koleksiyonu ve diğer adı tanımlayan tek bir ifadedir. İfade yalnızca bir varlık kümesi veya bir alt sorgu ya da bir koleksiyon türü olan başka bir ifade olabilir. Aşağıda bir örnek verilmiştir:

```sql
LOB.Customers as c
```

Diğer ad belirtimi isteğe bağlıdır. Yukarıdaki from yan tümcesi öğesinin alternatif bir belirtimi şunlar olabilir:

```sql
LOB.Customers
```

Diğer ad belirtilmemişse, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] koleksiyon ifadesini temel alan bir diğer ad oluşturmaya çalışır.

### <a name="join-from-clause-item"></a>Yan tümce öğesinden BIrLEŞTIr

Yan tümce öğesi iki `FROM` yan tümce öğesi arasında bir birleştirmeyi temsil eder. `JOIN FROM` [!INCLUDE[esql](../../../../../../includes/esql-md.md)]çapraz birleştirmeleri, iç birleştirmeleri, sol ve sağ dış birleştirmeleri ve tam dış birleştirmeleri destekler. Tüm bu birleştirmeler Transact-SQL ' de desteklendikleri yönteme benzer şekilde desteklenmektedir. Transact-SQL ' de olduğu gibi, `FROM` `JOIN` içinde yer alan iki yan tümce öğesi bağımsız olmalıdır. Diğer bir deyişle, bağıntılı olamaz. Bu durumlar `OUTER APPLY` için veyakullanılabilir.`CROSS APPLY`

#### <a name="cross-joins"></a>Çapraz birleşimler

Bir `CROSS JOIN` sorgu ifadesi, aşağıdaki örnekte gösterildiği gibi iki koleksiyonun Kartezyen çarpımını üretir:

`FROM C AS c CROSS JOIN D as d`

#### <a name="inner-joins"></a>İç birleştirmeler

, Aşağıdaki örnekte gösterildiği gibi iki koleksiyonun kısıtlı bir Kartezyen ürününü üretir:`INNER JOIN`

`FROM C AS c [INNER] JOIN D AS d ON e`

Önceki sorgu ifadesi, `ON` koşulun doğru olduğu yerde, sağ taraftaki koleksiyonun her öğesine karşı, sol taraftaki koleksiyonun her öğesinin bir birleşimini işler. Herhangi `ON` `CROSS JOIN`bir `INNER JOIN` koşul belirtilmemişse, bir, bir ' a üretir.

#### <a name="left-outer-joins-and-right-outer-joins"></a>Sol dış birleşimler ve sağ dış birleşimler

Bir `OUTER JOIN` sorgu ifadesi, aşağıdaki örnekte gösterildiği gibi iki koleksiyonun kısıtlı bir Kartezyen ürününü üretir:

`FROM C AS c LEFT OUTER JOIN D AS d ON e`

Önceki sorgu ifadesi, `ON` koşulun doğru olduğu yerde, sağ taraftaki koleksiyonun her öğesine karşı, sol taraftaki koleksiyonun her öğesinin bir birleşimini işler. `ON` Koşul false ise, ifade, sol taraftaki öğenin tek bir örneğini, null değeri ile sağ taraftaki öğeye karşı işler.

`RIGHT OUTER JOIN` Benzer bir şekilde ifade edilebilir.

#### <a name="full-outer-joins"></a>Tam dış birleşimler

Açık `FULL OUTER JOIN` , aşağıdaki örnekte gösterildiği gibi iki koleksiyonun kısıtlı bir Kartezyen çarpımını üretir:

`FROM C AS c FULL OUTER JOIN D AS d ON e`

Önceki sorgu ifadesi, `ON` koşulun doğru olduğu yerde, sağ taraftaki koleksiyonun her öğesine karşı, sol taraftaki koleksiyonun her öğesinin bir birleşimini işler. `ON` Koşul false ise, ifade, sol taraftaki öğenin bir örneğini, null değeri ile sağ taraftaki öğeye karşı işler. Ayrıca, sol taraftaki öğenin bir örneğini solda, null değeriyle birlikte işler.

> [!NOTE]
> SQL-92 ile uyumluluğu korumak için Transact-SQL içinde DıŞTAKI anahtar sözcüğü isteğe bağlıdır. `LEFT OUTER JOIN` Bunedenle`RIGHT OUTER JOIN`,, ve `FULL JOIN` ,, ve için`FULL OUTER JOIN`eşanlamlılardır. `LEFT JOIN` `RIGHT JOIN`

### <a name="apply-clause-item"></a>APPLY yan tümce öğesi

[!INCLUDE[esql](../../../../../../includes/esql-md.md)]iki tür `APPLY`destekler: `CROSS APPLY` ve `OUTER APPLY`.

, `CROSS APPLY` Sağ taraftaki ifade hesaplanarak oluşturulan koleksiyonun öğesi ile sol taraftaki koleksiyonun her bir öğesi için benzersiz bir eşleştirme üretir. `CROSS APPLY`İle, sağ taraftaki ifade, aşağıdaki ilişkili koleksiyon örneğinde gösterildiği gibi, sol taraftaki öğeye göre değişir:

`SELECT c, f FROM C AS c CROSS APPLY c.Assoc AS f`

Davranışı `CROSS APPLY` , JOIN listesine benzerdir. Sağdaki ifade boş bir koleksiyon `CROSS APPLY` olarak değerlendirilirse, sol taraftaki öğenin bu örneği için hiçbir eşleşme üretmez.

Bir eşleşme, `CROSS APPLY`sağdaki ifade boş bir koleksiyon olarak değerlendirilse bile hala üretildiğinde, bir a benzerdir.`OUTER APPLY` Aşağıda bir `OUTER APPLY`örneği verilmiştir:

`SELECT c, f FROM C AS c OUTER APPLY c.Assoc AS f`

> [!NOTE]
> Transact-SQL ' den farklı olarak, içinde [!INCLUDE[esql](../../../../../../includes/esql-md.md)]açık iç içe olmayan bir adım yoktur.

> [!NOTE]
> `CROSS`ve `OUTER APPLY` işleçleri SQL Server 2005 ' de tanıtılmıştı. Bazı durumlarda, sorgu işlem hattı ve/veya `CROSS APPLY` `OUTER APPLY` işleçlerini içeren Transact-SQL üretebilir. SQL Server 2005 ' den önceki SQL Server sürümleri de dahil olmak üzere bazı arka uç sağlayıcılar bu işleçleri desteklemediğinden, bu arka uç sağlayıcılarında bu sorgular yürütülemez.
>
> Çıktı sorgusunda `CROSS APPLY` ve/veya `OUTER APPLY` işleçleri varlığına neden olabilecek bazı tipik senaryolar şunlardır: sayfalama içeren bağıntılı alt sorgu; Bağıntılı bir alt sorgu üzerinden veya gezinti tarafından oluşturulan bir koleksiyon üzerinden AnyElement; Öğe seçiciyi kabul eden gruplandırma yöntemlerini kullanan LINQ sorguları; `CROSS APPLY` `DEREF` `REF` ya da 'ınaçıkçabelirttiğibirsorgu;biryapıüzerindeyapısına`OUTER APPLY` sahip olan bir sorgu.

## <a name="multiple-collections-in-the-from-clause"></a>FROM yan tümcesinde birden çok koleksiyon

Yan `FROM` tümce, virgülle ayrılmış birden fazla koleksiyon içerebilir. Bu durumlarda, koleksiyonların birlikte birleştirilme varsayılır. Bunları n yönlü bir çapraz JOIN olarak düşünün.

Aşağıdaki örnekte `C` ve `D` bağımsız `c.Names` koleksiyonlardır`C`, ancak bağımlıdır.

```sql
FROM C AS c, D AS d, c.Names AS e
```

Önceki örnek, aşağıdaki örneğe mantıksal olarak eşdeğerdir:

`FROM (C AS c JOIN D AS d) CROSS APPLY c.Names AS e`

## <a name="left-correlation"></a>Sol bağıntı
 Yan tümcesindeki öğeler `FROM` , önceki yan tümcelerde belirtilen öğelere başvurabilir. Aşağıdaki örnekte `C` ve `D` bağımsız `c.Names` koleksiyonlardır`C`, ancak bağımlıdır:

```sql
from C as c, D as d, c.Names as e
```

Bu, mantıksal olarak eşdeğerdir:

```sql
from (C as c join D as d) cross apply c.Names as e
```

## <a name="semantics"></a>İçeriyor

Mantıksal olarak, `FROM` yan tümcesindeki koleksiyonlar tek yönlü çapraz birleştirmenin bir `n`parçası olduğu varsayılır (1 yönlü çapraz birleşimin olması dışında). `FROM` Yan tümcesindeki diğer adlar soldan sağa işlenir ve daha sonra başvurmak üzere geçerli kapsama eklenir. Yan `FROM` tümce, bir dizi çoklu küme üreten kabul edilir. `FROM` Yan tümcesindeki her öğe için, o koleksiyon öğesinden tek bir öğeyi temsil eden bir alan olacaktır.

Yan tümcesi, c, d ve e alanlarının `C`, `D`, ve `c.Names`öğelerinin öğe türünde olduğu kabul edildiği satır türünde satırları (c, d, e) mantıksal olarak oluşturur. `FROM`

[!INCLUDE[esql](../../../../../../includes/esql-md.md)]kapsamdaki her basit `FROM` yan tümce öğesi için bir diğer ad tanıtır. Örneğin, aşağıdaki FROM yan tümcesi kod parçacığında, kapsamında tanıtılan adlar c, d ve e 'dir.

```sql
from (C as c join D as d) cross apply c.Names as e
```

' [!INCLUDE[esql](../../../../../../includes/esql-md.md)] De (Transact-SQL `FROM` ' den farklı olarak), yan tümce yalnızca kapsamdaki diğer adları tanıtır. Bu koleksiyonların sütunlarına (Özellikler) yapılan tüm başvurular diğer adla nitelenmelidir.

## <a name="pulling-up-keys-from-nested-queries"></a>Iç Içe sorgulardan anahtarları çekme

İç içe bir sorgudan anahtar çekmesini gerektiren bazı sorgu türleri desteklenmez. Örneğin, aşağıdaki sorgu geçerlidir:

```sql
select c.Orders from Customers as c
```

Ancak, iç içe sorgu herhangi bir anahtara sahip olmadığından aşağıdaki sorgu geçerli değildir:

```sql
select {1} from {2, 3}
```

## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
- [Sorgu İfadeleri](query-expressions-entity-sql.md)
- [Null Değer Atanabilir Yapılandırılmış Türler](nullable-structured-types-entity-sql.md)
