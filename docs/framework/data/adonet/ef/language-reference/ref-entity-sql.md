---
title: REF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
ms.openlocfilehash: 56ae576ac60d1716d86fbbb797882bf96e99813f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202246"
---
# <a name="ref-entity-sql"></a>REF (Entity SQL)

Bir varlık örneğine bir başvuru döndürür.  
  
## <a name="syntax"></a>Söz dizimi  
  
```sql  
REF( expression )
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

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
  
2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecutePrimitiveTypeQuery` :  
  
 [!code-sql[DP EntityServices Concepts#REF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#ref)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DEREF](deref-entity-sql.md)
- [CREATEREF](createref-entity-sql.md)
- [ANAHTAR](key-entity-sql.md)
- [Entity SQL Başvurusu](entity-sql-reference.md)
- [Tür Tanımları](type-definitions-entity-sql.md)
