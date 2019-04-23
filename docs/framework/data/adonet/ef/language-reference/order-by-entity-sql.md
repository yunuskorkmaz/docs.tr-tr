---
title: Sipariş (varlık tarafından SQL)
ms.date: 03/30/2017
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
ms.openlocfilehash: 4cf65637603fd6c20a33b1ae6ecd8b6ded36a246
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59328484"
---
# <a name="order-by-entity-sql"></a>Sipariş (varlık tarafından SQL)
Bir SELECT deyiminde döndürülen nesneler üzerinde kullanılan sıralama düzenini belirtir.  
  
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
 Herhangi bir geçerli sorgu ifade üzerinde sıralama yapılacak bir özelliğini belirterek. Birden çok sıralama ifadeleri belirtilebilir. ORDER BY yan tümcesinde sıralama ifadesi dizisini sıralanmış sonuç kümesinin kuruluş tanımlar.  
  
 COLLATE {collation_name}  
 ORDER BY işlemi belirtilen harmanlama göre yapılacağını belirtir `collation_name`. COLLATE yalnızca dize ifadeler için geçerlidir.  
  
 ASC  
 Belirtilen özellik değerleri, en yüksek değeri için en düşük değerden artan sırada sıralanması gerektiğini belirtir. Bu varsayılandır.  
  
 DESC  
 Belirtilen özellik değerleri, en yüksek değerinden düşük bir değere azalan sırada sıralanması gerektiğini belirtir.  
  
 SINIRI `n`  
 Yalnızca ilk `n` öğe seçilir.  
  
 ATLA `n`  
 İlk atlar `n` öğeleri.  
  
## <a name="remarks"></a>Açıklamalar  
 ORDER BY yan tümcesi, SELECT yan tümcesi sonucuna mantıksal olarak uygulanır. ORDER BY yan tümcesi select listesindeki öğeleri diğer adlarını kullanarak başvurabilirsiniz. ORDER BY yan tümcesi şu anda kapsamındaki diğer değişkenleri de başvurabilirsiniz. FARKLI bir değiştiriciyle SELECT yan tümcesi belirtilmiş, ancak ORDER BY yan tümcesi yalnızca diğer adlar SELECT yan tümcesi başvurabilir.  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 ORDER BY yan tümcesindeki her ifade sıralı eşitsizlik (küçüktür veya büyüktür, vb.) için karşılaştırılabilir tür değerlendirilmelidir. Bu genelde skalar temelleri sayılar, dizeler ve tarihler gibi türleridir. RowTypes karşılaştırılabilir türlerde, ayrıca karşılaştırılabilir sırası değildir.  
  
 Kodunuzu sıralı bir küme üzerinde yinelenir, dışında en üst düzey bir projeksiyon için çıkış korunur sırası olması garanti edilmez.  
  
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
  
 Sahip bir sıralı UNION, UNION ALL, EXCEPT veya INTERSECT işlemi için şu biçimi kullanın:  
  
```  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## <a name="restricted-keywords"></a>Sınırlı anahtar sözcükleri  
 Aşağıdaki anahtar sözcükler kullanıldığında tırnak içine alınmalıdır bir `ORDER BY` yan tümcesi:  
  
-   ÇAPRAZ  
  
-   TAM  
  
-   KEY  
  
-   SOL  
  
-   SIRASI  
  
-   DIŞ  
  
-   SAĞ  
  
-   ROW  
  
-   DEĞER  
  
## <a name="ordering-nested-queries"></a>İç içe geçmiş sorgular sıralama  
 Varlık Çerçevesi'nde, iç içe geçmiş bir ifade herhangi bir sorguda yerleştirilebilir; iç içe bir sorgu sırasını korunmaz.  
  
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
 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgusu ORDER BY işleci bir SELECT deyiminde döndürülen nesneler üzerinde kullanılan sıralama düzeni belirlemek için kullanır. Sorgu, AdventureWorks satış modelini temel alıyor. Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:  
  
1. Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#ORDERBY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#orderby)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu İfadeleri](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)
- [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)
- [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
