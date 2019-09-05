---
title: Büyük/küçük harf (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
ms.openlocfilehash: 79544f4180313a008669c56c4f2740c889043c6d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251248"
---
# <a name="case-entity-sql"></a>Büyük/küçük harf (Entity SQL)
Sonucu belirleyecek bir `Boolean` ifade kümesi değerlendirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
CASE  
     WHEN Boolean_expression THEN result_expression   
    [ ...n ]   
     [   
    ELSE else_result_expression   
     ]   
END  
```  
  
## <a name="arguments"></a>Arguments  
 `n`  
 , Yan `Boolean_expression` tümcelerinin `result_expression` kullanılabileceğini gösteren bir yer tutucudur.  
  
 NI`result_expression`  
 , Olarak `Boolean_expression` `true`değerlendirildiğinde döndürülen ifadedir. `result expression`geçerli bir ifadedir.  
  
 DEĞILSE`else_result_expression`  
 , Hiçbir karşılaştırma işleminin değerlendirilmediğinde `true`döndürülen ifadedir. Bu bağımsız değişken atlanırsa ve bir karşılaştırma işlemi olarak `true`değerlendiriliyorsa, Case null değerini döndürür. `else_result_expression`geçerli bir ifadedir. Ve ' `else_result_expression`ninveritürleri aynıolmalıdırveyaörtükbirdönüştürmeolmalıdır.`result_expression`  
  
 OLUŞTURULURKEN`Boolean_expression`  
 , Aranan Case biçimi kullanıldığında değerlendirilen ifadedir.`Boolean` `Boolean_expression`geçerli `Boolean` bir ifadedir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 İçindeki tür kümesinden en yüksek öncelik türünü, `result_expression` ve isteğe bağlı `else_result_expression`olarak döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Case ifadesi Transact-SQL Case ifadesine benzer. Hangi ifadenin uygun sonucu olacağını belirleyen bir dizi koşullu test oluşturmak için Case ifadesini kullanın. Case ifadesinin bu biçimi, doğru sonuç ifadesini belirlemekte bir veya daha fazla `Boolean` ifadeye yönelik bir dizi için geçerlidir.  
  
 Case işlevi, belirtilen `Boolean_expression` sırada her bir yan tümce için değerlendirilir ve öğesini değerlendiren `true`ilk `result_expression` `Boolean_expression` döndürür. Kalan ifadeler değerlendirilmez. Hiçbir `Boolean_expression` `else_result_expression` değerlendirme yoksa, veritabanı altyapısı Eğer bir else yan tümcesi belirtilmişse veya else yan tümcesi belirtilmemişse null değeri döndürür. `true`  
  
 CASE deyimleri bir çoklu küme döndüremez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu, sonucu tespit etmek için bir dizi `Boolean` ifadeyi değerlendirmek üzere Case ifadesini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Aşağıdaki adımları uygulayın: PrimitiveType sonuçları](../how-to-execute-a-query-that-returns-primitivetype-results.md)döndüren bir sorgu yürütün.  
  
2. Aşağıdaki sorguyu `ExecutePrimitiveTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [THEN](then-entity-sql.md)
- [SELECT](select-entity-sql.md)
- [Entity SQL Başvurusu](entity-sql-reference.md)
