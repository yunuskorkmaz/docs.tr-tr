---
title: Burada (Entity SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: b551d15d7de2cf07afc7455b7fd0a0faf6436ccf
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319177"
---
# <a name="where-entity-sql"></a>Burada (Entity SQL)
WHERE yan tümcesi [from](from-entity-sql.md) yan tümcesinden sonra doğrudan uygulanır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```sql  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Boolean türü.  
  
## <a name="remarks"></a>Açıklamalar  
 WHERE yan tümcesi Transact-SQL için açıklananla aynı semantiğe sahiptir. Kaynak koleksiyonlarının öğelerini koşulu geçecek olanlarla sınırlayarak sorgu ifadesi tarafından üretilen nesneleri kısıtlar.  
  
```sql  
select c from cs as c where e  
```  
  
 @No__t-0 ifadesi Boolean türünde olmalıdır.  
  
 WHERE yan tümcesi FROM yan tümcesinden sonra ve herhangi bir gruplandırma, sıralama veya projeksiyon gerçekleşmeden önce uygulanır. FROM yan tümcesinde tanımlanan tüm öğe adları WHERE yan tümcesinin ifadesi tarafından görülebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
- [Sorgu İfadeleri](query-expressions-entity-sql.md)
