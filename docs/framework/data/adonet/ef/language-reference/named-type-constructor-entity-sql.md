---
title: Adlandırılmış tür Oluşturucusu (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 549dea04-d93d-4c87-a292-f81b1598dbfd
ms.openlocfilehash: c673b58ee5811e3d3b74b3744d3f5291888e2253
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197787"
---
# <a name="named-type-constructor-entity-sql"></a>Adlandırılmış tür Oluşturucusu (Entity SQL)

Varlık veya karmaşık türler gibi kavramsal model nominal türlerin örneklerini oluşturmak için kullanılır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```sql  
[{identifier. }] identifier( [expression [{, expression }]] )  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `identifier`  
 Basit veya tırnaklı bir tanımlayıcı değeri. Daha fazla bilgi için bkz. [tanımlayıcılar](identifiers-entity-sql.md)  
  
 `expression`  
 Türün bildiriminde göründükleri sırada olduğu varsayılacak olan türün öznitelikleri.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Adlandırılmış karmaşık türlerin örnekleri ve varlık türleri.  
  
## <a name="remarks"></a>Açıklamalar  

 Aşağıdaki örneklerde nominal ve karmaşık türlerin nasıl oluşturulacağı gösterilmektedir:  
  
 Aşağıdaki ifade bir türün örneğini oluşturur `Person` :  
  
 `Person("abc", 12)`  
  
 Aşağıdaki ifade, karmaşık bir türün bir örneğini oluşturur:  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 Aşağıdaki ifade, iç içe geçmiş karmaşık türün bir örneğini oluşturur:  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 Aşağıdaki ifade, iç içe geçmiş karmaşık türe sahip bir varlığın örneğini oluşturur:  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 Aşağıdaki örnek, bir karmaşık türün özelliğinin null olarak nasıl başlatılacağını göstermektedir:`MyModel.ZipCode(‘98118’, null)`  
  
## <a name="example"></a>Örnek  

 Aşağıdaki Entity SQL sorgusu, kavramsal model türünün bir örneğini oluşturmak için adlandırılmış tür oluşturucusunu kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :  
  
 [!code-sql[DP EntityServices Concepts#NAMED_TYPE_CONSTRUCTOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#named_type_constructor)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Oluşturma Türleri](constructing-types-entity-sql.md)
- [Entity SQL Başvurusu](entity-sql-reference.md)
