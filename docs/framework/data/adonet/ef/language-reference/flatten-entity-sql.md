---
title: DÜZLEŞTIR (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
ms.openlocfilehash: 84b846e3db86c664bc42363f3d983a1001f5c318
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833815"
---
# <a name="flatten-entity-sql"></a>DÜZLEŞTIR (Entity SQL)
Bir koleksiyon koleksiyonunu düzleştirilmiş bir koleksiyona dönüştürür. Yeni koleksiyon eski koleksiyonla aynı öğeleri, ancak iç içe bir yapı olmadan içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```sql  
FLATTEN ( collection )  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `collection`  
 Tek bir koleksiyonda düzleştirmek için bir değer koleksiyonları koleksiyonu döndüren geçerli bir ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 `FLATTEN`, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kümesi işleçlerinden biridir. Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kümesi işleçleri soldan sağa değerlendirilir. @No__t-1 kümesi işleçleri için öncelik bilgisi [hariç](except-entity-sql.md) bölümüne bakın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu, bir koleksiyon koleksiyonunu düzleştirilmiş bir koleksiyona dönüştürmek için `FLATTEN` işlecini kullanır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-sql[DP EntityServices Concepts#FLATTEN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#flatten)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL başvurusu](entity-sql-reference.md)
