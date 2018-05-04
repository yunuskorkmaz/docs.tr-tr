---
title: (Varlıktan, SQL)
ms.date: 03/30/2017
ms.assetid: ff3e3048-0d5d-4502-ae5c-9187fcbd0514
ms.openlocfilehash: de2ad24e5c6399ed1ca91e3907da4a66c056e337
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="from-entity-sql"></a>(Varlıktan, SQL)
Kullanılan koleksiyon belirtir [seçin](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) deyimleri.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
FROM expression [ ,...n ] as C  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Bir kaynak olarak kullanılacak bir koleksiyon verir herhangi bir geçerli sorgu ifade bir `SELECT` deyimi.  
  
## <a name="remarks"></a>Açıklamalar  
 A `FROM` yan tümcesi olan bir veya daha fazla virgülle ayrılmış bir liste `FROM` yan tümcesi öğeleri. `FROM` Yan tümcesi için bir veya daha fazla kaynakları belirtmek için kullanılabilir bir `SELECT` deyimi. En basit biçimi bir `FROM` yan tümcesi bir toplama ve kaynağı olarak kullanılan bir diğer ad tanımlayan bir ifadedir tek bir sorgu bir `SELECT` deyimi, aşağıdaki örnekte gösterildiği gibi:  
  
 `FROM C as c`  
  
## <a name="from-clause-items"></a>Yan tümcesi öğeleri  
 Her `FROM` yan tümce öğesi, bir kaynak koleksiyondaki başvurduğu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Aşağıdaki sınıflarını destekleyen `FROM` yan tümcesi öğeleri: basit `FROM` yan tümcesi öğeleri `JOIN FROM` yan tümcesi öğeleri ve `APPLY FROM` yan tümcesi öğeleri. Bunların her biri `FROM` yan tümcesi öğeleri aşağıdaki bölümlerde daha ayrıntılı olarak açıklanmaktadır.  
  
### <a name="simple-from-clause-item"></a>Basit yan tümce öğesi  
 En basit `FROM` yan tümce öğesi olan bir koleksiyonu ve bir diğer ad tanımlayan tek bir ifade. İfade, yalnızca bir varlık kümesi veya alt sorgu veya koleksiyon türü herhangi bir ifade olabilir. Bir örnek verilmiştir:  
  
```  
LOB.Customers as c  
```  
  
 Diğer ad belirtimi isteğe bağlıdır. Yukarıdaki yan tümcesi öğesinden bir alternatif belirtimi şu olabilir:  
  
```  
LOB.Customers  
```  
  
 Diğer ad belirtilmezse, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Toplama ifadesi temelinde bir diğer ad oluşturmak çalışır.  
  
### <a name="join-from-clause-item"></a>Yan tümcesi öğesinden katılma  
 A `JOIN FROM` yan tümce öğesi temsil eden iki arasında bir birleşim `FROM` yan tümcesi öğeleri. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] destekler, birleşimler, İç birleşimler sol ve sağ dış birleşimler ve tam dış birleştirmeler arası. Bu birleştirmeler benzer şekilde, desteklenen desteklenen [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]. Olarak [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], iki `FROM` yan tümcesi öğeleri söz konusu `JOIN` bağımsız olması gerekir. Diğer bir deyişle, bunlar ilişkilendirilemez. A `CROSS APPLY` veya `OUTER APPLY` bu durumlar için kullanılabilir.  
  
#### <a name="cross-joins"></a>Birleştirmeler arası  
 A `CROSS JOIN` sorgu ifadesi aşağıdaki örnekte gösterildiği gibi iki koleksiyonların Kartezyen ürün oluşturur:  
  
 `FROM C AS c CROSS JOIN D as d`  
  
#### <a name="inner-joins"></a>İç birleşimler  
 Bir `INNER JOIN` aşağıdaki örnekte gösterildiği gibi iki koleksiyon, kısıtlı bir Kartezyen ürün oluşturur:  
  
 `FROM C AS c [INNER] JOIN D AS d ON e`  
  
 Önceki sorgu ifadesi her öğenin sağdaki nerede koleksiyonda her öğenin karşı eşleştirilmiş soldaki koleksiyonunun bileşimini işler `ON` koşul doğrudur. Öyle değilse `ON` koşulu belirtilirse, bir `INNER JOIN` için eğrisi bir `CROSS JOIN`.  
  
#### <a name="left-outer-joins-and-right-outer-joins"></a>Sol dış birleştirmeler ve sağ dış birleşimler  
 Bir `OUTER JOIN` sorgu ifadesi, aşağıdaki örnekte gösterildiği gibi iki koleksiyonları, kısıtlı bir Kartezyen ürün oluşturur:  
  
 `FROM C AS c LEFT OUTER JOIN D AS d ON e`  
  
 Önceki sorgu ifadesi her öğenin sağdaki nerede koleksiyonda her öğenin karşı eşleştirilmiş soldaki koleksiyonunun bileşimini işler `ON` koşul doğrudur. Varsa `ON` koşul yanlış ise, ifade hala soldaki null değerine sahip sağdaki öğesi karşı eşleştirilmiş öğesinde tek bir örneğini işler.  
  
 A `RIGHT OUTER JOIN` benzer bir şekilde ifade edilebilir.  
  
#### <a name="full-outer-joins"></a>Tam dış birleşimler  
 Açık bir `FULL OUTER JOIN` aşağıdaki örnekte gösterildiği gibi iki koleksiyonları, kısıtlı bir Kartezyen ürün oluşturur:  
  
 `FROM C AS c FULL OUTER JOIN D AS d ON e`  
  
 Önceki sorgu ifadesi her öğenin sağdaki nerede koleksiyonda her öğenin karşı eşleştirilmiş soldaki koleksiyonunun bileşimini işler `ON` koşul doğrudur. Varsa `ON` koşul yanlış ise, ifade null değerine sahip sağdaki öğesi karşı eşleştirilmiş soldaki öğesinin bir örneği hala işler. Ayrıca, soldaki null değerine sahip öğe karşı eşleştirilmiş sağdaki öğesinin bir örneğini işler.  
  
> [!NOTE]
>  İçinde SQL-92 ile uyumluluğu korumak için [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] dış anahtar sözcüğü isteğe bağlıdır. Bu nedenle, `LEFT JOIN`, `RIGHT JOIN`, ve `FULL JOIN` için eş anlamlı sözcükleri olan `LEFT OUTER JOIN`, `RIGHT OUTER JOIN`, ve `FULL OUTER JOIN`.  
  
### <a name="apply-clause-item"></a>Yan tümce öğesi UYGULA  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] iki tür destekler, `APPLY`: `CROSS APPLY` ve `OUTER APPLY`.  
  
 A `CROSS APPLY` her soldaki koleksiyon öğesi sağdaki ifadesinin hesaplanmasıyla oluşturulan koleksiyonun bir öğesi ile benzersiz eşleştirmesi üretir. İle bir `CROSS APPLY`, sağdaki ifade aşağıdaki ilişkili koleksiyon örnekte gösterildiği gibi işlevsel olarak öğesi solda, bağlı:  
  
 `SELECT c, f FROM C AS c CROSS APPLY c.Assoc AS f`  
  
 Davranışını `CROSS APPLY` birleştirme listesine benzer. Sağ ifade boş bir koleksiyon için değerlendirilirse `CROSS APPLY` soldaki öğesinin bu örneği için hiçbir değer çiftlerini üretir.  
  
 Bir `OUTER APPLY` benzer bir `CROSS APPLY`, sağdaki ifade boş bir koleksiyon için bile değerlendirirken, bir eşleştirme hala üretilen dışında. Aşağıdaki örneğidir bir `OUTER APPLY`:  
  
 `SELECT c, f FROM C AS c OUTER APPLY c.Assoc AS f`  
  
> [!NOTE]
>  Aksine, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], bir açık unnest adım için gerekli [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
> [!NOTE]
>  `CROSS` ve `OUTER APPLY` işleçleri sunuldu [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)]. Bazı durumlarda, içeren Transact-SQL sorgusu ardışık düzen üretebilir `CROSS APPLY` ve/veya `OUTER APPLY` işleçler. Çünkü SQL Server sürümleri dahil olmak üzere bazı arka uç sağlayıcıları öncesi [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)], bu işleçlere desteklemez, bu tür sorgular bu arka uç sağlayıcılarının yürütülemez.  
>   
>  Varlığı için yol açabilecek bazı tipik senaryolar `CROSS APPLY` ve/veya `OUTER APPLY` çıkış sorgusunda işleçler şunlardır: sayfalama ile; ilişkili bir alt sorgu İlişkili bir alt sorgu veya gezinti tarafından üretilen bir koleksiyon üzerinden AnyElement; LINQ bir öğe Seçicisi kabul yöntemleri gruplandırma kullanan sorgular; bir sorguda bir `CROSS APPLY` veya bir `OUTER APPLY` açıkça belirtilir; olan bir sorgu bir `DEREF` üzerinden oluşturmak bir `REF` oluşturun.  
  
## <a name="multiple-collections-in-the-from-clause"></a>Birden çok koleksiyon FROM yan tümcesi  
 `FROM` Yan tümcesi virgülle ayırarak birden fazla koleksiyon içerebilir. Bu durumlarda, birlikte birleştirilecek koleksiyonları varsayılır. Bunlar çok yönlü çapraz birleştirme olarak düşünün.  
  
 Aşağıdaki örnekte, `C` ve `D` bağımsız koleksiyonlar, ancak `c.Names` bağlı `C`.  
  
```  
FROM C AS c, D AS d, c.Names AS e  
```  
  
 Önceki örnekte aşağıdaki örneğe mantıksal olarak eşdeğerdir:  
  
 `FROM (C AS c JOIN D AS d) CROSS APPLY c.Names AS e`  
  
## <a name="left-correlation"></a>Sol bağıntı  
 Alanındaki öğelerin `FROM` yan tümcesi, önceki yan tümcelerinde belirtilen öğelere başvurabilir. Aşağıdaki örnekte, `C` ve `D` bağımsız koleksiyonlar, ancak `c.Names` bağlı `C`:  
  
```  
from C as c, D as d, c.Names as e  
```  
  
 Bu mantıksal olarak eşdeğerdir:  
  
```  
from (C as c join D as d) cross apply c.Names as e  
```  
  
## <a name="semantics"></a>Semantiği  
 Mantıksal olarak koleksiyonlarda `FROM` yan tümcesi parçası olarak kabul bir `n`-yönlü çapraz birleştirme (1 yönlü söz konusu olduğunda çapraz birleştirme dışında). Diğer adlar `FROM` yan tümcesi soldan sağa doğru işlem ve daha sonra başvurmak için geçerli bir kapsama eklenir. `FROM` Yan tümcesi multiset satır üretmek için varsayılır. Her öğe için bir alan olacaktır `FROM` tek bir öğe bu koleksiyon öğeyi temsil eden yan tümcesi.  
  
 `FROM` Üretir mantıksal olarak multiset satır türü (c, d, e) satır yan tümcesi burada alanları c, d ve e öğesi türünü varsayılır `C`, `D`, ve `c.Names`.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Her basit için diğer ad tanıtır `FROM` kapsamında yan tümce öğesi. Örneğin, aşağıdakileri yan tümcesi parçacığı gelen kapsam içine sunulan c, d ve e adlardır.  
  
```  
from (C as c join D as d) cross apply c.Names as e  
```  
  
 İçinde [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (aksine [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]), `FROM` yan tümcesi yalnızca kapsam içine diğer adları tanıtır. Bu koleksiyonlardaki sütunlar (Özellikler) yönelik tüm başvuruları diğer ad ile nitelenmiş olmalıdır.  
  
## <a name="pulling-up-keys-from-nested-queries"></a>İç içe geçmiş sorgularından anahtarlarını çekme  
 Belirli türde bir iç içe bir sorgu anahtarları çekme gerektiren sorguları desteklenmez. Örneğin, aşağıdaki sorgusu geçerli değil:  
  
```  
select c.Orders from Customers as c   
```  
  
 Ancak, iç içe sorgu herhangi bir anahtara sahip olmadığından aşağıdaki sorgusu geçerli değil:  
  
```  
select {1} from {2, 3}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Sorgu İfadeleri](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)  
 [Null Değer Atanabilir Yapılandırılmış Türler](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
