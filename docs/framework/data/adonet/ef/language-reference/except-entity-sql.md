---
title: EXCEPT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 69cc23e5-3f8f-4b49-b20e-2f84ff11c80d
ms.openlocfilehash: 6797f8038a83533b5a6bd41ad402daec7abdc7de
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148066"
---
# <a name="except-entity-sql"></a>EXCEPT (Entity SQL)

Sorgu ifadesinden, EXCEPT işleneninin sağına doğru döndürülmüyor harıç, EXCEPT işlecinin soluna ait herhangi bir farklı değerin bir koleksiyonunu döndürür. Tüm ifadeler aynı türde veya ortak bir temel veya türetilmiş türde olmalıdır `expression` .  
  
## <a name="syntax"></a>Söz dizimi  
  
```sql  
expression EXCEPT expression  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `expression`  
 Başka bir sorgu ifadesinden döndürülen koleksiyonla karşılaştırmak için bir koleksiyon döndüren geçerli bir sorgu ifadesi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Aynı türde veya ortak bir temel ya da türetilmiş türden bir koleksiyon `expression` .  
  
## <a name="remarks"></a>Açıklamalar  

 EXCEPT, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set işleçlerinden biridir. Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] küme işleçleri soldan sağa değerlendirilir. Aşağıdaki tabloda, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set işleçlerinin önceliği gösterilmektedir.  
  
|Önceliği|İşleçler|  
|----------------|---------------|  
|En yüksek|INTERSECT|  
||UNION<br /><br /> TÜMÜNÜ TOPLA|  
||EXCEPT|  
|Minimum|EXISTS<br /><br /> OVERLAPS<br /><br /> FLATTEN<br /><br /> SET|  
  
## <a name="example"></a>Örnek  

 Aşağıdaki Entity SQL sorgusu, iki sorgu ifadesinin farklı değerlerinin bir koleksiyonunu döndürmek için EXCEPT işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :  
  
 [!code-sql[DP EntityServices Concepts#EXCEPT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#except)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
