---
title: Büyük/küçük harf (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
ms.openlocfilehash: 65efedd36401db402a32748afaebff0f2af9f2a7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185229"
---
# <a name="case-entity-sql"></a>Büyük/küçük harf (Entity SQL)

`Boolean`Sonucu belirleyecek bir ifade kümesi değerlendirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```csharp  
CASE  
     WHEN Boolean_expression THEN result_expression
    [ ...n ]
     [
    ELSE else_result_expression
     ]
END  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `n`  
 , `Boolean_expression` Yan tümcelerinin kullanılabileceğini gösteren bir yer tutucudur `result_expression` .  
  
 NI `result_expression`  
 , Olarak değerlendirildiğinde döndürülen ifadedir `Boolean_expression` `true` . `result expression` geçerli bir ifadedir.  
  
 DEĞILSE `else_result_expression`  
 , Hiçbir karşılaştırma işleminin değerlendirilmediğinde döndürülen ifadedir `true` . Bu bağımsız değişken atlanırsa ve bir karşılaştırma işlemi olarak değerlendiriliyorsa `true` , Case null değerini döndürür. `else_result_expression` geçerli bir ifadedir. Ve ' nin veri türleri `else_result_expression` `result_expression` aynı olmalıdır veya örtük bir dönüştürme olmalıdır.  
  
 OLUŞTURULURKEN `Boolean_expression`  
 , `Boolean` Aranan Case biçimi kullanıldığında değerlendirilen ifadedir. `Boolean_expression` geçerli bir `Boolean` ifadedir.  
  
## <a name="return-value"></a>Dönüş Değeri  

 İçindeki tür kümesinden en yüksek öncelik türünü, `result_expression` ve isteğe bağlı olarak döndürür `else_result_expression` .  
  
## <a name="remarks"></a>Açıklamalar  

 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Case Ifadesi Transact-SQL Case ifadesine benzer. Hangi ifadenin uygun sonucu olacağını belirleyen bir dizi koşullu test oluşturmak için Case ifadesini kullanın. Case ifadesinin bu biçimi, `Boolean` doğru sonuç ifadesini belirlemekte bir veya daha fazla ifadeye yönelik bir dizi için geçerlidir.  
  
 CASE işlevi, `Boolean_expression` belirtilen sırada her bir yan tümce için değerlendirilir ve öğesini `result_expression` değerlendiren ilk döndürür `Boolean_expression` `true` . Kalan ifadeler değerlendirilmez. Hiçbir `Boolean_expression` değerlendirme yoksa `true` , veritabanı altyapısı `else_result_expression` Eğer bir else yan TÜMCESI belirtilmişse veya else yan tümcesi belirtilmemişse null değeri döndürür.  
  
 CASE deyimleri bir çoklu küme döndüremez.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki Entity SQL sorgusu, `Boolean` sonucu tespit etmek için bir dizi ifadeyi değerlendirmek üzere Case ifadesini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecutePrimitiveTypeQuery` :  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [NI](then-entity-sql.md)
- [SELECT](select-entity-sql.md)
- [Entity SQL Başvurusu](entity-sql-reference.md)
