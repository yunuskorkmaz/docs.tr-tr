---
title: ANAHTAR (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
ms.openlocfilehash: 14c0b5d273b26c71c9c63e8bbbcef863ac95a5f3
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319708"
---
# <a name="key-entity-sql"></a>ANAHTAR (Entity SQL)
Başvurunun veya bir varlık ifadesinin anahtarını ayıklar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```sql  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Bir varlık anahtarı, belirtilen varlık veya varlık başvurusunun doğru sırasındaki anahtar değerlerini içerir. Birden çok varlık kümesi aynı türe dayanabileceğinden, her bir varlık kümesinde aynı anahtar görünebilir. Benzersiz bir başvuru almak için `REF` kullanın. ANAHTAR işlecinin dönüş türü, varlığın her anahtarı için aynı sırada bir alan içeren bir satır türüdür.  
  
 Aşağıdaki örnekte, Key işleci, BadOrder varlığına bir başvuru geçirmiştir ve bu başvurunun anahtar bölümünü döndürür. Bu durumda, `Id` özelliğine karşılık gelen tam bir alan içeren bir kayıt türü.  
  
```sql  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )   
from LOB.Orders as o  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Entity SQL sorgusu, tür başvurusuyla bir ifadenin anahtar bölümünü ayıklamak için anahtar işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:  
  
 [!code-sql[DP EntityServices Concepts#KEY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#key)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
- [CREATEREF](createref-entity-sql.md)
- [REF](ref-entity-sql.md)
- [DEREF](deref-entity-sql.md)
