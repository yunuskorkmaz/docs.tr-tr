---
title: Büyük/küçük harf (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
ms.openlocfilehash: 7c1e02d44c674bf262f92df1c43bec6e9f2143c5
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039935"
---
# <a name="case-entity-sql"></a>Büyük/küçük harf (Entity SQL)
Sonucu belirleyecek bir `Boolean` ifadeleri kümesi değerlendirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp  
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
 `Boolean_expression`, `result_expression` yan tümcelerinin kullanılabileceğini gösteren bir yer tutucudur.  
  
 SONRA `result_expression`  
 , `Boolean_expression` `true`değerlendirildiğinde döndürülen ifadedir. `result expression` geçerli bir ifadedir.  
  
 ELSE `else_result_expression`  
 Bir karşılaştırma işlemi `true`olarak değerlendirilmediğinde ifade döndürülür. Bu bağımsız değişken atlanırsa ve hiçbir karşılaştırma işlemi `true`olarak değerlendirilirse, CASE null değerini döndürür. `else_result_expression` geçerli bir ifadedir. `else_result_expression` veri türleri ve herhangi bir `result_expression` aynı olmalıdır veya örtük bir dönüştürme olmalıdır.  
  
 `Boolean_expression` olduğunda  
 , Aranan CASE biçimi kullanıldığında `Boolean` ifade değerlendirilir. `Boolean_expression` geçerli `Boolean` ifadedir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `result_expression` ve isteğe bağlı `else_result_expression`tür kümesinden en yüksek öncelik türünü döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] case ifadesi Transact-SQL Case ifadesine benzer. Hangi ifadenin uygun sonucu olacağını belirleyen bir dizi koşullu test oluşturmak için Case ifadesini kullanın. Case ifadesinin bu biçimi, doğru sonuç ifadesini belirlemekte bir veya daha fazla `Boolean` ifadesi için geçerlidir.  
  
 CASE işlevi, belirtilen sırada her bir for yan tümcesi için `Boolean_expression` değerlendirir ve `true`değerlendirilen ilk `Boolean_expression` `result_expression` döndürür. Kalan ifadeler değerlendirilmez. Hiçbir `Boolean_expression` `true`değerlendiriyorsa, veritabanı altyapısı bir ELSE yan tümcesi belirtilmişse `else_result_expression` döndürür ya da ELSE yan tümcesi belirtilmemişse null bir değer olur.  
  
 CASE deyimleri bir çoklu küme döndüremez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu, sonucu tespit etmek için bir dizi `Boolean` ifadeyi değerlendirmek üzere CASE ifadesini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu `ExecutePrimitiveTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [THEN](then-entity-sql.md)
- [SELECT](select-entity-sql.md)
- [Entity SQL Başvurusu](entity-sql-reference.md)
