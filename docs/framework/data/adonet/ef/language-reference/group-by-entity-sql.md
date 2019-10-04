---
title: Gruplandırma ölçütü (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cf4f4972-4724-4945-ba44-943a08549139
ms.openlocfilehash: 711fbdc2d51177037cf349150c3431de14b11974
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833788"
---
# <a name="group-by-entity-sql"></a>Gruplandırma ölçütü (Entity SQL)
Sorgu ([Select](select-entity-sql.md)) ifadesi tarafından döndürülen nesnelerin yerleştirileceği grupları belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```sql  
[ GROUP BY aliasedExpression [ ,...n ] ]  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `aliasedExpression`  
 Gruplandırmada uygulanan geçerli bir sorgu ifadesi. `expression`, FROM yan tümcesi tarafından döndürülen bir özelliğe başvuran bir özellik veya toplama olmayan bir ifade olabilir. GROUP BY yan tümcesindeki her bir ifade, eşitlik için karşılaştırılabileceğiniz bir tür olarak değerlendirilmelidir. Bu türler genellikle sayılar, dizeler ve tarihler gibi skaler temel öğelerdir. Bir koleksiyona göre gruplandırma yapılamaz.  
  
## <a name="remarks"></a>Açıklamalar  
 Toplama işlevleri SELECT yan tümcesine dahil edilir \<select List >, GROUP BY her grup için bir Özet değeri hesaplar. GROUP BY belirtildiğinde, select listesindeki toplama olmayan bir ifadedeki her bir özellik adı, gruplama ölçütü listesine dahil edilmelidir, ya da GROUP BY ifadesi Select List ifadesiyle tam olarak eşleşmelidir.  
  
> [!NOTE]
> ORDER BY yan tümcesi belirtilmemişse GROUP BY yan tümcesinin döndürdüğü gruplar belirli bir sırada değildir. Verilerin belirli bir sıralamasını belirtmek için ORDER BY yan tümcesini her zaman kullanmanızı öneririz.  
  
 GROUP BY yan tümcesi belirtildiğinde, açıkça veya örtük olarak (örneğin, sorgudaki HAVING yan tümcesi tarafından), geçerli kapsam gizlidir ve yeni bir kapsam ortaya çıkartılır.  
  
 SELECT yan tümcesi, HAVING yan tümcesi ve ORDER BY yan tümcesi artık FROM yan tümcesinde belirtilen öğe adlarına başvuramayacak. Yalnızca gruplandırma ifadelerine başvurabilirsiniz. Bunu yapmak için, her gruplama ifadesine yeni adlar (diğer adlar) atayabilirsiniz. Gruplandırma ifadesi için bir diğer ad belirtilmemişse, [!INCLUDE[esql](../../../../../../includes/esql-md.md)], aşağıdaki örnekte gösterildiği gibi diğer ad oluşturma kurallarını kullanarak bir tane oluşturmaya çalışır.  
  
 `SELECT g1, g2, ...gn FROM c as c1`  
  
 `GROUP BY e1 as g1, e2 as g2, ...en as gn`  
  
 GROUP BY yan tümcesindeki ifadeler, aynı GROUP BY yan tümcesinde daha önce tanımlanan adlara başvuramaz.  
  
 Adları gruplandırma konusuna ek olarak, SELECT yan tümcesinde, HAVING yan tümcesinde ve ORDER BY yan tümcesinde toplamaları de belirtebilirsiniz. Bir toplama, grubun her öğesi için değerlendirilen bir ifade içerir. Toplam işleci, tüm bu ifadelerin değerlerini azaltır (genellikle, ancak her zaman tek bir değere değildir). Toplama ifadesi, üst kapsamda görünen özgün öğe adlarına veya GROUP BY yan tümcesinin kendisi tarafından tanıtılan yeni adlara başvuru yapabilir. Toplamaların SELECT yan tümcesinde, HAVING yan tümcesinde ve ORDER BY yan tümcesinde görünmesine karşın, bu değerler, aşağıdaki örnekte gösterildiği gibi gruplama ifadeleri ile aynı kapsam altında değerlendirilir.  
  
 `SELECT name, sum(o.Price * o.Quantity) as total`  
  
 `FROM orderLines as o`  
  
 `GROUP BY o.Product as name`  
  
 Bu sorgu, ürüne göre bölünmüş, sipariş edilen tüm ürünlerin maliyetinin bir raporunu oluşturmak için GROUP BY yan tümcesini kullanır. @No__t-0 ' ı, gruplandırma ifadesinin bir parçası olarak ürüne verir ve ardından SEÇIM listesinde bu ada başvurur. Ayrıca, sipariş satırının fiyat ve miktarına dahili olarak başvuran SEÇIM listesindeki toplam `sum` ' ı belirtir.  
  
 Her bir GROUP BY anahtar ifadesine giriş kapsamına en az bir başvuru olmalıdır:  
  
```sql  
SELECT FROM Persons as P  
GROUP BY Q + P   -- GOOD  
GROUP BY Q   -- BAD  
GROUP BY 1   -- BAD, a constant is not allowed  
```  
  
 GROUP BY kullanımına ilişkin bir örnek için bkz. [HAVING](having-entity-sql.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu, nesneleri bir sorgu tarafından döndürülen grupları belirtmek için GROUP BY işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu `ExecutePrimitiveTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-sql[DP EntityServices Concepts#GROUPBY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#groupby)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL başvurusu](entity-sql-reference.md)
- [Sorgu Ifadeleri](query-expressions-entity-sql.md)
