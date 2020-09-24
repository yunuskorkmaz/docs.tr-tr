---
title: (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ff3e3048-0d5d-4502-ae5c-9187fcbd0514
ms.openlocfilehash: 8affac82fb1813aa0282540b5dc2f47d42234a1b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148067"
---
# <a name="from-entity-sql"></a>(Entity SQL)

[Select](select-entity-sql.md) deyimlerinde kullanılan koleksiyonu belirtir.

## <a name="syntax"></a>Söz dizimi

```sql
FROM expression [ ,...n ] AS C
```

## <a name="arguments"></a>Bağımsız değişkenler

`expression` \
Bir deyimde kaynak olarak kullanılacak bir koleksiyon veren geçerli bir sorgu ifadesi `SELECT` .

## <a name="remarks"></a>Açıklamalar

`FROM`Yan tümce bir veya daha fazla yan tümce öğesinin virgülle ayrılmış listesidir `FROM` . `FROM`Yan tümce, bir deyimin bir veya daha fazla kaynağını belirtmek için kullanılabilir `SELECT` . Yan tümcesinin en basit biçimi, `FROM` `SELECT` Aşağıdaki örnekte gösterildiği gibi bir koleksiyonu ve bir deyimde kaynak olarak kullanılan diğer adı tanımlayan tek bir sorgu deyimidir:

`FROM C as c`

## <a name="from-clause-items"></a>FROM yan tümce öğeleri

Her `FROM` yan tümce öğesi sorgudaki bir kaynak koleksiyonu ifade eder [!INCLUDE[esql](../../../../../../includes/esql-md.md)] . [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Aşağıdaki `FROM` yan tümce öğelerini destekler: basit `FROM` yan tümce öğeleri, `JOIN FROM` yan tümce öğeleri ve `APPLY FROM` yan tümce öğeleri. Bu `FROM` yan tümce öğelerinin her biri, aşağıdaki bölümlerde daha ayrıntılı olarak açıklanmıştır.

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

`JOIN FROM`Yan tümce öğesi iki yan tümce öğesi arasında bir birleştirmeyi temsil eder `FROM` . [!INCLUDE[esql](../../../../../../includes/esql-md.md)] çapraz birleştirmeleri, iç birleştirmeleri, sol ve sağ dış birleştirmeleri ve tam dış birleştirmeleri destekler. Tüm bu birleştirmeler Transact-SQL ' de desteklendikleri yönteme benzer şekilde desteklenmektedir. Transact-SQL ' de olduğu gibi, içinde yer alan iki `FROM` yan tümce öğesi `JOIN` bağımsız olmalıdır. Diğer bir deyişle, bağıntılı olamaz. `CROSS APPLY` `OUTER APPLY` Bu durumlar için veya kullanılabilir.

#### <a name="cross-joins"></a>Çapraz birleşimler

Bir `CROSS JOIN` sorgu ifadesi, aşağıdaki örnekte gösterildiği gibi iki koleksiyonun Kartezyen çarpımını üretir:

`FROM C AS c CROSS JOIN D as d`

#### <a name="inner-joins"></a>İç birleştirmeler

`INNER JOIN`, Aşağıdaki örnekte gösterildiği gibi iki koleksiyonun kısıtlı bir Kartezyen ürününü üretir:

`FROM C AS c [INNER] JOIN D AS d ON e`

Önceki sorgu ifadesi, koşulun doğru olduğu yerde, sağ taraftaki koleksiyonun her öğesine karşı, sol taraftaki koleksiyonun her öğesinin bir birleşimini işler `ON` . Herhangi `ON` bir koşul belirtilmemişse, bir, bir ' `INNER JOIN` a üretir `CROSS JOIN` .

#### <a name="left-outer-joins-and-right-outer-joins"></a>Sol dış birleşimler ve sağ dış birleşimler

Bir `OUTER JOIN` sorgu ifadesi, aşağıdaki örnekte gösterildiği gibi iki koleksiyonun kısıtlı bir Kartezyen ürününü üretir:

`FROM C AS c LEFT OUTER JOIN D AS d ON e`

Önceki sorgu ifadesi, koşulun doğru olduğu yerde, sağ taraftaki koleksiyonun her öğesine karşı, sol taraftaki koleksiyonun her öğesinin bir birleşimini işler `ON` . `ON`Koşul false ise, ifade, sol taraftaki öğenin tek bir örneğini, null değeri ile sağ taraftaki öğeye karşı işler.

`RIGHT OUTER JOIN`Benzer bir şekilde ifade edilebilir.

#### <a name="full-outer-joins"></a>Tam dış birleşimler

Açık `FULL OUTER JOIN` , aşağıdaki örnekte gösterildiği gibi iki koleksiyonun kısıtlı bir Kartezyen çarpımını üretir:

`FROM C AS c FULL OUTER JOIN D AS d ON e`

Önceki sorgu ifadesi, koşulun doğru olduğu yerde, sağ taraftaki koleksiyonun her öğesine karşı, sol taraftaki koleksiyonun her öğesinin bir birleşimini işler `ON` . `ON`Koşul false ise, ifade, sol taraftaki öğenin bir örneğini, null değeri ile sağ taraftaki öğeye karşı işler. Ayrıca, sol taraftaki öğenin bir örneğini solda, null değeriyle birlikte işler.

> [!NOTE]
> SQL-92 ile uyumluluğu korumak için Transact-SQL içinde DıŞTAKI anahtar sözcüğü isteğe bağlıdır. Bu nedenle,, ve,, ve `LEFT JOIN` `RIGHT JOIN` `FULL JOIN` için eş anlamlılardır `LEFT OUTER JOIN` `RIGHT OUTER JOIN` `FULL OUTER JOIN` .

### <a name="apply-clause-item"></a>APPLY yan tümce öğesi

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] iki tür destekler `APPLY` : `CROSS APPLY` ve `OUTER APPLY` .

`CROSS APPLY`, Sağ taraftaki ifade hesaplanarak oluşturulan koleksiyonun öğesi ile sol taraftaki koleksiyonun her bir öğesi için benzersiz bir eşleştirme üretir. İle `CROSS APPLY` , sağ taraftaki ifade, aşağıdaki ilişkili koleksiyon örneğinde gösterildiği gibi, sol taraftaki öğeye göre değişir:

`SELECT c, f FROM C AS c CROSS APPLY c.Assoc AS f`

Davranışı, `CROSS APPLY` JOIN listesine benzerdir. Sağdaki ifade boş bir koleksiyon olarak değerlendirilirse, `CROSS APPLY` sol taraftaki öğenin bu örneği için hiçbir eşleşme üretmez.

Bir `OUTER APPLY` `CROSS APPLY` eşleşme, sağdaki ifade boş bir koleksiyon olarak değerlendirilse bile hala üretildiğinde, bir a benzerdir. Aşağıda bir örneği verilmiştir `OUTER APPLY` :

`SELECT c, f FROM C AS c OUTER APPLY c.Assoc AS f`

> [!NOTE]
> Transact-SQL ' den farklı olarak, içinde açık iç içe olmayan bir adım yoktur [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .

> [!NOTE]
> `CROSS` ve `OUTER APPLY` işleçleri SQL Server 2005 ' de tanıtılmıştı. Bazı durumlarda, sorgu işlem hattı `CROSS APPLY` ve/veya işleçlerini Içeren Transact-SQL üretebilir `OUTER APPLY` . SQL Server 2005 ' den önceki SQL Server sürümleri de dahil olmak üzere bazı arka uç sağlayıcılar bu işleçleri desteklemediğinden, bu arka uç sağlayıcılarında bu sorgular yürütülemez.
>
> `CROSS APPLY`Çıktı sorgusunda ve/veya işleçleri varlığına neden olabilecek bazı tipik senaryolar şunlardır `OUTER APPLY` : sayfalama içeren bağıntılı alt sorgu; Bağıntılı bir alt sorgu üzerinden veya gezinti tarafından oluşturulan bir koleksiyon üzerinden AnyElement; Öğe seçiciyi kabul eden gruplandırma yöntemlerini kullanan LINQ sorguları; `CROSS APPLY`ya da ' ın açıkça belirttiği bir sorgu; bir `OUTER APPLY` `DEREF` yapı üzerinde yapısına sahip olan bir sorgu `REF` .

## <a name="multiple-collections-in-the-from-clause"></a>FROM yan tümcesinde birden çok koleksiyon

`FROM`Yan tümce, virgülle ayrılmış birden fazla koleksiyon içerebilir. Bu durumlarda, koleksiyonların birlikte birleştirilme varsayılır. Bunları n yönlü bir çapraz JOIN olarak düşünün.

Aşağıdaki örnekte `C` ve `D` bağımsız koleksiyonlardır, ancak `c.Names` bağımlıdır `C` .

```sql
FROM C AS c, D AS d, c.Names AS e
```

Önceki örnek, aşağıdaki örneğe mantıksal olarak eşdeğerdir:

`FROM (C AS c JOIN D AS d) CROSS APPLY c.Names AS e`

## <a name="left-correlation"></a>Sol bağıntı

 `FROM`Yan tümcesindeki öğeler, önceki yan tümcelerde belirtilen öğelere başvurabilir. Aşağıdaki örnekte `C` ve `D` bağımsız koleksiyonlardır, ancak `c.Names` bağımlıdır `C` :

```sql
from C as c, D as d, c.Names as e
```

Bu, mantıksal olarak eşdeğerdir:

```sql
from (C as c join D as d) cross apply c.Names as e
```

## <a name="semantics"></a>Semantik

Mantıksal olarak, `FROM` yan tümcesindeki koleksiyonlar tek yönlü çapraz birleştirmenin bir parçası olduğu varsayılır `n` (1 yönlü çapraz birleşimin olması dışında). `FROM`Yan tümcesindeki diğer adlar soldan sağa işlenir ve daha sonra başvurmak üzere geçerli kapsama eklenir. `FROM`Yan tümce, bir dizi çoklu küme üreten kabul edilir. Yan tümcesindeki her öğe için, `FROM` o koleksiyon öğesinden tek bir öğeyi temsil eden bir alan olacaktır.

`FROM`Yan tümcesi, c, d ve e alanlarının,, ve öğelerinin öğe türünde olduğu kabul edildiği satır türünde satırları (c, d, e) mantıksal olarak oluşturur `C` `D` `c.Names` .

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] kapsamdaki her basit yan tümce öğesi için bir diğer ad tanıtır `FROM` . Örneğin, aşağıdaki FROM yan tümcesi kod parçacığında, kapsamında tanıtılan adlar c, d ve e 'dir.

```sql
from (C as c join D as d) cross apply c.Names as e
```

' De [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (Transact-SQL ' den farklı olarak), `FROM` yan tümce yalnızca kapsamdaki diğer adları tanıtır. Bu koleksiyonların sütunlarına (Özellikler) yapılan tüm başvurular diğer adla nitelenmelidir.

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
