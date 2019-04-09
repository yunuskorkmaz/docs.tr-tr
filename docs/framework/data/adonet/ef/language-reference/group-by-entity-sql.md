---
title: Grup (varlık tarafından SQL)
ms.date: 03/30/2017
ms.assetid: cf4f4972-4724-4945-ba44-943a08549139
ms.openlocfilehash: 581a18b75d6028089e96b97dc5adeb2d3986c088
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081924"
---
# <a name="group-by-entity-sql"></a>Grup (varlık tarafından SQL)
Bir sorgu tarafından döndürülen hangi nesnelere grupları belirtir ([seçin](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) ifade olan yerleştirilecek.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[ GROUP BY aliasedExpression [ ,...n ] ]  
```  
  
## <a name="arguments"></a>Arguments  
 `aliasedExpression`  
 Herhangi bir geçerli sorgu ifade üzerinde gruplandırma gerçekleştirilir. `expression` bir özellik veya FROM yan tümcesi tarafından döndürülen bir özelliğe başvuruda toplama olmayan bir ifade olabilir. GROUP BY yan tümcesindeki her ifade eşitlik için karşılaştırılması gereken bir tür değerlendirilmelidir. Bu genelde skalar temelleri sayılar, dizeler ve tarihler gibi türleridir. Bir koleksiyonda grubuna katılamaz.  
  
## <a name="remarks"></a>Açıklamalar  
 SELECT yan tümcesinde toplama işlevleri eklediyseniz \<seçim listesi >, GROUP BY her grup için bir toplam değerini hesaplar. GROUP BY belirtildiğinde, her bir özellik adı seçim listesinde zorunluluğu herhangi bir ifade, GROUP BY listesinde eklenmesi veya GROUP BY ifadesi seçim listesine ifade tam olarak eşleşmelidir.  
  
> [!NOTE]
>  ORDER BY yan tümcesi belirtilmezse, GROUP BY yan tümcesi tarafından döndürülen grupları herhangi belirli bir sırada değildir. Belirli bir sıralama verilerini belirtmek için her zaman ORDER BY yan tümcesi kullanmanızı öneririz.  
  
 Örtük olarak (örneğin, sorgudaki HAVING yan tümcesi tarafından) veya GROUP BY yan tümcesi, ya da açıkça belirtildiğinde geçerli kapsamdaki gizlidir ve yeni bir kapsam sunulmuştur.  
  
 SELECT yan tümcesi ve HAVING yan tümcesi ORDER BY yan tümcesi artık FROM yan tümcesinde belirtilen öğe adları başvurmak mümkün olacaktır. Yalnızca gruplandırma ifadeleri kendilerini başvurabilir. Bunu yapmak için her bir gruplandırma ifadesi için yeni adlardır (takma adlardır) atayabilirsiniz. Bir gruplandırma ifadesi için diğer ad yok belirtilirse [!INCLUDE[esql](../../../../../../includes/esql-md.md)] aşağıdaki örnekte gösterildiği gibi diğer ad oluşturma kurallarını kullanarak bir tane oluşturmak çalışır.  
  
 `SELECT g1, g2, ...gn FROM c as c1`  
  
 `GROUP BY e1 as g1, e2 as g2, ...en as gn`  
  
 GROUP BY yan tümcesindeki ifadelerin, daha önce aynı GROUP BY yan tümcesinde tanımlı adlarına başvuruda bulunamaz.  
  
 Gruplandırma adlarının yanı sıra, SELECT yan tümcesi, HAVING yan tümcesi ve ORDER BY yan tümcesi toplamalar de belirtebilirsiniz. Bir toplama grubunun her öğe için değerlendirilen bir ifade içeriyor. Toplama işleci tüm ifadelerin değerleri azaltır (genellikle, ancak her zaman, tek bir değer halinde). Toplama ifadesi, özgün öğe adları görünür ana kapsamında veya herhangi bir GROUP BY yan tümcesi tarafından kendisine sunulan yeni adları başvuruları yapabilirsiniz. Toplamlar SELECT yan tümcesi, HAVING yan tümcesi ve ORDER BY yan tümcesi görünse de, bunlar gerçekten gruplandırma ifadeler aynı kapsamı altında aşağıdaki örnekte gösterildiği gibi değerlendirilir.  
  
 `SELECT name, sum(o.Price * o.Quantity) as total`  
  
 `FROM orderLines as o`  
  
 `GROUP BY o.Product as name`  
  
 Bu sorguyu GROUP BY yan tümcesi bir sipariş edilen tüm ürünlerin Maliyet raporu oluşturmak için kullanır. ürün göre ayrılmış. Ad verir `name` ürüne gruplandırma ifadesi ve ardından adı seçim listesinde başvurular bir parçası olarak. Ayrıca toplamı belirtir `sum` seçim listesindeki fiyat ve miktar siparişi satırı dahili olarak başvurur.  
  
 Her GROUP By anahtar ifadesi giriş kapsamına en az bir başvuru olmalıdır:  
  
```  
SELECT FROM Persons as P  
GROUP BY Q + P   -- GOOD  
GROUP BY Q   -- BAD  
GROUP BY 1   -- BAD, a constant is not allowed  
```  
  
 GROUP BY kullanma örneği için bkz: [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusu GROUP BY işleci nesneleri bir sorgu tarafından döndürülen grupları belirlemek için kullanır. Sorgu, AdventureWorks satış modelini temel alıyor. Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:  
  
1.  Verilen yordamı izleyin [nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecutePrimitiveTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#GROUPBY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#groupby)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Sorgu İfadeleri](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
