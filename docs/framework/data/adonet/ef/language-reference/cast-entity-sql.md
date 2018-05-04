---
title: CAST (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 07b6d750-dfd4-48a9-b86c-3badcbba6f70
ms.openlocfilehash: b3ebd4a7fe9d9e1324210d9f4d1265115bd8617f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="cast-entity-sql"></a>CAST (varlık SQL)
Bir veri türünde bir ifadenin diğerine dönüştürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
CAST ( expression AS data_type )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Parametresinin geçerli bir ifade `data_type`.  
  
 `data_type`  
 Hedef sistem tarafından sağlanan veri türü. Basit (skaler) bir tür olmalıdır. `data_type` Kullanılan sorgu alan bağlıdır. Bir sorgu ile yürütülürse <xref:System.Data.EntityClient.EntityCommand>, kavramsal modelde tanımlanan bir türü veri türüdür. Daha fazla bilgi için bkz: [CSDL belirtimi](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md). Bir sorgu ile yürütülürse <xref:System.Data.Objects.ObjectQuery%601>, bir ortak dil çalışma zamanı (CLR) türü veri türüdür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aynı değeri döndürür `data_type`.  
  
## <a name="remarks"></a>Açıklamalar  
 Cast ifadesi benzer bir semantik vardır [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] Çevir ifade. Cast ifadesi, başka bir türdeki bir değere bir türde bir değer dönüştürmek için kullanılır.  
  
```  
CAST( e as T )  
```  
  
 E ise S ve S herhangi bir tür için T dönüştürülebilir olup, ardından geçerli cast ifadesi yukarıdaki ifadesidir. T ilkel (skaler) bir tür olmalıdır.  
  
 Kesinlik ve ölçek yönü, isteğe bağlı olarak tür atama zaman sağlanabilir değerleri `Edm.Decimal`. Açıkça verdiyse, varsayılan duyarlık ve ölçek 18 ve 0, sırasıyla değerler. Özellikle, aşağıdaki aşırı yüklemeleri için desteklenen `Decimal`:  
  
-   `CAST( d as Edm.Decimal );`  
  
-   `CAST( d as Edm.Decimal(precision) );`  
  
-   `CAST( d as Edm.Decimal(precision, scale) );`  
  
 Cast ifadesi kullanımını açık bir dönüştürme olarak kabul edilir. Açık dönüşümler veri kesme veya duyarlık kaybedersiniz.  
  
> [!NOTE]
>  CAST yalnızca ilkel türler ve Numaralandırma üye türleri üzerinde desteklenir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu ATAMA işleci için başka bir veri türünde bir ifadeyi dönüştürmek için kullanır. Sorgu AdventureWorks satış modelini temel alır. Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yordamı izleyin [nasıl yapılır: Sorgu döndürür PrimitiveType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecutePrimitiveTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#CAST](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#cast)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
