---
title: DÜZLEŞTIR (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
ms.openlocfilehash: 36ae2b2b1264150bc66d09366ee33723ed7b28a8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166714"
---
# <a name="flatten-entity-sql"></a>DÜZLEŞTIR (Entity SQL)

Bir koleksiyon koleksiyonunu düzleştirilmiş bir koleksiyona dönüştürür. Yeni koleksiyon eski koleksiyonla aynı öğeleri, ancak iç içe bir yapı olmadan içerir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```sql  
FLATTEN ( collection )  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `collection`  
 Tek bir koleksiyonda düzleştirmek için bir değer koleksiyonları koleksiyonu döndüren geçerli bir ifade.  
  
## <a name="remarks"></a>Açıklamalar  

 `FLATTEN` , [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ayarlanan işleçlerden biridir. Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] küme işleçleri soldan sağa değerlendirilir. Bkz. set işleçleri için öncelik bilgileri [hariç](except-entity-sql.md) [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .  
  
## <a name="example"></a>Örnek  

 Aşağıdaki Entity SQL sorgusu, bir koleksiyon `FLATTEN` koleksiyonunu düzleştirilmiş bir koleksiyona dönüştürmek için işlecini kullanır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :  
  
 [!code-sql[DP EntityServices Concepts#FLATTEN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#flatten)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
