---
title: "Sipariş (varlığıyla, SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e4ef6edfc56fe73cd509d466fcc26cdb24069c9f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="order-by-entity-sql"></a>Sipariş (varlığıyla, SQL)
SELECT deyimi içinde döndürülen nesne üzerinde kullanılan sıralama düzeni belirtir.  
  
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
 Herhangi bir geçerli sorgu ifade bir özelliği üzerinde sıralama yapılacak belirtme. Birden çok sıralama ifadeleri belirtilebilir. ORDER BY yan tümcesinde sıralama ifadesi dizisini sıralanmış sonuç kümesi organizasyonu tanımlar.  
  
 COLLATE {collation_name}  
 Belirtilen harmanlama göre sıralama işlemi gerçekleştirilmelidir belirtir `collation_name`. COLLATE yalnızca dize ifadeler için geçerlidir.  
  
 ASC  
 Belirtilen özellik değerleri, en yüksek değeri için en düşük değerden artan sırada sıralanması gerektiğini belirtir. Bu varsayılandır.  
  
 DESC  
 Belirtilen özellik değerleri, en yüksek değerden düşük değere azalan sırada sıralanması gerektiğini belirtir.  
  
 SINIRI`n`  
 Yalnızca ilk `n` öğeleri seçilir.  
  
 ATLA`n`  
 İlk atlar `n` öğeleri.  
  
## <a name="remarks"></a>Açıklamalar  
 ORDER BY yan tümcesi, SELECT yan tümcesi sonucuna mantıksal olarak uygulanır. ORDER BY yan tümcesi, select listesindeki öğeleri benzersizse kullanarak başvurabilirsiniz. ORDER BY yan tümcesi de şu anda kapsam diğer değişkenleri başvuruda bulunabilir. SELECT yan tümcesi ile ayrı bir değiştirici belirtildi, ancak, ORDER BY yan tümcesi yalnızca diğer adlar from SELECT yan tümcesi başvuruda bulunabilir.  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 ORDER BY yan tümcesinde her ifade sıralı eşitsizlik (küçük veya büyük, vb.) için karşılaştırılması gereken bazı türü değerlendirilmelidir. Bu sayı, dizeleri ve tarihleri gibi genellikle skaler temelleri türleridir. RowTypes karşılaştırılabilir türleri sıralı karşılaştırılabilir ayrıca değildir.  
  
 Kodunuzu bir sıralanmış küme üzerinde tekrarlanıyorsa dışında en üst düzey bir yansıtma için çıktı korunur, sipariş olması için kesin değildir.  
  
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
  
## <a name="restricted-keywords"></a>Sınırlı anahtar sözcükler  
 Aşağıdaki anahtar sözcükler kullanıldığında tırnak içine alınmalıdır bir `ORDER BY` yan tümcesi:  
  
-   ÇAPRAZ  
  
-   TAM  
  
-   ANAHTARI  
  
-   SOL  
  
-   SIRASI  
  
-   DIŞ  
  
-   SAĞ  
  
-   SATIR  
  
-   DEĞER  
  
## <a name="ordering-nested-queries"></a>İç içe geçmiş sorgular sıralama  
 Entity Framework iç içe geçmiş bir ifade herhangi bir yere sorguda yerleştirilebilir; iç içe bir sorgu sırası korunmaz.  
  
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
 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu ORDER BY işleci bir SELECT deyiminde döndürülen nesne üzerinde kullanılan sıralama düzenini belirlemek için kullanır. Sorgu AdventureWorks satış modelini temel alır. Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#ORDERBY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#orderby)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sorgu İfadeleri](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
 [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
 [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
