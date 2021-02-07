---
description: Hakkında daha fazla bilgi edinin:. (Üye erişimi) (Entity SQL)
title: . (Üye erişimi) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
ms.openlocfilehash: 94833d3525c7d17cadaef15065b3dcbdb43a6ded
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739384"
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
