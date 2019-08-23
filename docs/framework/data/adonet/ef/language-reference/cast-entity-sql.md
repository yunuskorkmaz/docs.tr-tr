---
title: CAST (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 07b6d750-dfd4-48a9-b86c-3badcbba6f70
ms.openlocfilehash: 253dcf092deadd1049d0556af4ea0630602110d0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935825"
---
# <a name="cast-entity-sql"></a>CAST (Entity SQL)
Bir veri türündeki bir ifadeyi diğerine dönüştürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
CAST ( expression AS data_type )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Dönüştürülebilir herhangi bir geçerli ifade `data_type`.  
  
 `data_type`  
 Hedef sistem tarafından sağlanan veri türü. Temel bir (skaler) türü olmalıdır. `data_type` Kullanılan sorgu alanına göre değişir. Bir sorgu ile <xref:System.Data.EntityClient.EntityCommand>yürütülürse, veri türü kavramsal modelde tanımlanan bir türdür. Daha fazla bilgi için bkz. [csdl belirtimi](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md). Bir sorgu ile <xref:System.Data.Objects.ObjectQuery%601>yürütülürse, veri türü ortak dil çalışma zamanı (CLR) türüdür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 İle `data_type`aynı değeri döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Cast ifadesinin Transact-SQL CONVERT ifadesine benzer anlamları vardır. Cast ifadesi bir tür değerini başka bir türün değerine dönüştürmek için kullanılır.  
  
```  
CAST( e as T )  
```  
  
 E bazı tür ve S, T 'ye dönüştürülesiyse, yukarıdaki ifade geçerli bir atama ifadesidir. T, ilkel (skaler) bir tür olmalıdır.  
  
 Duyarlık ve ölçek modelleri için değerler, öğesine `Edm.Decimal`atama sırasında isteğe bağlı olarak sağlanmayabilir. Açık olarak sağlanmazsa, duyarlık ve ölçek için varsayılan değerler sırasıyla 18 ve 0 ' dır. Özellikle, için `Decimal`aşağıdaki aşırı yüklemeler desteklenir:  
  
- `CAST( d as Edm.Decimal );`  
  
- `CAST( d as Edm.Decimal(precision) );`  
  
- `CAST( d as Edm.Decimal(precision, scale) );`  
  
 Atama ifadesinin kullanımı açık bir dönüştürme olarak değerlendirilir. Açık dönüşümler verileri kesebilir veya duyarlık kayıplarına sahip olabilirler.  
  
> [!NOTE]
> CAST yalnızca ilkel türler ve numaralandırma üye türleri üzerinde desteklenir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, bir veri türünün bir ifadesini diğerine dönüştürmek için cast işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Aşağıdaki adımları uygulayın: PrimitiveType sonuçları](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)döndüren bir sorgu yürütün.  
  
2. Aşağıdaki sorguyu `ExecutePrimitiveTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-csharp[DP EntityServices Concepts 2#CAST](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#cast)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
