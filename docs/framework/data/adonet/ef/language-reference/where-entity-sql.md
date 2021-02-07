---
description: 'Hakkında daha fazla bilgi edinin: (Entity SQL)'
title: Burada (Entity SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: e094a93927f6ac77aef772654f1d8d4fcf999cbd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712876"
---
# <a name="where-entity-sql"></a>Burada (Entity SQL)

WHERE yan tümcesi [from](from-entity-sql.md) yan tümcesinden sonra doğrudan uygulanır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```sql  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `expression`  
 Boolean türü.  
  
## <a name="remarks"></a>Açıklamalar  

 WHERE yan tümcesi Transact-SQL için açıklananla aynı semantiğe sahiptir. Kaynak koleksiyonlarının öğelerini koşulu geçecek olanlarla sınırlayarak sorgu ifadesi tarafından üretilen nesneleri kısıtlar.  
  
```sql  
select c from cs as c where e  
```  
  
 İfade, `e` Boolean türünde olmalıdır.  
  
 WHERE yan tümcesi FROM yan tümcesinden sonra ve herhangi bir gruplandırma, sıralama veya projeksiyon gerçekleşmeden önce uygulanır. FROM yan tümcesinde tanımlanan tüm öğe adları WHERE yan tümcesinin ifadesi tarafından görülebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
- [Sorgu İfadeleri](query-expressions-entity-sql.md)
