---
title: . (Üye erişimi) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
ms.openlocfilehash: 82cd2f17b2b5ea484a8202b50619047b428fe94a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192158"
---
# <a name="-member-access-entity-sql"></a>. (Üye erişimi) (Entity SQL)

Nokta işleci (.) [!INCLUDE[esql](../../../../../../includes/esql-md.md)] üye erişim işleçtir. Yapısal kavramsal model türü örneğinin bir özelliğinin veya alanının değerini elde etmek için üye erişim işlecini kullanırsınız.  
  
## <a name="syntax"></a>Söz dizimi  
  
```sql  
expression.identifier  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `expression`  
 Yapısal kavramsal model türünün bir örneği.  
  
 `identifier`  
 Bir nesne örneğine ait olan özellik veya alan.  
  
## <a name="remarks"></a>Açıklamalar  

 Nokta (.) işleci bir kayıttaki alanları ayıklamak için, karmaşık veya varlık türünün özelliklerinin ayıklanmasına benzer şekilde kullanılabilir. Örneğin, tür adı n, kişi türünde bir üyesiyse ve p, kişi türünde bir örnek ise p. n, tür adı değeri veren yasal bir üye erişim deyimidir.  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
