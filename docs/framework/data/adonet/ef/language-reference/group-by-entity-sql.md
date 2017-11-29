---
title: "Grup (varlığıyla, SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf4f4972-4724-4945-ba44-943a08549139
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cb19589fbba12bba710638e061defa198f9fa169
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="group-by-entity-sql"></a>Grup (varlığıyla, SQL)
Bir sorgu tarafından döndürülen hangi nesneleri içine grupları belirtir ([seçin](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) ifade olan yerleştirilecek.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[ GROUP BY aliasedExpression [ ,...n ] ]  
```  
  
## <a name="arguments"></a>Arguments  
 `aliasedExpression`  
 Herhangi bir geçerli sorgu ifade gruplandırma gerçekleştirildiği. `expression`bir özellik ya da FROM yan tümcesi tarafından döndürülen bir özelliğe başvuruyor toplama olmayan bir ifade olabilir. Her bir GROUP BY yan tümcesi ifadesinde eşitlik için karşılaştırılabilir bir türe değerlendirmeniz gerekir. Bu sayı, dizeleri ve tarihleri gibi genellikle skaler temelleri türleridir. Bir koleksiyona göre gruplandırma yapamazsınız.  
  
## <a name="remarks"></a>Açıklamalar  
 SELECT yan tümcesinde toplama işlevleri eklenirse \<seçim listesi >, GROUP BY her grup için bir Özet değer hesaplar. GROUP BY belirtildiğinde, her özellik adı seçim listesindeki herhangi bir zorunluluğu ifade GROUP BY listesinde eklenmesi veya GROUP BY ifadesi seçim listesi ifade tam olarak eşleşmelidir.  
  
> [!NOTE]
>  GROUP BY yan tümcesi tarafından döndürülen grupları ORDER BY yan tümcesi belirtilmezse, belirli bir sırada değildir. Belirli bir verinin sıralamasını belirtmek için her zaman ORDER BY yan tümcesi kullanmanızı öneririz.  
  
 Örtük olarak (örneğin, sorgudaki HAVING yan tümcesi tarafından) veya bir GROUP BY yan tümcesi, ya da açıkça belirtildiğinde geçerli kapsamdaki gizlidir ve yeni bir kapsam sunulmuştur.  
  
 SELECT yan tümcesi, HAVING yan tümcesi ve ORDER BY yan tümcesi artık FROM yan tümcesinde belirtilen öğe adları başvurmak mümkün olmayacaktır. Yalnızca gruplandırma ifadeleri kendilerini başvurabilir. Bunu yapmak için her gruplandırma ifadesi yeni adları (diğer adlar) atayabilirsiniz. Gruplandırma ifadesi için diğer ad belirtilmezse [!INCLUDE[esql](../../../../../../includes/esql-md.md)] aşağıdaki örnekte gösterildiği gibi diğer adı oluşturma kuralları kullanarak bir tane oluşturmak çalışır.  
  
 `SELECT g1, g2, ...gn FROM c as c1`  
  
 `GROUP BY e1 as g1, e2 as g2, ...en as gn`  
  
 GROUP BY yan tümcesinde ifade önceki aynı GROUP BY yan tümcesinde tanımlanan adlarına başvuruda bulunamaz.  
  
 Gruplandırma adları yanı sıra, SELECT yan tümcesi, HAVING yan tümcesi ve ORDER BY yan tümcesi toplamalar de belirtebilirsiniz. Bir toplama grubunun her öğe için değerlendirilen bir ifade içeriyor. Toplama işleci tüm ifadelerin değerlerini azaltır (genellikle, ancak her zaman, tek bir değer içine). Toplama ifadesi, özgün öğe adları görünür üst kapsamda veya GROUP BY yan tümcesi tarafından kendisine sunulan yeni adlarının herhangi biri için başvurular yapabilirsiniz. Toplamalar SELECT yan tümcesi, HAVING yan tümcesi ve ORDER BY yan tümcesi görünse de, bunlar aslında gruplandırma ifadeler aynı kapsamı altında aşağıdaki örnekte gösterildiği gibi değerlendirilir.  
  
 `SELECT name, sum(o.Price * o.Quantity) as total`  
  
 `FROM orderLines as o`  
  
 `GROUP BY o.Product as name`  
  
 Bu sorgu, sipariş, tüm ürünleri maliyetini bir raporu oluşturmak için GROUP BY yan tümcesi kullanır. ürün göre ayrılmış. Ad verir `name` ürüne gruplandırma ifadesi ve ardından bu seçim listesinde ad başvuruları bir parçası olarak. Ayrıca bir toplama işlevinde belirtir `sum` seçim listesindeki fiyat ve miktar sipariş satırının dahili olarak başvuruyor.  
  
 Her GROUP By anahtar ifadesi giriş kapsamına en az bir başvurusu olmalıdır:  
  
```  
SELECT FROM Persons as P  
GROUP BY Q + P   -- GOOD  
GROUP BY Q   -- BAD  
GROUP BY 1   -- BAD, a constant is not allowed  
```  
  
 GROUP BY kullanma örneği için bkz: [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusunu GROUP BY işleci nesneleri bir sorgu tarafından döndürülen grupları belirlemek için kullanır. Sorgu AdventureWorks satış modelini temel alır. Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yordamı izleyin [nasıl yapılır: Sorgu döndürür PrimitiveType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecutePrimitiveTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#GROUPBY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#groupby)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varlık SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Sorgu ifadeleri](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
