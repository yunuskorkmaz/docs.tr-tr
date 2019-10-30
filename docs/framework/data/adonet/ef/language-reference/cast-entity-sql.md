---
title: CAST (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 07b6d750-dfd4-48a9-b86c-3badcbba6f70
ms.openlocfilehash: c16270babe4daa8e703b24b27211c6fd6f53677d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039913"
---
# <a name="cast-entity-sql"></a>CAST (Entity SQL)
Bir veri türündeki bir ifadeyi diğerine dönüştürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
CAST ( expression AS data_type )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 `data_type`dönüştürülebilir geçerli bir ifade.  
  
 `data_type`  
 Hedef sistem tarafından sağlanan veri türü. Temel bir (skaler) türü olmalıdır. Kullanılan `data_type`, sorgu alanına göre değişir. <xref:System.Data.EntityClient.EntityCommand>bir sorgu yürütülürse, veri türü kavramsal modelde tanımlanan bir türdür. Daha fazla bilgi için bkz. [csdl belirtimi](csdl-specification.md). Bir sorgu <xref:System.Data.Objects.ObjectQuery%601>ile yürütülürse, veri türü ortak dil çalışma zamanı (CLR) türüdür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `data_type`ile aynı değeri döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Cast ifadesinin Transact-SQL CONVERT ifadesine benzer anlamları vardır. Cast ifadesi bir tür değerini başka bir türün değerine dönüştürmek için kullanılır.  
  
```csharp
CAST( e as T )  
```  
  
 E bazı tür ve S, T 'ye dönüştürülesiyse, yukarıdaki ifade geçerli bir atama ifadesidir. T, ilkel (skaler) bir tür olmalıdır.  
  
 Duyarlık ve ölçek modelleri için değerler, `Edm.Decimal`çevrim sırasında isteğe bağlı olarak sağlanmayabilir. Açık olarak sağlanmazsa, duyarlık ve ölçek için varsayılan değerler sırasıyla 18 ve 0 ' dır. Özellikle, `Decimal`için aşağıdaki aşırı yüklemeler desteklenir:  
  
- `CAST( d as Edm.Decimal );`  
  
- `CAST( d as Edm.Decimal(precision) );`  
  
- `CAST( d as Edm.Decimal(precision, scale) );`  
  
 Atama ifadesinin kullanımı açık bir dönüştürme olarak değerlendirilir. Açık dönüşümler verileri kesebilir veya duyarlık kayıplarına sahip olabilirler.  
  
> [!NOTE]
> CAST yalnızca ilkel türler ve numaralandırma üye türleri üzerinde desteklenir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgusu, bir veri türü ifadesini diğerine dönüştürmek için CAST işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu `ExecutePrimitiveTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-csharp[DP EntityServices Concepts 2#CAST](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#cast)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
