---
title: biçimindeki telefon numarasıdır. (Üye erişimi) (Varlık SQL)
ms.date: 03/30/2017
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
ms.openlocfilehash: 6ebedd2b381d035d199e151f64632acf7d502ff5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139717"
---
# <a name="-member-access-entity-sql"></a>biçimindeki telefon numarasıdır. (Üye erişimi) (Varlık SQL)
Nokta işleci (.), [!INCLUDE[esql](../../../../../../includes/esql-md.md)] üye erişimi işleci. Üye erişim işleci, bir özellik veya alan yapısal kavramsal model türünün bir örneğinin değerini elde etmek üzere kullanın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
expression.identifier  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Yapısal kavramsal model türünün bir örneği.  
  
 `identifier`  
 Bir özellik veya alan bir nesne örneğine ait.  
  
## <a name="remarks"></a>Açıklamalar  
 Nokta (.) işleci, karmaşık veya varlık türünün özelliklerini ayıklanması için benzer bir kaydın alanlarını ayıklamak için kullanılabilir. Örneğin, tür adı n kişi türündeki bir üyesi olduğundan ve p kişi türünün bir örneği p.n adı türünde bir değer döndüren bir yasal üye erişim ifadesi olan.  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
