---
title: "Adlı Tür oluşturucu (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 549dea04-d93d-4c87-a292-f81b1598dbfd
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 72a19094beb03982448a102a4c7362a026d9e611
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="named-type-constructor-entity-sql"></a>Adlı Tür oluşturucu (varlık SQL)
Kavramsal model nominal türleri gibi varlık veya karmaşık türler örneklerini oluşturmak için kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[{identifier. }] identifier( [expression [{, expression }]] )  
```  
  
## <a name="arguments"></a>Arguments  
 `identifier`  
 Bir basit ya da alıntı tanımlayıcısı değeri. Daha fazla bilgi için [tanımlayıcıları](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
  
 `expression`  
 Türü bildiriminde göründükleri gibi aynı sırada olduğu varsayılır türü öznitelikleri.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Adlandırılmış karmaşık türleri ve varlık türleri örnekleri.  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki örnekler nasıl nominal ve karmaşık türleri oluşturulacağını gösterir:  
  
 İfade bir örneğini oluşturur bir `Person` türü:  
  
 `Person("abc", 12)`  
  
 İfade karmaşık türün bir örneğini oluşturur:  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 Aşağıdaki ifade, iç içe geçmiş bir karmaşık tür bir örneğini oluşturur:  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 İfade bir varlık örneği ile iç içe geçmiş bir karmaşık tür oluşturur:  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 Aşağıdaki örnekte, bir özelliği null karmaşık türün başlatmak gösterilmektedir:`MyModel.ZipCode(‘98118’, null)`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusunu adlandırılmış Tür oluşturucu kavramsal model türünün bir örneği oluşturmak için kullanır. Sorgu AdventureWorks satış modelini temel alır. Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#NAMED_TYPE_CONSTRUCTOR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#named_type_constructor)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Türleri oluşturma](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
 [Varlık SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
