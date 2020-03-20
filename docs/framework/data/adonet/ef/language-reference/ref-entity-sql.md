---
title: REF (Varlık SQL)
ms.date: 03/30/2017
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
ms.openlocfilehash: 40a5afd7eb99dba7cae8fe14ed0a45213fda94a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149953"
---
# <a name="ref-entity-sql"></a>REF (Varlık SQL)
Bir varlık örneğine başvuru verir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```sql  
REF( expression )
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `expression`  
 Varlık türü örneği veren geçerli bir ifade.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Belirtilen varlık örneğine bir başvuru.  
  
## <a name="remarks"></a>Açıklamalar  
 Varlık başvurusu varlık anahtarı ve varlık kümesi adından oluşur. Farklı varlık kümeleri aynı varlık türüne dayalı olabileceğinden, belirli bir varlık anahtarı birden çok varlık kümesinde görünebilir. Ancak, bir varlık başvurusu her zaman benzersizdir. Giriş ifadesi kalıcı bir varlığı temsil ediyorsa, bu varlığa yapılan bir başvuru döndürülür. Giriş ifadesi kalıcı bir varlık değilse, null başvurusu döndürülür.  
  
 Özellik çıkarma işleci (.) bir varlığın özelliğine erişmek için kullanılırsa, başvuru otomatik olarak başvurudan çıkarılatır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu, bir giriş varlık bağımsız değişkeni için başvuruyu döndürmek için REF işleci kullanır. Ürün varlığının bir özelliğine erişmek için bir özellik çıkarma işlemi (.) kullandığımız için aynı sorgu başvuruyu dereferences. Sorgu AdventureWorks Satış Modeli dayanmaktadır. Bu sorguyı derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [İlkel Tip Sonuçlarını Döndüren Bir Sorguyu Yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md): Nasıl Yapılır'daki yordamı izleyin.  
  
2. Aşağıdaki sorguyu bağımsız değişken `ExecutePrimitiveTypeQuery` olarak yönteme geçirin:  
  
 [!code-sql[DP EntityServices Concepts#REF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#ref)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DEREF](deref-entity-sql.md)
- [CREATEREF](createref-entity-sql.md)
- [Anahtar](key-entity-sql.md)
- [Entity SQL Başvurusu](entity-sql-reference.md)
- [Tür Tanımları](type-definitions-entity-sql.md)
