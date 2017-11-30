---
title: "Durum (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f4e92d9a7c66d176357499bc831f07c56f36c90d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="case-entity-sql"></a>Durum (varlık SQL)
Bir dizi değerlendirir `Boolean` sonucu belirlemek için ifadeler.  
  
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
 Bu çoklu gösteren bir yer tutucudur zaman `Boolean_expression` sonra `result_expression` yan tümceleri kullanılabilir.  
  
 ARDINDAN`result_expression`  
 İfade ne zaman döndürülür `Boolean_expression` değerlendiren `true`. `result expression`Geçerli bir ifade değil.  
  
 ELSE`else_result_expression`  
 İfade karşılaştırma işlemi için hesaplar, döndürülen `true`. Bu bağımsız değişkeni boş bırakılırsa ve karşılaştırma işlemi değerlendiren `true`, servis talebi null döndürür. `else_result_expression`Geçerli bir ifade değil. Veri türlerini `else_result_expression` ve tüm `result_expression` örtük bir dönüştürme olmalıdır veya aynı olmalıdır.  
  
 NE ZAMAN`Boolean_expression`  
 Olan `Boolean` Aranan servis talebi biçimi kullanıldığında değerlendirilen ifade. `Boolean_expression`Tüm geçerli `Boolean` ifade.  
  
## <a name="return-value"></a>Dönüş Değeri  
 En yüksek öncelik türüyle türlerinde kümesinden döndürür `result_expression` ve isteğe bağlı `else_result_expression`.  
  
## <a name="remarks"></a>Açıklamalar  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Servis talebi ifade benzer [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] durumda ifade. Case deyimi, bir dizi hangi ifade uygun sonucu verecek olan belirlemek için koşullu test yapmak için kullanın. Bir dizi bir veya daha fazla bilgi için bu formu servis talebi ifadesinin geçerlidir `Boolean` doğru elde edilen ifadesi belirlemek için deyimleri.  
  
 Durum işlevi değerlendirir `Boolean_expression` her zaman yan tümcesi sırada belirtilen ve döndürür `result_expression` ilk `Boolean_expression` , hesaplar için `true`. Kalan ifadeler değerlendirilmez. Yoksa `Boolean_expression` değerlendiren `true`, veritabanı altyapısı döndürür `else_result_expression` ELSE yan tümcesinin belirtilmişse veya hiçbir ELSE yan tümcesi belirtilmişse, bir null değer.  
  
 CASE deyimi bir çoklu küme döndüremez.  
  
## <a name="example"></a>Örnek  
 Bir dizi değerlendirmek için büyük/küçük HARFE ifade aşağıdaki varlık SQL sorgusunu kullanır `Boolean` sonucu belirlemek için ifadeler. Sorgu AdventureWorks satış modelini temel alır. Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yordamı izleyin [nasıl yapılır: Sorgu döndürür PrimitiveType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecutePrimitiveTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ARDINDAN](../../../../../../docs/framework/data/adonet/ef/language-reference/then-entity-sql.md)  
 [SEÇİN](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)  
 [Varlık SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
