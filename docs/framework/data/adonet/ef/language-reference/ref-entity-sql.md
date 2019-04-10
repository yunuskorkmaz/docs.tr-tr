---
title: REF (varlık SQL)
ms.date: 03/30/2017
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
ms.openlocfilehash: 05e687f951930d92797a863410181585278b067d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59330668"
---
# <a name="ref-entity-sql"></a>REF (varlık SQL)
Bir varlık örneği için bir başvuru döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
REF( expression )   
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Bir varlık türünün bir örneği döndüren herhangi bir geçerli ifade.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Belirtilen varlık örneğine başvuru.  
  
## <a name="remarks"></a>Açıklamalar  
 Varlık anahtarı bir varlık başvurusu oluşur ve bir varlık kümesinin adı. Farklı varlık kümeleri, aynı varlık türüne göre çünkü bir özel varlık anahtarı birden çok varlık kümelerinde görünebilir. Ancak, bir varlık başvurusu her zaman benzersizdir. Giriş ifadesi kalıcı bir varlığı temsil ediyorsa, bu varlık için bir başvuru döndürülür. Giriş ifadesi kalıcı bir varlık değil ise, bir null başvurusu döndürülür.  
  
 Özellik çıkarma işleci (.), bir varlığın bir özelliğe erişmek için kullanılır, otomatik olarak başvurusu kaldırılmış bir başvurudur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusu için giriş varlığı bağımsız değişken başvuru döndürmek için başvuru işleci kullanır. Bir ürün varlığı özelliğine erişmek için bir özelliği ayıklama işlemi (.) kullanıyoruz çünkü aynı sorgu başvuru başvurusunu kaldırır. Sorgu, AdventureWorks satış modelini temel alıyor. Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:  
  
1. Verilen yordamı izleyin [nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecutePrimitiveTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#REF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)
- [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)
- [KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)
- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Tür Tanımları](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)
