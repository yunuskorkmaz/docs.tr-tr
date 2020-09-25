---
title: Burada (Entity SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: 1907b8786622d3c8019c75916f997c830cc07cfb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91180965"
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
