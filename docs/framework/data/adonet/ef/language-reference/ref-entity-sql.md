---
title: "REF (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 1836b91876ac3c993f07902a644c130dda76f158
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ref-entity-sql"></a>REF (varlık SQL)
Bir varlık örneği için bir başvuru döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
REF( expression )   
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Bir varlık türünün bir örneği üretir herhangi geçerli ifade.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Belirtilen varlık örneğine başvuru.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir varlık başvurusu Varlık anahtarı içerir ve bir varlık kümesinin adı. Farklı varlık kümeleri aynı varlık türüne dayalı olabilir çünkü belirli Varlık anahtarı birden çok varlık kümesinde yer alabilir. Ancak, bir varlık başvurusunun her zaman benzersizdir. Giriş ifadesi kalıcı bir varlığı temsil ediyorsa, bu varlığa bir başvuru döndürülür. Giriş ifadesi kalıcı bir varlık değilse, bir null başvuru döndürülür.  
  
 Özellik ayıklama işleci (.), bir varlığın bir özelliğe erişmek için kullanılırsa, otomatik olarak dereferenced başvurudur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusunu REF işleci giriş varlık bağımsız değişken için başvuru döndürmek için kullanır. Ürün varlık bir özelliğe erişmek için bir özellik ayıklama işlemi (.) kullanıyoruz çünkü aynı sorgu başvuru dereferences. Sorgu AdventureWorks satış modelini temel alır. Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yordamı izleyin [nasıl yapılır: Sorgu döndürür PrimitiveType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecutePrimitiveTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#REF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)  
 [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
 [KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Tür Tanımları](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)
