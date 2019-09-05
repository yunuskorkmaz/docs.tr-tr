---
title: SıRALAMA ölçütü (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
ms.openlocfilehash: f3310274766ff3619604e30bfb5f5ca437cb1acd
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249760"
---
# <a name="order-by-entity-sql"></a>SıRALAMA ölçütü (Entity SQL)
Bir SELECT ifadesinde döndürülen nesnelerde kullanılan sıralama düzenini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[ ORDER BY   
   {  
      order_by_expression [SKIP n] [LIMIT n]  
      [ COLLATE collation_name ]  
      [ ASC | DESC ]  
   }  
   [ ,…n ]   
]  
```  
  
## <a name="arguments"></a>Arguments  
 `order_by_expression`  
 Üzerinde sıralanacak bir özellik belirten geçerli bir sorgu ifadesi. Birden çok sıralama ifadesi belirlenebilir. ORDER BY yan tümcesindeki sıralama ifadelerinin sırası, sıralanmış sonuç kümesinin organizasyonunu tanımlar.  
  
 {Collation_name} Harmanla  
 ORDER BY işleminin ' de `collation_name`belirtilen harmanlamaya göre gerçekleştirilmesi gerektiğini belirtir. HARMANLAMA yalnızca dize ifadeleri için geçerlidir.  
  
 ASC  
 Belirtilen özelliğindeki değerlerin, en düşük değerden en yüksek değere göre artan sırada sıralanması gerektiğini belirtir. Bu varsayılandır.  
  
 KÜMESINDE  
 Belirtilen özelliğindeki değerlerin, en yüksek değerden en düşük değere göre azalan sırada sıralanması gerektiğini belirtir.  
  
 SINIRLI`n`  
 Yalnızca ilk `n` öğeler seçilecek.  
  
 ŞIMDILIK`n`  
 İlk `n` öğeleri atlar.  
  
## <a name="remarks"></a>Açıklamalar  
 ORDER BY yan tümcesi, SELECT yan tümcesinin sonucuna mantıksal olarak uygulanır. ORDER BY yan tümcesi, seçim listesindeki öğelere diğer adlarını kullanarak başvurabilir. ORDER BY yan tümcesi, şu anda kapsamda olan diğer değişkenlere de başvurabilir. Ancak, SELECT yan tümcesi ayrı bir değiştiriciyle belirtilmişse, ORDER BY yan tümcesi yalnızca SELECT yan tümcesindeki diğer adlara başvurabilir.  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 ORDER BY yan tümcesindeki her bir ifade, sıralı eşitsizlik (küçüktür veya büyüktür, vb.) için karşılaştırılabileceğiniz bazı tür olarak değerlendirilmelidir. Bu türler genellikle sayılar, dizeler ve tarihler gibi skaler temel öğelerdir. Karşılaştırılabilir türlerin RowTypes da sıralı karşılaştırılabilir.  
  
 Kodunuz, üst düzey projeksiyon için dışında, sıralı bir küme üzerinde yinelenir, çıkışın sırasının korunması garanti edilmez.  
  
```  
-- In the following sample, order is guaranteed to be preserved:  
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
  
 Sıralı bir UNıON, UNıON ALL, EXCEPT veya ıNTERSECT işlemine sahip olmak için aşağıdaki kalıbı kullanın:  
  
```  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## <a name="restricted-keywords"></a>Kısıtlanmış anahtar sözcükler  
 Aşağıdaki anahtar sözcükler, bir `ORDER BY` yan tümcesinde kullanıldığında tırnak işaretleri içine alınmalıdır:  
  
- ÜSTÜNÜ  
  
- TÜMÜNÜ  
  
- KEY  
  
- TARAFTA  
  
- SIPARIŞI  
  
- DIŞ  
  
- RIGHT  
  
- ROW  
  
- DEERI  
  
## <a name="ordering-nested-queries"></a>Iç Içe sorguları sıralama  
 Entity Framework, iç içe geçmiş bir ifade sorgunun herhangi bir yerine yerleştirilebilir; iç içe geçmiş bir sorgunun sırası korunmaz.  
  
```  
-- The following query will order the results by the last name.  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query, ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, Select ifadesinde döndürülen nesneler üzerinde kullanılan sıralama düzenini belirtmek için order by işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Aşağıdaki adımları uygulayın: StructuralType sonuçları](../how-to-execute-a-query-that-returns-structuraltype-results.md)döndüren bir sorgu yürütün.  
  
2. Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-csharp[DP EntityServices Concepts 2#ORDERBY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#orderby)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu İfadeleri](query-expressions-entity-sql.md)
- [Entity SQL Başvurusu](entity-sql-reference.md)
- [SKIP](skip-entity-sql.md)
- [LIMIT](limit-entity-sql.md)
- [TOP](top-entity-sql.md)
