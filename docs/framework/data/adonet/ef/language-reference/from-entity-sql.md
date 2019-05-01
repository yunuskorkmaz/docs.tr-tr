---
title: (Varlıktan, SQL)
ms.date: 03/30/2017
ms.assetid: ff3e3048-0d5d-4502-ae5c-9187fcbd0514
ms.openlocfilehash: 3cc02b4c51b32d0faace4d89d0c6c1f6923dd138
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879586"
---
# <a name="from-entity-sql"></a>(Varlıktan, SQL)
Kullanılan koleksiyon belirtir [seçin](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) deyimleri.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
FROM expression [ ,...n ] as C  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Bir kaynağı olarak kullanılacak bir koleksiyon verir herhangi bir geçerli sorgu ifade bir `SELECT` deyimi.  
  
## <a name="remarks"></a>Açıklamalar  
 A `FROM` yan tümcesi, bir veya daha fazla virgülle ayrılmış listesi `FROM` yan tümcesi öğeleri. `FROM` Yan tümcesi için bir veya daha fazla kaynakları belirtmek için kullanılabilir bir `SELECT` deyimi. En basit biçimi bir `FROM` yan tümcesi olan bir koleksiyon ve kaynak olarak kullanılan bir diğer ad tanımlayan tek bir sorgu ifadesinin bir `SELECT` aşağıdaki örnekte gösterildiği gibi deyimi:  
  
 `FROM C as c`  
  
## <a name="from-clause-items"></a>Yan tümcesi öğeleri  
 Her `FROM` yan tümce öğesi bir kaynak koleksiyonu başvurduğu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Aşağıdaki sınıfları destekler `FROM` yan öğeler: basit `FROM` yan tümcesi öğeleri `JOIN FROM` yan tümcesi öğeleri ve `APPLY FROM` yan tümcesi öğeleri. Bunların her biri `FROM` yan öğeler aşağıdaki bölümlerde daha ayrıntılı açıklanmıştır.  
  
### <a name="simple-from-clause-item"></a>Basit yan tümce öğesi  
 En basit `FROM` yan tümce öğesi olan bir koleksiyon ve bir diğer ad tanımlayan tek bir ifade. İfade, yalnızca bir varlık kümesini veya alt sorgu veya koleksiyon türü herhangi bir ifade olabilir. Bir örnek verilmiştir:  
  
```  
LOB.Customers as c  
```  
  
 Diğer ad belirtimi isteğe bağlıdır. Yan tümce öğesi Yukarıdakilerden alternatif bir belirtimi şu olabilir:  
  
```  
LOB.Customers  
```  
  
 Diğer ad yok belirtilirse, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] koleksiyon ifadeye göre bir diğer ad oluşturmaya çalışır.  
  
### <a name="join-from-clause-item"></a>FROM yan tümce öğesi katılın  
 A `JOIN FROM` yan tümce öğesi temsil eder, ikisi arasında bir birleştirme `FROM` yan tümcesi öğeleri. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] destekler, birleşimler, İç birleşimler sol ve sağ dış birleşimler ve tam dış birleştirmeler arası. Bu birleştirme benzer şekilde, desteklenen desteklenen [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]. Olarak [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], iki `FROM` söz konusu yan tümcesi öğeleri `JOIN` bağımsız olmalıdır. Diğer bir deyişle, bunlar büyük olamaz. A `CROSS APPLY` veya `OUTER APPLY` bu durumlarda kullanılabilir.  
  
#### <a name="cross-joins"></a>Çapraz birleştirme  
 A `CROSS JOIN` sorgu ifadesi, aşağıdaki örnekte gösterildiği gibi iki koleksiyon Kartezyen ürün oluşturur:  
  
 `FROM C AS c CROSS JOIN D as d`  
  
#### <a name="inner-joins"></a>İç birleşimler  
 Bir `INNER JOIN` aşağıdaki örnekte gösterildiği gibi iki koleksiyon kısıtlanmış bir Kartezyen ürün oluşturur:  
  
 `FROM C AS c [INNER] JOIN D AS d ON e`  
  
 Önceki sorgu ifadesinin sağ nerede hakkında koleksiyonun her öğesine karşı eşleştirilmiş sol taraftaki koleksiyonun her öğesine bir birleşimini işler `ON` koşul true ise. Hayır ise `ON` koşul belirtilirse, bir `INNER JOIN` için degenerates bir `CROSS JOIN`.  
  
#### <a name="left-outer-joins-and-right-outer-joins"></a>Sol dış birleştirmeler ve sağ dış birleşimler  
 Bir `OUTER JOIN` sorgu ifadesi, aşağıdaki örnekte gösterildiği gibi iki koleksiyon kısıtlanmış bir Kartezyen ürün oluşturur:  
  
 `FROM C AS c LEFT OUTER JOIN D AS d ON e`  
  
 Önceki sorgu ifadesinin sağ nerede hakkında koleksiyonun her öğesine karşı eşleştirilmiş sol taraftaki koleksiyonun her öğesine bir birleşimini işler `ON` koşul true ise. Varsa `ON` koşul false ise, ifade hala öğesi null değerine sahip sağdaki karşı eşleştirilmiş soldaki öğeyi tek bir örneğini işler.  
  
 A `RIGHT OUTER JOIN` benzer bir şekilde ifade edilebilir.  
  
#### <a name="full-outer-joins"></a>Tam dış birleşimler  
 Açık bir `FULL OUTER JOIN` aşağıdaki örnekte gösterildiği gibi iki koleksiyon kısıtlanmış bir Kartezyen ürün oluşturur:  
  
 `FROM C AS c FULL OUTER JOIN D AS d ON e`  
  
 Önceki sorgu ifadesinin sağ nerede hakkında koleksiyonun her öğesine karşı eşleştirilmiş sol taraftaki koleksiyonun her öğesine bir birleşimini işler `ON` koşul true ise. Varsa `ON` koşul false ise, ifade hala öğesi null değerine sahip sağdaki karşı eşleştirilmiş soldaki öğesinin bir örneğini işler. Ayrıca, öğe null değeri ile sol taraftaki karşı eşleştirilmiş sağdaki öğesinin bir örneğini işler.  
  
> [!NOTE]
>  İçinde SQL 92, uyumluluğu korumak için [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] dış anahtar sözcüğü isteğe bağlıdır. Bu nedenle, `LEFT JOIN`, `RIGHT JOIN`, ve `FULL JOIN` için eş anlamlı sözcükler olan `LEFT OUTER JOIN`, `RIGHT OUTER JOIN`, ve `FULL OUTER JOIN`.  
  
### <a name="apply-clause-item"></a>Geçerli yan tümce öğesi  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] iki tür destekler, `APPLY`: `CROSS APPLY` ve `OUTER APPLY`.  
  
 A `CROSS APPLY` sol taraftaki koleksiyonun her öğesine sağ ifade tarafından değerlendirilen koleksiyonun bir öğesi ile benzersiz eşleştirmesi üretir. İle bir `CROSS APPLY`, sağdaki ifade ilişkili koleksiyon aşağıdaki örnekte gösterildiği gibi işlevsel olarak öğe sol taraftaki bağlıdır:  
  
 `SELECT c, f FROM C AS c CROSS APPLY c.Assoc AS f`  
  
 Davranışını `CROSS APPLY` birleştirme listeye benzer. Sağ ifade boş bir koleksiyon olarak değerlendirilirse `CROSS APPLY` öğenin sol taraftaki Bu örnek için hiçbir değer çiftlerini oluşturur.  
  
 Bir `OUTER APPLY` benzer bir `CROSS APPLY`bile boş bir koleksiyon için sağ taraftaki ifade sonucunu verdiğinde bir eşleştirme hala üretilen dışında. Aşağıdaki örneğidir bir `OUTER APPLY`:  
  
 `SELECT c, f FROM C AS c OUTER APPLY c.Assoc AS f`  
  
> [!NOTE]
>  Aksine, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], gerekli olmadığı için bir açık unnest adımda [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
> [!NOTE]
>  `CROSS` ve `OUTER APPLY` işleçleri de kullanıma sunulmuştur [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)]. Bazı durumlarda, sorgu işlem hattındaki içeren Transact-SQL üretebilir `CROSS APPLY` ve/veya `OUTER APPLY` işleçleri. İçin SQL Server sürümleri dahil olmak üzere bazı arka uç sağlayıcıları öncesi [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)], bu işleçleri desteklemez, bu arka uç sağlayıcılarında sorgularını yürütülemez.  
>   
>  Varlığı için yol açabilecek bazı genel senaryolara `CROSS APPLY` ve/veya `OUTER APPLY` çıkış sorgu işleçler şunlardır: disk belleği ile; ilişkili alt sorgu AnyElement bağıntılı alt sorgu veya gezinti tarafından üretilen bir koleksiyon üzerinden; LINQ öğe Seçici kabul yöntemleri gruplandırma kullanan sorgular; bir sorguda bir `CROSS APPLY` veya `OUTER APPLY` açıkça belirtilir; olan bir sorgu bir `DEREF` üzerinden oluşturmak bir `REF` oluşturun.  
  
## <a name="multiple-collections-in-the-from-clause"></a>Birden çok koleksiyon FROM yan tümcesi  
 `FROM` Yan tümcesi, virgülle ayırarak birden fazla koleksiyon bulunabilir. Bu durumlarda, koleksiyonları birlikte katılması kabul edilir. Bu çok yönlü çapraz birleştirme olarak düşünün.  
  
 Aşağıdaki örnekte, `C` ve `D` bağımsız koleksiyonlar, ancak `c.Names` bağlıdır `C`.  
  
```  
FROM C AS c, D AS d, c.Names AS e  
```  
  
 Önceki örnekte, mantıksal olarak aşağıdaki örneğe eşdeğerdir:  
  
 `FROM (C AS c JOIN D AS d) CROSS APPLY c.Names AS e`  
  
## <a name="left-correlation"></a>Sol bağıntı  
 Öğeler `FROM` yan tümcesi, önceki yan tümcelerinde belirtilen öğelere başvurabilir. Aşağıdaki örnekte, `C` ve `D` bağımsız koleksiyonlar, ancak `c.Names` bağlıdır `C`:  
  
```  
from C as c, D as d, c.Names as e  
```  
  
 Bu mantıksal olarak eşdeğerdir.  
  
```  
from (C as c join D as d) cross apply c.Names as e  
```  
  
## <a name="semantics"></a>Semantiği  
 Mantıksal olarak koleksiyonlarında `FROM` yan tümcesi olduğu varsayılır parçası olarak bir `n`-(1-şekilde söz konusu olduğunda çapraz birleştirme dışında) şekilde çapraz birleştirme. Diğer adlar `FROM` yan tümcesi, soldan sağa doğru işlem ve daha sonra başvurmak için geçerli bir kapsama eklenir. `FROM` Yan tümcesi, bir çoklu küme satır üretmek için varsayılır. Her öğe için bir alan olacaktır `FROM` yan tümcesi bu koleksiyon öğesi tek bir öğeyi temsil eder.  
  
 `FROM` Üretir mantıksal olarak bir çoklu küme türü (c, d, e) satır satır yan tümcesi burada alanları c, d ve e öğe türünde oldukları varsayılır `C`, `D`, ve `c.Names`.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Her basit için bir diğer ad tanıtır `FROM` kapsamda yan tümce öğesi. Örneğin, aşağıdakilerden yan tümcesi kod parçacığı, kapsam içinde tanıtılan c, d ve e adlarıdır.  
  
```  
from (C as c join D as d) cross apply c.Names as e  
```  
  
 İçinde [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (aksine [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]), `FROM` yan tümce kapsamına yalnızca diğer adları ortaya çıkarır. Bu koleksiyonun sütunları (özellikleri) tüm başvuruları diğer adıyla nitelenmelidir.  
  
## <a name="pulling-up-keys-from-nested-queries"></a>İç içe geçmiş sorgularından anahtarlarını çekiliyor  
 Belirli türlerdeki anahtarlarını iç içe geçmiş bir sorgunun çekmek gerektiren sorguları desteklenmez. Örneğin, aşağıdaki sorgusu geçerli değil:  
  
```  
select c.Orders from Customers as c   
```  
  
 Ancak, iç içe sorgu herhangi bir anahtar olmadığından aşağıdaki sorgu geçerli değil:  
  
```  
select {1} from {2, 3}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Sorgu İfadeleri](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
- [Null Değer Atanabilir Yapılandırılmış Türler](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
