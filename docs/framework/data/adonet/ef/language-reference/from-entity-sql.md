---
title: (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ff3e3048-0d5d-4502-ae5c-9187fcbd0514
ms.openlocfilehash: 2334a30009d6bef9544d2ca1e0ab923a7441d6f2
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833825"
---
# <a name="from-entity-sql"></a>(Entity SQL)
[Select](select-entity-sql.md) deyimlerinde kullanılan koleksiyonu belirtir.

## <a name="syntax"></a>Sözdizimi

```sql
FROM expression [ ,...n ] AS C
```

## <a name="arguments"></a>Bağımsız Değişkenler

`expression` \
`SELECT` deyiminde kaynak olarak kullanılacak bir koleksiyon veren geçerli bir sorgu ifadesi.

## <a name="remarks"></a>Açıklamalar

`FROM` yan tümcesi bir veya daha fazla `FROM` yan tümce öğesinin virgülle ayrılmış listesidir. `FROM` yan tümcesi, bir `SELECT` deyimi için bir veya daha fazla kaynak belirtmek üzere kullanılabilir. Bir `FROM` yan tümcesinin en basit biçimi, aşağıdaki örnekte gösterildiği gibi bir koleksiyonu ve `SELECT` kaynak olarak kullanılan diğer adı tanımlayan tek bir sorgu deyimidir:

`FROM C as c`

## <a name="from-clause-items"></a>FROM yan tümce öğeleri

Her `FROM` yan tümce öğesi, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgusunda bir kaynak koleksiyonu anlamına gelir. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] aşağıdaki `FROM` yan tümce öğelerinin sınıflarını destekler: basit `FROM` yan tümce öğeleri, `JOIN FROM` yan tümce öğeleri ve `APPLY FROM` yan tümce öğeleri. Bu `FROM` yan tümce öğelerinin her biri, aşağıdaki bölümlerde daha ayrıntılı olarak açıklanmıştır.

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

`JOIN FROM` yan tümce öğesi iki `FROM` yan tümce öğesi arasında bir birleştirmeyi temsil eder. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] çapraz birleştirmeleri, iç birleştirmeleri, sol ve sağ dış birleştirmeleri ve tam dış birleştirmeleri destekler. Tüm bu birleştirmeler Transact-SQL ' de desteklendikleri yönteme benzer şekilde desteklenmektedir. Transact-SQL ' de olduğu gibi, `JOIN` dahil olan iki `FROM` yan tümce öğesi bağımsız olmalıdır. Diğer bir deyişle, bağıntılı olamaz. Bu durumlar için bir `CROSS APPLY` veya `OUTER APPLY` kullanılabilir.

#### <a name="cross-joins"></a>Çapraz birleşimler

`CROSS JOIN` bir sorgu ifadesi, aşağıdaki örnekte gösterildiği gibi iki koleksiyonun Kartezyen çarpımını üretir:

`FROM C AS c CROSS JOIN D as d`

#### <a name="inner-joins"></a>İç Birleşimler

`INNER JOIN`, aşağıdaki örnekte gösterildiği gibi iki koleksiyonun kısıtlı bir Kartezyen çarpımını üretir:

`FROM C AS c [INNER] JOIN D AS d ON e`

Önceki sorgu ifadesi, sol taraftaki koleksiyonun her öğesinin bir bileşimini, `ON` koşulun doğru olduğu, sağ taraftaki koleksiyonun her öğesine karşı işler. `ON` koşul belirtilmemişse, bir `INNER JOIN` `CROSS JOIN`kaldırır.

#### <a name="left-outer-joins-and-right-outer-joins"></a>Sol dış birleşimler ve sağ dış birleşimler

`OUTER JOIN` bir sorgu ifadesi, aşağıdaki örnekte gösterildiği gibi iki koleksiyonun kısıtlı bir Kartezyen çarpımını üretir:

`FROM C AS c LEFT OUTER JOIN D AS d ON e`

Önceki sorgu ifadesi, sol taraftaki koleksiyonun her öğesinin bir bileşimini, `ON` koşulun doğru olduğu, sağ taraftaki koleksiyonun her öğesine karşı işler. `ON` koşulu false ise, ifade, sol taraftaki öğenin tek bir örneğini, null değeri ile sağ taraftaki öğeye karşı işler.

`RIGHT OUTER JOIN` benzer bir şekilde ifade edilebilir.

#### <a name="full-outer-joins"></a>Tam dış birleşimler

Açık bir `FULL OUTER JOIN`, aşağıdaki örnekte gösterildiği gibi iki koleksiyonun kısıtlı bir Kartezyen çarpımını üretir:

`FROM C AS c FULL OUTER JOIN D AS d ON e`

Önceki sorgu ifadesi, sol taraftaki koleksiyonun her öğesinin bir bileşimini, `ON` koşulun doğru olduğu, sağ taraftaki koleksiyonun her öğesine karşı işler. `ON` koşulu false ise, ifade, sol taraftaki öğenin bir örneğini, null değeri ile sağ taraftaki öğeye karşı işler. Ayrıca, sol taraftaki öğenin bir örneğini solda, null değeriyle birlikte işler.

> [!NOTE]
> SQL-92 ile uyumluluğu korumak için Transact-SQL içinde DıŞTAKI anahtar sözcüğü isteğe bağlıdır. Bu nedenle, `LEFT JOIN`, `RIGHT JOIN`ve `FULL JOIN` `LEFT OUTER JOIN`, `RIGHT OUTER JOIN`ve `FULL OUTER JOIN`için eş anlamlılardır.

### <a name="apply-clause-item"></a>APPLY yan tümce öğesi

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] iki tür `APPLY`destekler: `CROSS APPLY` ve `OUTER APPLY`.

`CROSS APPLY`, sağ taraftaki ifade hesaplanarak oluşturulan koleksiyonun bir öğesi ile sol taraftaki koleksiyonun her bir öğesi için benzersiz bir eşleştirme üretir. `CROSS APPLY`, sağdaki ifade, aşağıdaki ilişkili koleksiyon örneğinde gösterildiği gibi, sol taraftaki öğe üzerinde işlevsel olarak değişir:

`SELECT c, f FROM C AS c CROSS APPLY c.Assoc AS f`

`CROSS APPLY` davranışı, JOIN listesine benzerdir. Sağdaki ifade boş bir koleksiyon olarak değerlendirilirse, `CROSS APPLY` sol taraftaki öğenin bu örneği için bir eşleşme üretmez.

Bir `OUTER APPLY` `CROSS APPLY`benzer, çünkü sağdaki ifade boş bir koleksiyon olarak değerlendirilse bile bir eşleştirme yine de oluşturulur. Aşağıda bir `OUTER APPLY`örneği verilmiştir:

`SELECT c, f FROM C AS c OUTER APPLY c.Assoc AS f`

> [!NOTE]
> Transact-SQL ' den farklı olarak, [!INCLUDE[esql](../../../../../../includes/esql-md.md)]açık iç içe geçme bir adım gerekmez.

> [!NOTE]
> `CROSS` ve `OUTER APPLY` işleçleri SQL Server 2005 ' de tanıtılmıştı. Bazı durumlarda sorgu işlem hattı, `CROSS APPLY` ve/veya `OUTER APPLY` işleçlerini içeren Transact-SQL üretebilir. SQL Server 2005 ' den önceki SQL Server sürümleri de dahil olmak üzere bazı arka uç sağlayıcılar bu işleçleri desteklemediğinden, bu arka uç sağlayıcılarında bu sorgular yürütülemez.
>
> Çıktı sorgusunda `CROSS APPLY` ve/veya `OUTER APPLY` işleçlerinin varlığına neden olabilecek bazı tipik senaryolar şunlardır: sayfalama ile bağıntılı bir alt sorgu; Bağıntılı bir alt sorgu üzerinden veya gezinti tarafından oluşturulan bir koleksiyon üzerinden AnyElement; Öğe seçiciyi kabul eden gruplandırma yöntemlerini kullanan LINQ sorguları; `CROSS APPLY` veya `OUTER APPLY` açıkça belirtildiği bir sorgu; `REF` yapısı üzerinde `DEREF` yapısına sahip bir sorgu.

## <a name="multiple-collections-in-the-from-clause"></a>FROM yan tümcesinde birden çok koleksiyon

`FROM` yan tümcesi, virgülle ayrılmış birden fazla koleksiyon içerebilir. Bu durumlarda, koleksiyonların birlikte birleştirilme varsayılır. Bunları n yönlü bir çapraz JOIN olarak düşünün.

Aşağıdaki örnekte, `C` ve `D` bağımsız koleksiyonlardır, ancak `c.Names` `C`bağımlıdır.

```sql
FROM C AS c, D AS d, c.Names AS e
```

Önceki örnek, aşağıdaki örneğe mantıksal olarak eşdeğerdir:

`FROM (C AS c JOIN D AS d) CROSS APPLY c.Names AS e`

## <a name="left-correlation"></a>Sol bağıntı
 `FROM` yan tümcesindeki öğeler, önceki yan tümcelerde belirtilen öğelere başvurabilir. Aşağıdaki örnekte, `C` ve `D` bağımsız koleksiyonlardır, ancak `c.Names` `C`bağımlıdır:

```sql
from C as c, D as d, c.Names as e
```

Bu, mantıksal olarak eşdeğerdir:

```sql
from (C as c join D as d) cross apply c.Names as e
```

## <a name="semantics"></a>İçeriyor

Mantıksal olarak, `FROM` yan tümcesindeki koleksiyonlar, bir `n`yönlü çapraz birleştirmenin parçası olduğu varsayılır (1 yönlü çapraz birleşimin olması dışında). `FROM` yan tümcesindeki diğer adlar soldan sağa işlenir ve daha sonra başvurmak üzere geçerli kapsama eklenir. `FROM` yan tümcesi, birden çok satır kümesi üreten varsayılır. Bu koleksiyon öğesinden tek bir öğeyi temsil eden `FROM` yan tümcesindeki her öğe için bir alan olacaktır.

`FROM` yan tümcesi, c, d ve e alanlarının `C`, `D`ve `c.Names`öğe türünde olduğu kabul edildiği satır türünde satırları (c, d, e) mantıksal olarak oluşturur.

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] kapsamdaki her bir basit `FROM` yan tümce öğesi için bir diğer ad tanıtır. Örneğin, aşağıdaki FROM yan tümcesi kod parçacığında, kapsamında tanıtılan adlar c, d ve e 'dir.

```sql
from (C as c join D as d) cross apply c.Names as e
```

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] (Transact-SQL ' den farklı olarak), `FROM` yan tümcesi yalnızca kapsamdaki diğer adları tanıtır. Bu koleksiyonların sütunlarına (Özellikler) yapılan tüm başvurular diğer adla nitelenmelidir.

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
