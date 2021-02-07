---
description: 'Daha fazla bilgi edinin: CAST (Entity SQL)'
title: CAST (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 07b6d750-dfd4-48a9-b86c-3badcbba6f70
ms.openlocfilehash: f6a90c0ec2557391c2da6e46511a020f90d32ab7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739488"
---
# <a name="cast-entity-sql"></a>CAST (Entity SQL)

Bir veri türündeki bir ifadeyi bir diğerine dönüştürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
CAST ( expression AS data_type )  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `expression`  
 Dönüştürülebilir herhangi bir geçerli ifade `data_type` .  
  
 `data_type`  
 Hedef sistem tarafından sağlanan veri türü. Temel bir (skaler) türü olmalıdır. `data_type`Kullanılan sorgu alanına göre değişir. Bir sorgu ile yürütülürse <xref:System.Data.EntityClient.EntityCommand> , veri türü kavramsal modelde tanımlanan bir türdür. Daha fazla bilgi için bkz. [csdl belirtimi](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec). Bir sorgu ile yürütülürse <xref:System.Data.Objects.ObjectQuery%601> , veri türü ortak dil çalışma zamanı (CLR) türüdür.  
  
## <a name="return-value"></a>Dönüş Değeri  

 İle aynı değeri döndürür `data_type` .  
  
## <a name="remarks"></a>Açıklamalar  

 Cast ifadesinin Transact-SQL CONVERT ifadesine benzer anlamları vardır. Cast ifadesi bir tür değerini başka bir türün değerine dönüştürmek için kullanılır.  
  
```csharp
CAST( e as T )  
```  
  
 E bazı tür ve S, T 'ye dönüştürülesiyse, yukarıdaki ifade geçerli bir atama ifadesidir. T, ilkel (skaler) bir tür olmalıdır.  
  
 Duyarlık ve ölçek modelleri için değerler, öğesine atama sırasında isteğe bağlı olarak sağlanmayabilir `Edm.Decimal` . Açık olarak sağlanmazsa, duyarlık ve ölçek için varsayılan değerler sırasıyla 18 ve 0 ' dır. Özellikle, için aşağıdaki aşırı yüklemeler desteklenir `Decimal` :  
  
- `CAST( d as Edm.Decimal );`  
  
- `CAST( d as Edm.Decimal(precision) );`  
  
- `CAST( d as Edm.Decimal(precision, scale) );`  
  
 Atama ifadesinin kullanımı açık bir dönüştürme olarak değerlendirilir. Açık dönüşümler verileri kesebilir veya duyarlık kayıplarına sahip olabilirler.  
  
> [!NOTE]
> CAST yalnızca ilkel türler ve numaralandırma üye türleri üzerinde desteklenir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, bir veri türünün bir ifadesini diğerine dönüştürmek IÇIN cast işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecutePrimitiveTypeQuery` :  
  
 [!code-csharp[DP EntityServices Concepts 2#CAST](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#cast)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
