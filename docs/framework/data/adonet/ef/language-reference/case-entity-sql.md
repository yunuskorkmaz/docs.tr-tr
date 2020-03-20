---
title: CASE (Varlık SQL)
ms.date: 03/30/2017
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
ms.openlocfilehash: 58b21d3be8e13a0a2204a4fd6d355f734207c509
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150473"
---
# <a name="case-entity-sql"></a>CASE (Varlık SQL)
Sonucu belirlemek için `Boolean` bir dizi ifadeyi değerlendirir.  
  
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
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `n`  
 Birden çok WHEN `Boolean_expression` THEN `result_expression` yan tümcelerinin kullanılabileceğini gösteren bir yer tutucudur.  
  
 Sonra`result_expression`  
 Değerlendirildiğinde `Boolean_expression` ifade döndürülür `true`mü? `result expression`geçerli bir ifadedir.  
  
 Başka`else_result_expression`  
 Hiçbir karşılaştırma işlemi değerlendirilmezse ifade `true`döndürülür mü. Bu bağımsız değişken atlanırsa ve hiçbir karşılaştırma `true`işlemi değerlendirirse , CASE null döndürür. `else_result_expression`geçerli bir ifadedir. Veri türleri `else_result_expression` ve `result_expression` herhangi bir örtük bir dönüştürme aynı veya olmalıdır.  
  
 Tesis`Boolean_expression`  
 `Boolean` Aranan CASE biçimi kullanıldığında ifade değerlendirilir. `Boolean_expression`geçerli `Boolean` bir ifadedir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Ve isteğe bağlı `result_expression` `else_result_expression`tür kümesinden en yüksek öncelik türünü verir.  
  
## <a name="remarks"></a>Açıklamalar  
 Büyük/küçük [!INCLUDE[esql](../../../../../../includes/esql-md.md)] harf ifadesi Transact-SQL büyük/küçük harf ifadesini benzer. Hangi ifadenin uygun sonucu vereceğini belirlemek için bir dizi koşullu test yapmak için servis talebi ifadesini kullanırsınız. Bu servis talebi ifadesi biçimi, doğru sonucu `Boolean` ortaya çıkan ifadeyi belirlemek için bir veya daha fazla ifade dizisi için geçerlidir.  
  
 CASE işlevi belirtilen `Boolean_expression` sırada her WHEN yan tümcesi `Boolean_expression` için değerlendirir `true`ve `result_expression` ilk in 'e göre değerlendirir. Kalan ifadeler değerlendirilmez. Hiçbir `Boolean_expression` değerlendirme yoksa `true`, Veritabanı Altyapısı `else_result_expression` eğer bir ELSE yan tümcesi belirtilirse döndürür veya ELSE yan tümcesi belirtilmemişse null değeri.  
  
 CASE deyimi çok set döndüremez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu, sonucu belirlemek için `Boolean` bir dizi ifadeyi değerlendirmek için CASE ifadesini kullanır. Sorgu AdventureWorks Satış Modeli dayanmaktadır. Bu sorguyı derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [İlkel Tip Sonuçlarını Döndüren Bir Sorguyu Yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md): Nasıl Yapılır'daki yordamı izleyin.  
  
2. Aşağıdaki sorguyu bağımsız değişken `ExecutePrimitiveTypeQuery` olarak yönteme geçirin:  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sonra](then-entity-sql.md)
- [Seçin](select-entity-sql.md)
- [Entity SQL Başvurusu](entity-sql-reference.md)
