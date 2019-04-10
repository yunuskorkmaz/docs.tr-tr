---
title: Adlandırılmış Tür oluşturucu (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 549dea04-d93d-4c87-a292-f81b1598dbfd
ms.openlocfilehash: f95f0dcb92068675b2efff0af7e97b349976bf42
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59329472"
---
# <a name="named-type-constructor-entity-sql"></a>Adlandırılmış Tür oluşturucu (varlık SQL)
Varlık gibi kavramsal model nominal türü veya karmaşık türler örneklerini oluşturmak için kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[{identifier. }] identifier( [expression [{, expression }]] )  
```  
  
## <a name="arguments"></a>Arguments  
 `identifier`  
 Basit veya tırnak işaretli tanımlayıcı değeri. Daha fazla bilgi edinmek, [tanımlayıcıları](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
  
 `expression`  
 Tür bildiriminde göründükleri gibi aynı sırada olduğu varsayılır öznitelikleri türü.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Adlandırılmış karmaşık türler ve varlık türleri örnekleri.  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki örnekler, nominal ve karmaşık türler gösterilmektedir:  
  
 Aşağıdaki ifade bir örneğini oluşturur. bir `Person` türü:  
  
 `Person("abc", 12)`  
  
 Aşağıdaki ifade, karmaşık bir türün örneğini oluşturur:  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 Aşağıdaki ifade, iç içe geçmiş bir karmaşık tür örneği oluşturur:  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 Aşağıdaki ifade ile iç içe geçmiş bir karmaşık türü bir varlık örneği oluşturur:  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 Aşağıdaki örnek, bir karmaşık türü null bir özelliğini başlatmak gösterilmektedir:`MyModel.ZipCode(‘98118’, null)`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusu adlandırılmış Tür oluşturucu kavramsal model türünün örneğini oluşturmak için kullanır. Sorgu, AdventureWorks satış modelini temel alıyor. Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:  
  
1. Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#NAMED_TYPE_CONSTRUCTOR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#named_type_constructor)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Oluşturma Türleri](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)
- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
