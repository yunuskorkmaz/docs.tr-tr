---
title: ANAHTAR (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
ms.openlocfilehash: 07160467dcee60377e3ef448fdc66092da4e06e7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161977"
---
# <a name="key-entity-sql"></a>ANAHTAR (Entity SQL)

Başvurunun veya bir varlık ifadesinin anahtarını ayıklar.  
  
## <a name="syntax"></a>Syntax  
  
```sql  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a>Açıklamalar  

 Bir varlık anahtarı, belirtilen varlık veya varlık başvurusunun doğru sırasındaki anahtar değerlerini içerir. Birden çok varlık kümesi aynı türe dayanabileceğinden, her bir varlık kümesinde aynı anahtar görünebilir. Benzersiz bir başvuru almak için kullanın `REF` . ANAHTAR işlecinin dönüş türü, varlığın her anahtarı için aynı sırada bir alan içeren bir satır türüdür.  
  
 Aşağıdaki örnekte, Key işleci, BadOrder varlığına bir başvuru geçirmiştir ve bu başvurunun anahtar bölümünü döndürür. Bu durumda, özelliğine karşılık gelen tam bir alan içeren bir kayıt türü `Id` .  
  
```sql  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )
from LOB.Orders as o  
```  
  
## <a name="example"></a>Örnek  

 Aşağıdaki Entity SQL sorgusu, tür başvurusuyla bir ifadenin anahtar bölümünü ayıklamak için anahtar işlecini kullanır. Sorgu AdventureWorks Sales modelini temel alır. Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:  
  
1. [Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.  
  
2. Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :  
  
 [!code-sql[DP EntityServices Concepts#KEY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#key)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
- [CREATEREF](createref-entity-sql.md)
- [REF](ref-entity-sql.md)
- [DEREF](deref-entity-sql.md)
