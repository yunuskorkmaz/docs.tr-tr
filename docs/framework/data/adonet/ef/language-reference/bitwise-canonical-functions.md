---
title: Bit düzeyinde kurallı işlevleri
ms.date: 03/30/2017
ms.assetid: 993868ca-16e3-47b6-9915-c29cd63b0a21
ms.openlocfilehash: df3b81a47b8e1202884a5c38f55c7061279b245f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="bitwise-canonical-functions"></a>Bit düzeyinde kurallı işlevleri
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] bit düzeyinde kurallı işlevler içerir.  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki tabloda bitwise gösterilmektedir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevleri. Bu işlevler döndürülecek `Null` varsa `Null` giriş sağlanır. İşlev dönüş türü, bağımsız değişken türleri ile aynıdır. İşlev birden fazla bağımsız değişkeni alır, bağımsız değişkenleri aynı türde olmalıdır. Farklı türleri arasında bit düzeyinde işlemler gerçekleştirmek için aynı açıkça türe gerekir.  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|`BitWiseAnd (` `value1` `,`  `value2` `)`|Bit düzeyinde birlikte, döndürür `value1` ve `value2` türü olarak `value1` ve `value2`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `Byte`, `Int16`, `Int32`, ve `Int64`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns 1.`<br /><br /> `BitWiseAnd(1,3)`|  
|`BitWiseNot (` `value` `)`|Bit düzeyinde değilleme işlemi döndürür `value`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `Byte`, `Int16`, `Int32`, ve `Int64`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns -4.`<br /><br /> `BitWiseNot(3)`|  
|`BitWiseOr (` `value1` `,`  `value2` `)`|Bit düzeyinde ayrım, döndürür `value1` ve `value2` türü olarak `value1` ve `value2`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `Byte`, `Int16`, `Int32` ve `Int64`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns 3.`<br /><br /> `BitWiseOr(1,3)`|  
|`BitWiseXor (` `value1` `,`  `value2` `)`|Bit düzeyinde özel ayrım, döndürür `value1` ve `value2` türü olarak `value1` ve `value2`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `Byte`, `Int16`, `Int32` ve `Int64`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns 2.`<br /><br /> `BitWiseXor (1,3)`|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kurallı İşlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
