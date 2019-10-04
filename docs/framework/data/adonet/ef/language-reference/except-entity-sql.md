---
title: EXCEPT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 69cc23e5-3f8f-4b49-b20e-2f84ff11c80d
ms.openlocfilehash: c4df8c2b72ee60a425c98c64a13a1e2d43d4506e
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833856"
---
# <a name="except-entity-sql"></a>EXCEPT (Entity SQL)
Sorgu ifadesinden, EXCEPT işleneninin sağına doğru döndürülmüyor harıç, EXCEPT işlecinin soluna ait herhangi bir farklı değerin bir koleksiyonunu döndürür. Tüm ifadeler aynı türde veya ortak bir temel ya da türetilmiş türden `expression` olmalıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```sql  
expression EXCEPT expression  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `expression`  
 Başka bir sorgu ifadesinden döndürülen koleksiyonla karşılaştırmak için bir koleksiyon döndüren geçerli bir sorgu ifadesi.  
  
## <a name="return-value"></a>Dönüş değeri  
 Aynı türde veya ortak bir temel ya da türetilmiş türden bir koleksiyon `expression` olarak.  
  
## <a name="remarks"></a>Açıklamalar  
 EXCEPT [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kümesi işleçlerinden biridir. Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kümesi işleçleri soldan sağa değerlendirilir. Aşağıdaki tabloda [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kümesi işleçlerinin önceliği gösterilmektedir.  
  
|Ayarlarından|İşleçler|  
|----------------|---------------|  
|En Yüksek|KESIŞ|  
||UNION<br /><br /> TÜMÜNÜ TOPLA|  
||KULLANıLDıKLARı|  
|En Düşük|BULUNUR<br /><br /> ÇAKıŞ<br /><br /> LEŞTIREBILIR<br /><br /> KURMAK|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu, iki sorgu ifadesinin farklı değerlerinin bir koleksiyonunu döndürmek için EXCEPT işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-sql[DP EntityServices Concepts#EXCEPT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#except)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL başvurusu](entity-sql-reference.md)
