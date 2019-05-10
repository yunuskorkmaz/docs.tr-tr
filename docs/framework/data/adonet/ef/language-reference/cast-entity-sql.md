---
title: ATAMA (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 07b6d750-dfd4-48a9-b86c-3badcbba6f70
ms.openlocfilehash: 36bf627c7dfabdcf4bbc279bec8f3933f7aafb2a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64631646"
---
# <a name="cast-entity-sql"></a>ATAMA (varlık SQL)
Bir veri türündeki bir ifade diğerine dönüştürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
CAST ( expression AS data_type )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Dönüştürülebilen herhangi bir geçerli ifade `data_type`.  
  
 `data_type`  
 Hedef sistem tarafından sağlanan veri türü. Basit (skaler) türü olmalıdır. `data_type` Kullanılan Sorgu alanı bağlıdır. Bir sorgu ile yürütülürse <xref:System.Data.EntityClient.EntityCommand>, kavramsal modelde tanımlı bir tür veri türüdür. Daha fazla bilgi için [CSDL belirtimi](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md). Bir sorgu ile yürütülürse <xref:System.Data.Objects.ObjectQuery%601>, ortak dil çalışma zamanı (CLR) tür veri türüdür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aynı değeri döndürür `data_type`.  
  
## <a name="remarks"></a>Açıklamalar  
 Cast ifadesi için benzer semantiğe sahip [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] dönüştürme ifadesi. Cast ifadesi, başka bir türü bir değere bir türün bir değerini dönüştürmek için kullanılır.  
  
```  
CAST( e as T )  
```  
  
 E ise bazı S ve S T için dönüştürülebilir türüdür ve ardından yukarıdaki ifadeyi geçerli atama ifadesidir. T (skaler) basit tür olmalıdır.  
  
 Kesinlik ve ölçek özellikleri, isteğe bağlı olarak tür atama olduğunda sağlanabilir değerleri `Edm.Decimal`. Açıkça sağlanan, kesinlik ve ölçek için varsayılan değerleri 18 ve 0, sırasıyla. Özellikle, aşağıdaki aşırı yüklemeler için desteklenen `Decimal`:  
  
- `CAST( d as Edm.Decimal );`  
  
- `CAST( d as Edm.Decimal(precision) );`  
  
- `CAST( d as Edm.Decimal(precision, scale) );`  
  
 Cast ifadesi kullanımı açık bir dönüştürme olarak kabul edilir. Açık dönüştürmeler truncate veri veya duyarlık kaybı.  
  
> [!NOTE]
>  ATAMA, yalnızca ilkel türler ve sabit listesi üye türleri üzerinde desteklenir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu için başka bir veri türündeki bir ifadeye dönüştürmek için tür dönüştürme işleci kullanır. Sorgu, AdventureWorks satış modelini temel alıyor. Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:  
  
1. Verilen yordamı izleyin [nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecutePrimitiveTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#CAST](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#cast)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
