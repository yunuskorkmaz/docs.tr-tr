---
title: biçimindeki telefon numarasıdır. (Üye erişimi) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
ms.openlocfilehash: 8e63caba9e9efb91d5c4629b9da0b1feca905ace
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319656"
---
# <a name="-member-access-entity-sql"></a>biçimindeki telefon numarasıdır. (Üye erişimi) (Entity SQL)
Nokta işleci (.) [!INCLUDE[esql](../../../../../../includes/esql-md.md)] üye erişim işleçtir. Yapısal kavramsal model türü örneğinin bir özelliğinin veya alanının değerini elde etmek için üye erişim işlecini kullanırsınız.  
  
## <a name="syntax"></a>Sözdizimi  
  
```sql  
expression.identifier  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Yapısal kavramsal model türünün bir örneği.  
  
 `identifier`  
 Bir nesne örneğine ait olan özellik veya alan.  
  
## <a name="remarks"></a>Açıklamalar  
 Nokta (.) işleci bir kayıttaki alanları ayıklamak için, karmaşık veya varlık türünün özelliklerinin ayıklanmasına benzer şekilde kullanılabilir. Örneğin, tür adı n, kişi türünde bir üyesiyse ve p, kişi türünde bir örnek ise p. n, tür adı değeri veren yasal bir üye erişim deyimidir.  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
