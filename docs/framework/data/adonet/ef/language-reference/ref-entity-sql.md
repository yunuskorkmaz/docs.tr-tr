---
title: REF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
ms.openlocfilehash: 08bcaad4fdc0cf5324ff9976fcf48c23b206e72f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319389"
---
# <a name="ref-entity-sql"></a>REF (Entity SQL)
Bir varlık örneğine bir başvuru döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```sql  
REF( expression )   
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Bir varlık türünün örneğini veren geçerli bir ifade.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Belirtilen varlık örneğine bir başvuru.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir varlık başvurusu, Varlık anahtarından ve bir varlık kümesi adından oluşur. Farklı varlık kümeleri aynı varlık türünü temel alan için, belirli bir varlık anahtarı birden fazla varlık kümesinde görünebilir. Ancak, bir varlık başvurusu her zaman benzersizdir. Giriş ifadesi kalıcı bir varlığı temsil ediyorsa, bu varlığa yönelik bir başvuru döndürülür. Giriş ifadesi kalıcı olmayan bir varlık değilse, null bir başvuru döndürülür.  
  
 Özellik ayıklama işleci (.) bir varlığın bir özelliğine erişmek için kullanılırsa, başvuru otomatik olarak başvuru yapılır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu, bir giriş varlığı bağımsız değişkeninin başvurusunu döndürmek için REF işlecini kullanır. Ürün varlığının bir özelliğine erişmek için bir özellik ayıklama işlemi (.) kullandığından aynı sorgu başvurunun başvurusunu kaldırır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu `ExecutePrimitiveTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-sql[DP EntityServices Concepts#REF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#ref)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DEREF](deref-entity-sql.md)
- [CREATEREF](createref-entity-sql.md)
- [KEY](key-entity-sql.md)
- [Entity SQL Başvurusu](entity-sql-reference.md)
- [Tür Tanımları](type-definitions-entity-sql.md)
