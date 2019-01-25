---
title: biçimindeki telefon numarasıdır. (Üye erişimi) (Varlık SQL)
ms.date: 03/30/2017
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
ms.openlocfilehash: e2874e5bff8d8c34f700a81bf52c6729df49aca5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54626680"
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
